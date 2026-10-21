# DeepSeek-V3.2-Speciale Chat

A responsive, browser-based chat interface designed for a hosted inference server running **DeepSeek-V3.2-Speciale**. This repository is a frontend only: it does not bundle, download, or run model weights.

## Features

- One fixed model target: DeepSeek-V3.2-Speciale (no model picker)
- No local model downloads or WebGPU dependency
- Connect to a user-configured OpenAI-compatible `/v1/chat/completions` endpoint
- Browser-stored conversations, per-chat deletion, restart-from-message, and JSON export
- Sends the full saved conversation as context on each request
- Does not set an app-level message-count limit or send a `max_tokens` cap
- Responsive desktop and mobile interface

## Setup

1. Arrange access to a hosted inference server that has loaded `deepseek-ai/DeepSeek-V3.2-Speciale` and exposes an OpenAI-compatible chat-completions endpoint.
2. Open the site and go to **Connection & settings**.
3. Enter the full endpoint URL, the server API key if required, and the exact model ID exposed by your server.
4. Save settings, then use **Test connection**.
5. Start chatting when the test succeeds.

The Speciale API announced by DeepSeek in December 2025 used a temporary endpoint that expired on December 15, 2025. This frontend does not assume that temporary endpoint still works. You must provide a currently working hosted server.

## Hosting and security

GitHub Pages only serves the website; it cannot host the model or keep a private API key secret. The API key you enter is stored in this browser's local storage and sent to the endpoint you configure. Do not place keys in this repository. Only use a server you trust, and understand that messages sent to a hosted server leave your device and are subject to that server's data handling and access policies.

The endpoint must allow browser requests from the website's origin (CORS). If you control the inference server, configure CORS there. For production use with multiple users, prefer a backend proxy that authenticates requests and keeps provider credentials server-side rather than sharing one key in the browser.

## Chat history and limits

When saving is enabled, conversations are stored in this browser's local storage. The frontend sends the full conversation history for each request and does not add a message-count limit or include a `max_tokens` output limit in its requests. However, browser storage capacity, the inference server's context window, server-side output limits, timeouts, and usage quotas still apply. Very long conversations may exceed the model/server context window. Export conversations periodically for backup.

## Local development

From this folder run:

```bash
python -m http.server 8000
```

Then open http://localhost:8000.
