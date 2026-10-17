# AI Receptionist FAQ Bot (WhatsApp)

An n8n workflow that answers customer questions on WhatsApp like a receptionist, using only the business information you give it. If it does not know the answer, it tells the customer a team member will follow up and alerts the owner on WhatsApp.

## How it works

1. **WhatsApp Webhook** receives incoming messages from Evolution API.
2. **Extract Message** pulls out the sender and text, and ignores groups and your own messages.
3. **Business Info** holds your hours, prices, location and services in one place.
4. **AI Agent** (OpenAI, with per-chat memory) answers using only that info and returns structured JSON.
5. **Send Reply** sends the answer back through Evolution API.
6. **Needs Human?** checks whether the agent could not answer.
7. **Alert Owner** sends the owner a WhatsApp message with the customer's question.

## Tools

n8n, OpenAI API, WhatsApp (Evolution API)

## Setup

1. Run an Evolution API server and connect a WhatsApp number to an instance (scan the QR code).
2. Import the JSON into n8n (Workflows, Import from file). n8n must be reachable from the internet (n8n Cloud or a hosted n8n).
3. Open the **Config** node and fill in your Evolution server URL, instance name and API key.
4. In Evolution API, open the instance webhook settings, paste this workflow's **production** webhook URL, and enable the `MESSAGES_UPSERT` event.
5. Add a credential for OpenAI.
6. Edit **Business Info** with your real hours, prices, location and services.
7. Set your own WhatsApp number in **Config** (`owner_number`, country code, no +) and replace `[YOUR BUSINESS NAME]` in the **AI Agent** system message.
8. Activate the workflow and message the connected WhatsApp number.

## Screenshot

Add a screenshot of the workflow canvas here.

## Author

Ashad Rashid
