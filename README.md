# 🚀 Trump "truth" alert: The $1/mo Sentiment Tracker

![n8n](https://img.shields.io/badge/Built_with-n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![OpenAI](https://img.shields.io/badge/AI-GPT--4o--mini-412991?style=for-the-badge&logo=openai&logoColor=white)
![Cost](https://img.shields.io/badge/Cost-<$1/mo-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

<img width="1260" height="473" alt="Screenshot 2026-08-13 at 12 44 43 PM" src="https://github.com/user-attachments/assets/fd3fcc17-2b7a-44d7-a2f3-48e48458d6e5" />


Wall Street hedge funds are reportedly paying up to **$100,000 a month** for Truth Social's new "Truth API" to get millisecond-level access to market-moving presidential posts. 

This repository contains a complete, automated Open-Source Intelligence (OSINT) pipeline that bypasses the institutional paywall and delivers structured, AI-filtered geopolitical alerts directly to your Discord server for **under $1 a month**.

## 🧠 How It Works

This is a lightweight, zero-database workflow built on [n8n](https://n8n.io/). 

1. **Automated Fetching:** Securely polls the Truth Social timeline every minute using the **BrightData Web Unlocker** to transparently bypass Cloudflare and anti-bot protections.
2. **Smart State Management:** Uses n8n's native global static data (`last_id`) to track state seamlessly, ensuring you never process duplicate posts.
3. **Regex Pre-Filtering:** A lightweight regex gatekeeper drops 90% of standard political noise immediately, keeping your OpenAI API costs at pennies per month.
4. **AI Classification:** OpenAI's `gpt-4o-mini` analyzes the context of the post, determines its relevance to global conflicts (e.g., crude oil, proxy wars, sanctions), and assigns a severity rating.
5. **Discord Alerting:** High-signal alerts are instantly dispatched to your designated Discord webhook in a clean, readable embed.

## ⏱️ Latency & Expectations
To be completely transparent: Wall Street is paying six figures for a *millisecond* advantage to feed High-Frequency Trading (HFT) bots. 

This workflow operates on a **1-minute polling cycle**. You will not use this to front-run institutional algorithms. However, if you are an independent swing trader, OSINT analyst, or community manager looking for automated sentiment alerts without paying $100,000/month, this is exactly what you need.

## 🛠️ Prerequisites

To deploy this workflow, you need active accounts with the following services:

* **[n8n Instance](https://n8n.io/):** Either Self-Hosted or n8n Cloud.
* **[BrightData Account](https://brightdata.com/):** You must set up a **Web Unlocker** zone to handle the API extraction without getting blocked.
* **OpenAI API Key:** Head to [platform.openai.com](https://platform.openai.com/) to generate an API key with active credits. *(Note: This requires an API key, NOT a $20/mo ChatGPT Plus subscription).*
* **Discord Webhook URL:** Free to generate inside any Discord server you manage.

## 🚀 Quick Start Guide

1. **Download the JSON:** Clone this repository or download the `Truth_to_Discord.json` file.
2. **Import into n8n:** Open your n8n workspace, click **Add Workflow**, select the menu in the top right, and click **Import from File**.
3. **Configure Credentials:**
   * Open the `Fetch new statuses - BrightData` node and add your BrightData HTTP Bearer token.
   * Open the `OpenAI Chat Model` node and add your OpenAI API Key.
4. **Set Your Destination:** Open the `Send discord` node and paste your Webhook URL.
5. **Activate:** Toggle the workflow to **Active** in the top right corner.

*Note: Upon the very first execution, the workflow will likely send an alert for the most recent post as it establishes its baseline `last_id`. After that, it will only trigger on net-new posts.*

## 🤝 Contributing & Customization
Want to tweak the AI to track a different macro sector (like crypto regulation or tech policy)? You can easily edit the `Extract Classification (GPT)` node to adjust the system prompt and the `Keyword Prefilter` node to change the regex triggers. 

Pull requests for workflow optimizations or alternative webhook destinations (Slack, Telegram) are welcome!

## ⚖️ Disclaimer
This project is an independent open-source tool. It is not affiliated with, endorsed by, or sponsored by Truth Social, Trump Media & Technology Group, OpenAI, or Discord. Use this software responsibly and in accordance with all applicable platform Terms of Service.
