# 🎬 AI ASMR Video Generator

### End-to-End AI Video Generation & Social Media Publishing Automation

An n8n workflow designed to automate AI-assisted ASMR video creation, from prompt generation to video processing and social media publishing.

## 📸 Workflow Overview

![AI ASMR Video Generator Workflow](AI%20video%20generator.png)

## 🎯 Project Objective

Demonstrate how AI services and workflow automation can be integrated to reduce repetitive tasks involved in short-form video content production.

The workflow connects AI prompt generation, video generation APIs, asynchronous job monitoring, validation, and publishing into a single automated process.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow orchestration and scheduling |
| Google Vertex AI | AI-assisted prompt generation |
| Google Veo | AI video generation |
| REST APIs | Communication with external services |
| JWT / OAuth | API authentication |
| JavaScript | Workflow logic and data preparation |
| YouTube API | Video publishing |
| Facebook Graph API | Video publishing |

## ⚙️ How It Works

1. **Scheduled Trigger:** Starts the automation on a configured schedule.
2. **AI Prompt Generation:** Uses Google Vertex AI and structured output parsing to generate video prompts, titles, and descriptions.
3. **Authentication:** Prepares service-account authentication and exchanges a signed JWT for an access token.
4. **Video Generation:** Sends the generated prompt to the Google Veo API to request a vertical ASMR video.
5. **Asynchronous Monitoring:** Waits and polls for completion of the video-generation operation.
6. **Validation:** Checks generation status, compliance-related responses, and error conditions.
7. **Video Processing:** Converts the returned video data into a file.
8. **Publishing:** Routes the generated video to YouTube and Facebook publishing integrations.

## 💡 Technical Highlights

- AI prompt engineering with structured JSON outputs
- REST API integrations and JWT-based authentication
- Asynchronous processing and polling logic
- Conditional branching and response validation
- Binary file conversion
- Multi-platform publishing workflow design

## 📁 Project Files

- [View Workflow JSON](ASMR_Video_Generator_GitHub_Safe.json)
- [View Workflow Screenshot](AI%20video%20generator.png)

## 🔐 Security & Setup Notes

This repository contains a sanitized portfolio version of the workflow. Credentials and project-specific authentication details must be configured separately before execution.

To explore the workflow:

1. Download the JSON file.
2. Import it into a compatible n8n environment.
3. Configure your own Google Cloud project, API permissions, and service credentials.
4. Replace the placeholder authentication configuration.
5. Connect authorized YouTube and Facebook accounts.
6. Review API settings, model availability, and publishing permissions before testing.

**Note:** The sanitized workflow is provided as a technical demonstration and is not ready to run without additional configuration.

## 🌐 About the Developer

**Alvin John Ramos** — AI Automation & Workflow Specialist

I build AI-powered workflows and integrations using n8n, Make, Zapier, JavaScript, and REST APIs.

[🌐 View My Portfolio](https://work-wit-charm.lovable.app/)
  
