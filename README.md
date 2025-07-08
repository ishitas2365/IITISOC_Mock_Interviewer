# **Interbot – Smart Multimodal Interview Simulator**

**Interbot** is a voice-interactive AI system designed to simulate realistic mock interviews. It dynamically generates domain-specific questions, evaluates user responses, provides real-time feedback, and delivers constructive suggestions—all within an intuitive Gradio interface. The tool empowers users to improve their interview skills, boost confidence, and track performance in a controlled environment.

---

## **Objective**

To create and deploy an AI-powered mock interview system that:

- Simulates real-world interview scenarios  
- Generates relevant, context-specific questions  
- Evaluates spoken responses using large language models  
- Delivers real-time feedback, hints, and correct answers  
- Tracks user performance and provides summary feedback

---

##  **Tech Stack**

- **LLM**: Meta-LLaMA-3-8B-Instruct (via Hugging Face Inference API)  
- **Frontend**: Gradio (for UI and user interaction)  
- **Speech-to-Text**: Python `speech_recognition` library (Google API)  
- **Text-to-Speech**: `gTTS` (Google Text-to-Speech)  
- **Backend**: Python (with threading to handle sequential audio playback)

---

##  **Execution Flow**

1. User enters:
   - Name  
   - Interview Topic  
   - Position (e.g., SDE, Analyst, etc.)  
   - Difficulty Level (Easy/Medium/Hard)
   
2. `conduct_interview()` initiates:
   - First few questions are general (future plans, job role)
   - Then proceeds to domain/topic-specific questions

3. Each answer is:
   - Captured via microphone  
   - Transcribed  
   - Verified

4. Response handling:
   -  Correct → Praise → Next question  
   -  Incorrect → Hint → Retry  
     - Still incorrect → Reveal answer → Continue

5. At any point, the user can **say "finish interview"** to end the session.

6. After the interview ends:
   - Accuracy = ( Correct Answers / Total Questions)  
   - Constructive feedback is generated using conversation history

7. The entire experience is presented via a Gradio interface with text and audio.
   
