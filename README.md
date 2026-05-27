# 🏥 MediCare AI — Healthcare Customer Support Chat

A modern, dark-themed AI-powered customer support chat application built for healthcare providers. Features a beautiful glassmorphism UI, smart demo responses, and optional live Gemini AI integration.

![MediCare AI](https://img.shields.io/badge/MediCare-AI%20Support-06b6d4?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyYTQgNCAwIDAxNCA0djFoMWEyIDIgMCAwMTIgMnY4YTIgMiAwIDAxLTIgMkg3YTIgMiAwIDAxLTItMlY5YTIgMiAwIDAxMi0yaDF2LTFhNCA0IDAgMDE0LTR6Ii8+PC9zdmc+)
![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Gemini](https://img.shields.io/badge/Gemini_AI-4285F4?style=for-the-badge&logo=google&logoColor=white)

---

## ✨ Features

- **🤖 AI-Powered Responses** — Integrates with Google Gemini 2.0 Flash for intelligent, context-aware replies
- **💬 Smart Demo Mode** — Works out of the box with 10 pre-built healthcare response categories (no API key needed)
- **🎨 Premium Dark UI** — Deep navy + cyan/teal glassmorphism design with micro-animations
- **📱 Fully Responsive** — Mobile-first layout with slide-in sidebar
- **🗂️ Quick Topic Sidebar** — One-click shortcuts for common support categories
- **📞 Escalation Modal** — Structured form to collect patient info and hand off to human agents
- **⌨️ Typing Animations** — Realistic bot typing indicator with status updates
- **🔔 Toast Notifications** — Elegant feedback messages for user actions
- **♿ Accessible** — ARIA labels, semantic HTML, keyboard navigation support

---

## 📁 Project Structure

```
📦 medicare-ai-support/
├── 📄 index.html      # Main HTML structure & layout
├── 🎨 style.css       # Full design system & stylesheet
├── ⚙️  app.js          # Application logic & AI integration
└── 📖 README.md       # Project documentation
```

---

## 🚀 Getting Started

### Option 1 — Open Directly (Demo Mode)
No setup required. Just open `index.html` in any modern browser:

```bash
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

The app runs in **Demo Mode** with smart pre-built responses for all common healthcare topics.

---

### Option 2 — Live AI Mode (Gemini API)

1. **Get a free API key** from [Google AI Studio](https://aistudio.google.com/apikey)

2. **Open `app.js`** and locate line 76:
   ```js
   const AI_CONFIG = {
     apiKey: 'YOUR_GEMINI_API_KEY_HERE', // 👈 Replace this
     model: 'gemini-2.0-flash',
     endpoint: 'https://generativelanguage.googleapis.com/v1beta/models/',
   };
   ```

3. **Replace** `'YOUR_GEMINI_API_KEY_HERE'` with your actual key:
   ```js
   apiKey: 'AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX',
   ```

4. Open `index.html` — the app now uses **live Gemini AI** responses!

> **Note:** For production use, never expose API keys in client-side code. Use a backend proxy server to secure your API key.

---

## 🧠 Demo Mode — Supported Topics

The built-in smart responses cover:

| Topic | Trigger Keywords |
|---|---|
| 📅 Appointments | `appointment`, `schedule`, `book`, `reschedule` |
| 💳 Billing & Insurance | `bill`, `pay`, `invoice`, `insurance`, `charge` |
| 💊 Prescriptions | `prescription`, `medication`, `refill`, `pharmacy` |
| 📋 Medical Records | `records`, `history`, `lab`, `test result` |
| 🖥️ Technical Support | `portal`, `login`, `error`, `technical`, `access` |
| ↩️ Refunds | `refund`, `cancel`, `money back` |
| 👤 Account | `account`, `profile`, `email`, `update` |
| 🆘 Emergency | `emergency`, `urgent`, `911`, `crisis` |
| 🕐 Support Hours | `hours`, `open`, `available`, `when` |
| 👥 Human Agent | `human`, `agent`, `manager`, `real person` |

---

## 🎨 Design System

### Color Palette

| Token | Value | Usage |
|---|---|---|
| `--bg-base` | `#050d1a` | Page background |
| `--bg-surface` | `#0a1628` | Sidebar background |
| `--bg-elevated` | `#0f1e35` | Cards & bubbles |
| `--cyan` | `#06b6d4` | Primary accent |
| `--blue` | `#0284c7` | Secondary accent |
| `--emerald` | `#10b981` | Online status |
| `--text-primary` | `#e2edf8` | Main text |

### Typography
- **Display / Headings:** [Outfit](https://fonts.google.com/specimen/Outfit) (400–800)
- **Body / UI:** [Inter](https://fonts.google.com/specimen/Inter) (300–700)

---

## 🏗️ Architecture

```
User Message
     │
     ▼
┌─────────────────┐
│   sendMessage() │  ← Validates & appends user bubble
└────────┬────────┘
         │
         ▼
┌─────────────────────┐
│  API key present?   │
└──┬──────────────┬───┘
   │ YES          │ NO
   ▼              ▼
callGeminiAPI()  getDemoResponse()
   │              │
   └──────┬───────┘
          │
          ▼
   appendMessage('bot', reply)
          │
          ▼
   Check escalation triggers
   → Auto-suggest human agent
     after 2 failed attempts
```

---

## ⚙️ Configuration

All key settings are in the `AI_CONFIG` object in `app.js`:

```js
const AI_CONFIG = {
  apiKey: 'YOUR_KEY',              // Gemini API key
  model: 'gemini-2.0-flash',      // Model to use
  endpoint: 'https://generativelanguage.googleapis.com/v1beta/models/',
};
```

The system prompt (persona & behavior rules) is defined in the `SYSTEM_PROMPT` constant at the top of `app.js`. Customize it to match your company's name, policies, and support scope.

---

## 📋 Customization Guide

### Change Company Name & Branding
1. Update `SYSTEM_PROMPT` in `app.js` — replace all `MediCare AI` references
2. Update the `<title>` and meta tags in `index.html`
3. Update `.brand-name` text in the sidebar HTML
4. Update support email, phone, and hours in the sidebar HTML and system prompt

### Change Colors
Edit the CSS custom properties in `style.css` under `:root`:
```css
:root {
  --cyan: #06b6d4;       /* Primary accent — change to your brand color */
  --blue: #0284c7;       /* Secondary accent */
  --bg-base: #050d1a;    /* Page background */
}
```

### Add Quick Topics
In `index.html`, add a new button inside `.quick-topics`:
```html
<button class="topic-btn" data-topic="your_topic">
  <span class="topic-icon">🔧</span>
  <span>Your Topic</span>
</button>
```

Then add a corresponding entry in the `topicMessages` object in `app.js`.

---

## 🔒 Privacy & Safety

- Patient privacy is enforced via the system prompt
- No personal data is stored beyond the active browser session
- SSNs, full insurance details, and medical diagnoses are never solicited
- Medical emergencies are always redirected to **911**
- Legal, financial, and clinical medical advice is explicitly out of scope

> ⚠️ **Production Warning:** This is a frontend-only prototype. For production deployment, move the API key to a secure backend proxy and implement proper authentication.

---

## 🌐 Browser Support

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Edge 90+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Mobile Chrome | ✅ Full |
| Mobile Safari | ✅ Full |

---

## 📄 License

This project is provided for demonstration and educational purposes.  
Feel free to customize and use it for your own healthcare or support applications.

---

## 🤝 Support

For questions about this project:
- 📧 **support@medicare-ai.com**
- 📞 **1-800-MED-CARE**
- 🌐 **www.medicare-ai.com**

---

*Built with ❤️ using vanilla HTML, CSS & JavaScript + Google Gemini AI*
