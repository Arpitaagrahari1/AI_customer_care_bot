# ECHOMIND – Advanced AI Customer Care Supervisor & Bot

![ECHOMIND Hero](./public/Screenshot%202026-07-19%20152817.png)

Welcome to **ECHOMIND**, the next-generation AI Customer Care Bot and Supervisor system. Designed for modern enterprises, ECHOMIND leverages a cutting-edge microservice architecture to deliver real-time speech and text tone processing, semantic context lookup, hallucination policing, and offline reinforcement learning.

This README serves as the complete, comprehensive documentation for the project, covering everything from architectural design and folder structures to detailed deployment and API usage instructions.

---

## 📖 Table of Contents

1. [Project Overview](#-project-overview)
2. [Key Features](#-key-features)
3. [Technology Stack](#-technology-stack)
4. [System Architecture](#-system-architecture)
5. [Directory Structure](#-directory-structure)
6. [User Interface Showcase](#-user-interface-showcase)
7. [Prerequisites](#-prerequisites)
8. [Installation & Local Setup](#-installation--local-setup)
9. [Environment Variables](#-environment-variables)
10. [API Documentation](#-api-documentation)
11. [Database Schema](#-database-schema)
12. [Machine Learning Pipeline](#-machine-learning-pipeline)
13. [Deployment Guide](#-deployment-guide)
14. [Troubleshooting & FAQ](#-troubleshooting--faq)
15. [Contributing](#-contributing)
16. [License](#-license)

---

## 🌟 Project Overview

Customer care is evolving. Rule-based chatbots and simple LLM wrappers are no longer sufficient to handle complex, emotionally charged customer interactions. **ECHOMIND** bridges this gap by introducing a multi-layered AI system that not only understands user intent but also analyzes emotional undertones and verifies AI responses before they are sent to the user.

### Why ECHOMIND?
- **Emotion-Aware:** Processes user input to gauge frustration, satisfaction, or urgency.
- **Safe & Supervised:** An independent "AI Supervisor" layer intercepts hallucinations or toxic outputs.
- **Contextual Memory:** Uses vector databases to retrieve historical interactions and semantic context.
- **Self-Improving:** The Hindsight Learning Engine allows the system to learn from edge cases over time.

---

## ✨ Key Features

### 1. Emotion Engine (Real-Time Processing)
- Analyzes textual and audio inputs to detect underlying emotional states.
- Adjusts response parameters dynamically based on user frustration levels.
- Generates live emotion index charts on the supervisor dashboard.

### 2. Memory Core (Vector Search)
- Integrates with ChromaDB (or similar vector stores) for semantic lookups.
- Maintains long-term context across multiple customer sessions.
- Injects verified cache responses for frequently asked complex queries.

### 3. AI Supervisor (Safety & Compliance)
- Acts as a middleman between the generative AI and the customer.
- Flags sensitive data leaks, toxic language, or hallucinated policies.
- Automatically intervenes and rewrites responses to meet brand guidelines.

### 4. Hindsight Learning Engine
- Collects edge cases and flagged interactions throughout the week.
- Processes these logs offline to update neural weights and improve future accuracy.
- Displays synchronization status and improvement metrics on the dashboard.

---

## 🛠 Technology Stack

The application is built using a modern **Microservice Architecture**, splitting the application into three independent, highly scalable services:

### Frontend (User Interface & Dashboard)
- **Framework:** React 18 with Vite for blazing-fast builds.
- **Styling:** Tailwind CSS 4, utilizing advanced custom properties and glassmorphism.
- **Animations:** Framer Motion for liquid-smooth transitions and micro-interactions.
- **Charting:** Chart.js and React-Chartjs-2 for real-time data visualization.
- **Icons:** Lucide-React for clean, scalable vector iconography.

### Backend (API Gateway & Logic)
- **Runtime:** Node.js.
- **Framework:** Express.js for robust REST API routing.
- **ORM:** Prisma for type-safe database interactions.
- **Database:** PostgreSQL for relational data storage (users, logs, metrics).
- **Communication:** Axios for inter-service HTTP requests.

### ML Service (The Brain)
- **Language:** Python 3.9+.
- **Framework:** FastAPI for high-performance ML endpoints.
- **ML/AI:** PyTorch, HuggingFace Transformers (NLP and Emotion detection).
- **Vector DB:** ChromaDB / FAISS for memory retrieval.

---

## 📐 System Architecture

The system operates across three primary layers:

1. **Client Layer (React):** Sends requests via HTTP to the API Gateway. Displays real-time dashboards and chat interfaces.
2. **Gateway Layer (Node.js):** Acts as the central nervous system. It authenticates requests, logs data to PostgreSQL, and routes AI-specific tasks to the ML Service.
3. **Intelligence Layer (Python):** Executes heavy tensor computations, natural language processing, and memory retrieval.

### Data Flow Example (Chat Prediction)
1. User types a message in the React Frontend.
2. Frontend sends `POST /api/predict` to Node.js Backend.
3. Node.js Backend proxies the request to Python ML Service.
4. Python runs the input through the Emotion Engine, Memory Core, and AI Supervisor.
5. Python returns the prediction and emotion data to Node.js.
6. Node.js saves the interaction (User Text, Intent, Emotion) to PostgreSQL.
7. Node.js returns the final payload to the Frontend.

---

## 📁 Directory Structure

A comprehensive look at the project's folder layout:

```text
AI_customer_care_bot/
├── frontend/                     # React + Vite Frontend Application
│   ├── public/                   # Static assets
│   ├── src/
│   │   ├── animations/           # Framer Motion animation variants
│   │   ├── assets/               # Images, SVGs, and global stylesheets
│   │   ├── charts/               # Chart.js component wrappers (e.g., EmotionChart.jsx)
│   │   ├── components/           # Reusable UI components (GlassCard, Sidebar, etc.)
│   │   ├── layouts/              # Route layouts (MainLayout.jsx)
│   │   ├── pages/                # Route components (Dashboard, Chat, Settings, etc.)
│   │   │   ├── auth/             # Authentication pages (Login, Signup)
│   │   │   └── Dashboard.jsx     # Main ECHOMIND Command Center
│   │   ├── services/             # API client services and utilities
│   │   ├── App.jsx               # Main React Router setup
│   │   ├── index.css             # Tailwind base styles and CSS variables
│   │   └── main.jsx              # React DOM entry point
│   ├── package.json
│   ├── tailwind.config.js
│   └── vite.config.js
│
├── node_backend/                 # Express API Gateway
│   ├── prisma/                   # Database schema and migrations
│   │   └── schema.prisma         # PostgreSQL schema definition
│   ├── .env                      # Database URL and config
│   ├── index.js                  # Express server and route handlers
│   └── package.json
│
├── ml_service/                   # Python FastAPI Machine Learning Service
│   ├── models/                   # Pre-trained models and weights (ignored in git)
│   ├── utils/                    # Helper scripts for text processing
│   ├── app.py                    # FastAPI server entry point
│   └── requirements.txt          # Python dependencies
│
├── public/                       # Global project screenshots and documentation assets
├── .gitignore                    # Global git ignore rules
└── README.md                     # This documentation file
```

---

## 📸 User Interface Showcase

Below are comprehensive screenshots of the ECHOMIND platform. We have prioritized a sleek, modern, "glassmorphism" aesthetic with deep analytics and real-time monitoring capabilities.

*(Click on any image to view it in higher resolution if supported by your Markdown viewer)*

<div align="center">
  <img src="./public/Screenshot%202026-07-19%20152817.png" alt="ECHOMIND View 1" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />
  
  <img src="./public/Screenshot%202026-07-19%20152822.png" alt="ECHOMIND View 2" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />
  
  <img src="./public/Screenshot%202026-07-19%20152826.png" alt="ECHOMIND View 3" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20152834.png" alt="ECHOMIND View 4" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20152844.png" alt="ECHOMIND View 5" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20152859.png" alt="ECHOMIND View 6" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162526.png" alt="ECHOMIND Dashboard Analytics" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162532.png" alt="ECHOMIND View 8" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162536.png" alt="ECHOMIND View 9" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162540.png" alt="ECHOMIND View 10" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162543.png" alt="ECHOMIND View 11" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162547.png" alt="ECHOMIND View 12" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162551.png" alt="ECHOMIND View 13" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />

  <img src="./public/Screenshot%202026-07-19%20162554.png" alt="ECHOMIND View 14" width="800" style="border-radius: 10px; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.2);" />
</div>

---

## ⚙️ Prerequisites

Before you begin, ensure you have the following installed on your machine:

1. **Node.js** (v18.0.0 or higher) - Required for Frontend and API Gateway.
2. **Python** (v3.9 or higher) - Required for the ML Service.
3. **PostgreSQL** - A running instance of PostgreSQL (local or cloud like Supabase/Neon).
4. **Git** - Version control.

---

## 🚀 Installation & Local Setup

Because this is a microservice architecture, you will need to start **three separate terminals** to run the full stack locally. Follow the steps exactly as written below.

### Step 1: Database & Node.js API (Gateway)
This service handles all database operations, API routing, and proxies AI requests to the Python service.

Open Terminal 1:
```bash
cd node_backend

# 1. Install dependencies
npm install

# 2. Configure Environment Variables
# Create a .env file if it doesn't exist and add your PostgreSQL credentials:
echo "DATABASE_URL=postgresql://postgres:password@localhost:5432/echomind?schema=public" > .env
echo "PORT=3000" >> .env

# 3. Synchronize the Database Schema
# This will push the Prisma schema to your PostgreSQL database
npx prisma db push

# 4. Generate Prisma Client
npx prisma generate

# 5. Start the Node.js server
npm run dev
```
*(The Node.js gateway should now be running on `http://localhost:3000`)*

### Step 2: Python ML Service (The Brain)
This service strictly handles PyTorch intent prediction, audio analysis, and vector search. It runs heavily optimized Python code.

Open Terminal 2:
```bash
cd ml_service

# 1. Create a Python virtual environment
python -m venv venv

# 2. Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On Mac/Linux:
# source venv/bin/activate

# 3. Install required Python packages
pip install -r requirements.txt

# 4. Start the FastAPI server (Runs on port 8000 by default)
python app.py
```
*(The Python ML Service should now be running on `http://127.0.0.1:8000`)*

### Step 3: Frontend (React + Vite)
This is the gorgeous, highly interactive user interface.

Open Terminal 3:
```bash
cd frontend

# 1. Install Node dependencies
npm install

# 2. Start the Vite development server
npm run dev
```
*(The Frontend should now be accessible at `http://localhost:5173`)*

---

## 🔐 Environment Variables

Proper configuration is critical for the application to function. Ensure the following variables are set in their respective `.env` files.

### `node_backend/.env`
| Variable | Description | Example |
|----------|-------------|---------|
| `DATABASE_URL` | Connection string for PostgreSQL database | `postgresql://user:pass@localhost:5432/db` |
| `PORT` | Port for the Express server to listen on | `3000` |
| `PYTHON_ML_URL` | URL where the Python ML service is hosted | `http://127.0.0.1:8000` |

### `frontend/.env` (Optional)
| Variable | Description | Example |
|----------|-------------|---------|
| `VITE_API_URL` | Base URL for backend API requests | `http://localhost:3000` |

---

## 📡 API Documentation

The Node.js Gateway acts as a reverse proxy for the Python ML service while also handling database interactions. All frontend requests should hit the Node.js Gateway on Port 3000.

### 1. Health Checks
**`GET /health`**
- **Description:** Checks the status of both Node.js and the Python ML Service.
- **Response:**
  ```json
  {
      "status": "healthy",
      "node_version": "v18.17.0",
      "ml_service_status": { "status": "online", "model": "loaded" }
  }
  ```

### 2. AI & Prediction Endpoints
**`POST /api/predict`**
- **Description:** Sends text to the AI for intent and emotion prediction. Logs the result to the DB.
- **Body:** `{ "text": "I am extremely frustrated with my recent bill." }`
- **Response:**
  ```json
  {
      "intent": "billing_complaint",
      "emotion": "high_frustration",
      "confidence": 0.94,
      "suggested_response": "I sincerely apologize for the confusion regarding your bill..."
  }
  ```

**`POST /api/voice/analyze`**
- **Description:** Analyzes voice/audio tone (Proxies audio buffers to Python).
- **Body:** `{ "audio_data": "base64_encoded_string" }`
- **Response:** `{ "tone": "agitated", "speech_rate": "fast" }`

**`POST /api/memory/search`**
- **Description:** Performs a vector similarity search across past context.
- **Body:** `{ "query": "refund policy delays", "customer_id": "12345" }`

### 3. Analytics & Logging Endpoints
**`GET /api/metrics`**
- **Description:** Retrieves combined system metrics for the Dashboard.
- **Response:**
  ```json
  {
      "active_sessions": 24,
      "supervision_rate": 99.8,
      "recovery_rate": 88.5,
      "interventions": 3,
      "totalInteractionsSaved": 1402
  }
  ```

**`GET /api/hindsight/logs`**
- **Description:** Retrieves the 50 most recent interaction logs from PostgreSQL.

---

## 💾 Database Schema

The system uses Prisma ORM with PostgreSQL. Below is a conceptual representation of the core data models.

```prisma
model ChatLog {
  id        String   @id @default(uuid())
  userText  String
  aiIntent  String
  aiEmotion String
  createdAt DateTime @default(now())
}

model Feedback {
  id        String   @id @default(uuid())
  rating    Int
  comments  String?
  createdAt DateTime @default(now())
}
```
*Note: Run `npx prisma studio` inside the `node_backend` directory to view and manage your data via a GUI.*

---

## 🧠 Machine Learning Pipeline

The ECHOMIND Python service is not a simple API wrapper. It implements a rigorous inference pipeline:

1. **Preprocessing:** Text is cleaned, tokenized, and normalized. Audio is converted to standardized waveforms.
2. **Intent Classification:** A fine-tuned transformer model categorizes the customer's request into actionable intents.
3. **Sentiment & Emotion Analysis:** A secondary model gauges the emotional polarity (anger, sadness, joy, neutral).
4. **Safety Verification:** The AI Supervisor module checks the generated response against a strict set of rule-based and semantic constraints to prevent hallucinations.
5. **Hindsight Sync:** Periodically, flagged interactions are reviewed and weights are adjusted using a localized reinforcement learning script.

---

## 🌍 Deployment Guide

To take ECHOMIND from local development to production, follow these steps. 

### 1. Deploying the Frontend (Vercel)
Vercel is highly optimized for React/Vite applications.
1. Create a `vercel.json` file in the `frontend` root to rewrite API requests:
   ```json
   {
     "rewrites": [
       { "source": "/api/:path*", "destination": "YOUR_NODE_BACKEND_URL/api/:path*" },
       { "source": "/(.*)", "destination": "/index.html" }
     ]
   }
   ```
2. Push your code to GitHub.
3. Import the repository in Vercel. Select `frontend` as the Root Directory.
4. Framework Preset: **Vite**. Build Command: `npm run build`.
5. Deploy!

### 2. Deploying the Node.js API (Render / Railway)
1. Create a new Web Service on Render or Railway.
2. Select the `node_backend` directory.
3. Build Command: `npm install && npx prisma generate`
4. Start Command: `node index.js`
5. Add Environment Variables (`DATABASE_URL`, `PYTHON_ML_URL`).

### 3. Deploying the Python ML Service (Render / Railway / AWS)
1. Create another Web Service for the Python backend.
2. Select the `ml_service` directory.
3. Build Command: `pip install -r requirements.txt`
4. Start Command: `uvicorn app:app --host 0.0.0.0 --port 8000`
5. Note: ML services require more RAM. Ensure your hosting tier provides at least 1GB - 2GB of RAM depending on model size.

---

## 🛑 Troubleshooting & FAQ

**Q: The Dashboard is showing a white screen!**
**A:** This was a known issue caused by undefined metrics data. Ensure you have the latest code, as we have added fallback values and safe rendering (`data.supervision_rate ?? 99.8`). Also, check if your Node.js server is running and accessible.

**Q: Prisma says `Database connection failed`.**
**A:** Ensure your PostgreSQL server is running locally and the credentials in `node_backend/.env` are 100% correct.

**Q: Python throws a `ModuleNotFoundError`.**
**A:** Ensure you have activated your virtual environment (`venv\Scripts\activate`) before running `pip install -r requirements.txt`.

**Q: Can I use MySQL instead of PostgreSQL?**
**A:** Yes. Change the `provider` in `prisma/schema.prisma` to `"mysql"`, update your `DATABASE_URL`, and run `npx prisma db push`.

---

## 🤝 Contributing

We welcome contributions to ECHOMIND! 
1. Fork the repository.
2. Create a new feature branch (`git checkout -b feature/amazing-feature`).
3. Commit your changes (`git commit -m 'Add amazing feature'`).
4. Push to the branch (`git push origin feature/amazing-feature`).
5. Open a Pull Request.

Please ensure you run `npm run lint` in the frontend and use `flake8` or `black` for Python code formatting.

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---
*Built with ❤️ by the ECHOMIND Team. Shaping the future of AI-driven customer success.*
