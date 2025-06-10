# LocalmultimodalAssistants
# Ollama Multimodal Chat++

An advanced, feature-rich desktop chat client for [Ollama](https://ollama.com/) that brings together streaming, Text-to-Speech (TTS), and state-of-the-art, hands-free Voice Activity Detection (VAD) for a seamless conversational AI experience.

![image](https://github.com/user-attachments/assets/7242c6ca-e0dd-476a-a989-b84d9c7a215f)

This application is designed for power users who want a responsive, multimodal, and highly interactive way to chat with local LLMs. It leverages extensive threading to ensure the UI remains fluid and responsive, even while handling audio processing, transcription, and model inference simultaneously.

## ✨ Features

-   **Real-time Streaming:** Get responses from Ollama models as they're generated, word by word.
-   **Advanced Voice-to-Text:** A complete hands-free experience!
    -   **Voice Activity Detection (VAD):** Uses Silero VAD to automatically detect when you start and stop speaking. No "push-to-talk" button needed.
    -   **High-Quality Transcription:** Employs OpenAI's Whisper (or the optimized `faster-whisper`) to accurately transcribe your speech into text.
    -   **TTS-Aware:** VAD automatically pauses when the AI is speaking to prevent recording its own voice.
-   **Integrated Text-to-Speech (TTS):**
    -   Have the AI's responses read aloud to you in real-time.
    -   Intelligently queues and speaks complete sentences for natural-sounding delivery.
    -   Customize the voice and speech rate on the fly.
-   **Multimodal Input:** Chat with more than just text.
    -   **Image Support:** Attach images to your prompts for vision-capable models.
    -   **PDF & Text File Support:** Load the content of entire PDF documents or text/code files directly into the prompt.
-   **Flexible File Handling:**
    -   **Drag & Drop:** Drop images, PDFs, or text files directly onto the application.
    -   **Clipboard Pasting:** Paste images directly from your clipboard (`Ctrl+V` / `Cmd+V`).
-   **Rich UI Controls:**
    -   Select from any of your locally installed Ollama models.
    -   Choose your preferred Whisper model size (from `tiny` to `turbo-large`).
    -   Select transcription language or use auto-detect.
    -   Toggle TTS and Voice Input with a single click.
-   **Highly Responsive:** Built with a multi-threaded architecture to ensure the UI never freezes.

## 📋 Prerequisites

Before you begin, ensure you have the following installed on your system:

1.  **Python 3.8+**
2.  **[Ollama](https://ollama.com/)**: Make sure the Ollama service is installed and running.
3.  **An Ollama Model**: Pull at least one model. For multimodal features, use a vision model like `llava`.
    ```bash
    ollama pull gemma3:27b
    ollama pull llava
    ```
4.  **FFmpeg**: Required by `openai-whisper` for audio processing.
    -   **On macOS (via Homebrew):** `brew install ffmpeg`
    -   **On Windows (via Chocolatey):** `choco install ffmpeg`
    -   **On Debian/Ubuntu:** `sudo apt-get install ffmpeg`
5.  **PortAudio**: Required by `PyAudio` for microphone access.
    -   **On macOS (via Homebrew):** `brew install portaudio`
    -   **On Debian/Ubuntu:** `sudo apt-get install portaudio19-dev`

## ⚙️ Installation & Setup

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/ollama-multimodal-chat.git
    cd ollama-multimodal-chat
    ```

2.  **Create a Virtual Environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install Dependencies:**
    Install all the required Python packages from the `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```
    *Note: `torch` and `torchaudio` can be large. The installation might take some time.*

## 🚀 How to Run

1.  Ensure the **Ollama application is running** in the background.
2.  Run the main Python script:
    ```bash
    python main_script_name.py 
    ```
    *(Replace `main_script_name.py` with the actual name of your Python file.)*

## 📖 Usage Guide

-   **Model Selection:** Choose your desired Ollama model from the top-left dropdown.
-   **Sending a Message:** Type your message in the input box at the bottom and press `Enter` to send. Use `Shift+Enter` to create a new line.

### Voice Input (VAD)
1.  **Enable Voice:** Check the "Enable Voice" box in the "Voice Input (VAD)" section. The app will initialize the audio system, VAD, and Whisper models.
2.  **Speak Naturally:** The status indicator will show "Listening...". Simply start speaking. When you speak, the status will change to "Recording...".
3.  **Pause:** When you pause for more than a second, the app will stop recording, transcribe your speech, and place the text into the input box.
4.  **Auto-Send:** If "Auto-send after transcription" is checked, the message will be sent to Ollama automatically.

### Text-to-Speech (TTS)
1.  **Enable TTS:** Check the "Enable TTS" box.
2.  **Customize:** Use the dropdown to select a system voice and the slider to adjust the talking speed.
3.  As the AI responds, the text will be spoken aloud.

### Working with Files
-   **Attach an Image:**
    -   **Drag & Drop:** Drag an image file onto the "No Image" preview area.
    -   **Paste:** Copy an image to your clipboard and press `Ctrl+V` / `Cmd+V`.
    -   **Open File:** Click the "Open File" button.
-   **Load a PDF or Text File:**
    -   **Drag & Drop:** Drag a `.pdf`, `.txt`, `.py`, etc., file directly into the main text input area. The file's content will be loaded as your prompt.
    -   **Open File:** Click "Open File" and select a non-image file.

## 🛠️ Technology Stack

-   **GUI:** `tkinter`, `tkinterdnd2-universal`
-   **LLM Interaction:** `ollama`
-   **Voice Activity Detection (VAD):** `silero-vad` via `torch`
-   **Speech-to-Text (STT):** `openai-whisper` and `faster-whisper`
-   **Text-to-Speech (TTS):** `pyttsx3`
-   **Audio I/O:** `PyAudio`
-   **File & Image Handling:** `Pillow`, `PyMuPDF`
-   **Concurrency:** `threading`, `queue`

## ⚖️ License

See the `LICENSE` file for details.
