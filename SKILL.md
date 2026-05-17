---
name: auto-ppt-generator
description: "MANDATORY skill for generating beautiful professional PPTs. Triggers on '生成一份精美的PPT', 'make a PPT from uploaded files', '自动制作带图标的PPT', 'research and create presentation', '从资料生成演示文稿', '查找资料和照片做PPT'. PRIORITIZES optimization for ChatGPT & Codex models: uses extremely explicit 'MUST / FORCE / ALWAYS / YOU MUST' language. FORCES: (1) secondary analysis + optimal image positioning & material structure layout from user uploads; (2) full web + image search if NO uploads; (3) heavy use of generate_image for layouts/icons/visuals; (4) maximum chart utilization; (5) end-to-end PPTX generation via PptxGenJS with strict QA."
---

# Auto PPT Generator Skill — ChatGPT & Codex Optimized (强制版)

**核心强制原则（YOU MUST ALWAYS FOLLOW）**:
- **优先优化 ChatGPT & Codex**：所有指令使用最严格的“YOU MUST / FORCE / ALWAYS / MANDATORY”语言，确保在 ChatGPT / Codex / 任何模型中都能100%执行。
- **材料优先 + 二次分析**：用户提供任何材料/图片 → MUST 先深度分析 → MUST 进行二次布局分析（图片位置、结构优化、视觉流）。
- **无材料强制搜索**：如果用户未上传任何材料 → YOU MUST 立即调用 web_search + search_images + browse_page 收集可靠信息和高质量图片。
- **强制使用图像生成布局**：YOU MUST 使用 generate_image（Grok Imagine / image tools）生成自定义图标、背景、视觉元素或布局辅助图，辅助排版决策。
- **充分使用图表**：任何定量数据 → MUST 创建至少 1 个专业图表（柱状/折线/饼图/面积图），优先使用 PptxGenJS addChart。
- **最终输出**：始终生成高质量 .pptx 文件 + 预览图 + 来源说明。

## 激活与初始强制分析（Step 0 — YOU MUST 执行）
当用户请求生成 PPT 时，YOU MUST 立即执行以下强制步骤：
1. 完整解析用户需求：主题、受众、语气、风格偏好（颜色/现代/极简等）、幻灯片数量、特殊要求（图标/图表/中英双语）。
2. 扫描上下文中的**所有上传文件**（PDF/DOCX/PPTX/图片）。**优先级最高**。
3. **如果没有任何上传材料** → **FORCE** 执行完整网络研究（见 Step 2）。
4. **无论是否有材料** → 都 MUST 创建“内容-视觉映射表”（记录每段材料对应的最佳图片位置、图表类型、图标需求）。

## Step 1: 强制提取 + 二次分析用户材料与图片布局（MANDATORY）
**YOU MUST** 对用户提供的**所有材料和图片**执行两次分析：

**第一次分析（内容提取）**：
- PDF → 使用 pdf skill 或 `python -m markitdown` 提取全部文本、表格、图片描述。
- DOCX → 使用 docx skill 提取结构化内容。
- 图片 → 使用视觉能力详细描述内容、风格、适合的幻灯片位置。
- 现有 PPTX → 使用 pptx 技能解包并提取原有结构。
- 输出：结构化大纲（标题、 4-8 个核心章节、关键数据点、引用、图片列表）。

**第二次强制分析（布局与结构优化）**：
- **YOU MUST** 重新审视所有提取内容 + 每张图片。
- **强制决策每张图片的精确位置**（封面英雄图 / 章节配图 / 背景 / 图标旁 / 全出血视觉页）。
- **强制优化用户材料结构**：将原始材料重新组织成最适合视觉叙事的顺序（例如：问题→数据→解决方案→案例→展望）。
- **强制生成布局决策文档**（内部）：记录“图片A → 第3页右侧 40% 宽度，保持纵横比，添加浅色圆角背景”。
- 识别数据点 → 标记必须创建图表的位置。
- 输出：最终优化后的幻灯片结构 + 每页“图片+图表+文本”精确布局方案。

## Step 2: 无材料时强制网络资源搜索（NO UPLOADS → MANDATORY）
如果 Step 0 检测到**零上传材料**，YOU MUST 立即执行：
- 使用 `web_search`（num_results=10-15）搜索“[主题] 2026 最新可靠数据 site:.edu OR site:.gov OR site:statista.com OR site:forbes.com”。
- 使用 `browse_page` 深入前3-5个高质量来源，提取事实、统计、时间线、专家观点。
- **同步强制图片搜索**：使用 `search_images` 至少搜索 8-12 张高质量图片（英雄图、配图、背景、数据可视化参考）。
- 保存所有图片到 `/home/workdir/artifacts/images/`。
- 编译至少 3-5 个高影响力数据点 + 来源列表（用于引用页）。

## Step 3: 强制视觉资产生成（图像生成布局 + 图标 + 图表）
**YOU MUST** 最大化使用图像工具：

- **布局辅助生成**：对关键幻灯片（封面、视觉冲击页、总结页），使用 `generate_image` 创建“专业排版参考图”或“增强背景/装饰元素”（提示词必须包含“clean professional layout, balanced composition, modern corporate style, high resolution”）。
- **自定义图标（绘制图标强制）**：为每个核心概念生成 1-2 个主题一致的扁平/线稿图标（提示词示例：“minimalist line icon of [概念], single accent color #2563EB, transparent background, 512x512, business professional”）。至少生成 6-10 个图标。
- **图表强制使用**：所有数值数据必须用 PptxGenJS `addChart` 实现（柱状图优先展示对比，折线图展示趋势，饼图展示占比）。每个数据幻灯片至少 1 个图表，图表样式与模板色彩完全一致。
- 所有图片/图标必须**严格保持原始宽高比**，使用 `sizing: {type: 'contain'}` 或 `cover`。

## Step 4: 强制模板选择与颜色覆盖
- 使用 `python3 /root/.grok/skills/pptx/scripts/search_templates.py` 搜索最匹配模板（关键词包含用户风格 + “modern” + “clean” + “icon friendly”）。
- **YOU MUST** 挑选视觉最优模板（而非第一个）。
- 复制模板并**强制覆盖颜色**（如果用户指定颜色或从材料中提取主色）。
- 准备最终 JS 文件：`/home/workdir/ppt-template.js`。

## Step 5: 强制构建 PPT（使用优化后的布局方案）
**YOU MUST** 严格按照 Step 1 第二次分析产生的“布局决策”构建：

标准强制结构（可根据二次分析调整）：
1. 封面：大标题 + 副标题 + 英雄图片/大图标 + generate_image 生成的装饰元素。
2. 目录/执行摘要：带图标的 4-6 项 + 小图表（如适用）。
3-7. 内容页：每页严格遵循“标题 + 3-5 精炼要点 + 右侧/背景图片（位置按二次分析） + 至少 1 个图表（如有数据）”。
8. 视觉冲击页：全出血 generate_image 或搜索图片 + 叠加关键洞见。
9. 关键收获：编号列表 + 配套图标。
10. 致谢/Q&A：来源列表 + 联系方式 + 最终图标。

使用 PptxGenJS 最佳实践 + 所有图片/图标/图表按精确坐标和尺寸放置。
生成命令：`node /home/workdir/ppt-template.js`

## Step 6: 强制 QA 与最终输出
YOU MUST 执行完整 pptx 技能 QA 流程（不可跳过任何一步）：
1. unpack → check_overlaps.py --fix → detect_fonts.py
2. render_slides.py 生成所有幻灯片预览图
3. 人工视觉检查（无重叠、无溢出、图片位置正确、图表清晰、图标锐利、对比度 ≥4.5:1、无占位符）
4. 必要时迭代修复（修改 JS → 重新生成 → 重新 QA）
5. 最终文件输出到 `/home/workdir/artifacts/[主题]_专业演示文稿.pptx`

**交付内容**（强制提供）：
- 最终 .pptx 文件路径
- 5 张幻灯片预览图
- 研究来源列表（如使用网络搜索）
- “布局优化说明”（简要说明如何放置图片和优化结构）

## 特殊强制规则
- **中文内容**：完全支持，自然中文表达。
- **数据图表优先**：任何数字 → 必须用图表呈现，禁止纯文字堆砌。
- **无材料场景**：100% 执行 Step 2 网络+图片搜索。
- **图片位置决策**：所有图片必须有明确、合理的幻灯片位置记录在二次分析中。
- **隐私**：本地处理，绝不外传敏感文件。

**此 Skill 确保**：无论用户是否提供材料，都能通过强制二次分析、强制图像生成、强制图表、强制网络搜索，产出**视觉极致、专业、数据驱动、布局完美的 PPT**。每一步均为 MANDATORY，不可省略。

现在 Skill 已完全按照您的“强制要求”升级完毕，ChatGPT/Codex 风格的极致显式指令已内置。随时使用！🚀