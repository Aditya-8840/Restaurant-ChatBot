# 🍔 AI-Powered Restaurant WhatsApp Chatbot

An intelligent, fully automated WhatsApp chatbot designed for "MDA Restaurant". This bot leverages Google Gemini AI to handle customer inquiries, process food orders, and manage inventory seamlessly via n8n and Google Sheets.

## 🚀 Features

- **Conversational AI**: Uses the powerful **Google Gemini 3.6 Flash** model to talk naturally with customers, acting as a smart food ordering assistant.
- **WhatsApp Integration**: Listens to customer messages on WhatsApp and replies instantly using the WhatsApp Business API.
- **Order Management**: Automatically extracts order details (Customer Name, Food Item, Quantity, Date, Status) and logs them into a **Google Sheets** "Orders" database.
- **Inventory & FAQ Access**: The AI agent is equipped with tools to query your "Inventory" and "FAQ" sheets dynamically to answer customer questions accurately.
- **Contextual Memory**: Remembers the context of the conversation per user (tied to their WhatsApp number) to provide a smooth, continuous conversational experience.

## 🛠️ Architecture / Tech Stack

- **[n8n](https://n8n.io/)**: For the workflow automation and orchestration.
- **Google Gemini (PaLM) API**: Serves as the AI brain of the chatbot.
- **WhatsApp Business API**: The communication channel with the customers.
- **Google Sheets**: Serves as the database for Orders, FAQs, and Inventory.
- **LangChain**: Used within n8n to provide Memory (Buffer Window) and Agent logic.

## 📦 Getting Started

### Prerequisites

You will need accounts and API keys for the following services:
1. **n8n**: A running instance (Cloud or Self-hosted).
2. **Google Cloud Console**: For the Gemini API Key and Google Sheets OAuth2 setup.
3. **Meta Developer Portal**: For WhatsApp Business API access.

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/Aditya-8840/Restaurant-ChatBot.git
   ```
2. Open your n8n workspace.
3. Go to **Workflows** -> **Import from File...** and select `Resturant chat bot.json`.
4. The workflow will be imported. 

### 🔐 Setting up Credentials

For security purposes, all secret keys and IDs have been removed from the provided JSON file. You will need to create and map your own credentials in n8n:

1. **Google Gemini**: Create a Google Gemini(PaLM) API credential and link it to the *Google Gemini Chat Model* node.
2. **Google Sheets**: Create a Google Sheets OAuth2 credential and link it to the *Post*, *FAQ*, and *for Inventory* nodes.
   - Update the Spreadsheet ID to point to your own Google Sheet (replace `YOUR_GOOGLE_SPREADSHEET_ID`).
3. **WhatsApp**:
   - Set up the **WhatsApp Trigger** node with your Webhook credentials.
   - Link the **Send message** node to your WhatsApp API credentials and update the Phone Number ID (replace `YOUR_WHATSAPP_PHONE_NUMBER_ID`).

## 📊 Google Sheets Setup

Create a new Google Spreadsheet named **Food Delivery System** and create the following sheets:

1. **Orders** (Columns: `Customer Name`, `Food Item`, `Quantity Ordered`, `Order Date`, `Status`)
2. **FAQ** (To store frequently asked questions and answers)
3. **Inventory** (To store available food items and stock limits)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 📝 License

This project is open-source and available for customization.
