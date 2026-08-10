# AI-DRIVEN-STUDENT-MENTAL-WELLNESS-MONITORING-SYTEM
Desktop app (Python/Tkinter/OpenCV/TensorFlow) that identifies students via webcam face recognition, detects their emotions in real time, and scores classroom wellness. Features batch photo enrollment, live class scans, a sortable dashboard, and per-student trend reports — all stored locally, no cloud required.

🎓 Student Wellness Tracker
Emotion-aware classroom intelligence — a desktop app that identifies students by face and tracks their emotional wellness over time.
Built with Python, Tkinter, OpenCV, and TensorFlow, this app lets teachers enroll students with reference photos, run a live classroom camera scan to detect and identify faces, infer emotional state per student, and review wellness trends through a sortable dashboard and individual student reports.

✨ Features
Batch Enrollment — Add multiple students to a queue before capturing any photos, then save them all at once.
Reference Photo Capture — Capture multiple face photos per student directly from the webcam to improve recognition accuracy.
Automatic Face Matching — An LBPH (Local Binary Patterns Histograms) face recognizer trained on enrolled students' photos identifies who's who during a scan.
Live Class Scan — A single camera session detects all faces in frame, matches them to enrolled students, and classifies their emotion in real time.
Emotion Detection — A CNN (mini-XCEPTION) model classifies each detected face into one of 7 emotions (Angry, Disgust, Fear, Happy, Sad, Surprise, Neutral).
Wellness Scoring — Emotions are mapped to a 0–100 wellness score, aggregated per session and over time.
Smart Dashboard — All students sorted lowest-wellness-first with color-coded status badges (Thriving / Good / Okay / Needs Attention).
Individual Reports — Full session history, sparkline wellness trend chart, and TXT export per student.
Persistent Storage — Simple, portable local storage using a students.json file and a face_db/ photo folder — no external database required.

🖥️ Tech Stack
Component	Technology
UI	Tkinter (custom dark-themed widgets)
Face Detection	OpenCV Haar Cascade
Face Recognition	OpenCV LBPH Face Recognizer
Emotion Classification	TensorFlow / Keras (mini-XCEPTION, FER2013)
Image Handling	Pillow (PIL)
Data Storage	JSON (local file-based)

📦 Requirements
Python 3.8+
A webcam
The following Python packages:
opencv-contrib-python
tensorflow
numpy
pillow



On first launch, the app will automatically download the Haar cascade face detector and the pretrained emotion recognition model. This requires an internet connection the first time only.

🧭 How It Works
Enroll — Go to the Enroll page, fill in a student's name/ID/class, add them to the queue, then open the camera and capture 5–8 reference photos per student for best recognition accuracy.
Save All — Once photos are captured, save the queue. This writes student records to students.json and photos to face_db/, then retrains the face recognizer.
Scan — Start a Class Scan session. The app detects all faces on camera, matches them against enrolled students, and logs an emotion reading each frame.
Stop & Save — Ending the scan computes each identified student's session wellness score and appends it to their history.
Dashboard — View all students sorted by wellness (lowest first) with color-coded status.
Report — Double-click any student to see their full history, a wellness trend sparkline, and export a text report.


📁 Project Structure
.
├── app23.py                 # Main application (all pages & logic)
├── students.json             # Auto-generated: student records & session history
├── face_db/                  # Auto-generated: reference face photos
├── haarcascade_frontalface_default.xml   # Auto-downloaded on first run
└── emotion_model.hdf5        # Auto-downloaded on first run


⚠️ Notes & Limitations
Face recognition accuracy depends heavily on the number and variety of reference photos captured per student (more angles/lighting = better accuracy).
This project is intended for educational/demo purposes involving facial recognition and emotion inference — consider privacy, consent, and applicable regulations (e.g. student data privacy laws) before deploying in a real classroom setting.
students.json and face_db/ contain personally identifiable data and should not be committed to a public repository. Add them to .gitignore.


