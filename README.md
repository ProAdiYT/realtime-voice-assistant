# realtime-voice-assistant
# 🎙️ Murf Falcon Voice AI Assistant
A real-time conversational voice assistant built using **Murf Falcon Text-to-Speech (TTS)** and **ASR (Automatic Speech Recognition)** such as Deepgram or AssemblyAI.  
This project was created for a hackathon to demonstrate how **fast, natural, and interactive** Falcon-powered speech systems can be.

---

## 🚀 Project Overview
This prototype allows a user to **speak**, have their voice converted to text (ASR), processed by the system, and then **spoken back instantly** using Murf Falcon TTS.

The goal is to show a functional voice-first application that demonstrates:
- Real-time speech generation  
- Low latency  
- Natural voice output  
- Continuous conversation  
- Securely managed API keys  
- Use of the **1,000,000 free TTS characters** from Murf  

This project can be adapted for:
- Customer support agents  
- Accessibility tools  
- Productivity automation  
- Language learning  
- Narration / storytelling  
- Voice-driven assistants  

---

## 🧩 Features
- 🎤 **Real-time Speech Recognition (ASR)**  
- 🗣️ **Ultra-fast TTS using Murf Falcon**  
- 🔄 **Continuous conversational interaction**  
- ⚡ Low latency audio response  
- 🔐 **Environment variable–based API key protection**  
- 🧠 Can be extended with LLMs for intelligent responses  
- 🎧 Works as a voice-driven AI agent  

---

## 🛠️ Tech Stack
- **Node.js / TypeScript** (Backend)
- **Express.js**
- **React + Vite** (Frontend, if included)
- **TailwindCSS**
- **Murf Falcon TTS API**
- **Deepgram / AssemblyAI ASR API**
- **WebSockets** (optional for streaming)
- **Drizzle ORM + PostgreSQL** (if enabled)

---

## 📁 Project Structure (Simplified)
project-root/
│── server/
│ ├── index.ts # Backend server
│ ├── routes/ # API endpoints
│ └── services/ # ASR + TTS logic
│
│── client/
│ └── src/ # Frontend UI
│
│── package.json
│── .env.example
│── README.md


---

## 🔑 Environment Variables

Create a `.env` file in your root folder using:

MURF_API_KEY=your_murf_falcon_key
ASR_API_KEY=your_asr_key # Deepgram or AssemblyAI
PORT=3000


**Never commit your actual keys to GitHub.**

---

## 📦 Installation & Setup

### **1️⃣ Install dependencies**
```bash
npm install

2️⃣ Add your API keys
Copy the example env file and edit it:

cp .env.example .env

3️⃣ Run the backend
npm run dev

4️⃣ Run the frontend (if included)
npm run dev:client



