# Evangadi Forum

A full-stack Q&A forum built for the Evangadi Tech community. Users can post questions, provide answers, chat in real-time, and utilize Google Gemini AI for semantic search, answer-fit evaluation, and draft coaching.

🔗 **Live Demo:** [https://evangadi-forum-tsion.vercel.app](https://evangadi-forum-tsion.vercel.app)

---

## ✨ Features

- **Q&A Core**: Post questions, provide answers, like answers, and save questions for later.
- **AI Draft Coach**: Get real-time feedback on your question drafts before posting.
- **AI Answer Fit**: Automatically evaluates if an answer actually addresses the original question.
- **Semantic Search**: Uses Gemini embeddings to find similar questions based on meaning, not just keywords.
- **RAG (Retrieval-Augmented Generation)**: Upload PDFs and chat with your documents using AI.
- **Discussion Rooms & Private Chat**: Real-time messaging with Socket.IO. Supports text, image attachments, file uploads, and voice recordings.
- **Unread Badges & Read State**: Tracks which messages you've read across rooms and DMs.
- **Authentication**: Secure login with Email/Password (JWT) and Google OAuth.
- **Mobile Responsive**: Fully responsive UI for mobile, tablet, and desktop.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React, Vite, React Router, CSS Modules |
| **Backend** | Node.js, Express, Socket.IO (WebSockets) |
| **Database** | MySQL (Hosted on Aiven) |
| **AI Integration** | Google Gemini (`@google/genai`) |
| **Authentication** | JWT, Google OAuth 2.0 |
| **Deployment** | Vercel (Frontend), Render (Backend) |

---

## 🚀 Local Development Setup

### Prerequisites
- Node.js 18+
- MySQL (MAMP, XAMPP, or standalone)
- Google Gemini API Key

### 1. Clone the repository
```bash
git clone https://github.com/Zion-phil/evangadi-forum.git
cd evangadi-forum

2. Backend Setup
cd backend
npm install

Create a .env file in the backend folder:
PORT=3777
DB_HOST=localhost
DB_PORT=8889
DB_USER=root
DB_PASSWORD=root
DB_DATABASE=evangadi_forum
JWT_SECRET=your_super_secret_jwt_key
JWT_EXPIRES_IN=1d
GEMINI_API_KEY=your_gemini_api_key
GEMINI_TEXT_MODEL=gemini-3.5-flash-lite
GEMINI_EMBEDDING_MODEL=gemini-embedding-001

Start the backend:
npm run dev

3. Frontend Setup
cd ../frontend
npm install

Create a .env file in the frontend folder:
VITE_API_BASE_URL=http://localhost:3777
VITE_GOOGLE_CLIENT_ID=your_google_oauth_client_id.apps.googleusercontent.com

Start the frontend:
npm run dev

Database Setup
1. Create a database named evangadi_forum.

2. Import the schema from backend/db/schema.sql.

3. Note for deployment: Linux (Aiven/Render) is strictly case-sensitive. Ensure all SQL queries use lowercase table names (questions, users, answers).

Project Structure
evangadi-forum/
├── backend/
│   ├── db/               # Database config & SQL schemas
│   ├── src/
│   │   ├── api/          # Controllers, Routes, Services (auth, questions, chat, etc.)
│   │   ├── socket/       # Socket.IO server setup
│   │   ├── middleware/   # Auth and Error handlers
│   │   └── utils/        # AI helpers, Gemini config
│   └── index.js          # Express entry point
├── frontend/
│   ├── src/
│   │   ├── components/   # UI Components (MessageThread, VoiceRecorder, etc.)
│   │   ├── pages/        # Route pages
│   │   └── context/      # React Contexts (Auth, Message, Confirm)
│   └── vite.config.js
└── README.md



🌐 Deployment Guide
This project uses Aiven for the database, Render for the backend, and Vercel for the frontend.

Database (Aiven)
1. Create a MySQL service on Aiven.

2. Create a database named evangadi-forum.

3. Run your SQL schema to create the tables.

Backend (Render)
1. Create a new Web Service, root directory: backend.

2. Build Command: npm install

3. Start Command: node index.js

4. Add all environment variables from your backend .env.

Important: Add FRONTEND_URL=https://your-vercel-app.vercel.app (no trailing slash) to enable CORS.

Frontend (Vercel)
1. Import the repo, root directory: frontend.

2. Framework preset: Vite.

3. Add environment variable: VITE_API_BASE_URL=https://your-render-url.onrender.com

4. Add environment variable: VITE_GOOGLE_CLIENT_ID=...

5. Add a vercel.json in the frontend folder to handle React Router SPA fallback:
{
  "rewrites": [{ "source": "/(.*)", "destination": "/index.html" }]
}

📄 License
Built for the Evangadi Tech Bootcamp. Not affiliated with OpenAI or Gemini.