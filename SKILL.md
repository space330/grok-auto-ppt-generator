---
name: auto-pdf-generator
description: "MANDATORY skill for generating beautiful professional PDF reports. Triggers on '生成一份精美的PDF', 'make a PDF report from uploaded files', '自动制作专业PDF报告', 'research and create PDF report', '从资料生成PDF文稿', '查找资料和照片做PDF'. PRIORITIZES optimization for ChatGPT & Codex models: uses extremely explicit 'MUST / FORCE / ALWAYS / YOU MUST' language. FORCES: (1) secondary analysis + optimal layout & visual flow from user uploads; (2) full web + image search if NO uploads; (3) heavy use of generate_image for covers/icons/visuals; (4) maximum chart utilization (embedded as high-quality images); (5) end-to-end professional PDF generation via ReportLab with strict QA."
---

# Auto PDF Generator Skill — ChatGPT & Codex Optimized (强制版)

**核心强制原则（YOU MUST ALWAYS FOLLOW）**:
- **优先优化 ChatGPT & Codex**：所有指令使用最严格的“YOU MUST / FORCE / ALWAYS / MANDATORY”语言，确保在 ChatGPT / Codex / 任何模型中都能100%执行。
- **材料优先 + 二次分析**：用户提供任何材料/图片 → MUST 先深度分析 → MUST 进行二次布局分析（页面结构、图片位置、视觉流、章节顺序）。
- **无材料强制搜索**：如果用户未上传任何材料 → YOU MUST 立即调用 web_search + search_images + browse_page 收集可靠信息和高质量图片。
- **强制使用图像生成**：YOU MUST 使用 generate_image（Grok Imagine / image tools）生成自定义封面、图标、背景、视觉元素或布局参考图，辅助专业排版。
- **充分使用图表**：任何定量数据 → MUST 创建至少 1 个专业图表（柱状/折线/饼图/面积图），使用 matplotlib 生成高清 PNG 后嵌入 PDF。
- **最终输出**：始终生成高质量 .pdf 文件 + 多页预览图 + 来源说明 + 布局优化报告。

## 激活与初始强制分析（Step 0 — YOU MUST 执行）
当用户请求生成 PDF 报告时，YOU MUST 立即执行以下强制步骤：
1. 完整解析用户需求：主题、受众、语气、风格偏好（颜色/现代/极简/学术等）、页数范围、特殊要求（图标/图表/中英双语/封面风格）。
2. 扫描上下文中的**所有上传文件**（PDF/DOCX/PPTX/图片/表格）。**优先级最高**。
3. **如果没有任何上传材料** → **FORCE** 执行完整网络研究（见 Step 2）。
4. **无论是否有材料** → 都 MUST 创建“内容-视觉映射表”（记录每段材料对应的最佳页面位置、图表类型、图标需求、图片尺寸建议）。

## Step 1: 强制提取 + 二次分析用户材料与图片布局（MANDATORY）
**YOU MUST** 对用户提供的**所有材料和图片**执行两次分析：

**第一次分析（内容提取）**：
- PDF → 使用 pdf skill 提取全部文本、表格、图片描述。
- DOCX → 使用 docx skill 提取结构化内容。
- 图片 → 使用视觉能力详细描述内容、风格、适合的页面位置与尺寸。
- 现有 PPTX → 使用 pptx 技能解包并提取原有结构与数据。
- 输出：结构化大纲（标题、4-8 个核心章节、关键数据点、引用、图片列表、表格数据）。

**第二次强制分析（布局与结构优化）**：
- **YOU MUST** 重新审视所有提取内容 + 每张图片。
- **强制决策每张图片/图表的精确位置**（封面英雄图 / 章节配图 / 背景装饰 / 图标旁 / 全页视觉冲击页 / 数据页图表区）。
- **强制优化用户材料结构**：将原始材料重新组织成最适合专业报告叙事的顺序（例如：问题→数据分析→解决方案→案例研究→结论展望）。
- **强制生成布局决策文档**（内部）：记录“图片A → 第2页右侧 45% 宽度，保持纵横比，添加浅色边框；图表B → 第4页底部，宽度80%，高度适配”。
- 识别数据点 → 标记必须创建图表的位置。
- 输出：最终优化后的 PDF 页面结构 + 每页“标题 + 正文 + 图片/图表 + 引用”精确布局方案。

## Step 2: 无材料时强制网络资源搜索（NO UPLOADS → MANDATORY）
如果 Step 0 检测到**零上传材料**，YOU MUST 立即执行：
- 使用 `web_search`（num_results=10-15）搜索“[主题] 2026 最新可靠数据 site:.edu OR site:.gov OR site:statista.com OR site:forbes.com OR site:reuters.com”。
- 使用 `browse_page` 深入前3-5个高质量来源，提取事实、统计、时间线、专家观点、最新数据。
- **同步强制图片搜索**：使用 `search_images` 至少搜索 8-12 张高质量图片（封面英雄图、章节配图、数据可视化背景、图标参考）。
- 保存所有图片到 `/home/workdir/artifacts/images/`。
- 编译至少 3-5 个高影响力数据点 + 来源列表（用于引用页和图表）。

## Step 3: 强制视觉资产生成（图像生成 + 图标 + 图表）
**YOU MUST** 最大化使用图像工具：

- **封面与布局辅助生成**：对关键页面（封面、视觉冲击页、结论页），使用 `generate_image` 创建“专业报告封面参考图”或“增强背景/装饰元素”（提示词必须包含“clean professional corporate report layout, balanced composition, modern minimalist style, high resolution, subtle gradient, business color palette”）。
- **自定义图标（绘制图标强制）**：为每个核心概念生成 1-2 个主题一致的扁平/线稿/渐变图标（提示词示例：“minimalist line icon of [概念], single accent color #1E40AF, transparent background, 512x512, professional business style”）。至少生成 8-12 个图标。
- **图表强制使用**：所有数值数据必须用 matplotlib 生成高清专业图表（柱状图优先展示对比，折线图展示趋势，饼图展示占比，面积图展示累积），保存为 PNG 后嵌入 PDF。每个数据页面至少 1 个图表，图表样式与整体配色完全一致（使用 seaborn 或 reportlab 风格）。
- 所有图片/图标必须**严格保持原始宽高比**，使用高质量缩放。

## Step 4: 强制模板选择与颜色覆盖
- 基于用户风格偏好或材料主色，**YOU MUST** 选择最匹配的现代专业报告配色方案（主色 + 辅助色 + 强调色）。
- **强制覆盖颜色**到所有生成元素（封面、图标、图表、边框、标题）。
- 准备最终 Python 生成脚本：`/home/workdir/pdf-template.py`（使用 ReportLab + matplotlib + Pillow）。

## Step 5: 强制构建 PDF（使用优化后的布局方案）
**YOU MUST** 严格按照 Step 1 第二次分析产生的“布局决策”构建：

标准强制结构（可根据二次分析调整，推荐 8-15 页）：
1. 封面：大标题 + 副标题 + 英雄图片/大图标 + generate_image 生成的装饰背景 + 日期/作者。
2. 执行摘要/目录：带图标的 4-6 项要点 + 小型关键数据图表。
3-8. 内容页：每页严格遵循“标题 + 精炼要点（3-5 条） + 右侧/背景图片（位置按二次分析） + 至少 1 个专业图表（如有数据） + 底部引用”。
9. 视觉冲击页：全页 generate_image 或搜索图片 + 叠加 1-2 个关键洞见（大字体）。
10. 数据汇总页：多个图表并排 + 关键统计表格。
11. 关键收获：编号列表 + 配套图标 + 来源总结。
12. 参考文献与致谢：完整来源列表（带得分/验证信息，如适用） + 联系方式 + 最终图标。

使用 ReportLab 最佳实践（Canvas + Paragraph + Image + Table + Flowables） + 所有图片/图标/图表按精确坐标、尺寸、边距放置。
生成命令：`python3 /home/workdir/pdf-template.py`

## Step 6: 强制 QA 与最终输出
YOU MUST 执行完整 PDF 质量检查流程（不可跳过任何一步）：
1. 使用 pdf skill 验证页面数量、元数据、字体嵌入、无损坏。
2. 使用 Python 脚本渲染前 5 页 + 最后 2 页为高清预览图（使用 pdf2image 或等效工具，若不可用则用 reportlab 内置渲染）。
3. 人工视觉检查（无文字溢出、无图片变形、图表清晰、图标锐利、对比度 ≥4.5:1、页边距一致、页码正确）。
4. 必要时迭代修复（修改 pdf-template.py → 重新生成 → 重新 QA）。
5. 最终文件输出到 `/home/workdir/artifacts/[主题]_专业研究报告.pdf`

**交付内容**（强制提供）：
- 最终 .pdf 文件路径
- 至少 5 张页面预览图（封面 + 关键内容页 + 结论页）
- 研究来源列表（如使用网络搜索，含验证得分）
- “布局优化说明”（简要说明图片/图表放置与结构优化逻辑）
- PDF 元数据（标题、作者、主题、创建日期）

## 特殊强制规则
- **中文内容**：完全支持，自然流畅的中文专业表达，标题与正文协调。
- **数据图表优先**：任何数字 → 必须用专业图表呈现，禁止纯文字堆砌。
- **无材料场景**：100% 执行 Step 2 网络+图片搜索 + 二次分析。
- **图片位置决策**：所有图片必须有明确、合理的页面位置记录在二次分析中。
- **隐私**：本地处理，绝不外传敏感文件。
- **专业报告标准**：页码、页眉页脚、目录可点击、书签导航、嵌入字体、打印友好。

**此 Skill 确保**：无论用户是否提供材料，都能通过强制二次分析、强制图像生成、强制图表、强制网络搜索，产出**视觉极致、专业、数据驱动、布局完美的 PDF 研究报告**。每一步均为 MANDATORY，不可省略。

现在 Skill 已完全按照您的“强制要求”升级完毕，ChatGPT/Codex 风格的极致显式指令已内置。随时使用！🚀