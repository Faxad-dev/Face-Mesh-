# Face Mesh Pro

A browser-based, real-time face analysis dashboard built with **MediaPipe Face Mesh** and vanilla JavaScript. It tracks facial landmarks from your webcam and turns them into live metrics: blink count, mouth-open detection, gaze direction, head pose, and approximate distance from the camera.

Everything runs locally in your browser. No video is uploaded or stored anywhere.

**Live demo:** file:///C:/Users/faada/Desktop/face_mesh.html

![Face Mesh Pro screenshot](file:///C:/Users/faada/Desktop/Screenshot_1.png)

## Features

- **Face mesh overlay:** 468+ landmarks with tesselation, face oval, lips, eyes, and eyebrows
- **Iris tracking and gaze direction:** LEFT / CENTER / RIGHT
- **Blink counter** using Eye Aspect Ratio (EAR)
- **Mouth-open detection** using Mouth Aspect Ratio (MAR)
- **Head pose estimation:** pitch, yaw, and roll (approximate)
- **Distance estimate** from the camera (approximate)
- **Expression hints:** Neutral, Eyes closed, Surprised / Talking, Looking up/down/sideways
- **Multi-face support** (up to 2 faces)
- **5 display modes:** Full, Mesh only, Contours, Minimal, Iris only
- **Toggles** for mesh, iris, bounding box, and HUD
- **Screenshot capture** saved as PNG
- **Live HUD and sidebar** with FPS, gauges, and stats

## Keyboard shortcuts

| Key | Action |
|-----|--------|
| `S` | Take screenshot |
| `M` | Cycle display mode |
| `B` | Toggle bounding box |
| `I` | Toggle iris |
| `H` | Toggle HUD |
| `T` | Toggle mesh |
| `R` | Reset blink counter |

## How it works

| Metric | Method |
|--------|--------|
| Blink | EAR from 6 eye landmarks per eye. A blink is counted when EAR drops below `0.21` and recovers. |
| Mouth open | MAR from the inner lip landmarks. Triggers above `0.35`. |
| Gaze | Iris center position relative to the eye outline. |
| Head pose | Estimated from nose, chin, and eye landmark geometry. |
| Distance | Estimated from the pixel distance between the eyes. |

Head pose and distance use simple geometric approximations, so treat them as indicative values, not precise measurements.

## Run locally

1. Clone the repo:
   ```bash
   git clone https://github.com/YOUR-USERNAME/face-mesh-pro.git
   cd face-mesh-pro
   ```
2. Serve it on localhost (browsers allow camera access only on HTTPS or `localhost`):
   ```bash
   python -m http.server 8000
   ```
   Or use the **Live Server** extension in VS Code.
3. Open `http://localhost:8000` in Chrome.
4. Click **START CAMERA** and allow camera permission.

An internet connection is required because MediaPipe is loaded from a CDN.

## Tech stack

- HTML, CSS, JavaScript (single file, no build step)
- [MediaPipe Face Mesh](https://github.com/google-ai-edge/mediapipe) (Google)
- Canvas 2D API

## Credits

Face detection and landmark extraction are provided by Google's MediaPipe. The dashboard, metric calculations (EAR, MAR, gaze, head pose), UI, and visualization modes are my own work.

## Author

**Fahad Akhtar**
NFC Institute of Engineering and Technology (NFC-IET), Multan

## License

MIT
