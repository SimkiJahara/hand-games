# ✋ Neural Link — Hand Games

Play **Tic Tac Toe** and **Connect Four** against a friend using nothing but your webcam and hand gestures. No mouse, no keyboard — just your hands, real-time hand tracking, and a live video call between players.

A single, self-contained `index.html` powers everything: gesture detection, game logic, multiplayer sync, and peer-to-peer video chat.

## ✨ Features

- **Hand gesture controls** — powered by [MediaPipe Hands](https://developers.google.com/mediapipe) for real-time hand & finger tracking
- **Two games in one room** — Tic Tac Toe (3×3) and Connect Four (6×7), switchable mid-session
- **Online multiplayer** — create a room, share a 6-character code, and play with a friend anywhere
- **Live video call** — see and hear your opponent via WebRTC while you play
- **Recording & sharing** — record your match (game canvas + camera) and download or share the clip
- **Animated cyberpunk UI** — glowing skeleton overlays, neon boards, and a futuristic lobby

## 🎮 How to Play

| Gesture | Action |
|---|---|
| ✋ Right hand | Aim / hover over a cell or column |
| 🤜 Left fist (held ~0.6s) | Confirm and place your piece |
| ✌️✌️ Both hands "peace" (held ~0.8s) | Start a new game |

The video background automatically switches between your camera and your opponent's camera depending on whose turn it is.

## 🚀 Getting Started

1. Clone or download this repository.
2. Set up a free [Firebase](https://firebase.google.com/) project with a Realtime Database (used for matchmaking and game state sync).
3. Set up a free [TURN/STUN server](https://www.metered.ca/tools/openrelay/) (needed for reliable peer-to-peer video across networks).
4. Open `index.html` and fill in your credentials in the two config blocks near the top of the `<script>` section:

```js
// Firebase project config
const firebaseConfig = {
  apiKey: "YOUR_FIREBASE_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.YOUR_REGION.firebasedatabase.app",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.firebasestorage.app",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

// TURN/STUN servers for video calls
const ICE_SERVERS = {
  iceServers: [
    { urls: "stun:stun.metered.ca:80" },
    { urls: "turn:global.relay.metered.ca:80", username: "...", credential: "..." }
    // ...add your TURN credentials here
  ]
};
```

5. Host the file on **HTTPS** (camera/microphone access requires a secure context — `localhost` also works for local testing).
6. Open the page, allow camera & microphone access, and either **Create a Room** or **Join** with a friend's code.

## 🛠️ Tech Stack

- **MediaPipe Hands** — hand landmark detection
- **Firebase Realtime Database** — room creation, matchmaking, and game state sync
- **WebRTC** — peer-to-peer video/audio calls and hand-landmark data channel
- **Canvas API** — game board rendering and gesture skeleton overlay
- Vanilla HTML / CSS / JavaScript — no build step required

## 🌐 Requirements

- A modern browser with WebRTC and `getUserMedia` support (Chrome, Edge, or Firefox recommended)
- Webcam and microphone
- HTTPS hosting (or localhost)

## 📄 License

This project is licensed under the [MIT License](LICENSE) — © 2026 Umme Jahara Simki & Mirza Golam Karim Chowdhury.
