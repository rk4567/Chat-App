# Chat App (React + Vite + Firebase)

This is a small real-time chat application built with React, Vite and Firebase.

It demonstrates a simple chat flow with authentication, profile update, real-time messaging, image uploads (Firebase Storage), and a responsive UI.

---

## Features ✅
- Email/password signup and login
- Password reset via email
- Profile update (name, bio, avatar upload)
- Search users and start conversations
- Real-time chat with messages
- Image upload (Firebase Storage)
- Notification UI with `react-toastify`

---

## Tech Stack 🔧
- React 18
- Vite
- Firebase (Auth, Firestore, Storage)
- react-router-dom
- react-toastify
- ESLint

---

## Quick Start 💡

Prerequisites:
- Node.js 18+ (recommended)

1) Clone the repo and install dependencies:

```bash
git clone <repo-url>
cd chat-app
npm install
```

2) Configure Firebase

- Create a project in Firebase Console.
- Enable Email/Password Authentication.
- Enable Firestore and (optionally) Storage.
- Add your Firebase credentials to a `.env` file with the `VITE_` prefix. Example values are in `.env.example`.

Example `.env` file (root of project):
```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

> Note: This project reads Firebase config from environment variables (Vite `import.meta.env`) — see `src/config/firebase.js`. This avoids committing production keys to Git (also `.env` is in `.gitignore`).

3) Start the development server:

```bash
npm run dev
```

4) Build & preview for production:

```bash
npm run build
npm run preview
```

---

## Scripts
- `npm run dev` - Run development server (Vite HMR)
- `npm run build` - Production build
- `npm run preview` - Serve the built app locally
- `npm run lint` - Run ESLint on the codebase

---

## Project Structure 📁

- `index.html` - App entry (Vite)
- `src/main.jsx` - React app bootstrap
- `src/App.jsx` - App routes and main layout
- `src/assets` - Icons and images
- `src/components` - Reusable UI components (LeftSidebar, ChatBox, RightSidebar)
- `src/pages` - Page screens (Login, Chat, ProfileUpdate)
- `src/config/firebase.js` - Firebase initialization & auth functions (login/signup/logout/reset)
- `src/context/AppContext.jsx` - App-level context to store user/chat state
- `src/lib/upload.js` - Image upload using Firebase Storage

---

## Firebase Collections and Expected Data

- `users` collection — holds user profiles (id, email, username, avatar, name, bio, lastSeen)
- `chats` collection — stores a 'chats' document for each user with `chatsData` list (messageId, rId, lastMessage, updatedAt, messageSeen)
- `messages` collection — each doc represents a conversation with `messages` array and an index for message IDs

The app creates a `chats` document automatically on signup and creates a new `messages` doc as conversations are started.

---

## Deployment 🚀
- This repo includes a `vercel.json` file for convenient deployment on Vercel, but you can use any static host that supports single-page apps.

Suggested steps to deploy to Vercel:
```bash
npm run build
# Use vercel cli or connect the repo to vercel.com for automatic deployments
```

---

## Security and Environment Tips ⚠️
- Do not push production `firebaseConfig` credentials to a public repository.
- Configure Firestore and Storage security rules to prevent unauthorized access.
- Prefer environment variables (`.env`) for secrets with Vite (e.g., `VITE_FIREBASE_API_KEY`) and reference them in `src/config/firebase.js`.

---

## Contributing
Contributions are welcome — open an issue or submit a PR.

---

## License
MIT

---

If you'd like a quick patch to move Firebase configuration into `.env` and load it from `import.meta.env` (Vite), I can implement that change next. 💡
# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available: 12

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh
