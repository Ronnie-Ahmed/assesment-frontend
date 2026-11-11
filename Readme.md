# Secure Notes Frontend

A minimal single-page frontend for the Secure Notes API. It is one static file (`index.html`) with no build step and no dependencies. Visual polish was not a goal, so it focuses on functionality and integration.

## Links

- Live frontend: `https://assesment-frontend-opal.vercel.app/`
- Live backend API: https://assesment-gamma-taupe.vercel.app
- Backend repository: `https://github.com/Ronnie-Ahmed/Assesment_2026`

Login details for a test admin account are in the submission message.

## What it does

- Register and log in (the token is kept in `localStorage`).
- **Notes tab:** create, edit, delete and list your own notes, with "Load more" pagination.
- **Posts tab:** create posts, browse everyone's posts, and show all posts of one user by id.
- **Admin tab** (admin accounts only): add, edit, delete and list users, list everyone's notes, and view users grouped by interest, optionally filtered to one interest.
- Returns you to the login form when your session expires.

The Admin tab is hidden for regular users as a convenience only. The real protection is on the API, which answers 403 to non-admins.

## How it talks to the API

The page calls the API at the address in the `API_BASE` constant near the top of the script in `index.html`. Requests send `Authorization: Bearer <token>`. The backend allows this page through CORS using its `FRONTEND_ORIGIN` setting, which must match this site's exact URL.

All user-supplied text is inserted with `textContent`, never `innerHTML`, so stored text cannot run as script.

## Run locally

Open `index.html` in a browser, or serve the folder with any static server. To use a local backend, change `API_BASE` to `http://localhost:5000` and set the backend's `FRONTEND_ORIGIN` to the origin you are serving from.

## Deploy

Import this repository into Vercel (or drag the folder onto Netlify) with the framework preset set to "Other" and no build command.