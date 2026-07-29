# Bug Bounty Radar

An automated monitoring tool that tracks new bug bounty programs and scope additions across major platforms, sending real-time notifications to Telegram via GitHub Actions.

## Overview

This repository uses scheduled GitHub Actions workflows to monitor public target data from top bug bounty platforms. When a new program or target is detected, the workflow automatically commits the updated records and sends an alert directly to your Telegram chat.

### Supported Platforms
* HackerOne
* Bugcrowd
* Intigriti
* YesWeHack
* Federacy

## Features

* **Automated Scheduling:** Runs continuously on a 30-minute interval using GitHub Actions cron jobs.
* **Serverless Architecture:** Completely automated within GitHub without requiring an external server or virtual machine.
* **Reliable Delivery:** Automatically divides large sets of new targets into manageable messages (15 items per batch) to ensure compliance with Telegram API character limits and prevent missed alerts.

## Setup Instructions

### 1. Fork the Repository
Create a personal fork of this repository to your GitHub account.

### 2. Obtain Telegram Credentials
1. Create a Telegram bot using `@BotFather` and record the generated **Bot Token**.
2. Retrieve your personal or group **Chat ID** using an ID bot (for example, `@userinfobot`).

### 3. Configure GitHub Secrets
Navigate to your repository's settings:  
**Settings** -> **Secrets and variables** -> **Actions** -> **New repository secret**

Add the following credentials:
* `TELEGRAM_BOT_TOKEN`: The API token provided by BotFather.
* `TELEGRAM_CHAT_ID`: Your numerical Telegram Chat ID.

### 4. Enable Workflows
1. Navigate to the **Actions** tab of your repository.
2. Enable workflows if prompted.
3. You may test the setup immediately by selecting the workflow and clicking **Run workflow**.

## Technical Details

The synchronization script fetches target data from the [arkadiyt/bounty-targets-data](https://github.com/arkadiyt/bounty-targets-data) repository, compares the latest entries against the local JSON files stored in the `/data` directory, and identifies programs that have not been previously recorded.

## Disclaimer

This repository is developed for educational purposes and to assist ethical security researchers. Users must adhere to the rules of engagement and defined scope of each bug bounty program.

## License

Distributed under the MIT License.