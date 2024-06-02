
# AI BASED EXAM PROCTORING SYSTEM

**Overview:**
The AI-Based Exam Proctoring System is an advanced solution designed to ensure the integrity and security of online examinations. Leveraging cutting-edge artificial intelligence technologies, this system monitors students during exams to detect and prevent cheating, ensuring a fair and credible assessment process.

**Features:**
- **Real-Time Monitoring:** The system uses webcam and microphone inputs to continuously monitor the test-taker, ensuring they remain focused on the exam.
- **Facial Recognition:** Verifies the identity of the test-taker to prevent impersonation.
- **Behavior Analysis:** Detects suspicious behaviors such as looking away from the screen frequently, unusual movements, or multiple people in the room.
- **Audio Analysis:** Monitors for sounds that might indicate cheating, such as conversations or the use of unauthorized devices.
- **Environment Scanning:** Uses computer vision to scan the test-taker's surroundings for unauthorized materials or devices.
- **Automated Alerts:** Generates real-time alerts for any detected anomalies, allowing human proctors to review flagged events promptly.
- **Post-Exam Review:** Provides detailed reports and recordings of the exam session for further review and analysis.

**Target Audience:**
- **Educational Institutions:** Schools, colleges, and universities seeking a reliable method to administer online exams with integrity.
- **Certification Bodies:** Organizations that offer professional certifications and need to maintain high standards of exam security.
- **Corporate Training Programs:** Companies providing internal training and certification programs for employees, ensuring the credibility of the assessments.
- **Online Course Providers:** Platforms offering MOOCs (Massive Open Online Courses) and other e-learning programs that require secure testing environments.

By ensuring a secure and fair examination process, the AI-Based Exam Proctoring System helps educational and certification institutions uphold their standards and maintain the trust of their stakeholders.

**Prerequisites:**

To run the programs in this repository, follow these steps:

1. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   ```
   - **Windows users:** 
     ```bash
     cd ./venv/Scripts/activate
     ```
   - **Mac and Linux users:** 
     ```bash
     source ./venv/bin/activate
     ```
2. **Install the requirements:**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```
Once the requirements are installed, the programs will run successfully, except for the `person_and_phone.py` script, which requires an additional model download (details provided later).

**Vision Prerequisites:**

- TensorFlow > 2
- OpenCV
- scikit-learn 0.19.1 (for face spoofing; newer versions are not supported)

**Audio Prerequisites:**

- PyAudio
- SpeechRecognition
- NLTK

**Vision Functionalities:**

1. **Eye Tracking:**
   - Tracks eyeballs and reports if the candidate is looking left, right, or up.
   - Implemented in `eye_tracker.py`.

2. **Mouth Opening Detection:**
   - Detects if the candidate opens their mouth by recording the initial distance between lips.
   - Implemented in `mouth_opening_detector.py`.

3. **Person Counting and Mobile Phone Detection:**
   - Counts the number of people and reports if no one or more than one person is detected.
   - Detects instances of mobile phones.
   - Requires YOLOv3 model in TensorFlow 2.
   - Implemented in `person_and_phone.py`.

4. **Head Pose Estimation:**
   - Determines the direction in which the person is looking.
   - Implemented in `head_pose_estimation.py`.

5. **Face Spoofing Detection:**
   - Detects whether the face is real or a photograph/image.
   - Implemented in `face_spoofing.py`.

6. **Face Detection:**
   - Compares different face detection models; OpenCV's DNN module provides the best results.
   - Implemented in `face_detector.py`.

**Facial Landmarks:**
- Initially used Dlib's model, but switched to a TensorFlow-based model for better performance with angled faces.
- Implemented in `face_landmarks.py`.

**Note:** If you want to use Dlib models, check out the `old-master` branch.

**Audio Functionalities:**

1. **Speech to Text:**
   - Records audio from the microphone and converts it to text using Google's speech recognition API.
   - Runs in a separate thread to avoid disturbing the recording process.
   - Implemented in `audio_part.py`.

2. **Text Comparison:**
   - Removes stopwords from the recorded text and the question paper (in txt format).
   - Compares the contents and presents the common words and their frequencies to the proctor.
   - Implemented in `audio_part.py`.

**Problems:**

- Speech-to-text conversion may not work well for all dialects.







