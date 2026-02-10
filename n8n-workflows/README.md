# N8N Workflows — The Hardware Marketing Brief

## Import Instructions
1. Go to https://n8n.ridleyserver.com
2. Click **Add Workflow** → **Import from File**
3. Import each JSON file below

## Workflows

### 01 - TechCrunch Hardware Scraper
- **Schedule:** Daily 6am ET
- **Sources:** TechCrunch Hardware RSS
- **What it does:** Pulls TC hardware articles, filters for funding/hardware keywords
- **Output:** Google Sheets (configure credentials) or manual review

### 02 - Crunchbase & Funding Monitor
- **Schedule:** Daily 7am ET
- **Sources:** Crunchbase News RSS + TechCrunch Funding RSS
- **What it does:** Monitors both feeds, filters for hardware/deeptech, extracts funding amounts and round types, deduplicates
- **Output:** JSON file per day (configure output node)

### 03 - LinkedIn & Industry News Monitor
- **Schedule:** Daily 8am ET
- **Sources:** Google News (3 targeted queries):
  - "hardware startup funding" (past 7 days)
  - "robotics startup raised OR funding" (past 7 days)
  - "series a/b hardware OR deeptech OR climatetech" (past 7 days)
- **What it does:** Aggregates news across sources, deduplicates, extracts funding data, generates digest email
- **Output:** Email digest (configure SMTP credentials)

## Setup Checklist
- [ ] Import all 3 workflows
- [ ] Configure Google Sheets credentials (workflow 01)
- [ ] Configure SMTP/email credentials (workflow 03)
- [ ] Optionally connect Crunchbase API (if you have a key — replaces RSS approach)
- [ ] Activate workflows
- [ ] Test each workflow manually first (click "Execute Workflow")

## Notes
- LinkedIn doesn't offer public RSS, so we use Google News as a proxy for LinkedIn-shared funding announcements
- Crunchbase's API requires a paid plan ($29/mo) for full funding data — RSS gives us the news feed for free
- Disabled output nodes (marked with ⏸) need credentials configured before enabling
- All times are ET (America/New_York timezone set in N8N)
