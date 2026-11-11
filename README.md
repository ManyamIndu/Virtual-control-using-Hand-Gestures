<div align="center">

# ✋ Voice & Gesture Control

Control common desktop actions with spoken commands and hand gestures.

Built with **Python**, **OpenCV**, and **MediaPipe**.

</div>

---

## ✨ What it does

The project listens for a voice command, then uses your webcam to recognize hand gestures and trigger desktop actions.

| Script | Voice command | Gesture/action |
| --- | --- | --- |
| [`main.py`](main.py) | `stop application` | Make a fist to send **Alt + F4** |
|  | `control volume` | Change the distance between thumb and index finger |
|  | `switch tab` | Pinch thumb and index finger to send **Alt + Tab** |
|  | `scroll` | Swipe your index finger up or down to scroll |
| [`CSP.py`](CSP.py) | `detect app` | Make a fist to send **Alt + F4** |
| [`CSP2.py`](CSP2.py) | `detect volume` | Change the distance between thumb and index finger |
| [`CSP3.py`](CSP3.py) | `switch tab` | Pinch thumb and index finger to send **Alt + Tab** |
| [`CSP4.py`](CSP4.py) | `scroll` | Swipe your index finger up or down to scroll |

`main.py` is the combined version. The `CSP*.py` scripts are separate, single-action examples.

## 🚀 Get started

### Requirements

- Python installed with a version supported by your installed MediaPipe release
- A webcam
- A microphone
- An internet connection for Google speech recognition

### Install dependencies

From the project directory, install the libraries used by the scripts:

```bash
python -m pip install opencv-python mediapipe pyautogui SpeechRecognition
```

SpeechRecognition needs **PyAudio** for microphone input. If microphone initialization fails, install PyAudio using the instructions for your operating system and Python version.

### Run a controller

Start the combined voice-and-gesture controller:

```bash
python main.py
```

Or run a single-action example:

```bash
python CSP.py
python CSP2.py
python CSP3.py
python CSP4.py
```

Speak the command shown in the table when prompted. When the webcam window opens, press **Q** to close the gesture-control window.

## 🧭 How it works

1. SpeechRecognition captures a command and sends it to Google's speech-recognition service.
2. OpenCV reads frames from the default camera.
3. MediaPipe Hands tracks hand landmarks in each frame.
4. The script maps recognized gestures to keyboard shortcuts, volume keys, or scrolling through PyAutoGUI.

## ⚠️ Safety & privacy

- These scripts can control the **currently active desktop session**. In particular, a fist in `CSP.py` or while `main.py` is listening for `stop application` sends **Alt + F4** and may close the foreground application.
- Use the gesture controls only when you intend to trigger desktop actions, and close the camera window with **Q** to stop gesture processing.
- Speech recognition uses Google's online service. Do not speak sensitive information while using it.
- Webcam frames are processed locally by MediaPipe; the speech-recognition request requires an internet connection.

## 🛠️ Troubleshooting

| Problem | Try this |
| --- | --- |
| Camera window does not open | Check that a webcam is connected and available to other applications. |
| Microphone initialization fails | Confirm microphone access is enabled and install PyAudio for your Python environment. |
| Speech is not recognized | Speak the expected command clearly and check your internet connection. |
| Desktop action does not work | Keep the intended target application active and check that your operating system permits keyboard automation. |

## 📁 Project files

```text
.
├── main.py   # Combined voice-controlled gesture actions
├── CSP.py    # Fist gesture: close the active window
├── CSP2.py   # Pinch distance: volume control
├── CSP3.py   # Pinch gesture: switch windows
└── CSP4.py   # Swipe gesture: scroll
```

---

<div align="center">
Made for hands-free desktop interaction · Use thoughtfully
</div>
