# Interactive Anatomy WebAR

A browser based augmented reality prototype for exploring heart and body anatomy using custom visual markers, 3D models, and interactive audio labels.

The project explores how marker-based AR can make anatomical structures easier to inspect through a web interface. It combines camera tracking with labeled models and spoken explanations, without requiring a dedicated mobile application.

**Status:** Educational prototype. Marker-based viewing is the primary demonstration; broader device testing and usability evaluation remain future work.

## Author and Contribution

Developed independently by [HindAlz](https://github.com/HindAlz).

I designed and developed the prototype, including the interface, AR scene, marker tracking integration, model presentation, anatomical labels, and interaction controls. The project uses A-Frame and AR.js as its underlying libraries.

## Features

- **Marker based anatomy visualization:** Display a heart or body model when the camera detects its corresponding custom marker.
- **Interactive audio labels:** Tap a speaker label for the aorta, right ventricle, liver, stomach, or ribcage to hear its associated explanation.
- **Labels that follow the models:** Audio buttons track their anatomical anchor positions as the marker or model moves. The visible label is also the tap target.
- **Single clip playback:** Selecting another label switches the explanation. Playback stops when the associated marker is lost.
- **Fixed model sizes:** The body model uses an enlarged display scale. Placement and model zoom controls are not included in the current interface.

## Run Locally

The application is located in **`WebAr/` on the `main` branch**.

Requirements:

- Git and Python 3
- A browser with webcam access
- An internet connection to load A-Frame and AR.js
- The matching visual markers for the heart and body models

```bash
git clone --branch main https://github.com/HindAlz/Interactive-Anatomy-WebAR-Prototype.git anatomy-webar
cd anatomy-webar
python -m http.server 8001 --bind 127.0.0.1 --directory WebAr
```

If your system uses `python3`, replace `python` with `python3`.

Open [http://127.0.0.1:8001/](http://127.0.0.1:8001/) and allow camera access. Serving `WebAr` explicitly opens the active application and keeps its relative asset paths intact.

For phone testing, use an HTTPS deployment. The local address above only works on the computer running the server.

## Using the Prototype

1. Open the application and select **Tap to Start**.
2. Allow camera access when prompted.
3. Point the camera at the matching heart or body marker, printed on paper or displayed on another screen. The **Marker Mode** button provides a reminder of these instructions.
4. Keep the marker fully visible and well lit to display the model and labels.
5. Tap or click a speaker label to play its explanation. Selecting another label switches the audio.

If playback fails, check the connection and tap the label again. Moving the marker out of view stops its audio and hides its labels.

### Marker Requirements

The application uses two custom pattern files:

| Model | Tracking pattern |
| --- | --- |
| Heart | `WebAr/heart-marker.patt` |
| Body | `WebAr/marker.patt` |

These `.patt` files contain tracking data, not printable images. The corresponding visual markers are required; a generic Hiro marker will not substitute for them. Clearly identified printable markers still need to be documented so others can reproduce the demonstration.

## Technology

| Technology | Role |
| --- | --- |
| HTML and CSS | Interface, audio buttons, and styling |
| JavaScript | Application state, interactions, and playback |
| A-Frame | 3D scene and custom components |
| AR.js | Webcam integration and marker tracking |
| Three.js through A-Frame | Projection of model label positions onto the screen |
| GLB and MP3 assets | Anatomical models and audio explanations |

The application runs on the client side and does not require an application backend or database.

## Project Structure

| Path | Purpose |
| --- | --- |
| `WebAr/index.html` | Active application, scene, styling, and interaction code |
| `WebAr/heart.glb` | Heart model |
| `WebAr/body.glb` | Body model |
| `WebAr/audio/` | Anatomical explanation clips |
| `WebAr/heart-marker.patt` | Heart marker pattern |
| `WebAr/marker.patt` | Body marker pattern |
| `WebAr/camera_para.dat` | Camera calibration asset |
| `WebAr/assets/` and `WebAr/models/` | Additional project assets |


## Credits

Built with [A-Frame](https://aframe.io/) and [AR.js](https://github.com/AR-js-org/AR.js).

Sources, creators, and license details for the bundled models, audio, and marker/calibration assets are pending documentation.
