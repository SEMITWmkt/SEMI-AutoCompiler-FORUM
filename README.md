Web Deployment Automation Compiler (SEMI Taiwan)

A high-performance, frontend-based automation compiler engineered to transform unstructured, multi-dimensional spreadsheet data into standardized, brand-compliant digital assets for SEMICON Taiwan.

Current production version: v9.13

CP Team Chinese user guide:

- [CP_User_Guide_zh-TW.md](CP_User_Guide_zh-TW.md)

Operational usage:

1. Open `index.html` in a browser or through the GitHub Pages deployment.
2. Choose the correct source type first: Excel data, or non-Excel Word/text content.
3. Review and complete forum metadata, topic, outline, people, registration links, venue, and logos.
4. Use the logo controls to normalize inconsistent vendor-provided assets.
5. Generate Chinese and English HTML.
6. Copy the generated code into the corresponding Drupal page.

Workflow separation:

- General forum editing and partner forum editing are separated in Step 2.
- General forum mode hides partner-only fields to reduce CP Team editing noise.
- Partner forum mode hides CP Excel-specific people and output option controls, while keeping shared design output.
- The generator defines the required editing workflow; source teams should provide clean data that fits the workflow rather than expecting the page editor to absorb every inconsistent source format.

Excel input resilience:

- Excel parsing is header-based where possible, not tied only to fixed column positions.
- Required recognizable headers include Registration, Time, Forum, 論壇名稱, Venue, 中文地點, plus optional Theme, 中文連結, 英文連結.
- Repeated section headers may omit some labels; missing header positions inherit from the previous complete header row.
- Current supported source is Program-at-a-glance(L), but future sheets should preserve clear header names to remain compatible.

Partner forum mode:

- A dedicated non-Excel Word/text input path is available in Step 1.
- Use this mode for externally provided or co-hosted forum content that does not come from the CP Excel sheet.
- Topic and outline are shown directly instead of being collapsed in an accordion.
- URLs and email addresses in outlines and registration notes are automatically converted into clickable links.
- Partner organization text links can be published first, then replaced or supplemented with logos later.
- Partner organizations with the same role, such as multiple co-organizers, are grouped under one role label while keeping each organization as its own clickable link.
- If AI accidentally repeats the role label as the organization name, the generator prevents that label from being published as the visible organization name and repairs known partner URLs when possible.
- Banquet registration and association website links stay inside the provided text/remarks instead of being extracted as standalone related-link buttons.

Logo output layout:

- Desktop output uses a compact five-column logo grid.
- Mobile output uses a compact four-column logo grid.
- Logo section labels use compact, content-width spacing to keep the output flatter.
- Co-branded logos span two grid slots to preserve readability for wide assets.

Important handover notes:

- Drafts are currently stored in browser `localStorage`, so they are tied to the same browser, computer, and deployed URL.
- Do not commit API keys, vendor-private assets, or unpublished internal content to GitHub.
- Keep the deployed GitHub Pages URL stable when possible, because changing the URL can make existing browser drafts unavailable.
- Future recommended improvement: add project JSON export/import so CP Team can move work across computers and handovers safely.

This project demonstrates the transition from a highly manual, error-prone content management workflow into a fully automated, zero-defect generation pipeline.

1. The Business Pain Point

Prior to this automation, the web deployment process for major international forums relied heavily on manual data entry and hardcoding. This legacy approach created several critical operational bottlenecks:

Unstructured Data at Scale: Handling dynamic inputs (pricing tiers, schedules, dynamic anchor links, speaker profiles) from 150+ vendors and stakeholders.

High Error Rates: Manual copy-pasting into legacy CMS (Drupal) architectures resulted in frequent data misalignment and formatting breakages.

Inconsistent Visual Identity: Lack of standardized UI templates led to severe UX degradation and visual inconsistencies (the "layer cake" effect of conflicting CSS/blocks).

Cross-Functional Overhead: Excessive communication back-and-forth between operational teams and developers to fix minor typographical or layout errors, draining hundreds of operational hours.

2. The Solution

Architected and deployed an end-to-end HTML/JS-based compiler that instantly parses and structures diverse, chaotic inputs into production-ready digital assets.

Zero-Defect Automated Pipeline: Replaces the manual copy-paste workflow entirely. The compiler features a robust CSV parsing engine equipped with quote/comma storm protection, ensuring 100% data alignment regardless of raw input formatting.

Brand-Compliant Standardization: Generates strictly structured, responsive UI components (e.g., dynamic accordions, pricing tables, inline-flex anchor navigation) that seamlessly inject into the existing CMS without CSS pollution.

Native DOM Interception: Implemented smart JavaScript triggers that automatically detect CMS environments and activate cross-section navigation (e.g., Speaker and Agenda buttons) only when the respective content exists, eliminating dead links.

3. Development & AI-Assisted Agile Approach (敏捷開發與 AI 協作)

This tool was designed with a ruthless focus on efficiency, utilizing modern development paradigms:

100% Frontend Architecture: Built entirely with vanilla HTML, CSS, and JavaScript. Zero backend dependencies, meaning it is instantly deployable, globally accessible via a browser, and requires zero server maintenance.

AI-Driven Prompt Engineering: Leveraged advanced AI-assisted tooling (LLMs) to radically accelerate the development cycle.

Rapid Prototyping & Iteration: Utilized high-level prompt architecture to instantly debug complex logic (e.g., multi-dimensional array mapping, regex edge cases), refactor UI for visual downgrade (UI minimalism), and push continuous deployment (CI/CD mindset) from v1.0 to a rock-solid v8.3.

Operational Empowerment: The final product strips away engineering complexity for the end-user, returning absolute control and speed to the operations team.

Developed for SEMI Taiwan to optimize internal operations and scale digital deployment capabilities.
