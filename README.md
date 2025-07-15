# WhatsApp Translator using n8n + Groq LLM

This project is an **AI-powered WhatsApp message enhancer** built using `n8n`, `Groq LLM`, and the `Evolution API`. It enables users to send translated, polished, and professional versions of their messages to specific WhatsApp groups by using a mention-based trigger format.

## ✨ Features

- Listens to WhatsApp messages via Webhook
- Detects commands in the format `@"Group Name" message` or `@groupname message`
- Fetches the latest 20 messages from the group as context
- Sends the user's message and context to a Groq-hosted LLaMA 3.3 70B LLM
- Rewrites the message in a professional and respectful tone
- Sends the translated message back to the target WhatsApp group
- Gracefully handles input errors and unknown group names

## 🧠 How It Works

1. **Webhook** node receives incoming WhatsApp messages
2. **Code node** parses and validates the command format
3. **HTTP Request** node fetches available WhatsApp group data
4. **Matching Logic** finds the group ID based on provided name
5. **Conditional Logic (If nodes)**
   - If group found: Fetch recent messages for context
   - If not: Respond with error and list of available groups
6. **LangChain LLM node (Groq)** builds a polished version of the message
7. **Evolution API node** posts the final message back to the group

## 🚀 Usage

### WhatsApp Command Format:

```bash
@"Team Marketing" please send your EOD by 6 PM.
```

### Output:

> "Kindly ensure your EOD updates are submitted by 6 PM. Thank you."

## 🎥 Demo

- YouTube Demo: [Insert Demo Link Here]
- Example Workflow Screenshot:&#x20;

## 🚀 Stack

- **n8n** - Workflow orchestration
- **Groq Cloud** - LLM inference (LLaMA 3.3 70B)
- **Evolution API** - WhatsApp group message integration

## 🚧 Setup Instructions

1. Clone this repository or import the `WhatsApp_Translator.json` into n8n.
2. Configure your credentials:
   - Groq API Key
   - Evolution API Auth
   - HTTP Header credentials for group/message fetch
3. Replace the `ngrok` URLs with your own tunnel or production endpoint.
4. Deploy the webhook and share the trigger format with WhatsApp users.

## 🚫 Invalid Command Response

If the command format is wrong:

> Invalid format. Use: @"group name" message OR @groupname message

## 📅 Future Improvements

- Add language translation
- Support for image-to-caption response
- More advanced tone adjustments (e.g., formal/informal)

## ✉️ Contact

For questions or improvements, please reach out via GitHub or email.

---

Built with ❤️ using open-source tools and AI.

