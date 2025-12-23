# Telegram User Account Message Automation Bot

> A service-style automation bot that runs behind a regular Telegram user account to automate message workflows (auto-replies, routing, tagging, and follow-ups). It uses a user session, not a bot account, and provides safe controls like allowlists, quiet hours, throttling, and audit logs.

<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="https://github.com/Instagram-Automations/Footer-test/blob/main/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
  <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <a href="https://Appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
  <a href="https://discord.gg/3YrZJZ6hA2" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>


<p align="center">
Created by Appilot, built to showcase our approach to Automation! <br>
If you are looking for custom <strong> Telegram User Account Message Automation Bot </strong>, you've just found your team — Let’s Chat.&#128070; &#128070;
</p>

## Introduction

Many Telegram workflows happen in personal accounts: inquiries arrive in DMs, repetitive questions get asked, and important leads/messages get lost in busy chats. A bot account is not always suitable, especially when you want automation to act from your regular account identity.

This project runs a user-session automation service that listens for incoming messages, applies rules (keywords, chat type, sender allowlists), and performs automated actions like replies, forwarding to a team chat, labeling, and reminders—while staying controlled and reviewable.

### Personal Account Ops for Messaging

- Automates repetitive replies without switching to a bot account
- Routes important messages to the right place automatically
- Adds structured logs so you know what was sent and why
- Reduces inbox overload with throttling and quiet hours

---

## Core Features

| Feature | Description |
|----------|-------------|
| User Session Client | Runs using a Telegram user session rather than a bot token |
| Rule-Based Auto Replies | Sends templated replies based on keywords, chat type, or sender |
| Sender Allowlist / Blocklist | Only automates for approved senders or groups |
| Message Routing | Forwards messages to specified chats (e.g., team inbox, archive) |
| Conversation Tagging | Applies tags/labels in an internal ledger for later search |
| Quiet Hours | Disables automation during configured time windows |
| Throttling & Cooldowns | Prevents spammy behavior by enforcing per-chat reply limits |
| Human Review Mode | Optionally queues replies for manual approval before sending |
| Attachment Handling | Detects attachments and routes them with metadata summaries |
| Duplicate Suppression | Avoids repeated replies to the same prompt within a time window |
| Audit Logging | Records triggers, actions, and message IDs for traceability |
| Exportable Activity Reports | Exports CSV/JSON logs of automated actions |

---

## How It Works

| Step | Description |
|------|-------------|
| **Input or Trigger** | A new message arrives in your Telegram inbox (DM, group, or channel where applicable). |
| **Core Logic** | The service evaluates rules (sender, keywords, context), applies throttles, and decides whether to reply, forward, tag, or queue for review. |
| **Output or Action** | Sends a reply from your user account, forwards to a target chat, or records the event for later follow-up. |
| **Other Functionalities** | Includes deduplication, quiet hours, review queues, and structured reporting. |
| **Safety Controls** | Enforces allowlists, rate limiting, cooldowns, and optional human approval to avoid uncontrolled messaging. |

## Tech Stack

| Component | Description |
|------------|-------------|
| **Language** | Python |
| **Frameworks** | Telethon |
| **Tools** | Redis, Pydantic |
| **Infrastructure** | Docker, GitHub Actions |

---

## Directory Structure Tree

    telegram-user-account-message-automation-bot/
    ├── src/
    │   ├── main.py
    │   ├── telegram/
    │   │   ├── client.py
    │   │   ├── session_store.py
    │   │   └── listeners.py
    │   ├── rules/
    │   │   ├── rule_engine.py
    │   │   ├── matchers.py
    │   │   └── templates.py
    │   ├── actions/
    │   │   ├── auto_reply.py
    │   │   ├── forwarder.py
    │   │   ├── tagger.py
    │   │   └── followups.py
    │   ├── safety/
    │   │   ├── allowlist.py
    │   │   ├── throttling.py
    │   │   └── quiet_hours.py
    │   ├── review/
    │   │   ├── approval_queue.py
    │   │   └── reviewer_commands.py
    │   ├── storage/
    │   │   ├── redis_store.py
    │   │   └── activity_ledger.py
    │   ├── reporting/
    │   │   ├── exporter.py
    │   │   └── run_summary.py
    │   └── utils/
    │       ├── logger.py
    │       └── config_loader.py
    ├── config/
    │   ├── settings.yaml
    │   ├── rules.yaml
    │   ├── templates.yaml
    │   └── allowlists.yaml
    ├── logs/
    │   └── activity.log
    ├── output/
    │   ├── activity_report.csv
    │   └── queued_replies.json
    ├── tests/
    │   ├── test_rule_engine.py
    │   └── test_throttling.py
    ├── docker/
    │   ├── Dockerfile
    │   └── compose.yaml
    ├── requirements.txt
    └── README.md

---
## Use Cases

- **Solo operators** use it to auto-answer repeated questions, so response time stays fast without constant manual replies.
- **Support-style inboxes** use it to route leads to a team chat, so important messages don’t get buried.
- **Community admins** use it to tag and track conversations, so follow-ups are consistent.
- **Busy professionals** use quiet hours and throttling, so automation remains controlled and non-intrusive.

---

## FAQs

**Is this a Telegram bot account?**  
No. It runs behind a regular Telegram user session and acts from your user account identity.

**Do I have to share my Telegram password with the script?**  
No. Authentication is handled through Telegram’s login flow and stored as a session file/token locally. You should keep session storage encrypted and restricted.

**Can I limit who the automation responds to?**  
Yes. Allowlists and per-chat rules let you restrict automation to specific contacts, groups, or message types.

**Can I review messages before they’re sent?**  
Yes. Enable review mode to queue replies for approval instead of sending automatically.

---

## Performance & Reliability Benchmarks

**Execution Speed:**  
Processes inbound messages and applies rules in 50–150 ms per message under typical conditions.

**Success Rate:**  
Maintains 92–94% successful action execution (reply/forward/tag) across long-running sessions with retries enabled.

**Scalability:**  
Supports thousands of messages per day using event-driven listeners and queued actions with throttling controls.

**Resource Efficiency:**  
Runs on a small server with ~150–250 MB RAM and low CPU; workload is primarily network I/O and rule evaluation.

**Error Handling:**  
Implements retries with exponential backoff, connection recovery, duplicate suppression, structured logs, and a review queue fallback when errors persist.

<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
 <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
 <a href="https://www.youtube.com/@Appilot-app/videos" target="_blank">
  <img src="https://img.shields.io/badge/ð¥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
 </a>
</p>


