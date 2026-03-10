# PSL Sign Language Translation — Frontend

Web interface for the Audio-to-Sign-Language translation system. Users upload an MP3 file and watch a 3D avatar perform Pakistan Sign Language (PSL) gestures in real-time with Three.js.

## Live URL

| Service | URL |
|---------|-----|
| **Frontend UI** | https://frontend-ten-black-54.vercel.app |
| **Backend API** | https://psl-sign-language-api.onrender.com |

## How It Works

1. User uploads an MP3 audio file
2. Frontend sends it to the backend API (`POST /upload`)
3. Polls `/status/<job_id>` every second for live progress updates
4. Displays intermediate results as they arrive:
   - **Step 1:** Transcribed text (from Whisper)
   - **Step 2:** Gloss notation (NLP conversion)
   - **Step 3:** Matched PSL video sequence
   - **Step 4:** Extracted keypoints
5. When processing completes, loads the animated GLTF avatar via Three.js
6. Plays the sign language animation with synchronized captions

## Project Structure

```
frontend/
├── index.html      # Main application (HTML + CSS + JS)
├── config.js       # Backend URL configuration (edit this for your deployment)
├── vercel.json     # Vercel deployment config
├── netlify.toml    # Netlify deployment config (alternative)
└── .gitignore
```

## Configuration

Edit `config.js` to point to your backend:

```javascript
window.BACKEND_URL = 'https://psl-sign-language-api.onrender.com';
```

For local development:
```javascript
window.BACKEND_URL = 'http://localhost:5000';
```

## Local Development

```bash
# Clone
git clone https://github.com/Usman-debug-coder/sign-language-frontend.git
cd sign-language-frontend

# Serve with any static file server
python3 -m http.server 8080

# Open http://localhost:8080
# Make sure the backend is running at the URL in config.js
```

## Deployment (Vercel — Free)

This repo is deployed on [Vercel](https://vercel.com) with auto-deploy on push to `main`.

- **Project:** `frontend` under `p229114ict-7198s-projects`
- **Production URL:** https://frontend-ten-black-54.vercel.app
- **Connected repo:** `Usman-debug-coder/sign-language-frontend`

To deploy your own:
1. Fork this repo
2. Go to [vercel.com](https://vercel.com) → New Project → Import your fork
3. Framework Preset: **Other** (it's a static site)
4. Click Deploy
5. Update `config.js` with your backend URL and push

## Tech Stack

- **Three.js** (v0.159.0) — 3D avatar rendering & GLTF animation
- **OrbitControls** — Camera controls for the 3D viewer
- **GLTFLoader** — Loading animated avatar models
- **Vanilla JS** — No framework dependencies

## Related

- Backend API: [Usman-debug-coder/sign-language-backend](https://github.com/Usman-debug-coder/sign-language-backend)
