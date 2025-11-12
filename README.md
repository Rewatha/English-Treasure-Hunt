# 🎮 English Treasure Hunt Game

An interactive web-based educational game for English Day events. Players complete picture puzzles, riddles, and English challenges to unlock the treasure and win prizes!

---

## 📋 Table of Contents

- [Features](#-features)
- [Demo](#-demo)
- [How to Play](#-how-to-play)
- [Installation](#-installation)
- [Customization Guide](#-customization-guide)
- [File Structure](#-file-structure)
- [Browser Support](#-browser-support)
- [Contributing](#-contributing)
- [License](#-license)
- [Credits](#-credits)

---

## ✨ Features

- 🎯 **3 Game Stages**: Login → Entry Challenges → Treasure Hunt
- 🖼️ **30 Picture Puzzles**: Emoji combinations to English words
- 🧠 **100 Riddles**: Text-based brain teasers
- 🏆 **5 Envelope Challenges**: Vocabulary, Grammar, Idioms, Logic, Final Treasure
- ⏱️ **Timed Challenges**: 30s for entry, 8 minutes for main game
- 💡 **Hint System**: Get help when stuck (with time penalty)
- ⏭️ **Skip System**: Skip difficult questions (limited uses)
- 📊 **Progress Tracking**: Save attempts and play count
- 🎉 **Prize System**: Rewards for completing all challenges
- 📱 **Fully Responsive**: Works on mobile, tablet, and desktop
- 🔄 **Random Puzzles**: Different questions each time
- 🎨 **Colorful UI**: Engaging design with animations

---

## 🎮 Demo

**[Play the Game Here](#)** *https://rewatha.github.io/English-Treasure-Hunt/*

---

## 📖 How to Play

### **Step 1: Login** 🔐
1. Enter your **name**
2. Enter your **Gmail address**
3. Click **"Start Treasure Hunt"**

### **Step 2: Picture Puzzle Challenge** 🖼️
- Pick a lucky number from **1-30**
- Guess the English word from emoji pictures
- **Time limit:** 30 seconds
- **Hint:** Available at 15 seconds
- ✅ Pass → Move to Riddle Challenge
- ❌ Fail → Restart from login

### **Step 3: Riddle Challenge** 🧠
- Pick a lucky number from **1-100**
- Solve the riddle
- **Time limit:** 30 seconds
- **Hint:** Available at 15 seconds
- ✅ Pass → Start Treasure Hunt
- ❌ Fail → Restart from login

### **Step 4: Treasure Hunt** 🏴‍☠️
Complete **5 envelopes** in **8 minutes**:

| Envelope | Challenge |
|----------|-----------|
| 📚 Envelope 1 | Vocabulary Vault |
| 📝 Envelope 2 | Grammar Gate |
| 🔐 Envelope 3 | Idiom/Cipher Code |
| 🧠 Envelope 4 | Logic Lock |
| 🏆 Envelope 5 | Final Treasure |

**Help Options:**
- 💡 **Hints**: Unlimited (costs -1 minute each)
- ⏭️ **Skip Question**: 2 total (costs -30 seconds each)
- ➡️ **Give Up**: Skip envelope (no marks for that envelope)

### **Step 5: Results** 🎊
- View your score and statistics
- **Complete all 5?** Show screen to Game Master for prizes!
- Print or save your results
- Click **Home** to play again

---

## 🚀 Installation

### **Quick Start (No Server Required)**

1. **Download the files:**
```bash
   git clone https://github.com/rewatha/english-treasure-hunt.git
   cd english-treasure-hunt
```

2. **Open in browser:**
   - Simply double-click `index.html`
   - Or drag `index.html` into your browser

That's it! No installation or setup needed.

### **Deploy to GitHub Pages**

1. **Push to GitHub:**
```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
```

2. **Enable GitHub Pages:**
   - Go to repository Settings
   - Navigate to Pages section
   - Select `main` branch
   - Click Save

3. **Access your game:**
```
   https://rewatha.github.io/English-Treasure-Hunt/
```

### **Run Local Server (Optional)**

**Python:**
```bash
python -m http.server 8000
# Open: http://localhost:8000
```

**Node.js:**
```bash
npx http-server -p 8000
# Open: http://localhost:8000
```

---
## 🛠️ Customization Guide

### **⏱️ Change Time Limits**

#### Entry Challenges Timer (60 seconds)
```javascript
// In picture-puzzle.html and riddle-challenge.html
// Find this line (around line 80):
const [timeLeft, setTimeLeft] = useState(60);
// and
setTimeLeft(60);

// Change to your desired seconds:
const [timeLeft, setTimeLeft] = useState(120); // 120 seconds
// and
setTimeLeft(120);
```

#### Treasure Hunt Timer (8 minutes)
```javascript
// In treasure-hunt.html
// Find this line (around line 42):
const [timeLeft, setTimeLeft] = useState(480); // 480 = 8 minutes

// Change to your desired time:
const [timeLeft, setTimeLeft] = useState(600); // 10 minutes
const [timeLeft, setTimeLeft] = useState(300); // 5 minutes
```

#### Hint Appearance Time (30 seconds)
```javascript
// In picture-puzzle.html and riddle-challenge.html
// Find this line:
timeLeft <= 30

// Change to show hint earlier/later:
timeLeft <= 40  // Hint appears at 40 seconds
timeLeft <= 60  // Hint appears at 60 seconds
```

---

### **📝 Add/Edit Questions**

#### Picture Puzzles
```javascript
// In picture-puzzle.html
// Find: const PICTURE_PUZZLES = [...]
// Add new puzzle:

{ 
  id: 31, 
  emojis: "🌙 + 💡", 
  answer: "moonlight", 
  hint: "Light from the moon" 
}
```

#### Riddles
```javascript
// In riddle-challenge.html
// Find: const RIDDLES = [...]
// Add new riddle:

{ 
  id: 101, 
  riddle: "What has a head and a tail but no body?", 
  answer: "coin", 
  hint: "Used for money" 
}
```

#### Treasure Hunt Questions
```javascript
// In treasure-hunt.html
// Find these arrays and add to them:

// Vocabulary Puzzles
const VOCABULARY_PUZZLES = [
  { 
    question: "I mean 'happy' but I'm bigger than glad. What am I?", 
    answer: "joyful", 
    hint: "Rhymes with 'toyful'" 
  }
];

// Grammar Puzzles
const GRAMMAR_PUZZLES = [
  { 
    question: "Choose: He ____ to school yesterday (go/went/goes)", 
    answer: "went", 
    hint: "Past tense" 
  }
];

// Idiom Puzzles
const IDIOM_CIPHER_PUZZLES = [
  { 
    question: "What does 'break the ice' mean?", 
    answer: "startconversation", 
    hint: "Begin talking to someone new" 
  }
];

// Logic Puzzles
const LOGIC_PUZZLES = [
  { 
    question: "If you have me, you want to share me. If you share me, you lose me. What am I?", 
    answer: "secret", 
    hint: "Something private" 
  }
];

// Final Treasure Codes
const TREASURE_CODES = [
  { 
    question: "Decode: 8-5-1-18-20 (A=1, B=2...)", 
    answer: "heart", 
    hint: "H=8, E=5, A=1..." 
  }
];
```

---

### **🎯 Change Skip/Hint Settings**

#### Total Skips Allowed
```javascript
// In treasure-hunt.html
// Find this line (around line 45):
const [totalSkipsLeft, setTotalSkipsLeft] = useState(2);

// Change to allow more/fewer skips:
const [totalSkipsLeft, setTotalSkipsLeft] = useState(3); // 3 skips
const [totalSkipsLeft, setTotalSkipsLeft] = useState(1); // 1 skip
```

#### Skip Time Penalty
```javascript
// In treasure-hunt.html
// Find this line:
setTimeLeft(Math.max(0, timeLeft - 30));

// Change penalty amount:
setTimeLeft(Math.max(0, timeLeft - 45)); // -45 seconds
setTimeLeft(Math.max(0, timeLeft - 20)); // -20 seconds
```

#### Hint Time Penalty
```javascript
// In treasure-hunt.html
// Find this line:
setTimeLeft(Math.max(0, timeLeft - 60));

// Change penalty amount:
setTimeLeft(Math.max(0, timeLeft - 90));  // -90 seconds (1.5 min)
setTimeLeft(Math.max(0, timeLeft - 30));  // -30 seconds
```

---

### **🎨 Change Colors & Design**

#### Background Gradients
```javascript
// Each page has a gradient class like:
className="bg-gradient-to-br from-blue-500 via-purple-500 to-pink-500"

// Change colors:
from-red-500 via-orange-500 to-yellow-500  // Warm colors
from-green-500 via-teal-500 to-blue-500    // Cool colors
from-purple-500 via-pink-500 to-red-500    // Vibrant
```

#### Button Colors
```javascript
// Find button classes like:
className="bg-gradient-to-r from-green-500 to-emerald-600"

// Change to:
from-blue-500 to-indigo-600   // Blue button
from-red-500 to-pink-600      // Red button
from-yellow-500 to-orange-600 // Yellow button
```
---

### **🏆 Customize Prizes**
```javascript
// In results.html
// Find the prize list section:

React.createElement('ul', { className: "text-left text-gray-700 space-y-2" },
  React.createElement('li', null, '🍫 Mini chocolates'),
  React.createElement('li', null, '📖 English-themed bookmarks'),
  React.createElement('li', null, '🏅 "English Detective" badge')
)

// Change to your prizes:
React.createElement('li', null, '🎁 Gift card'),
React.createElement('li', null, '📚 Book voucher'),
React.createElement('li', null, '⭐ Certificate of achievement')
```

---

### **📧 Change Login from Gmail to Email**
```javascript
// In index.html
// Find the validateGmail function:

const validateGmail = (email) => {
  const gmailPattern = /^[a-zA-Z0-9._%+-]+@gmail\.com$/i;
  return gmailPattern.test(email);
};

// Change to accept any email:
const validateEmail = (email) => {
  const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  return emailPattern.test(email);
};

// Also update the label and placeholder text
```

---

## 📁 File Structure
```
english-treasure-hunt/
│
├── index.html                  # Login & registration
├── picture-puzzle.html         # Picture puzzle challenge
├── riddle-challenge.html       # Riddle challenge
├── treasure-hunt.html          # Main treasure hunt game
├── results.html                # Results & prizes
│
└── README.md                   # This file
```

**Total:** 5 HTML files + documentation

**Size:** ~150KB total (very lightweight!)

---

## 🌐 Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | ✅ Fully Supported |
| Firefox | 88+ | ✅ Fully Supported |
| Safari | 14+ | ✅ Fully Supported |
| Edge | 90+ | ✅ Fully Supported |
| Mobile Safari | 14+ | ✅ Fully Supported |
| Chrome Android | 90+ | ✅ Fully Supported |

**Requirements:**
- JavaScript enabled
- localStorage enabled
- Modern CSS support
- Internet connection (first load only)

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### **Report Bugs**
- Open an issue with detailed description
- Include browser version and screenshots
- Provide steps to reproduce

### **Suggest Features**
- Open an issue with [Feature Request] tag
- Describe the feature and use case
- Explain why it would be valuable

### **Submit Puzzles**
- Fork the repository
- Add your puzzles to appropriate files
- Submit a pull request
- Include puzzle + answer + hint

### **Improve Documentation**
- Fix typos or unclear instructions
- Add examples or screenshots
- Translate to other languages

### **Development Guidelines**
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📜 License

---

## 🙏 Credits

---

## 📞 Support