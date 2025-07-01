# Aurora Player 🎵  
*A zero-distraction, desktop-first music player for macOS — 100 % offline, 0 % paywall.*

---

## Table of Contents
1. [Project Vision](#project-vision)  
2. [Feature Highlights](#feature-highlights)  
3. [Tech Stack & Architecture](#tech-stack--architecture)  
4. [Screenshots](#screenshots)  
5. [Getting Started](#getting-started)  
6. [Roadmap](#roadmap)  
7. [Contributing](#contributing)  
8. [License](#license)

---

## Project Vision
Aurora Player aims to be a **visually immersive, professional-grade local music player**.  
No accounts, streaming services, or in-app purchases — just your audio files and powerful tools that stay entirely on-device.

> "Read local audio, play it beautifully, empower everyone — hobby DJ to language learner — all offline."

---

## Feature Highlights

### Core Playback
* Drag-&-drop file / folder import with background tag scanning  
* Lossless decoding: WAV, AIFF, FLAC, ALAC, AAC, MP3  
* Smooth transport controls – play/pause, previous/next, scrubbing, volume, mute  

### Advanced Utilities
| Utility | Details |
|---------|---------|
| **Custom Playlists** | Manual lists or rule-based (genre, BPM, year, …) |
| **Variable Speed** | Real-time granular 0.1× – 3× time-stretch (pitch-corrected) |
| **Cross-fade & Mix-in** | Adjustable 0–20 s, optional reverb tails |
| **10-band EQ** | Factory presets + user curves (import/export) |
| **A-B Loop & Bookmarks** | Perfect for practice or transcription |
| **AI-Powered Lyrics** | Offline Whisper-cpp or Llama-cpp tiny; auto-transcribe & align |
| **Artwork Fetch** | Embedded → local "artwork" directory → manual drag-in fallback |

### Personalisation
* Light / Dark / Custom themes  
* Global shortcuts & Touch Bar support  
* Multilingual UI (English / Chinese, easily extensible)

---

## Tech Stack & Architecture

| Layer | Technologies | Notes |
|-------|--------------|-------|
| **UI** | SwiftUI 5, Core Animation | Glass-morphism, live colour extraction |
| **Audio Engine** | AVFoundation, Audio Unit, FFmpeg | Custom time-stretch & cross-fade kernel |
| **Data** | Core Data (SQLite) | Track metadata, lyrics timeline |
| **AI Module** | Whisper-cpp (tiny) / Llama-cpp | Runs fully offline on Apple Silicon & Rosetta |
| **CI/CD** | XCTest, fastlane, TestFlight | Automated unit/UI tests & beta distribution |

Approx. offline model size: Whisper-tiny ≈ 75 MB → entire installer < 150 MB.  
Models are lazily downloaded and can be removed via Preferences.

---

## Screenshots
> _Coming soon_ – see the [UI Design prompts](Docs/UI DesignColorPrompt.txt) for styling references.

---

## Getting Started

### Prerequisites
* macOS 14 (Sonoma) or later  
* Xcode 15  
* Apple Silicon **or** Intel with Rosetta 2  

### Build & Run
```bash
git clone https://github.com/your-handle/aurora-player.git
cd aurora-player/AuroraPlayer
open AuroraPlayer.xcodeproj   # or .xcworkspace if you add SwiftPM deps
```
1. Select the `AuroraPlayer` scheme.  
2. Hit **Run** (⌘ R).

The first launch will auto-create the Core Data store and prompt you to import music.

---

## Roadmap
- [ ] Import watch folders & auto-sync  
- [ ] Smart playlists (BPM, key, last played)  
- [ ] Waveform-based scrub bar  
- [ ] Lyrics timeline editor  
- [ ] Plug-in SDK for DSP effects  
Full details live in [`Docs/DevPlan.md`](Docs/DevPlan.md).

---

## Contributing
Pull requests are welcome!  
If you hit a crash or want to propose a feature, please open an issue and follow the template.

1. Fork + clone  
2. Create a feature branch: `git checkout -b feature/waveform-scrubbar`  
3. Commit & push  
4. Open a PR against `main`

### Development Notes
* Follow the _Swift API Design Guidelines_.  
* Keep UI pure-SwiftUI; fall back to AppKit only when necessary.  
* Write unit tests where logic is non-trivial — we gate CI on **≥ 90 %** coverage.

---

## License
Aurora Player is released under the **MIT License**.  
See [`LICENSE`](LICENSE) for details.

Made with ❤️ + 🎧 in California. 