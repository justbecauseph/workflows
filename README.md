# Workflows

## MikuExpo 2025 Ticket Status Monitor

[![MikuExpo Ticket Status Monitor](https://github.com/justbecauseph/workflows/actions/workflows/mikuexpo2025.yml/badge.svg)](https://github.com/justbecauseph/workflows/actions/workflows/mikuexpo2025.yml)

This repository includes a GitHub Actions workflow that automatically monitors the ticket status for MikuExpo 2025 (Asia) and sends notifications when the status changes.

### Features

- Checks the official [MikuExpo Asia 2025 website](https://mikuexpo.com/asia2025/) every 15 minutes.
- Uses Puppeteer to scrape the ticket status.
- Tracks status changes from current status and checkes via a cron schedule.
- Sends notifications to Slack and Telegram when status has changed.
- Commits status changes to the repository for tracking.

### How It Works

1. **Scheduled Monitoring:**  
   The workflow runs every 30 minutes and can also be triggered manually.

2. **Status Check:**  
   - Puppeteer navigates to the ticket page and scrapes the ticket status.
   - Compares the current status to the previous status stored in `previous_status.txt`.

3. **Notification:**  
   - If the status changes from previous status to something else, notifications are sent to Slack and Telegram using secrets for webhook URLs and tokens.

4. **Commit Tracking:**  
   - Updates `previous_status.txt` and commits changes to the repository.

### Setup

Add your Slack webhook URL, Telegram bot token, and Telegram chat ID as GitHub secrets:

- `SLACK_WEBHOOK_URL`
- `TELEGRAM_BOT_TOKEN`
- `TELEGRAM_CHAT_ID`

**Telegram Notification Logic:**

- Only the chat specified by `TELEGRAM_CHAT_ID` will receive notifications.
- To notify a different user or group, update the `TELEGRAM_CHAT_ID` secret with their chat ID.
- To notify multiple chats, modify the workflow to send messages to each chat ID (e.g., duplicate the Telegram notification step for each chat).

### Workflow File

See `.github/workflows/mikuexpo2025.yml` for the full workflow configuration.
