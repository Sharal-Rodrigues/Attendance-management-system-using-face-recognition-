# Attendance Management System Using Face Recognition

[![Made with Python](http://ForTheBadge.com/images/badges/made-with-python.svg)](https://www.python.org/)
[![Python 3.9](https://img.shields.io/badge/python-3.9-blue.svg)](https://www.python.org/downloads/release/python-390/)

An attendance system that uses face recognition to automatically identify students and mark their attendance, removing the need for manual roll calls. The repository includes **two implementations**:

1. A **desktop application** (Python, OpenCV, Tkinter) — the original offline version.
2. A **full-stack web application** (Next.js frontend + Flask/MongoDB backend) — a modern, browser-based version with student/teacher roles.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started — Desktop App](#getting-started--desktop-app)
- [Getting Started — Web App](#getting-started--web-app)
- [Screenshots](#screenshots)
- [Notes](#notes)
- [Contributing](#contributing)
- [License](#license)

---

## Features

### Desktop App
- Register new students by capturing face images via webcam
- Train a face-recognition model on the captured images
- Automatically detect faces and mark attendance in real time
- Attendance saved as subject-wise CSV files with timestamps
- View attendance records in a simple table view
- Text-to-speech feedback during registration/recognition

### Web App
- Modern responsive UI built with Next.js and Tailwind CSS
- In-browser face detection using `face-api.js`
- Separate **Student** and **Teacher** roles with authentication
- Teachers can start attendance sessions; students can register and view their own attendance
- Deep learning–based face recognition on the backend (DeepFace + MTCNN)
- Data stored in MongoDB
- Real-time updates via Socket.IO

---

## Tech Stack

| Layer | Technologies |
|---|---|
| Computer Vision / ML | OpenCV, Haar Cascade classifiers, DeepFace, MTCNN |
| Desktop App | Python, Tkinter, Pandas, NumPy, Pillow, pyttsx3 |
| Backend (Web) | Flask, Flask-CORS, Flask-Bcrypt, PyMongo, python-dotenv |
| Frontend (Web) | Next.js 15, React 19, TypeScript, Tailwind CSS, face-api.js, Socket.IO client |
| Database | MongoDB |

---

## Project Structure

```
Attendance-Management-system-using-face-recognition/
│
├── attendance.py               # Main desktop app entry point (Tkinter GUI)
├── takeImage.py                 # Capture student face images
├── trainImage.py                 # Train the face recognition model
├── automaticAttedance.py        # Real-time face recognition + attendance marking
├── takemanually.py               # Manual attendance entry
├── show_attendance.py            # View attendance records
├── haarcascade_frontalface_*.xml # Pretrained face detection classifiers
├── TrainingImageLabel/            # Trained model output
├── StudentDetails/                # Registered student data (CSV)
├── requirements.txt
│
├── backend/                     # Flask REST API (web app)
│   ├── app.py
│   ├── recognition.py
│   ├── auth/                    # Signup / login routes
│   ├── student/                 # Registration, attendance view, demo session
│   ├── teacher/                 # Attendance session management
│   └── requirements.txt
│
└── frontend/                    # Next.js web client
    ├── app/
    │   ├── student/              # Student dashboard, registration, attendance view
    │   ├── teacher/              # Teacher dashboard, start session, update details
    │   ├── signin/, signup/
    │   └── components/           # UI components (camera capture, navbar, sections, etc.)
    └── package.json
```

---

## Getting Started — Desktop App

### Requirements
- Python 3.6+
- A working webcam

### Installation

```bash
git clone https://github.com/<your-username>/Attendance-Management-system-using-face-recognition.git
cd Attendance-Management-system-using-face-recognition
pip install -r requirements.txt
```

### Usage

1. Create a `TrainingImage` folder in the project root (if not already present).
2. Open `attendance.py` and `automaticAttedance.py` and update any file paths to match your system.
3. Run the app:
   ```bash
   python attendance.py
   ```
4. **Register a new student** — click *Register New Student*, enter an ID and name, then click *Take Image* to capture face samples via webcam.
5. Click **Train Image** to train the recognition model on the captured images.
6. Click **Automatic Attendance**, enter the subject name, and the system will recognize faces and mark attendance automatically.
7. Click **View Attendance** to see records in tabular format. A separate CSV file is generated per subject.

---

## Getting Started — Web App

### Requirements
- Node.js 18+
- Python 3.9+
- MongoDB (local or hosted, e.g. MongoDB Atlas)

### Backend Setup

```bash
cd backend
pip install -r requirements.txt
```

Create a `.env` file in `backend/` with:

```
MONGODB_URI=mongodb://localhost:27017/
DATABASE_NAME=facerecognition
```

Run the backend:

```bash
python app.py
```

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The app will be available at `http://localhost:3000`.

---

## Screenshots

| Registration | Attendance |
|---|---|
| ![Register](UI_Image/register.png) | ![Attendance](UI_Image/attendance.png) |

More screenshots are available in the [`Project Snap`](./Project%20Snap) folder.

---

## Notes

- Face recognition accuracy depends on image quality and lighting — capture more, well-lit training images for better results.
- The desktop app requires reasonable processing power for real-time detection.
- `__pycache__`, `.next`, `.idea`, and `.vscode` folders are build/editor artifacts and are excluded from version control (see `.gitignore`).

---

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to open a pull request or issue.

## License

This project is open source. Add a `LICENSE` file to specify usage terms (e.g., MIT).

---

⭐ If you find this project useful, consider starring the repository!
