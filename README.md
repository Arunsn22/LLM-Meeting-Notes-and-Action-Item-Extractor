# LLM-Meeting-Notes-and-Action-Item-Extractor
# Learning Log - AI Meeting Summarizer Project

## Timeline of Learning

### 1. **Audio Handling & Conversion**

-   **Learned:** How to handle audio uploads (`.mp3`, `.wav`, `.m4a`,
    `.mkv`) in Streamlit.\
-   **Issue:** `.mkv` files were not directly supported by Whisper.\
-   **Solution:** Used **FFmpeg** to convert `.mkv` → `.mp3`
    automatically before transcription.

------------------------------------------------------------------------

### 2. **Speech-to-Text with Whisper**

-   **Learned:** Integrated **OpenAI Whisper (base model)** to
    transcribe uploaded meeting audio.\
-   **Issue:**
    `UserWarning: FP16 is not supported on CPU; using FP32 instead`
    appeared.\
-   **Solution:** Understood it was just a performance warning (not an
    error). Whisper falls back to FP32 on CPU.

------------------------------------------------------------------------

### 3. **Extracting Meeting Notes & Action Items**

-   **Learned:** Basic **NLP-style keyword detection** (using regex &
    keyword matching) to classify transcript sentences into:
    -   **Meeting Notes**
    -   **Action Items / Tasks**
-   **Issue:** At first, action tasks were empty or transcript text
    appeared under the wrong section.\
-   **Solution:** Improved keyword filtering logic and sentence
    splitting to better detect tasks vs notes.

------------------------------------------------------------------------

### 4. **Testing with Synthetic Audio**

-   **Learned:** How to generate synthetic meeting audio for testing
    using **gTTS (Google Text-to-Speech)**.\
-   **Issue:** Needed meaningful meeting-style audio to test
    transcription pipeline.\
-   **Solution:** Created realistic meeting dialogue text → converted to
    audio (`test_meeting_audio.mp3`) with gTTS.

------------------------------------------------------------------------

### 5. **UI/UX Enhancements in Streamlit**

-   **Learned:** Customizing the Streamlit interface with **colors,
    headings, markdown, and emojis**.\
-   **Issue:** Default Streamlit UI was too plain and lacked clarity.\
-   **Solution:** Used `st.markdown()` with HTML/CSS for styling and
    added structured sections.

------------------------------------------------------------------------

### 6. **Download Functionality**

-   **Learned:** Added ability to **download transcript, notes, and
    tasks** as `.txt` file.\
-   **Issue:** After download, the app was **re-triggering transcription
    automatically**.\
-   **Solution:** Separated download logic from transcription logic,
    ensuring no rerun was triggered unnecessarily.

------------------------------------------------------------------------

### 7. **Reloading the App**

-   **Learned:** How to refresh/reload the Streamlit app after one
    meeting is processed.\
-   **Issue:**
    `AttributeError: module 'streamlit' has no attribute 'experimental_rerun'`
    appeared because `st.experimental_rerun()` was deprecated.\
-   **Solution:** Replaced with **`st.rerun()`** which works in newer
    Streamlit versions.

------------------------------------------------------------------------

### 8. **Final Workflow**

-   Upload meeting file\
-   Convert (if needed)\
-   Transcribe using Whisper\
-   Extract notes & tasks\
-   Display results with styled UI\
-   Allow **download as `.txt`**\
-   Provide **"Upload Another File"** button to reload the app

------------------------------------------------------------------------

## Key Learnings

-   **Audio processing** with FFmpeg & Streamlit file uploader.\
-   **Whisper model integration** for transcription.\
-   **Basic NLP** to separate notes vs tasks.\
-   **gTTS** for generating test audio.\
-   **UI improvements** with Streamlit (colors, emojis, markdown).\
-   **Session management** with `st.rerun()` to reset app state.\
-   **Error handling & debugging** (warnings, rerun issues, empty
    results).

