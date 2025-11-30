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
