# 🧠 Hacker News Job Monitor

A fully automated job monitoring system using **n8n** that scrapes the [Hacker News "Who’s Hiring"](https://news.ycombinator.com/jobs) RSS feed, extracts useful job info, deduplicates entries, and saves them into **Google Sheets** on a schedule.

---

## 🔧 What It Does

- Fetches latest job posts from Hacker News Jobs RSS (`https://hnrss.org/jobs`)
- Parses and extracts:
  - Job title
  - Company name (intelligently parsed from title)
  - Job URL
  - Posted date
  - Scraped timestamp
- Deduplicates using SQL Merge
- Saves unique jobs to Google Sheets
- Scheduled to run every 5 minutes (or as needed)

---

## 💡 Features

- 📰 RSS parsing via `XML` node
- 🧠 Company name extraction using regex + fallback logic
- 🕒 ISO timestamp conversion to readable format
- ✅ Deduplication via SQL Merge on `job URL`
- 🗓 Cron scheduling (every 5 mins or daily)
- 📄 Google Sheets integration

---

## 🛠 Tools Used

| Tool        | Purpose                        |
|-------------|---------------------------------|
| n8n         | Automation orchestration       |
| Google Sheets | Job storage & deduplication  |
| RSS Feed    | Source: Hacker News Jobs RSS   |

---

## 📁 Files

- `Hacker News Job Monitor.json`: Import this into your n8n instance
- `screenshots/`: Optional screenshots showing the workflow and output

---

## ✅ Setup Instructions

1. **Create Google Sheet** with columns:
   - `title`, `company`, `url`, `pubDate`, `scraped_at`, `clean_date`
2. **Import** the provided `.json` workflow into n8n
3. Update:
   - Google Sheets credentials
   - Spreadsheet ID and Sheet name
4. Enable the Cron node (e.g., every 5 minutes)
5. **Save** and activate the workflow

---

## 🧪 Sample Output

| Title                                                | Company     | URL                                                  | Date & Time |
|------------------------------------------------------|-------------|-------------------------------------------------------|-------------|
| MindsDB is hiring an AI solutions engineer           | MindsDB     | https://job-boards.greenhouse.io/mindsdb/...         | 2025-07-02  |
| Lago is hiring for ten roles                         | Lago        | https://www.ycombinator.com/companies/lago/jobs      | 2025-06-28  |
| Bitmovin is hiring a Junior Solutions Engineer       | Bitmovin    | https://bitmovin.com/careers/7943569002/             | 2025-06-27  |

---

## 📸 Optional Screenshots

- `screenshots/hn_gs_output.png` — sample sheet
- `screenshots/n8n_workflow.png` — visual layout

---

## 🚀 License

MIT

---

## 🙌 Author

Built by [@shooshka133](https://github.com/shooshka133)
