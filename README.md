# Local AI

A responsive, browser-based chat interface for locally running language models. The frontend connects to an Ollama instance on your own machine and stores chat history and preferences in your browser.

## Features

- Responsive dark interface for desktop and mobile
- Connect to an Ollama server and discover installed models
- Chat with local models using Ollama's chat API
- Saved conversations, per-chat deletion, and JSON export
- Custom system instructions, creativity, and response-length controls
- No cloud AI API key and no account required by this frontend

## Run it

1. Install Ollama from https://ollama.com/ and start it.
2. Download a model using the Ollama app or terminal, for example: `ollama pull llama3.2`.
3. Open `index.html` in a browser or serve the repository with a local static web server.
4. Open **Models & connection**, set the Ollama address (normally `http://localhost:11434`), and connect.
5. Choose an installed model and chat.

## Browser access / CORS

Browsers may block requests to Ollama from a page served on another origin. If that happens, configure Ollama's allowed origins for your specific local development or hosted origin, then restart Ollama. Keep the local server private; do not expose it directly to the public internet. A GitHub Pages site is only the frontend and cannot install or run Ollama on visitors' devices.

For a local static server, from this folder run:

```bash
python -m http.server 8000
```

Then open http://localhost:8000.

## Privacy

Chat messages are sent to the Ollama address configured by the user. The frontend does not intentionally send chat content to a hosted AI API. Saved chats and settings are kept in this browser's local storage when chat saving is enabled. Browser storage can be cleared at any time; use Export conversations to make a backup.

## Limitations

This repository contains a frontend, not a bundled model runtime. Users must install and start Ollama (or adapt the frontend to another local runtime) themselves. Model capabilities, refusals, speed, and hardware requirements depend on the chosen model.
