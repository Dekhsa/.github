# Dicatat.in 🚀

**Elevating the Way You Learn, Inclusively.**

Dicatat.in is an advanced, AI-powered note-taking platform built to transform messy, unstructured handwritten notes into beautifully structured, highly visual digital formats. It leverages a dynamic interactive canvas, a sophisticated AI processing pipeline, and proven pedagogical methods to help students and professionals learn more effectively.

This repository serves as the central hub for the Dicatat.in ecosystem, which is divided into three main microservices: Frontend, Backend, and Machine Learning.

---

## 🏗️ System Architecture & Ecosystem

The Dicatat.in platform consists of three core services working seamlessly together:

1. **[FE] Frontend (`fe-dicatatin`)**: The user-facing application built with React. It provides an interactive infinite canvas (React Flow), 3D flashcards, and a premium dark-mode UI.
2. **[BE] Backend (`be-dicatatin`)**: The robust API gateway built with Laravel. It handles user authentication, workspace persistence (PostgreSQL), image asset management (Cloudinary), and orchestrates asynchronous tasks with the ML service.
3. **[ML] Machine Learning Engine (`ml-dicatatin`)**: The core AI processing pipeline built with FastAPI. It performs OCR using OpenAI Vision API, sanitizes text, transforms unstructured notes into structured React Flow graphs, and generates SM-2 compliant flashcards.

### Data Flow
`User uploads image (FE) -> Backend API (BE) -> Queue -> Processed by ML Engine (ML) -> Structured JSON output saved to DB (BE) -> Rendered on Canvas (FE)`

---

## ✨ Key Features

*   **7 Proven Note-Taking Methods**: The AI automatically structures notes into Mind Map, Cornell Notes, Boxing, Charting, Zettelkasten, Sketchnoting, or Feynman Technique.
*   **Smart AI Pipeline**: End-to-end processing including OCR (Vision API), text sanitization (typo fixing & abbreviation expansion), and semantic chunking.
*   **Interactive Infinite Canvas**: Fully editable A4 workspace with drag-and-drop, connection edges, smart auto-layout (`elkjs`), and zooming capabilities.
*   **Active Recall Flashcards**: Automatically generated 3D-flippable flashcard system using spaced-repetition algorithms (SM-2) for active learning.
*   **High-Fidelity PDF Export**: Vector-like PDF exports of the A4 canvas, capturing all complex SVG paths and nodes.
*   **Accessibility First**: Built-in Dyslexia-friendly mode featuring the OpenDyslexic font and tailored CSS spacing adjustments.
*   **Premium Dark Theme**: Carefully crafted, professional dark mode UI with glassmorphism effects and fluid micro-animations.

---

## 🛠️ Tech Stack

### 🎨 Frontend (`fe-dicatatin`)
*   **Framework**: React 19 (Vite)
*   **State Management**: Zustand
*   **Canvas Engine**: React Flow (`@xyflow/react`) & ELK Layout (`elkjs`)
*   **Styling**: Tailwind CSS v4 & custom CSS tokens
*   **Utilities**: `html-to-image`, `jsPDF`, Axios

### ⚙️ Backend (`be-dicatatin`)
*   **Framework**: Laravel (PHP)
*   **Database**: PostgreSQL
*   **Authentication**: Laravel Sanctum (Token-based)
*   **Storage**: Cloudinary
*   **Infrastructure**: Docker & Docker Compose
*   **API Docs**: Swagger / OpenAPI 3.0

### 🧠 Machine Learning (`ml-dicatatin`)
*   **Framework**: FastAPI (Python 3.11+)
*   **AI Engine**: OpenAI API (`gpt-4o-mini`)
*   **Structured Output**: Instructor & Pydantic
*   **Algorithms**: SM-2 for Flashcards

---

## 🚀 Getting Started

The project is designed to be easily set up locally using Docker for the backend services and npm for the frontend.

### 1. Backend & ML Services
The Backend and ML services are containerized. You'll need Docker Desktop running.

```bash
cd be-dicatatin
cp .env.example .env
# Start the services (Postgres, Laravel, Queue worker, ML FastAPI)
docker compose up -d
# Setup database
docker exec dicatatin-backend php artisan key:generate
docker exec dicatatin-backend php artisan migrate
```
*API Docs available at `http://localhost:8000/docs`*

### 2. Frontend Application
```bash
cd fe-dicatatin
npm install
npm run dev
```
*App running at `http://localhost:5173`*

*(Please refer to the `README.md` inside each respective folder for detailed environment variable setups and advanced commands).*

---

## 📂 Project Structure

```text
project-dicatatin/
├── fe-dicatatin/       # React SPA (Vite, Tailwind v4, React Flow)
├── be-dicatatin/       # Laravel REST API (Auth, Workspace CRUD, Queue)
├── ml-dicatatin/       # FastAPI AI Engine (OCR, Transform, Flashcards)
├── infra-dicatatin/    # Infrastructure and deployment configurations
└── .github/            # GitHub templates and profile README
```

---

## 📄 License

This project is proprietary and currently maintained by the Dicatat.in development team.
