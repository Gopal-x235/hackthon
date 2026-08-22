# QuizForge AI — Professional Full-Stack EdTech Platform

> **"Turn any note into a quiz — online or off."**

QuizForge AI is a startup-grade, production-ready EdTech platform that transforms student study notes into interactive quizzes, evaluates responses with smart AI explanations, and tracks long-term learning progress across both Online and Offline modes.

---

## 🌟 Key Features

1. **Purposeful 3D Animation Layer**:
   - **Hero 3D Scene**: Floating Three.js 3D note cards that rotate and morph into a 3D quiz card with floating A/B/C/D answer options and interactive cursor parallax tilt.
   - **3D Animated Logo**: Morphing book-to-checkmark mark with sub-1.5s load animation settling into a clean static brand logo.
   - **Dashboard Card Depth**: Perspective hover tilt (`rotateX`/`rotateY`) on stat cards.
   - **3D Question Card Transitions**: Smooth 3D flip transform (`QuizCard3D`) when advancing between questions.
   - **Score 3D Reveal Card**: 3D flip card reveal on the Results page.
   - **Accessibility**: Automatic fallback for `prefers-reduced-motion` and non-WebGL environments.

2. **Dual-Engine Architecture (Online + Offline)**:
   - **Online AI Mode**: Powered by Google Gemini API / `AIService` abstraction with in-depth wrong answer analysis, summary generation, and adaptive difficulty.
   - **Offline Mode**: Python & Client-Side JavaScript Rule-Based NLP engine. Operates 100% in-browser with zero internet connection via IndexedDB & SQLite.

3. **Student Dashboard & Analytics**:
   - Overview Stat Cards (Total Notes, Quizzes Generated, Quizzes Attempted, Average Score, Current Streak).
   - Chart.js progress visualizers: Weekly Score Trend, Subject Performance Radar/Bars, Accuracy Breakdown.
   - Weak vs Mastered topic identification.

4. **Notes Manager**:
   - Full CRUD: Create, Edit, Delete, Search, Filter by Subject/Tags.
   - File text parser: Upload `.txt`, `.md`, or `.json` files to auto-fill notes.

---

## 🚀 Quick Start Guide

### Prerequisites
- Node.js v18+
- Python 3.10+

### 1. Run Backend Server (Flask)
```bash
cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```
*Backend runs on `http://127.0.0.1:5000`*

### 2. Run Frontend App (Vite + React)
```bash
cd frontend
npm install
npm run dev
```
*Frontend runs on `http://localhost:3000`*

---

## 📁 Project Structure

```
quizforge-ai/
├── backend/
│   ├── app.py                  # Flask REST API entry point
│   ├── config.py               # App configuration
│   ├── database/
│   │   ├── schema.sql          # SQLite / MySQL schema
│   │   └── db.py               # DB manager & demo data seeder
│   ├── models/                 # DB models
│   ├── offline/
│   │   └── quiz_engine.py      # Python Rule-Based NLP quiz generator
│   ├── services/
│   │   ├── ai_service.py       # Gemini API / Smart Fallback AIService
│   │   └── auth_service.py     # JWT & Password hashing
│   └── routes/                 # Auth, Notes, Quizzes, Dashboard, Health
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── 3d/             # Hero3DScene, AnimatedLogo, TiltCard, QuizCard3D, ScoreFlipReveal
│   │   │   ├── DashboardView.jsx
│   │   │   ├── NotesManagerView.jsx
│   │   │   ├── QuizGeneratorModal.jsx
│   │   │   ├── QuizPlayerView.jsx
│   │   │   ├── QuizResultsView.jsx
│   │   │   └── AnalyticsView.jsx
│   │   ├── context/            # AuthContext & NetworkContext
│   │   ├── services/           # Unified API fetch & offline fallback
│   │   └── utils/              # ClientQuizEngine & OfflineStorage
└── README.md
```
