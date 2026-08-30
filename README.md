# LinkedIn Auto-Publisher & Weekly Report

Publishes scheduled LinkedIn posts and rolls engagement into a weekly top-post Slack report.

![n8n](https://img.shields.io/badge/-n8n-333?style=flat-square) ![LinkedIn API](https://img.shields.io/badge/-LinkedIn%20API-333?style=flat-square) ![Slack](https://img.shields.io/badge/-Slack-333?style=flat-square)
![n8n](https://img.shields.io/badge/n8n-workflow-EA4B71?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

---

**[Open the visual project page →](./index.html)**

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Workflow](#workflow)
- [Tech Stack](#tech-stack)
- [Demo status](#demo-status)
- [Setup](#setup)
- [Repository Structure](#repository-structure)
- [Disclaimer](#disclaimer)

## Overview

**Trigger:** Webhook (LinkedIn schedule: content, media_url, scheduled_time)

Publishes scheduled LinkedIn posts and rolls engagement into a weekly top-post Slack report.

### Key Features

- Time-gated scheduled publishing
- Engagement tracking (reactions/comments/shares)
- Weekly top-post reporting

## Architecture

The diagram below represents the sanitized template flow. External services, credentials, and environment-specific identifiers must be configured before execution.

```mermaid
flowchart TD
    A["Queued LinkedIn post trigger"] --> B{"Scheduled time reached?"}
    B -->|No| C["Leave queued"]
    B -->|Yes| D["Publish through UGC Posts API"]
    D --> E["Store post ID"]
    E --> F["Wait 24 hours"]
    F --> G["Fetch engagement metrics"]
    G --> H["Post top-post summary to Slack"]
```

## Workflow

1. LinkedIn schedule trigger receives the queued post
2. Check whether the current time matches the scheduled time
3. At the right time: publish via the LinkedIn UGC Posts API and track the post ID
4. Wait 24 hours, then fetch reactions, comments, and shares
5. Post a weekly top-post summary to Slack

## Tech Stack

- n8n
- LinkedIn API
- Slack

## Demo status

A configured live-run recording is not included yet. Credentials and service identifiers remain placeholders.


## Setup

1. Import `workflow/T27_LinkedIn_Auto_Publisher.json` into your n8n instance (**Workflows → Import from File**).
2. Replace every placeholder credential/URL in the workflow (e.g. `YOUR_..._API_KEY`, `YOUR_..._URL`) with your own service credentials.
3. Activate the workflow and point the relevant integration (webhook source, scheduled trigger, etc.) at the generated webhook URL.
4. Test with a sample payload before going live.

## Repository Structure

```text
.
├── index.html
├── README.md
├── LICENSE
├── .gitignore
└── workflow/
    └── T27_LinkedIn_Auto_Publisher.json
```


## Disclaimer

This workflow was built as a portfolio/template project to demonstrate n8n workflow automation and AI integration. API credentials and sensitive configuration have been removed before publication — replace all `YOUR_..._KEY` / `YOUR_..._URL` placeholders with your own before use.

---

Designed and engineered by

**Oyekola Ololade**

AI Systems & Integration Engineer

- LinkedIn: <http://linkedin.com/in/ololade-oyekola-5b1797397>
- Email: <oyekolaololade69@gmail.com>
