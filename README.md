# QuickGPT

QuickGPT is a full-stack AI chat application with a React/Vite frontend and an Express/MongoDB backend. It supports authenticated chat sessions, chat history, credits, and a community area.

## Tech Stack

- Frontend: React, Vite, Tailwind CSS
- Backend: Node.js, Express
- Database: MongoDB
- AI: OpenAI-compatible API configured for Google Gemini
- Payments: Stripe webhooks
- Media: ImageKit

## Project Structure

```text
QuickGPT/
├── client/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   │   ├── assets.js
│   │   │   └── prism.css
│   │   ├── components/
│   │   │   ├── ChatBox.jsx
│   │   │   ├── Message.jsx
│   │   │   └── Sidebar.jsx
│   │   ├── context/
│   │   │   └── AppContext.jsx
│   │   ├── pages/
│   │   │   ├── Community.jsx
│   │   │   ├── Credits.jsx
│   │   │   ├── Loading.jsx
│   │   │   └── Login.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   └── vercel.json
├── server/
│   ├── configs/
│   │   ├── db.js
│   │   ├── imageKit.js
│   │   └── openai.js
│   ├── controllers/
│   │   ├── chatController.js
│   │   ├── creditController.js
│   │   ├── messageController.js
│   │   ├── userController.js
│   │   └── webhooks.js
│   ├── middlewares/
│   │   └── auth.js
│   ├── models/
│   │   ├── Chat.js
│   │   ├── Transaction.js
│   │   └── User.js
│   ├── routes/
│   │   ├── chatRoutes.js
│   │   ├── creditRoutes.js
│   │   ├── messageRoutes.js
│   │   └── userRoutes.js
│   ├── package.json
│   ├── server.js
│   └── vercel.json
├── README.md
└── QuickGPT_How_To_Run_Project.pdf
```

### Client Layout

- `src/components/` contains reusable UI pieces like the chat box, message bubble, and sidebar.
- `src/pages/` contains route-level screens such as login, loading, credits, and community.
- `src/context/AppContext.jsx` manages shared app state.
- `src/assets/` stores icons, images, and prism styles.

### Server Layout

- `configs/` contains database and external service configuration.
- `controllers/` contains request handlers for chat, credits, messages, users, and webhooks.
- `middlewares/` contains authentication middleware.
- `models/` contains MongoDB schemas.
- `routes/` contains API route definitions.
- `server.js` boots the Express server and registers all routes.

## Features

- User login and session handling
- AI chat with saved conversations
- Credit-based usage flow
- Community page
- Stripe webhook handling on the backend

## Prerequisites

- Node.js 18 or newer
- MongoDB connection string
- AI API key for the backend

## Environment Variables

Create a `.env` file in `server/` with at least:

- `MONGODB_URI` - MongoDB connection string
- `GEMINI_API_KEY` - API key used by the OpenAI-compatible client
- `PORT` - optional server port, defaults to `3000`

Create a `.env` file in `client/` with at least:

- `VITE_SERVER_URL` - backend URL for the frontend API calls

## Install

From the `QuickGPT/` directory, install dependencies for both apps:

```bash
cd server
npm install

cd ../client
npm install
```

## Run Locally

Start the backend first:

```bash
cd server
npm run start
```

In a second terminal, start the frontend:

```bash
cd client
npm run dev
```

## Build

To build the frontend for production:

```bash
cd client
npm run build
```

## Notes

- The backend health check responds at `/`.
- The frontend expects the API server URL through `VITE_SERVER_URL`.
- Stripe webhook traffic is handled at `/api/stripe`.