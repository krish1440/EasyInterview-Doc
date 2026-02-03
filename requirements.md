# Requirements Specification: EasyInterview

**Version:** 1.0  
**Status:** Draft  
**Last Updated:** 2026-02-04

---

## 1. Executive Summary
EasyInterview is an AI-powered, multimodal interview coaching platform designed to simulate realistic job interviews. It leverages Google Gemini 2.5 to analyze both verbal responses and non-verbal cues (posture, eye contact) in real-time, providing candidates with actionable feedback to improve their employability.

## 2. Functional Requirements

### 2.1 User Onboarding & Setup
- **REQ-01:** The system shall allow users to enter their name and professional role target.
- **REQ-02:** The system must accept **Resumes** (PDF/Text) via drag-and-drop or file upload.
- **REQ-03:** The system must accept a target **Job Description (JD)** (Text/URL) to tailor the interview context.
- **REQ-04:** The system shall perform a "System Check" to validate Microphone and Webcam permissions before starting the session.

### 2.2 Core Interview Simulation (The "Ava" Engine)
- **REQ-05:** The system shall feature an interactive AI Avatar ("Ava") that speaks questions audibly using Text-to-Speech (TTS).
- **REQ-06:** The system must support **Hands-Free Operation**, where the AI automatically detects when the user has finished speaking (Silence Detection) or allows a manual "Finish Answer" trigger.
- **REQ-07:** The AI must generate questions dynamically based on the uploaded Resume and Job Description, covering:
    - Technical Competency
    - Behavioral/Situational (STAR method)
    - Cultural Fit
- **REQ-08:** The conversation must be **Multi-turn**, meaning the AI can ask follow-up questions based on the user's previous answer.

### 2.3 Multimodal Analysis (Real-Time)
- **REQ-09:** The system shall analyze **Video Streams** locally or via API to detect:
    - **Head Pose:** Alert if the user is looking away or down for extended periods.
    - **Face Visibility:** Ensure the user is centered in the frame.
    - **Posture:** Detect slouching or leaning.
- **REQ-10:** The system shall analyze **Audio Streams** for:
    - **Clarity/WPM:** Words per minute (Pacing).
    - **Volume:** Detect if the user is mumbling or too loud.

### 2.4 Live Feedback Loop
- **REQ-11:** The UI must display **Ephemeral Nudges** (Toast notifications) during the interview for immediate correction (e.g., "Look at the camera", "Slow down").
- **REQ-12:** The system must display a real-time **Speech-to-Text transcript** of both the AI and User for accessibility.

### 2.5 Post-Interview Analytics
- **REQ-13:** Upon session completion, the system must generate a **Performance Report** containing:
    - **Radar Chart:** Visual score across 5 axes (Technical, Communication, Confidence, Body Language, Relevance).
    - **Question-by-Question Breakdown:** Specific feedback on what was good vs. what needs improvement.
    - **Actionable Roadmap:** A list of 3-5 concrete steps to improve.

## 3. Non-Functional Requirements (NFRs)

### 3.1 Performance & Latency
- **NFR-01:** Speech-to-Text latency should be under **500ms** to ensure natural conversation consistency.
- **NFR-02:** AI Response generation (LLM inference) should average under **2-3 seconds**.
- **NFR-03:** Video frame analysis must run at a minimum of **15 FPS** on standard consumer hardware.

### 3.2 Privacy & Security
- **NFR-04:** **Local-First Processing:** Video streams should ideally be analyzed client-side (via TensorFlow.js or MediaPipe) where possible to minimize data egress.
- **NFR-05:** **Ephemeral Data:** Audio/Video recordings must not be stored on the server permanently unless explicitly opted-in by the user.
- **NFR-06:** API Keys (Gemini) must be secured via environment variables or backend proxy headers.

### 3.3 Usability & Accessibility
- **NFR-07:** The interface must support **Dark Mode** for reduced eye strain.
- **NFR-08:** The application must be fully responsive for Desktop/Laptop resolutions (Min-width: 1024px). *Note: Mobile blocked for performance reasons.*

### 3.4 Reliability
- **NFR-09:** The system must handle network interruptions gracefully, allowing the user to resume the current question.

## 4. System Constraints
- **CON-01:** Browser Support: Transforming features (WebSpeech API, MediaStream) requires **Chrome, Edge, or Brave**.
- **CON-02:** Hardware: Requires a functionally active Webcam and Microphone.

## 5. Technology Standards
- **Frontend:** React 18, TypeScript, Tailwind CSS.
- **AI Core:** Google Gemini 2.5 (Multimodal).
- **State Management:** React Context API / Zustand.
- **Analytics:** Vercel Analytics.
