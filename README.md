# AI ASMR Video Generator v2.0

Live Workflow Demonstration

Watch the Full Loom Walkthrough
https://www.loom.com/share/6de02ed3311642c293b457ff2630cac5

This approximately five-minute walkthrough demonstrates the 29-node n8n automation, including AI-generated structured prompts, duplicate-title detection, asynchronous Google Veo video generation, and automated publishing to YouTube and Facebook.

Video Chapters
- 00:00 — Introduction and Workflow Overview
- 01:21 — AI Prompt Generation and Video Styling
- 03:07 — Live Workflow Demonstration and Results

![Workflow Overview](assets/workflow-overview.png)

## What changed in v2.0

| Area | v2.0 capability |
|---|---|
| Prompt generation | Google Vertex AI chat model and structured JSON output |
| Duplicate prevention | Compares meaningful title keywords with titles in Google Sheets and rejected candidates |
| Regeneration | Loops back to prompt generation when a duplicate is detected, with a configured retry limit |
| Video generation | Google Veo 3.1 asynchronous generation and polling |
| Publishing | Uploads the generated MP4 to YouTube and Facebook |
| Tracking | Logs video title, execution ID, timestamp, and per-platform success/failure statuses in Google Sheets |
| Resilience | Platform upload nodes retry on failure and route errors to status updates |

## Architecture

1. Schedule trigger reads previously logged titles from Google Sheets.
2. Vertex AI generates a structured prompt, video title and description.
3. JavaScript checks title keywords against existing and rejected titles.
4. Duplicate candidates enter a bounded regeneration branch; accepted candidates proceed.
5. Google Cloud authentication and Veo 3.1 generation run through HTTP/JWT nodes.
6. Polling waits for the video operation to finish; downstream checks route errors and filtered results.
7. The video is converted from base64 to an MP4 binary.
8. YouTube and Facebook upload branches independently update their statuses in Google Sheets.

## Workflow file

[`workflow/ASMR_Video_Generator_v2_PUBLIC_TEMPLATE.json`](workflow/ASMR_Video_Generator_v2_PUBLIC_TEMPLATE.json)

**Important:** This is a **sanitized reference template**, not a ready-to-run import. Credentials, service-account payload, project identifiers and spreadsheet identifiers have been removed or replaced with placeholders. Configure authentication securely inside n8n before running. The `Secret Payload` node deliberately throws an error until it is replaced with secure credential handling. Never paste service-account private keys into public workflow files.

### Setup requirements

- n8n instance with Google Vertex AI, Google Sheets, YouTube, Facebook Graph API, JWT and HTTP Request node support
- Google Cloud project with access to the required Vertex AI and Veo model
- Secure service-account/JWT authentication configured in n8n
- Google Sheets log with columns `Video Title`, `Date & Time`, `ID`, `Facebook Status`, `YouTube Status`
- Authorized YouTube and Facebook publishing credentials
- Replace `YOUR_GOOGLE_CLOUD_PROJECT_ID`, `YOUR_SPREADSHEET_ID`, and `YOUR_SHEET_NAME` placeholders
- Verify OAuth scopes, permissions, video API availability and platform publishing policies

## Validation and limitations

A recorded execution and screenshots show successful publication of a glass-grapefruit video to YouTube and Facebook, with corresponding Success statuses in Google Sheets. This is a project demonstration, not a claim of unattended production uptime or comprehensive load testing.

Duplicate checking uses overlapping non-stopword title keywords. This is a useful heuristic but not semantic similarity detection, and it can reject different titles sharing a fruit-related keyword. The exported workflow contains a configured retry limit; test exhaustion and loop state behavior in your own n8n environment before treating it as production-hardened.

## Tools

n8n · Google Vertex AI · Google Veo 3.1 · JavaScript (n8n Code nodes) · Google Sheets · YouTube API · Facebook Graph API · JWT · HTTP requests

## Portfolio note

Built as a hands-on AI automation project, iterating from an earlier video-generation workflow to add duplicate detection, bounded regeneration and independent publishing outcomes.
