# **InterBot – Smart Multimodal Interview Simulator**

InterBot is a voice-interactive AI system designed to simulate realistic mock interviews. It dynamically generates domain-specific questions, evaluates user responses, analyzes facial expressions, and provides real-time feedback—all within an intuitive Gradio interface. The tool empowers users to improve their interview skills, boost confidence, and track performance both verbally and visually in a controlled environment.

---

## Objective

To create and deploy an AI-powered mock interview system that:

- Simulates real-world interview scenarios  
- Generates relevant, context-specific questions  
- Evaluates spoken responses using large language models  
- Delivers real-time feedback, hints, and correct answers  
- Analyzes user facial expressions from video responses  
- Tracks user performance and provides summary feedback

---

## Tech Stack

- **LLM**: `Meta-LLaMA-3-8B-Instruct` (via Hugging Face Inference API)  
- **Frontend**: Gradio (for UI and user interaction)  
- **Speech-to-Text**: Python `speech_recognition` library (Google API)  
- **Text-to-Speech**: `gTTS` (Google Text-to-Speech)  
- **Facial Expression Analysis**: `vit-face-expression` model via Hugging Face API  
- **Backend**: Python (with threading to handle sequential audio playback)

---

## Execution Flow

1. User enters:
   - Name  
   - Interview Topic (e.g., Machine Learning)  
   - Position (e.g., SDE, Analyst)  
   - Difficulty Level (Easy/Medium/Hard)

2. `conduct_interview()` initiates:
   - First few questions are general (future plans, job role)  
   - Then proceeds to domain/topic-specific questions

3. Each answer is:
   - Captured via microphone  
   - Transcribed  
   - Verified

4. Response handling:
   - Correct → Praise → Next question  
   - Incorrect → Hint → Retry  
     - Still incorrect → Reveal answer → Continue

5. At any point, the user can **say "finish interview"** to end the session.

6. After the interview ends:
   - **Accuracy** = (Correct Answers / Total Questions)  
   - **Dominant Facial Expression** = Based on video analysis (smile, frown, neutral, etc.)  
   - **Feedback** includes:  
     - Strengths and weaknesses  
     - Suggested improvements  
     - Sentiment/emotion pattern throughout the session

7. The entire experience is presented via a multimodal Gradio interface with real-time text + audio + visual feedback.

   
