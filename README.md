# workflows

## MikuExpo 2025 Ticket Status Monitor

This repository includes a GitHub Actions workflow that automatically monitors the ticket status for MikuExpo 2025 (Asia) and sends notifications when tickets become available.

### Features

- Checks the official [MikuExpo Asia 2025 website](https://mikuexpo.com/asia2025/) every 30 minutes.
- Uses Puppeteer to scrape the ticket status.
- Tracks status changes from "Coming Soon" to available.
- Sends notifications to Slack and Telegram when tickets are available.
- Commits status changes to the repository for tracking.

### How It Works

1. **Scheduled Monitoring:**  
   The workflow runs every 30 minutes and can also be triggered manually.

2. **Status Check:**  
   - Puppeteer navigates to the ticket page and scrapes the ticket status.
   - Compares the current status to the previous status stored in `previous_status.txt`.

3. **Notification:**  
   - If the status changes from "Coming Soon" to something else, notifications are sent to Slack and Telegram using secrets for webhook URLs and tokens.

4. **Commit Tracking:**  
   - Updates `previous_status.txt` and commits changes to the repository.

### Setup

- Add your Slack webhook URL, Telegram bot token, and chat ID as GitHub secrets:
  - `SLACK_WEBHOOK_URL`
  - `TELEGRAM_BOT_TOKEN`
  - `TELEGRAM_CHAT_ID`

### Workflow File

See `.github/workflows/mikuexpo2025.yml` for the full workflow configuration.