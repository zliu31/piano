# 🎹 Air Piano - Vintage Hand Tracking Piano Game

A browser-based interactive piano game that uses webcam hand tracking to play a full-screen vintage piano keyboard. Play music with just your hand movements!

![Air Piano Demo](https://img.shields.io/badge/Status-Ready%20to%20Play-success)
![No Dependencies](https://img.shields.io/badge/Dependencies-Zero%20Install-blue)
![Single File](https://img.shields.io/badge/Format-Single%20HTML-orange)

## ✨ Features

### 🎨 **Full-Screen Vintage Aesthetics**
- Immersive full-screen piano keyboard that fills your entire browser
- Realistic aged ivory and ebony key styling
- Antique wooden background with vintage texture
- Warm lighting with subtle vignette effect
- Realistic key depression and glow animations
- Professional shading between keys

### 🎥 **Webcam Hand Tracking**
- Powered by **MediaPipe Hands** for accurate real-time tracking
- Track your index finger position across the screen
- Automatic mapping to 12 note zones (full chromatic scale: C, C#, D, D#, E, F, F#, G, G#, A, A#, B)
- Intelligent downward tap detection
- Visual finger position indicator

### 🔊 **Rich Piano Sound**
- Web Audio API-generated vintage piano tones
- Multiple harmonics for realistic piano timbre
- ADSR envelope for authentic attack and decay
- Optional soft reverb for concert hall ambiance
- 12 playable notes (7 white keys + 5 black keys)

### 🎮 **Two Game Modes**

#### 1. **Free Play Mode**
- Play any notes freely by moving your finger
- Perfect for musical exploration
- No rules, just creativity

#### 2. **Melody Challenge Mode**
- Game generates random 3-5 note sequences
- Listen to the sequence played automatically
- Reproduce it using hand gestures
- Instant feedback on accuracy
- New challenge after each success

## 🚀 Quick Start

### 🌐 Play Online (Public Access)

**Live Demo:** Visit the deployed version at:
- GitHub Pages: `https://zliu31.github.io/piano/`
- Or: `https://zliu31.github.io/piano/air-piano.html`

### 💻 Run Locally (Zero Installation Required!)

1. **Open the file in your browser:**
   ```bash
   # Option 1: Double-click index.html or air-piano.html in your file explorer

   # Option 2: Use a local server (recommended for best performance)
   python3 -m http.server 8000
   # Then visit: http://localhost:8000/

   # Option 3: Use Node.js http-server
   npx http-server
   # Then visit the URL shown
   ```

2. **Grant webcam permissions** when prompted by your browser

3. **Position yourself** so your hand is clearly visible in the webcam preview (top-right corner)

4. **Start playing!** Read the instructions overlay for detailed guidance

### 🚀 Deploy Your Own

Want to host your own version? See **[DEPLOYMENT.md](DEPLOYMENT.md)** for complete deployment instructions including:
- GitHub Pages setup
- Custom domain configuration
- Alternative hosting options (Netlify, Vercel)
- Self-hosting guide

### System Requirements

- **Browser:** Chrome 90+, Edge 90+, or any Chromium-based browser (Safari/Firefox may have limited support)
- **Webcam:** Any built-in or external webcam
- **Lighting:** Good lighting conditions for optimal hand tracking
- **Permissions:** Camera access must be granted

## 🎯 How to Play

### Basic Controls

1. **Position Your Hand:**
   - Hold your hand up in front of the webcam
   - Keep your index finger pointing/extended
   - Ensure your hand is clearly visible

2. **Select Notes:**
   - Move your hand horizontally (left to right)
   - The golden indicator shows your finger position on screen
   - Different horizontal positions = different notes (all 12 chromatic notes from C to B)

3. **Play Notes:**
   - Make a quick **downward tapping motion** with your index finger
   - Like pressing an invisible piano key in the air
   - The note will play and the key will light up

4. **Visual Feedback:**
   - Golden indicator: Shows your finger position
   - Key depression: Pressed keys move down
   - Golden glow: Keys glow when triggered by hand
   - Hand skeleton: Visible in webcam preview

### Game Controls

- **Switch Mode:** Toggle between Free Play and Melody Challenge
- **Instructions:** View detailed help at any time
- **Click Keys:** You can also click keys with your mouse for testing

## 🛠️ Technical Details

### Architecture

The entire application is contained in a **single HTML file** (`air-piano.html`) with:
- **HTML:** Structure and layout
- **CSS:** Full-screen vintage piano styling with animations
- **JavaScript:** Hand tracking, audio generation, and game logic

### Key Technologies

1. **MediaPipe Hands (via CDN)**
   - Google's ML solution for hand tracking
   - Tracks 21 hand landmarks in real-time
   - No installation required - loaded from CDN

2. **Web Audio API**
   - Browser-native audio synthesis
   - Multi-oscillator piano tone generation
   - ADSR envelope for realistic sound
   - Reverb effect for vintage ambiance

3. **Canvas API**
   - Real-time hand skeleton visualization
   - Overlay rendering on webcam feed

### Code Architecture

```
📁 air-piano.html
├── 🎨 CSS Styling
│   ├── Full-screen piano layout
│   ├── Vintage key styling
│   ├── Animations and effects
│   └── UI overlays
│
├── 🎹 HTML Structure
│   ├── Piano keyboard (7 white + 5 black keys)
│   ├── Webcam container
│   ├── UI overlays
│   └── Controls
│
└── 🧠 JavaScript Logic
    ├── Audio Engine
    │   ├── Web Audio Context setup
    │   ├── Note generation (harmonics + ADSR)
    │   └── Reverb effects
    │
    ├── Hand Tracking
    │   ├── MediaPipe Hands initialization
    │   ├── Finger position mapping
    │   ├── Tap detection algorithm
    │   └── Visual feedback
    │
    └── Game Logic
        ├── Free Play mode
        ├── Challenge mode (sequence generation)
        ├── Score tracking
        └── Mode switching
```

### Hand Tracking Algorithm

```javascript
1. MediaPipe detects hand landmarks (21 points)
2. Extract index finger tip position (landmark #8)
3. Map X-coordinate to note zones (7 equal divisions)
4. Track Y-coordinate changes over time
5. Detect downward movement (deltaY > threshold)
6. Trigger note when tap detected
7. Apply cooldown to prevent double-taps
```

### Note Zone Mapping

```
Screen Width: 0% ───────────────────────────────────────────────── 100%
             │ C │C#│ D │D#│ E │ F │F#│ G │G#│ A │A#│ B │
Zones:       │8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│8.3%│
             (12 equal zones for full chromatic scale)
```

### Piano Sound Synthesis

Each note is created using:
- **Fundamental frequency** (the main note)
- **4 harmonics** (overtones for richness):
  - 2x frequency (octave)
  - 3x frequency (fifth)
  - 4x frequency (two octaves)
  - 5x frequency (major third)
- **ADSR Envelope:**
  - Attack: 0.02s (quick onset)
  - Decay: 0.1s (initial fade)
  - Sustain: 0.4 (maintained volume)
  - Release: 0.5s (fade out)

## 🎨 Visual Features

### Key Styling
- **White Keys:** Aged ivory with sepia tone, yellowed appearance
- **Black Keys:** Glossy ebony with subtle highlights
- **Depression Effect:** Keys move down 8px when pressed
- **Glow Animation:** Golden glow pulse on hand trigger
- **Shadows:** Realistic inset and drop shadows

### Background
- **Wood Grain:** Repeating linear gradient pattern
- **Vignette:** Radial gradient darkening at edges
- **Warm Tones:** Brown palette (#3d2817, #5c4033)
- **Depth:** Inset shadows for 3D effect

## 🐛 Troubleshooting

### Webcam Not Working
- **Check permissions:** Ensure browser has camera access
- **Check other apps:** Close other apps using the webcam
- **Try different browser:** Chrome/Edge work best

### Hand Not Detected
- **Improve lighting:** Face a light source
- **Distance:** Move closer or further from camera
- **Hand visibility:** Ensure entire hand is in frame
- **Background:** Try a plain background

### Tap Not Registering
- **More deliberate motions:** Make clearer downward taps
- **Adjust sensitivity:** Modify `tapThreshold` in code (line 405)
- **Check cooldown:** Wait between taps (300ms default)

### No Sound
- **Check volume:** System and browser volume
- **User interaction:** Click somewhere first (browsers require user gesture)
- **Browser support:** Try Chrome/Edge

### Performance Issues
- **Close other tabs:** Free up browser resources
- **Lower quality:** Modify MediaPipe `modelComplexity` to 0
- **Disable effects:** Comment out reverb code

## 🔧 Customization

### Adjust Tap Sensitivity
```javascript
// Line ~405
let tapThreshold = 0.05; // Lower = more sensitive (try 0.03)
```

### Change Reverb Amount
```javascript
// Line ~418
dryGain.gain.value = 0.7; // Dry signal (0-1)
wetGain.gain.value = 0.3; // Wet signal (0-1)
```

### Modify Challenge Difficulty
```javascript
// Line ~662
const length = 3 + Math.floor(Math.random() * 3); // Change range (3-5 notes)
```

### Extend the Range
All 12 chromatic notes within one octave are already available. To add more octaves, duplicate the keys in HTML with higher/lower frequencies and expand the `noteZones` array accordingly.

## 📝 Notes

- **CDN Dependencies:** Requires internet connection for MediaPipe library
- **Browser Compatibility:** Best in Chrome/Edge (Chromium-based browsers)
- **Privacy:** All processing happens locally - no data sent to servers
- **Offline Use:** Download MediaPipe library for offline use

## 🎵 Musical Theory

The default scale is **C Major**:
- C, D, E, F, G, A, B (white keys)
- C#, D#, F#, G#, A# (black keys - for visual realism)

Frequencies are based on A440 tuning standard:
- A4 = 440 Hz
- Each semitone = previous note × 2^(1/12)

## 🚀 Future Enhancements

Potential improvements:
- Record and playback melodies
- Multiple difficulty levels
- Custom song library
- MIDI export
- Multi-hand support
- Sound bank selection
- Keyboard shortcuts
- Mobile support (tap instead of air gesture)

## 📄 License

This is a demonstration project. Feel free to use, modify, and distribute.

## 🙏 Credits

- **MediaPipe Hands:** Google's hand tracking solution
- **Web Audio API:** Browser-native audio synthesis
- **Vintage Design:** Classic piano aesthetics

---

**Enjoy playing your Air Piano!** 🎹✨

For issues or questions, feel free to experiment with the code - everything is in one file!
