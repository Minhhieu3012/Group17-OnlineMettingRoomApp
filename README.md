# 🧑🏻‍💻 HPH Meeting - Online Meeting Application

## 📌 Introduction
HPH Meeting is a simulated online meeting application that supports real-time text chat, voice chat, video calling, and multi-room communication.
Built using a Client–Server architecture with TCP & UDP, the project focuses on being intuitive, easy to understand, and scalable.

---

## 👀 Objectives
- Provide a high-performance real-time communication platform.
- Ensure basic safety during login and data transmission.
- Deliver a simple and intuitive Tkinter-based GUI.

---

## 🔎 Key Features

### 💬 Text Chat (TCP)
- Reliable TCP messaging using length-prefixed JSON.
- Supports room-based group chat.
- Server handles message routing to correct recipients.

### 🎙️ Voice chat (UDP)
- Low-latency audio transmission with UDP.
- Uses PyAudio (16 kHz, mono, PCM).
- Supports microphone on/off control.

### 📹 Video call (UDP)
- Captures webcam → compresses to JPEG → packetizes (MTU 1200B) → sends via UDP.
- Server relays video frames based on active room.
- Client reassembles packets → decompresses → displays video.
- Uses sequence numbers to discard corrupted frames.
- Supports camera on/off control.

### 🏠 Multi-room
- Create, join, and leave rooms.
- Server maintains the room list and members.
- Lobby UI displays real-time room statistics. 

### 🔐 Security
- Login with username + email.
- AES-256-GCM session keys for TCP messages.
- Input validation via regex.
- UDP rate limiting to prevent flooding attacks.

### 🖥️ User Interface
- Tkinter GUI: Login, Lobby, Room.
- Controls for microphone, camera, chat, and room participation.
- WebSocket ⇄ TCP/UDP gateway support (for future expansion).

---

## 🏗️ Architecture
- Server: Manages users, rooms, routing, and relaying data.
- Client: Sends/receives chat, audio, and video.
- Multi-room: Fully supports multiple simultaneous rooms.  

---

## 📋 Requirements
- Python 3.8+
- Thư viện (xem requirements.txt):
-	cryptography>=42.0
-	numpy>=1.24
-	pyaudio>=0.2.13
-	opencv-python>=4.9.0
-	(Optional) Pillow for smoother GUI image processing.

---

## Installation

### 1. Install dependencies
```sh
pip install -r requirements.txt
```

### 2. (Optional) Install audio/video dependencies
#### For video processing:
```sh
pip install opencv-python
```

#### For audio processing (may require build tools):
```sh
pip install pyaudio

```

---

## Quick start

### 1. Start the server
```sh
python main.py
```

### 2. Launch the GUI client
```sh
python -m Client.meeting_gui_client
```


