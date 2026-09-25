# 🔐 Caesar Cipher Encryptor & Decryptor

An interactive, responsive web application built with vanilla **HTML5**, **CSS3**, and **JavaScript** that encrypts and decrypts messages using the classic **Caesar Cipher** substitution algorithm.

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Historical Background](#-historical-background)
- [Mathematical Formulation](#-mathematical-formulation)
- [Key Features](#-key-features)
- [User Interface & Design](#-user-interface--design)
- [Step-by-Step Example](#-step-by-step-example)
- [Cryptographic Analysis & Security](#-cryptographic-analysis--security)
- [Project Architecture & File Structure](#-project-architecture--file-structure)
- [Getting Started](#-getting-started)
- [Browser Compatibility](#-browser-compatibility)
- [Contributing & License](#-contributing--license)

---

## 📌 Overview

The **Caesar Cipher** (also known as the shift cipher, Caesar's code, or Caesar shift) is one of the earliest and simplest forms of encryption. It is a type of **substitution cipher** in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.

This web application offers a clean, distraction-free environment to experiment with cryptography concepts in real-time without relying on external libraries or frameworks.

---

## 🏛️ Historical Background

Named after **Julius Caesar**, who used it with a shift of three ($n = 3$) to protect messages of military significance when communicating with his generals. While ineffective against modern cryptanalysis, the Caesar Cipher laid the foundational concepts for symmetric key cryptography and modular substitution systems.

---

## 🧮 Mathematical Formulation

The Caesar Cipher maps letters of the Latin alphabet to integers from $0$ to $25$ ($A = 0, B = 1, \dots, Z = 25$).

### 1. Encryption
For a letter $x$ and shift key $k$ ($1 \le k \le 25$):

$$E_k(x) = (x + k) \pmod{26}$$

### 2. Decryption
To reverse the encryption and retrieve the original plaintext:

$$D_k(x) = (x - k) \pmod{26}$$

In modular arithmetic with positive indices, this is computed as:

$$D_k(x) = (x + 26 - (k \pmod{26})) \pmod{26}$$

---

## ⚡ Key Features

- **Bi-Directional Transformation**: Seamlessly encrypt and decrypt messages with a single click.
- **Customizable Shift Key**: Choose any integer shift between **1** and **25** (defaults to Caesar's historical shift of **3**).
- **Case Sensitivity Preserved**: Uppercase characters stay uppercase, and lowercase characters remain lowercase.
- **Special Character Handling**: Numbers, spaces, symbols, and punctuation marks remain unaltered.
- **Input Validation**: Automatically handles empty inputs and enforces shift boundary constraints ($1 - 25$).
- **One-Click Clipboard Copying**: Easily copy output results to your clipboard with modal feedback.
- **Quick Reset / Clear**: Reset input, output, and shift key back to initial states in one action.
- **Pure Vanilla Implementation**: Zero dependencies, minimal footprint, and lightning-fast execution.

---

## 🎨 User Interface & Design

The application features a clean, accessible layout designed for ease of use:

- **Theme Palette**:
  - **Background**: Soft calm blue (`#EAF6FF`)
  - **Card Container**: Clean white (`#FFFFFF`) with rounded corners and an ambient box shadow
  - **Action Accents**: Vibrant Royal Blue (`#2563EB`) with interactive hover states
- **Layout Organization**:
  - Input message textarea
  - Shift key input spinner ($1 - 25$)
  - Symmetrical action buttons: `[ Encrypt ] [ Decrypt ]`
  - Output message container (read-only)
  - Secondary utility buttons: `[ Copy ] [ Clear ]`
- **Interactive Modal**:
  - Displays a centered confirmation modal upon copying (`Copied output to clipboard!` or `No output text to copy!`)
  - Supports dismissal via click outside the modal dialog or pressing the `Escape` key.

---

## 🔍 Step-by-Step Example

### Example with Shift Key = 3

| Character Type | Plaintext | Shift (+3) | Ciphertext |
|---|---|---|---|
| Uppercase | `H` (7) | $(7 + 3) \pmod{26} = 10$ | `K` |
| Lowercase | `e` (4) | $(4 + 3) \pmod{26} = 7$ | `h` |
| Lowercase | `l` (11) | $(11 + 3) \pmod{26} = 14$ | `o` |
| Lowercase | `l` (11) | $(11 + 3) \pmod{26} = 14$ | `o` |
| Lowercase | `o` (14) | $(14 + 3) \pmod{26} = 17$ | `r` |
| Symbol / Space | ` ` | Untouched | ` ` |

- **Plaintext**: `Hello, World!`
- **Shift**: `3`
- **Encrypted**: `Khoor, Zruog!`
- **Decrypted**: `Hello, World!`

---

## 🛡️ Cryptographic Analysis & Security

While the Caesar Cipher is a great teaching tool, it is completely insecure for modern communication:

1. **Extremely Small Key Space**: Since the alphabet only has 26 letters, there are only 25 possible non-trivial keys. An attacker can test every single key in milliseconds using a **Brute-Force Attack**.
2. **Frequency Analysis Vulnerability**: Because it is a monoalphabetic substitution cipher, each plaintext letter always maps to the same ciphertext letter for a given key. Natural languages have predictable letter frequencies (e.g., in English, **E**, **T**, **A**, **O**, **I**, **N** are the most common letters). An analyst can determine the shift key quickly by inspecting letter frequency charts.
3. **No Integrity or Authentication**: The cipher offers no protection against tampering or message modification.

> [!NOTE]
> This tool is created for **educational purposes** to illustrate foundational concepts in cryptography and computer science.

---

## 📁 Project Architecture & File Structure

```
Caesar-Cipher/
├── index.html       # Semantic HTML5 markup, inputs, buttons, and modal dialog
├── style.css        # CSS3 styles, responsive flexbox layout, transitions, and theme
├── script.js       # Core algorithm logic, DOM event listeners, and clipboard API
└── README.md        # Comprehensive project documentation
```

### Technical Implementation Highlights

- **`caesarTransform(text, shift, mode)`**: Core algorithmic function that maps ASCII codes ($65-90$ for uppercase, $97-122$ for lowercase) with modular offset calculations.
- **`getShiftValue()`**: Enforces numeric input bounds and fallback defaults.
- **`copyOutput()`**: Uses modern `navigator.clipboard.writeText()` API with fallback handling.

---

## 🚀 Getting Started

No build tools or package managers required. Simply follow these steps:

### 1. Clone the Repository
```bash
git clone https://github.com/jesinmilesh/Caesar-Cipher.git
cd Caesar-Cipher
```

### 2. Run the Application
Open `index.html` in your favorite web browser:
- Double-click `index.html` in your file explorer, or
- Use VS Code Live Server extension, or
- Run a simple local HTTP server:
  ```bash
  # Python 3
  python -m http.server 8000
  ```
  Then navigate to `http://localhost:8000` in your browser.

---

## 🌐 Browser Compatibility

Tested and compatible with all modern browsers:
- Google Chrome (Desktop & Mobile)
- Mozilla Firefox
- Microsoft Edge
- Apple Safari (macOS & iOS)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
