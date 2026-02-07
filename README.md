# 🐋 Whale Protection And Routing

**Real-Time Bioacoustic Surveillance for Marine Conservation**

> A deep-learning system designed to prevent ship collisions by detecting whale vocalizations in real-time. Using a fine-tuned **Audio Spectrogram Transformer (AST)**, the system listens to live hydrophone data, filters out ocean noise, and alerts vessels of nearby marine life.



---

## 📖 About The Project

Ships frequently collide with whales because they are invisible beneath the surface. This project solves that by using underwater microphones to listen for whale songs. Our system filters out confusing ocean noises—like waves and engines—to detect whales instantly and alert the captain to slow down, preventing fatal accidents.

**Whale Hunter AI** operates as an "AI Lookout." Unlike traditional threshold-based triggers, this project uses a **Fine-Tuned Audio Spectrogram Transformer (AST)**—a state-of-the-art vision transformer adapted for audio—to distinguish complex whale songs from ocean noise, boat engines, and heavy rain.

---

## ✨ Key Features

* **Real-Time Detection:** Processes audio streams with <1s latency to provide immediate alerts.
* **Smart Noise Filtering:** Uses spectral analysis to reject high-frequency false positives (like snapping shrimp or human speech).
* **Edge-Cloud Architecture:**
    * **Client:** Lightweight Python script runs on low-power devices (Raspberry Pi/Laptop).
    * **Server:** Heavy AI inference runs on a cloud GPU (Google Colab/AWS).
* **Robust AI Model:** Trained on a balanced dataset of Humpback Whale songs vs. complex ocean background noise.

---

## ⚙️ How It Works

The system follows a **Client-Server** architecture to enable powerful AI analysis on low-resource hardware.

1.  **The Listener (Client):**
    * Records audio in 5-second chunks using a local microphone or hydrophone.
    * Performs a "Pitch Guard" check: If the sound is too high-pitched (e.g., wind, voice), it is discarded locally to save bandwidth.
    * Securely tunnels valid audio clips to the cloud server via **Ngrok**.

2.  **The Brain (Server):**
    * Receives the audio clip and converts it into a **Mel Spectrogram** (a visual representation of sound).
    * Passes the spectrogram through the **AST Model** (Audio Spectrogram Transformer).
    * Returns a confidence score (e.g., `Whale: 92%`).



3.  **The Alert:**
    * If confidence exceeds the threshold (default: 50%), the client logs a **"WHALE DETECTED"** event.

---

## 🛠️ Tech Stack

* **Language:** Python 3.9+
* **AI Model:** [AST (Audio Spectrogram Transformer)](https://huggingface.co/docs/transformers/model_doc/ast)
* **Libraries:** `Transformers` (Hugging Face), `Librosa` (Audio Processing), `PyTorch`, `Flask`.
* **Networking:** `PyNgrok` (Secure Tunneling), `Requests`.
* **Hardware:** Optimized for NVIDIA T4 GPUs (Server) and standard CPUs (Client).

---

## 🚀 Getting Started

Follow these steps to set up the project locally.

### 1. Clone the Repository
```bash
git clone [https://github.com/Viperz6884/Whale-Protection-And-Routing.git](https://github.com/Viperz6884/Whale-Protection-And-Routing.git)
cd Whale-Protectio-And-Routing

```

### 2. Set Up the Environment (Client)

Create a `requirements.txt` file with the following dependencies:

```text
numpy
sounddevice
soundfile
requests
librosa
torch
transformers

```

Then, install them using pip:

```bash
pip install -r requirements.txt

```

### 3. Start the Brain (Server)

1. Open the `Whale_Hunter_Server.ipynb` notebook in Google Colab.
2. Upload your `dataset/` folder (or use the pre-trained model provided).
3. Add your **Ngrok Auth Token** in the server script.
4. Run all cells. Copy the `public_url` (e.g., `https://xyz.ngrok-free.app`).

### 4. Start the Ear (Client)

1. Open `listener.py` in your code editor.
2. Paste the `public_url` into the `SERVER_URL` variable.
3. Run the listener:

```bash
python listener.py

```

*Play a whale sound or speak into the microphone to test!*

---

## 📊 Dataset Structure

The model expects data organized in the following folder structure:

```text
dataset/
├── whale/    # Contains .wav files of whale vocalizations
└── noise/    # Contains .wav files of ocean background (waves, rain, boats)

```

---

## 🤝 Contributing

Contributions make the open-source community an amazing place to learn, inspire, and create.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

## 📞 Contact

Your Name - your-email@example.com

Project Link: [https://github.com/your-username/whale-hunter-ai](https://github.com/your-username/whale-hunter-ai)

```

Would you like me to help you draft the `LICENSE` file or create a specific `requirements.txt` based on the exact versions of the libraries you used?

```
