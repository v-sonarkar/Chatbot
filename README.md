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

- `client/` - React app
- `server/` - API server

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