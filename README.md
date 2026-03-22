# 🔊 Text To Voice Converter

A clean and instant Text-to-Speech web app built with pure HTML, CSS, and JavaScript. Type or paste any text, choose a voice from the dropdown, and click "Listen" to hear it spoken aloud — powered by the browser's built-in **Web Speech API (SpeechSynthesis)**. No backend, no API key, deployed live on Vercel.

## 🌐 Live Demo

🔗 **[text-to-voice-converter-iota.vercel.app](https://text-to-voice-converter-iota.vercel.app)**

---

## ✨ Features

- 🎙️ **Text-to-Speech** — Converts any typed or pasted text into spoken audio instantly
- 🌍 **Multiple Voices** — Dropdown auto-populated with all voices available in the user's browser (varies by OS & browser — can include 20–50+ voices in different languages)
- ▶️ **Listen Button** — Click once to start speech; click again to stop/restart
- 📝 **Textarea Input** — Multi-line text area supports long passages, paragraphs & articles
- 🆓 **Zero Cost** — Uses the browser's native `SpeechSynthesis` API — no external API or key needed
- 📱 **Fully Responsive** — Works on mobile, tablet, and desktop
- 🪶 **Zero Dependencies** — Pure vanilla JavaScript, no libraries required

---

## 🗂️ Project Structure

```
Text-To-Voice-Converter/
│
├── index.html           # Textarea, voice select dropdown, Listen button
├── style.css            # Card layout, textarea styling, button & dropdown
├── script.js            # SpeechSynthesis API — populate voices, speak text
│
├── play-button.png      # Icon inside the Listen button
├── play.png             # Play icon variant
├── play icon.png        # Play icon variant
├── play img.png         # Play image asset
├── arrow down.png       # Dropdown arrow icon
└── dropdown img.png     # Dropdown styling asset
```

---

## ⚙️ How It Works

```
Page loads
    ↓
JS calls speechSynthesis.getVoices()
    ↓
All available browser voices populate the <select> dropdown
    ↓
User types text in the textarea
    ↓
User selects a preferred voice from dropdown
    ↓
User clicks "Listen"
    ↓
JS creates a new SpeechSynthesisUtterance(text)
    ↓
Sets the selected voice on the utterance
    ↓
speechSynthesis.speak(utterance) → browser reads aloud 🔊
```

---

## 🧠 Core Logic

```javascript
// Populate voice dropdown
window.speechSynthesis.onvoiceschanged = () => {
  const voices = speechSynthesis.getVoices();
  voices.forEach(voice => {
    const option = document.createElement("option");
    option.value = voice.name;
    option.textContent = `${voice.name} (${voice.lang})`;
    select.appendChild(option);
  });
};

// Speak the text
function speak() {
  const text    = document.querySelector("textarea").value;
  const utterance = new SpeechSynthesisUtterance(text);
  const voices  = speechSynthesis.getVoices();
  utterance.voice = voices.find(v => v.name === select.value);
  speechSynthesis.speak(utterance);
}
```

---

## 🛠️ Tech Stack

| Technology | Usage |
|------------|-------|
| **HTML5** | Textarea, voice `<select>`, Listen button |
| **CSS3** | Card layout, hero section, responsive styling |
| **JavaScript (Vanilla)** | Web Speech API — `SpeechSynthesis`, `SpeechSynthesisUtterance` |
| **Web Speech API** | Built-in browser API for text-to-speech synthesis |
| **Vercel** | Deployment & hosting |

---

## 💡 Key Concepts Demonstrated

- **Web Speech API (`SpeechSynthesis`)** — Native browser TTS engine, no external service needed
- **`SpeechSynthesisUtterance`** — Object that holds the text, voice, pitch, rate & volume settings
- **`speechSynthesis.getVoices()`** — Retrieves all voices installed on the user's OS/browser
- **`onvoiceschanged` Event** — Fires asynchronously when voices finish loading (crucial for correct voice list)
- **Dynamic `<select>` Population** — Building dropdown options from JS array via DOM manipulation
- **Cross-browser TTS** — Works on Chrome, Edge, Firefox, Safari (voice availability varies by browser)

---

## 🌐 Browser Voice Support

| Browser | Voices Available |
|---------|-----------------|
| **Google Chrome** | 40–50+ voices (includes Google US English, Google Hindi, etc.) |
| **Microsoft Edge** | 40+ Natural (neural) voices |
| **Safari** | System voices from macOS/iOS |
| **Firefox** | OS-level voices (fewer than Chrome) |

> 💡 Best experience on **Google Chrome** — has the largest voice library including multilingual voices!

---

## 🚀 Getting Started

### Run Locally

1. **Clone the repository**
   ```bash
   git clone https://github.com/Daniish-Qureshi/Text-To-Voice-Converter.git
   ```

2. **Navigate into the project folder**
   ```bash
   cd Text-To-Voice-Converter
   ```

3. **Open in browser**
   ```
   Open index.html in Google Chrome for best results
   — or use Live Server (VS Code extension)
   ```

> ✅ No API keys, no npm, no setup — just open and speak!

---

## 📱 Responsive Design

| Screen | Behavior |
|--------|----------|
| **Mobile** | Full-width textarea, stacked voice select & button |
| **Tablet** | Comfortable card layout |
| **Desktop** | Centered hero card with clean spacing |

---

## 👨‍💻 Author

**Danish Qureshi**  
BCA Final Year Student | Full Stack Developer  
📍 Dadri, Uttar Pradesh, India  
🔗 [GitHub — @Daniish-Qureshi](https://github.com/Daniish-Qureshi)  
🌐 [Portfolio](https://danish-qureshi-6ew5.vercel.app)

---

## 📄 License

This project is open source and free to use for **educational & portfolio purposes**.

---

⭐ If you found this useful, give it a **star** on GitHub!
