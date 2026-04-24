# pose-cam

Browser-based real-time pose, hand, and face detection — no server required.

**Live demo**: https://ota.github.io/pose-cam/

## Features

- Real-time skeleton visualization from camera input
- 5 selectable pose detection models
- Hand finger joint detection (21 keypoints per hand)
- Face mesh and facial feature visualization (478 landmarks)
- Camera flip and mirror mode
- Works on laptops and smartphones

## Models

| Model | Size | Notes |
|-------|------|-------|
| MoveNet Lightning | ~3 MB | Fast, lower accuracy |
| MoveNet Thunder | ~12 MB | Accurate, slower |
| MP Pose Lite | ~3 MB | MediaPipe, lightweight |
| MP Pose Full | ~6 MB | MediaPipe, balanced |
| MP Pose Heavy | ~26 MB | MediaPipe, most accurate |
| Hand Landmarker | ~8 MB | Loaded when Hand is ON |
| Face Landmarker | ~28 MB | Loaded when Face is ON |

## Privacy

All inference runs entirely in the browser. Camera footage is never sent to any server. Model files are downloaded from CDN on first load only.

## Tech Stack

- **TensorFlow.js** — MoveNet inference with WebGL GPU backend
- **MediaPipe Tasks Vision (WASM)** — Pose / Hand / Face landmarker inference
- **WebRTC (getUserMedia)** — Camera access
- **Canvas 2D API** — Skeleton overlay rendering

## Usage

Open https://ota.github.io/pose-cam/ in a browser and allow camera access. No installation needed.

To run locally:

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

> Note: Must be served over HTTP/HTTPS (not `file://`) due to browser security restrictions on WebAssembly and camera access.
