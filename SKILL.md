---
name: auto-pdf-generator
description: "Lightweight professional PDF report generator. Triggers: '生成一份精美的PDF', 'make a PDF report', '自动制作专业PDF报告', 'research and create PDF'. Performs secondary analysis, auto research if no uploads, image generation, charts, and ReportLab PDF output with QA."
---

# Auto PDF Generator (Lightweight Version)

**Core Principles**
- Secondary analysis: always do content extraction + layout optimization.
- No uploads → automatic web_search + search_images + browse_page.
- Generate visuals: use generate_image for covers/icons, matplotlib for all charts.
- Build clean professional PDF with ReportLab.
- Strict QA before final output.

## Step 0: Initial Analysis
1. Parse user request (topic, audience, style, page count, special needs).
2. Scan all uploaded files (PDF/DOCX/PPTX/images) — highest priority.
3. If zero uploads: immediately run web_search (latest reliable data), browse_page top 3-5 sources, and search_images (8-12 high-quality visuals).
4. Create a content-visual mapping table (best page placement for every image/chart).

## Step 1: Extract + Secondary Layout Analysis
**First pass (extraction)**: Use pdf/docx/pptx skills + vision to pull text, tables, image descriptions, and data.
**Second pass (layout)**: 
- Decide exact position, size, and style for every image and chart.
- Reorganize content into professional report flow (problem → data → solution → cases → conclusion).
- Output: optimized page structure + detailed layout decisions (e.g., "hero image on cover, chart on page 4 bottom 80% width").

## Step 2: Visual Asset Generation
- Use generate_image for cover backgrounds, section visuals, and 6-10 consistent theme icons (prompts: clean professional style, matching accent color).
- For every quantitative data point: generate matplotlib chart (bar/line/pie/area) as high-res PNG and embed.
- Maintain original aspect ratios and professional color scheme.

## Step 3: PDF Construction
Prepare `/home/workdir/pdf-template.py` (ReportLab + Pillow).
Build 8-15 page report following layout decisions:
1. Cover (title + hero visual + date)
2. Executive summary + table of contents
3-8. Content pages (title + bullets + image/chart + citation)
9. Visual impact page
10. Data summary (multiple charts + tables)
11. Key takeaways + icons
12. References + closing

Use ReportLab Flowables, precise positioning, embedded fonts, page numbers, and bookmarks.

## Step 4: QA & Delivery
1. Validate PDF structure and metadata with pdf skill.
2. Render 5+ preview images (cover + key pages).
3. Check for layout quality, readability, chart clarity, and contrast.
4. Fix if needed, then output final file.

**Final Deliverables**
- Professional .pdf report
- 5+ preview images
- Source list (with verification if applicable)
- Brief layout optimization notes

**Lightweight Rules**
- Always perform secondary layout analysis.
- Every number → chart.
- Professional Chinese output supported.
- Prioritize uploaded materials.
- No speculation — cite sources.

This version keeps full functionality with significantly lower token usage. Ready to use!