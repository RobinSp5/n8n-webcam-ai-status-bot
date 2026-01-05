# n8n Telegram Webcam Status Bot

This repository contains an **n8n workflow template** for a Telegram bot that provides
a live webcam status via chat commands.

The bot supports:
- 📸 Sending a live webcam image
- 🌡️ Current temperature
- 🌨️ Snow status and short-term forecast
- 🤖 AI-based image analysis (weather & people count)
- 🌙 Automatic night handling (no image analysis at night)

---

## 🛠️ Features

- `/status`
  - Sends the current webcam image
  - Shows weather interpretation based on AI image analysis
  - Displays temperature and snow forecast

- `/image`
  - Sends only the current live webcam image

- AI image analysis is **disabled at night** (22:00–05:00) and safely falls back to `DARK`.

---

## Visual Preview

<p align="center">
  <a href="https://<username>.github.io/<repo>">
    <img src="https://github.com/user-attachments/assets/3542340c-9e39-492f-9b07-904ad124d5b5"
         alt="n8n workflow preview"
         width="100%">
  </a>


---

## 🧱 Architecture Overview

- **Telegram Trigger**  
  Receives incoming bot commands

- **HTTP Request Nodes**
  - Fetch live webcam image
  - Fetch weather data (Open-Meteo)

- **AI Agent (OpenRouter)**
  - Classifies:
    - Weather condition
    - Number of people in the image

- **Custom JavaScript Logic**
  - Data normalization
  - Time-based night handling
  - Final message generation

---

## 🔧 Setup Instructions

### 1. Import Workflow
- Open n8n
- Import the provided JSON file

## 🔧 Setup Instructions

### 1. Import Workflow
- Open n8n
- Import the provided JSON file

### 2. Create Required Credentials in n8n
You must create and assign the following credentials:

- **Telegram API**
  - Create a Telegram bot via @BotFather
  - Add the credential in n8n
  - Assign it to all Telegram nodes

- **OpenRouter API**
  - Create an OpenRouter API key
  - Add it as a credential in n8n
  - Assign it to the AI Agent / Chat Model

### 3. Configure Placeholders
Replace the following values in the workflow:

- Webcam URL (HTTP Request node)
- Temperature API URL (HTTP Request node – see example **[here](https://open-meteo.com/en/docs)**)

</p>

