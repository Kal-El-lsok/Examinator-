# Examinator-
# Examinator – AI-Powered Exam Integrity System

**Built by Nasara John**


📌 Overview

Examinator is a complete, AI-powered exam monitoring system designed to detect, prevent, and document examination malpractice in real-time. It integrates **five detection layers** into one affordable, offline-capable system.



🎯 Problem Statement

Examination malpractice is a global crisis affecting educational integrity. Current solutions are failing:
- Human invigilators cannot monitor 100+ students alone
- CCTV records but does not alert in real-time
- Metal detectors only work at entry
- Signal jammers are illegal in most countries
- AI proctoring requires internet and is expensive



🚀 Solution

Examinator solves all of these problems with **five detection layers** working simultaneously:

1. Face Recognition
- WiFi cameras capture faces at entrance
- AI matches against registered database
- Flags unknown persons and duplicate entries
- Saves timestamped snapshots as evidence

2. Sound Triangulation
- 4-microphone array detects whispering and verbal cheating
- Triangulates exact sound source location
- Pinpoints which desk the sound came from
- Saves audio recordings as evidence

3. Movement & Lip AI
- Pose estimation tracks body movements
- Detects head turning and suspicious gestures
- Monitors lip movement (silent whispering)
- Saves video clips as evidence

4. Smart Paper Detection
- Thermal camera detects body heat from hidden notes
- UV LEDs reveal invisible ink
- IR sensors detect unauthorized objects on desks
- Saves thermal images and snapshots as evidence

5. Complete Phone Detection
- ESP32 sensors detect Bluetooth and WiFi signals
- RTL-SDR dongle detects mobile data (4G/5G)
- Triangulates device location to specific seat
- The **only system** that detects mobile data usage
- Saves device IDs and timestamps as evidence


🖥️ Web Dashboard

- **Live video feed** from all cameras
- **Interactive seat map** with color-coded alerts
- **Real-time event log** with timestamps
- **Audio warning controls** (manual or auto)
- **Evidence review section** (video, audio, images)
- **Accessible from any device** (phone, tablet, laptop)

 ⚙️ Technical Architecture

### Hardware
- Raspberry Pi 5 (8GB RAM) – Main brain
- 2x WiFi IP Cameras – Face recognition
- 1x USB Webcam – Movement detection
- 4x Microphone Modules – Sound triangulation
- 4x ESP32 Boards – Phone detection
- 1x RTL-SDR Dongle – Mobile data detection
- 1x Thermal Camera (MLX90640) – Paper detection
- 4x UV LEDs – Invisible ink detection
- 4x IR Sensors – Object detection
- 1x Arduino Nano – Sensor control
- USB Speakers – Audio warnings

Software
- Python (AI models, backend)
- OpenCV – Face and movement processing
- MediaPipe – Pose and lip detection
- Flask – Web dashboard
- SQLite – Evidence database
- gTTS – Text-to-speech warnings


📊 Current Status

| Area | Status |
|------|--------|
| Software Development | ✅ Complete |
| AI Models | ✅ Tested and working |
| Web Dashboard | ✅ Fully functional |
| Hardware Design | ✅ Complete |
| Bill of Materials | ✅ Finalized |
| Wiring Diagrams | ✅ Documented |
| Problem Validation | ✅ Confirmed with invigilators |
| School Interest | ✅ Multiple schools ready for pilot |
| Hardware Prototype | ⏳ Awaiting components |


🔗 Links
Email: kalelthelsok@gmail.com

📁 Documentation

- [Wiring Diagrams](docs/wiring_diagrams.md) – Complete wiring diagrams for all modules
- [Hardware BOM](docs/hardware_bom.md) – Complete Bill of Materials
- [System Architecture](docs/system_architecture.md) – Technical system design
- [Logo](images/logo.png) – Project logo

📧 Contact

Nasara John
Founder & Lead Developer, Examinator  
Email: kalelthelsok@gmail.com

"Fair exams for every student, in every country."


© 2026 Nasara John. All rights reserved.
