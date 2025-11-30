# 🚀 InkSync — Real-Time Collaborative Rich-Text Editor

InkSync is a production-grade, real-time, multi-user collaborative editor designed to power applications similar to **Notion** or **Google Docs**. It provides a robust foundation for real-time systems, WebSocket-based applications, and distributed collaboration tools.

Multiple users can edit the same document simultaneously, view each other’s cursor positions, and experience conflict-free, aligned updates backed by **CRDT** synchronization.

## ✨ Features

### ✅ Core Features (Already Implemented)
* **Real-Time Collaborative Editing** using **WebSockets** and **Django Channels**.
* **CRDT-based Conflict Resolution** powered by **Yjs**.
* **Rich-Text Editing** with **Remirror** (bold, italic, headings, lists, etc.).
* **Redis-powered Pub/Sub layer** for scaling WebSocket performance.
* **Live Typing Updates** with low-latency synchronization.
* **Cursor Broadcasting** — view active collaborators’ caret positions.
* **React (Vite) Frontend** for a fast, modern editing UX.
* **Backend** powered by **Django** for clean structure & future expansion.

---

### 🔥 Upcoming Enhancements (Your Add-on Features)
These improvements are perfect for resume and portfolio building:

#### 🚹 Live User Presence + Cursors 2.0
* Show active users in a sidebar.
* Display colored cursors with labels.
* Real-time join/leave presence tracking.
#### 📁 Multi-Document Workspace
* Create, rename, and switch between multiple documents.
* URL-based document rooms (`/doc/:id`).
* Separate CRDT states per document.
#### 🕒 Version History + Autosave
* Automatic periodic snapshotting.
* Restore previous versions.
* Last edited timestamp.
* Local fallback save if network drops.
#### 🔐 Authentication & Role-Based Access
* JWT or Django auth system.
* Permissions: owner, editor, viewer.
* Private/public document modes.

---

## 🛠 Tech Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Backend** | Python, Django, Django Channels | Primary logic, WebSocket handling, API |
| **Pub/Sub** | Redis | Message broker for scalable WebSocket broadcasts |
| **Server** | ASGI / Daphne | Asynchronous server interface |
| **Frontend** | React + Vite, TypeScript | Modern, fast UI framework |
| **Editor UI** | Remirror | Extensible rich-text editor toolkit |
| **Sync Engine** | Yjs (CRDTs) | Conflict-free Replicated Data Types for collaboration |
| **Styling** | TailwindCSS | Utility-first CSS framework |

---

## 📂 Project Structure
InkSync/
│
├── app-server/         
│   ├── core/           
│   ├── editor/        
│   ├── manage.py
│   ├── requirements.txt
│
├── app/                
│   ├── src/
│   ├── package.json
│   ├── vite.config.ts
│   └── index.html
│
└── README.md


---

## ⚙️ Setup Instructions

### 1️⃣ Backend Setup (Django + Channels)
cd app-server

### Create and activate virtual environment
python -m venv envenv # Windows
### or
source env/bin/activate # macOS/Linux

pip install -r requirements.txt
python manage.py migrate
python manage.py runserver

### 2️⃣ Start Redis
Redis is essential for the Pub/Sub layer and must be running on port 6379.

Recommended (Docker):

Bash

docker run -p 6379:6379 -d redis:latest
Alternative (Windows): Install and start Memurai (a Redis alternative): https://www.memurai.com/get-memurai

### 3️⃣ Frontend Setup (React + Vite)
Bash

cd app
npm install
npm run dev

### Frontend → http://localhost:3000

### Backend → http://localhost:8000

## 🧪 How Real-Time Sync Works
InkSync utilizes an event-driven, distributed architecture to achieve seamless, conflict-free collaboration.

The core synchronization flow is:

Client Edit: A user makes a change, and Yjs generates a CRDT update.

WebSocket Send: The update is sent to the Django Channels server.

Redis Broadcast: The server publishes the update to the Redis Pub/Sub layer.

Client Receive: Redis broadcasts the update to all connected clients (including the sender's).

Conflict-Free Merge: Each client's Yjs engine merges the update into its local document state, ensuring conflict-free results.

This architecture ensures:

Conflict-free merging

Sub-millisecond sync

Scalable WebSocket broadcasts

Multi-node deployment readiness


## 🤝 Contributing
Pull requests are welcome! Feel free to open an issue to request features or report bugs.

## 📝 License
This project is licensed under the MIT License.
