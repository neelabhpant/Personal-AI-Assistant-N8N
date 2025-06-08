# Personal AI Assistant on n8n

This project outlines a sophisticated **Personal AI Assistant** built on the **n8n** platform. It acts as a central hub to manage your digital life, intelligently delegating tasks to specialized agents for email, calendar, and internet research. The assistant is designed for seamless interaction via **Telegram**, supporting both text and voice commands.

---

## Key Features

### 🔧 Unified Command Center
- Interact with a single AI assistant that intelligently routes your requests to the correct tool.

### 🗣️ Multi-Modal Interaction
- Communicate with your assistant via text or voice messages through Telegram.

### 📧 Email Management
A dedicated agent handles all email-related tasks, including:
- **Sending and Drafting Emails**: Composes and sends emails on your behalf.
- **Contact Verification**: Verifies recipient email addresses with Google Contacts; asks for clarification if multiple matches are found.
- **Email Retrieval**: Searches your inbox for specific emails.
- **Professional Formatting**: Ensures emails have proper subject lines, salutations, and your signature.

### 📆 Calendar and Scheduling
A specialized agent manages your Google Calendar with:
- **Event Creation**: Schedules meetings, with or without attendees.
- **Attendee Verification**: Finds and verifies attendee emails using Google Contacts.
- **Availability Check**: Informs you about your availability and current schedule.

### 🌐 Internet Research
- Uses the **Tavily API** for real-time web search to deliver up-to-date information.

### 🧠 Context-Aware Conversations
- Remembers prior interactions for more natural and efficient conversations.

---

## How It Works

The assistant follows a **hub-and-spoke architecture** within n8n:

1. **Telegram Trigger**
   - Initiated when you send a message to your Telegram bot.
   - Secured to respond only to your user ID.

2. **Input Processing**
   - Checks if input is **text** or **voice**.
   - Voice messages are transcribed using **OpenAI**.

3. **Main AI Agent (The Hub)**
   - Determines intent and routes the task to a specialized agent/tool.

4. **Specialized Agents (The Spokes)**
   - **Email Agent**: Handles Gmail tasks with contact verification and formatting.
   - **Calendar Agent**: Manages Google Calendar events.
   - **Internet Research Tool**: Performs web searches via Tavily.

5. **Response**
   - Synthesized output is sent back to you via Telegram.

---

## Screenshots
![Screenshot 2025-06-08 at 11 38 28 AM](https://github.com/user-attachments/assets/00c2dc0b-ca6a-4827-ab4e-df15a35504da)
---

## Getting Started

You’ll need the following to run this assistant:

- An **n8n instance** (self-hosted or via [n8n.cloud](https://n8n.cloud))
- API credentials for:
  - **OpenAI**
  - **Telegram**
  - **Tavily**
  - **Google** (OAuth2 for Gmail, Calendar, and Contacts)
- The 3 workflow JSON files:
  - `Personal_AI_Assistant.json`
  - `Email_Agent.json`
  - `Calendar_Agent.json`

---

## Installation Steps

1. **Set up your n8n instance**
2. **Add API credentials** in the n8n credential store
3. **Import workflows**:
   - `Personal_AI_Assistant.json`
   - `Email_Agent.json`
   - `Calendar_Agent.json`
4. **Configure Workflows**:
   - Update the **Telegram Trigger** to accept only your chat ID
   - Ensure tool nodes are linked to correct credentials
5. **Activate the `Personal_AI_Assistant` workflow**

---

## Usage

Interact via Telegram with your bot. Example commands:

- "What's on my schedule for tomorrow?"
- "Send an email to Neelabh Pant and let him know I'll be 10 minutes late."
- "Who is the current president of France?"
- _(Voice Message)_ "Add 'Buy milk' to my to-do list."

---

## Future Work

Planned future extensions include:

- **📝 To-Do List Management**: Integrate with Todoist, Microsoft To Do, Trello
- **🧾 Note-Taking**: Connect to Notion or Evernote
- **🏠 Smart Home Integration**: Control devices via Home Assistant
- **💰 Financial Tracking**: Log expenses, get summaries from budgeting apps
- **📰 Custom News Briefings**: Use news APIs or RSS feeds for updates
