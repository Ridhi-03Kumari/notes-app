# Likho — Notes App

Likho is a small full-stack notes app I built to understand how authentication, a REST API, and a database actually fit together in a real project. You sign up, log in, and your notes stay yours — you can write, edit, search, tag, and delete them, in either a light or dark theme.

## Links

- Live demo: https://gilded-babka-4f914b.netlify.app
- Backend API: https://notes-app-production-86e1.up.railway.app
- Source code: https://github.com/Ridhi-03Kumari/notes-app

You can try it straight from the live demo above — create an account, or log in and start writing.

## What it does

- Lets you create an account and log in securely — passwords are hashed, and sessions use JWT
- Keeps each person's notes private, so you only ever see your own
- Covers the full set of note actions: create, read, update, and delete
- Lets you search across titles, content, and tags
- Lets you tag notes to keep them organised
- Comes with a light and a dark theme

## How it's built

The backend is a Node.js and Express REST API. It stores data in MongoDB Atlas through Mongoose and handles authentication with JSON Web Tokens and bcrypt. The frontend is a single HTML file with plain JavaScript that talks to the API using fetch — no framework, just the essentials.

In production, the frontend is hosted on Netlify, the backend runs on Railway, and the database lives on MongoDB Atlas.

## Project structure

```
notes-app/
├── backend/
│   ├── middleware/auth.js   # verifies the JWT on protected routes
│   ├── models/              # User and Note schemas
│   ├── routes/              # auth and notes routes
│   ├── index.js             # server entry point
│   └── package.json
└── frontend/
    └── index.html           # the entire frontend, in one file
```

## API reference

All protected routes expect an `Authorization: Bearer <token>` header.

| Method | Endpoint | What it does | Needs auth |
|--------|----------|--------------|------------|
| POST | `/api/auth/register` | Create a new account | No |
| POST | `/api/auth/login` | Log in and get a token | No |
| GET | `/api/notes` | List your notes | Yes |
| POST | `/api/notes` | Create a note | Yes |
| PUT | `/api/notes/:id` | Update a note | Yes |
| DELETE | `/api/notes/:id` | Delete a note | Yes |

## Running it locally

Start with the backend:

```bash
cd backend
npm install
```

Create a `.env` file inside `backend/` with your own values:

```
MONGO_URI=your_mongodb_atlas_connection_string
JWT_SECRET=your_secret_key
PORT=5000
```

Then start the server:

```bash
npm start
```

For the frontend, open `frontend/index.html` in your browser, or serve it with something like VS Code's Live Server. If you're running your own backend, point the `API` constant near the top of the file at your backend's address.

## About

Built by Ridhi Kumari. You can find more of my work on GitHub at [@Ridhi-03Kumari](https://github.com/Ridhi-03Kumari).
