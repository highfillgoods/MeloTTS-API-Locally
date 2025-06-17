# MeloTTS-API

A simple, robust, and OpenAI-compatible FastAPI wrapper for the [MyShell-AI/MeloTTS](https://github.com/myshell-ai/MeloTTS) text-to-speech engine.

This project provides an easy-to-use HTTP interface for MeloTTS, allowing you to integrate high-quality, natural-sounding text-to-speech into your applications with simple API calls. The API structure is designed to mimic common TTS services for easy integration.

## Features

-   **High-Quality TTS:** Leverages the power of MeloTTS for fast and natural-sounding speech synthesis.
-   **OpenAI-Compatible Endpoint:** Includes a `/v1/audio/speech` endpoint that mirrors the structure of OpenAI's TTS API for drop-in compatibility with tools like Open WebUI.
-   **RESTful Interface:** Provides clear endpoints to list available models and voices.
-   **Reliable Installation:** A comprehensive `requirements.txt` file ensures a clean and complete installation in an isolated environment.
-   **CPU Ready:** Configured to run on CPU out-of-the-box, no GPU required.

---

## 🚀 Installation

For a reliable setup and to avoid dependency issues, please follow these steps exactly. Tested in linux mint 20.

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/highfillgoods/MeloTTS-API-Locally.git](https://github.com/highfillgoods/MeloTTS-API-Locally.git)
    cd MeloTTS-API-Locally
    ```

2.  **Create and Activate a Clean Python Environment**
    Using a dedicated environment prevents conflicts with other projects. This example uses `conda`.
    ```bash
    conda create --name melo_api_env python=3.11 -y
    conda activate melo_api_env
    ```

3.  **Install All Dependencies**
    This single command installs all necessary packages from the perfected requirements file.
    ```bash
    pip install -r requirements.txt
    ```

---

## ▶️ Running the API Server

Once the installation is complete, start the API server with Uvicorn.

uvicorn melotts_api:app --host 0.0.0.0 --port 8000

The server will start, load the MeloTTS model into memory, and become available at http://0.0.0.0:8000.

## 🔌 Connecting to Open WebUI
![Open WebUI Audio Settings](open-webui-settings.png)
This API is designed to work directly with Open WebUI.

In Open WebUI, navigate to the Admin Panel by clicking your name in the bottom-left corner and selecting Settings.
Go to the Audio section.
Configure the TTS Settings section with the following values:
Text-to-Speech Engine: OpenAI
OpenAI API Base URL: http://localhost:8000/v1
OpenAI API Key: Can be set to anything (e.g., 12345).
Your settings should look like this:

Now you can input any of the available English voices (e.g., EN-BR, EN-US) you have previously downloaded from MeloTTS.

🛠️ Direct API Usage (Advanced)
You can also interact with the API directly using tools like curl.

## List Available Models
curl http://localhost:8000/v1/models

## List Available Voices
curl http://localhost:8000/v1/audio/voices

## Synthesize Speech
This example synthesizes text with the Australian voice and saves it as test_audio.mp3.


## audio generator .mp3 test
curl -X POST \
  http://localhost:8000/v1/audio/speech \
  -H "Content-Type: application/json" \
  --data '{
    "input": "Hello, this is a test from the land down under. your vegemite sandwich is ready.",
    "voice": "EN-AU",
    "model": "EN-AU"
  }' \
  --output test_audio.mp3



## Acknowledgments
This project is a wrapper around the excellent MeloTTS text-to-speech engine by MyShell.ai.
The API wrapper, debugging, documentation, and setup process were created with the assistance of Google Gemini.
License
This project is licensed under the MIT License.
