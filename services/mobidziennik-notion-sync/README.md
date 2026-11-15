# MobiDziennik to Notion Sync

A Python script that pulls homework and test schedules from the MobiDziennik school portal and syncs them to a Notion database. It runs on a Debian LXC container in Proxmox.

## Tech stack

* **Language:** Python 3
* **Libraries:** `requests`, `beautifulsoup4`, `python-dotenv`
* **APIs:** Notion API
* **Deployment:** Debian 12 LXC (Proxmox VE)
* **Automation:** cron

## How it works

1. **Authentication:** Logs in using `requests.Session()` to store and manage authentication cookies.
2. **Extraction:** Parses MobiDziennik's HTML with BeautifulSoup to pull assignment data from specific table rows.
3. **Date formatting:** Converts Polish text dates (like "19 lis 2026") into the ISO 8601 format (`2026-11-19`) required by Notion.
4. **Notion sync:** Maps the parsed data to Notion's property schema and pushes it to the database via POST request.
5. **Automation:** A cron job runs the script daily at 17:00 and logs output to `/var/log/mobidziennik.log`.

*Note: I used AI to help write the scraping logic and API formatting. I handled the Proxmox deployment, security, debugging, and cron automation manually.*

## Setup

The script uses environment variables for credentials so you don't have to hardcode them.

1. Clone the repository and navigate to the project directory.
2. Create a virtual environment and install the dependencies:
```bash
python3 -m venv venv
source venv/bin/activate
pip install requests beautifulsoup4 python-dotenv
```

3. **Set up the credentials:**
Copy the template file to create your local environment file:
```bash
cp .env.example .env
```
Open the new `.env` file and add your MobiDziennik login details and your Notion API `ntn_` secret.

4. **Test the pipeline manually:**
```bash
python3 scraper.py
```

5. **Schedule the daemon:**
Open your cron table (`crontab -e`) and add this line to execute the script daily at 17:00:
```bash
0 17 * * * cd /path/to/your/repo && /path/to/your/repo/venv/bin/python3 scraper.py >> /var/log/mobidziennik.log 2>&1
```
