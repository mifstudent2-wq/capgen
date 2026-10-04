# CapGen - CapCut-Style AI Video & Subtitle Editor

An interactive CapCut-inspired video editor with multi-track timeline, real-time audio extraction, AI4Bharat **IndicConformer 600M Multilingual ASR** integration, dynamic subtitle burning, and multi-format exports (.SRT, .VTT, .JSON, MP4/WebM).

---

## 🌟 Key Features

1. **CapCut Dark-Themed UI**:
   - Matches the reference layout with dark slate aesthetics (`#101114`).
   - Project title & date editor on the top left.
   - Clean top action bar with Undo/Redo and Export (no premature premium locks).
2. **Media Import & Automatic Audio Extraction**:
   - Drag-and-drop or click to import any video (`.mp4`, `.mov`, `.webm`, `.mkv`).
   - Quick source buttons: Google Drive, Dropbox, Camera Record, and Audio waveform import.
   - Automatically decodes audio and resamples it to **16kHz 16-bit Mono WAV** in the browser using the Web Audio API—the exact specification required by AI4Bharat IndicConformer.
3. **IndicConformer 600M Model Integration**:
   - Backend endpoint `/api/transcribe` proxies requests to your Windows laptop tunnel endpoint (default `http://192.168.1.38:8000/transcribe` or your tunnel URL).
   - Eliminates browser CORS issues with local IPs or tunnel domains.
   - Multi-language support: Tamil (`ta`), Hindi (`hi`), English (`en`), Telugu (`te`), Malayalam (`ml`), Kannada (`kn`), Marathi (`mr`), Bengali (`bn`), Gujarati (`gu`), etc.
   - Live endpoint status indicator with latency tracking.
4. **Equal Timeline Matching & Subtitle Segmentation**:
   - Intelligently splits the transcribed text (e.g. Tamil phrases) into natural chunks (3, 4, 5 words, or custom).
   - Equidistantly and proportionally distributes subtitle chunks across the audio duration (`duration_seconds`).
   - Live synchronized subtitle overlay on top of video playback with CapCut styling.
5. **Multi-Track Interactive Timeline**:
   - **Track 1 (Subtitles / SRT)**: Colored subtitle blocks with text preview, drag to reposition, resize handles on edges to adjust timing, inline double-click editing.
   - **Track 2 (Video)**: Continuous video duration track with auto-generated filmstrip thumbnails.
   - **Track 3 (Audio)**: Waveform visualization computed directly from the extracted audio peaks.
   - Time ruler with seconds and centiseconds markers.
   - Draggable red playhead scrubber line synchronized with video playback.
   - Snapping magnet, timeline zoom slider (20px/s to 250px/s), fit-to-view button, fullscreen preview.
6. **Timeline Editing Tools**:
   - `✂ Split (S)`: Split selected subtitle segment at current playhead position.
   - `❐ Duplicate`: Duplicate selected subtitle.
   - `🗑 Delete (Del)`: Delete selected subtitle.
   - `+ T`: Insert new caption at current playhead.
7. **Comprehensive Export Options**:
   - **Burned-in Video**: Records canvas with video + styled subtitles into video file (`.webm` / `.mp4`).
   - **SubRip Subtitles (.SRT)**: Standard SRT file with timed ranges.
   - **WebVTT (.VTT)**: Web-standard subtitle format.
   - **Model Transcript (.JSON)**: Raw response including latency, duration, model name, and segment list.

---

## 🚀 How to Run

1. Make sure Python 3 is installed.
2. Install the server dependencies (preferably in a virtual environment):
   ```bash
   python3 -m venv .venv
   . .venv/bin/activate
   pip install -r requirements.txt
   ```
3. Run the start script:
   ```bash
   ./start.sh
   ```
   Or directly with python:
   ```bash
   python3 server.py
   ```
4. Open your browser at:
   ```
   http://localhost:8080
   ```

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| **Space** | Play / Pause video |
| **J** | Step back 1 second |
| **L** | Step forward 1 second |
| **S** | Split selected subtitle segment at playhead |
| **Del / Backspace** | Delete selected subtitle segment |
| **Ctrl + Z / Cmd + Z** | Undo |
| **Ctrl + Y / Cmd + Y** | Redo |
| **Double Click Subtitle** | Open caption text and timestamp editor modal |
# capgen
