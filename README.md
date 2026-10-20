# Orbit AI — Business Assistant (GitHub Pages starter)

A responsive, single-file GitHub Pages frontend for a multilingual business AI assistant. It includes a dashboard, local chat preview, knowledge-note UI, social post drafting, and phone/social setup checklists.

## What works now
- Responsive frontend with navigation
- Local demo chat (not a live LLM)
- Session-only knowledge notes
- Social post draft generation and copy
- Optional chat endpoint configuration for a backend you deploy
- No third-party JavaScript dependencies

## What does NOT work until you connect services
- Real phone calls or call transfers
- Real WhatsApp/Instagram/Facebook/LinkedIn/X messages
- Publishing posts
- Live LLM/RAG responses unless a compatible backend is configured
- Persistent storage or login

## Deploy to GitHub Pages
1. Open your GitHub repository.
2. Back up the existing files (especially `index.html`) before replacing anything.
3. Upload `index.html` from this folder to the repository root (the same level as README.md).
4. Commit the change to the branch/folder configured in **Settings → Pages**.
5. In **Settings → Pages**, set the correct source branch and folder (commonly `main` and `/ (root)`).
6. Wait for the Pages deployment to finish, then open the published URL and refresh. If you still see a blank page, check that `index.html` is in the published root and inspect the browser console.

## Fixing a blank white page
- Confirm the filename is exactly `index.html` (not `Index.html` or `index.html.txt`).
- Confirm it is in the Pages source folder, not only inside a subfolder.
- Open **Actions** in GitHub and check the latest Pages workflow for errors.
- Open the published URL in a private/incognito tab or hard-refresh to avoid stale cached files.
- This starter uses plain HTML/CSS/JavaScript and no build step, framework, package manager, or external library.
- If your repository is a project site, its URL typically looks like `https://USERNAME.github.io/REPOSITORY/`; use that exact published URL.

## Connect a secure LLM/RAG backend (production outline)
1. Deploy an API using FastAPI/Node.js on a backend host. GitHub Pages is static hosting and must not hold secrets.
2. Add provider API keys as **server-side environment variables** in the backend host's secret settings. Never put keys in this repository or in frontend JavaScript.
3. Add authentication, authorization, rate limits, request validation, HTTPS, logging, and CORS allowlisting for your exact GitHub Pages origin.
4. Implement `POST /api/chat`, accepting JSON like:
   `{"message":"What are your opening hours?","language":"en"}`
   and returning JSON like:
   `{"reply":"Our hours are ..."}`
5. For RAG, ingest approved business documents/FAQs into a database, chunk the content, generate embeddings, retrieve relevant chunks per question, and provide only those chunks to the LLM. Enforce tenant/user access controls on every retrieval.
6. Set the API base URL and endpoint path in the frontend Settings section. This prototype keeps that URL in memory for the current page session.
7. Add a real authentication flow before exposing customer or business data. Do not rely on an unguessable URL as authentication.

## Phone-call integration
- Choose a telephony/voice provider that supports your region and desired languages.
- Configure the provider's inbound number/webhook to your backend.
- Use a real-time voice agent or speech-to-text + LLM + text-to-speech pipeline.
- Add consent/privacy notices, call recording rules, human handoff, timeouts, emergency handling, and audit logs.
- Test using a non-production number before routing business calls.

## Social media integration
- Use official APIs and follow each platform's business-account, permission, app review, messaging-window, and publishing rules.
- Configure OAuth on the backend. Keep access tokens server-side and encrypt them at rest.
- Receive platform webhooks on your backend and verify their signatures.
- Start with drafts and human approval; only enable sending/publishing after permissions and safeguards are tested.

## Suggested next steps
1. Deploy the static frontend and confirm it loads.
2. Choose a backend host and LLM provider.
3. Add secure login and `/api/chat`.
4. Add a database and RAG retrieval.
5. Connect one channel at a time (for example WhatsApp Business, then voice calls).
6. Add monitoring, consent, and human escalation before live use.
