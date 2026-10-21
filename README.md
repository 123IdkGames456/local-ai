# Local AI

A responsive, browser-based chat interface for locally running language models. The frontend connects to an Ollama instance on your own machine and stores chat history and preferences in your browser.

## Features

- Responsive dark interface for desktop and mobile
- Automatically opens a setup/model picker when Ollama is unreachable or no models are installed
- Choose from model options labelled with estimated storage, capability, and speed
- Download selected models directly through Ollama's local pull API with progress updates
- Connect to an Ollama server and discover installed models
- Chat with local models using Ollama's chat API
- Saved conversations, per-chat deletion, and JSON export
- Custom system instructions, creativity, and response-length controls
- No cloud AI API key and no account required by this frontend

## Run it

1. Install Ollama from https://ollama.com/ and start it.
2. Open this site. If it cannot find Ollama or there are no models installed, it opens the model setup menu.
3. Choose a model by estimated storage and capability, then select **Download selected AI**. The model is downloaded by Ollama to your computer.
4. If needed, use **Get Ollama runtime** in the menu to install Ollama, then return to the site.
5. If the browser blocks local requests, configure Ollama's allowed origins for this site's origin and try again.

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

This repository contains a frontend, not a bundled model runtime. A browser website cannot install system software or run background installers without user action. Users must install and start Ollama first; after that, this page can download models through Ollama. Model capabilities, refusals, speed, and hardware requirements depend on the chosen model.
