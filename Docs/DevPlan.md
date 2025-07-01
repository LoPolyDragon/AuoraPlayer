# Aurora Player — macOS Local-Music-Player Development Plan  
*(all-offline, zero in-app purchases)*

---

## 1  Project Overview
Aurora Player is a **desktop-first music player** that reads local audio files, delivers a visually immersive playback experience, and includes professional-grade utilities such as variable speed, cross-fade, EQ, and AI-generated lyrics. No network, account, or payment is ever required.

---

## 2  Target Audience & Pain Points

| Audience                          | Current Pain Points                                         | Aurora Player Solution                                |
|----------------------------------|-------------------------------------------------------------|-------------------------------------------------------|
| Casual music lovers & hobby DJs   | Stock Apple Music is stream-centric; pro tools cost money   | Free feature-complete local player with mixing tools  |
| Indie creators & podcasters       | Messy storage of demos/stems                                | Tag-based library, bulk metadata editor               |
| Language learners / musicians     | Need accurate slow-down & looping                           | 0.1×–3× time-stretch without pitch shift, A-B repeat  |

---

## 3  Feature Specification

### 3.1 Core Playback
1. **Import & Index** – drag-drop files/folders, background scan for ID3/FLAC tags  
2. **Lossless Decoding** – WAV, AIFF, FLAC, ALAC, AAC, MP3  
3. **Transport Controls** – play/pause, prev/next, scrubbing, volume, mute  

### 3.2 Advanced Utilities
| Feature                | Details                                                               |
|------------------------|-----------------------------------------------------------------------|
| Custom Playlists       | Manual or rule-based (genre, BPM, year…)                              |
| Variable Speed         | Real-time granular time-stretch 0.1×–3× (pitch-corrected)             |
| Cross-fade & Mix-in    | Adjustable 0–20 s, optional reverb tails                              |
| 10-band Equalizer      | Factory presets + user curves (import/export)                         |
| A-B Loop & Bookmarks   | Ideal for practice or transcription                                   |
| **AI Lyrics**          | Offline Whisper-cpp or Llama-cpp tiny model, auto-transcribe & align  |
| Artwork Fetch          | Embedded art → local “artwork” dir → manual drag-in fallback          |

### 3.3 Personalization
* Light / Dark / Custom themes  
* Global shortcuts & Touch Bar support  
* Multilingual UI (EN / ZH, extensible)

---

## 4  Tech Stack & Architecture

| Layer          | Tech Choices                         | Notes                                             |
|----------------|--------------------------------------|---------------------------------------------------|
| UI             | SwiftUI 5 + Core Animation           | Glass-morphism, live color extraction             |
| Audio Engine   | AVFoundation, Audio Unit, FFmpeg     | Custom time-stretch & cross-fade kernel           |
| Data Storage   | Core Data (SQLite)                   | Track metadata, lyrics timeline                   |
| AI Module      | Whisper-cpp (tiny) / Llama-cpp       | Runs fully offline on Apple Silicon & Rosetta     |
| CI/CD          | XCTest, fastlane, TestFlight         | Automated unit/UI tests & beta distribution       |

*Offline model size*: Whisper-tiny ≈ 75 MB → installer < 150 MB.  
*Model management*: Lazy-download & deletion in Preferences.

---

## 5  UI / UX Design

1. **Library View** – sidebar (playlists, folders, smart lists) + resizable album grid  
2. **Now Playing** (⌘ ↵ toggle) – large rotating artwork, waveform scrub bar, synced karaoke lyrics panel  
3. **Utility Drawer** – tabs for EQ, Mix, Speed; live audio preview  
4. **macOS Sonoma look** – dynamic blur, SF Symbols, smooth animations
