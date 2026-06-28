# ⬡ CipherForge v2.1
### Advanced Encryption Workstation
**Made by Krut Vyas**

---

## Overview

CipherForge is a sleek, cyberpunk-themed Windows desktop application for encrypting and decrypting both text and files. Built in C# (.NET 6 / Windows Forms), it features a dark hex-grid UI with glowing accents, an animated splash screen, and support for four industry-standard cipher algorithms.

---

## Features

| Feature | Details |
|---|---|
| **Algorithms** | AES-256, DES, TripleDES, RC2 |
| **Text Mode** | Encrypt/decrypt any plaintext → Base64 ciphertext |
| **File Mode** | Encrypt/decrypt any file (binary or text) |
| **Key Generation** | One-click random hex key & IV generator |
| **UI** | Dark space theme, hex-grid background, glowing borders |
| **Splash Screen** | Animated loading screen with progress bar |
| **Author Credit** | "Made by Krut Vyas" prominently displayed |

---

## Build Instructions

### Requirements
- [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0) (Windows)
- Visual Studio 2022 **or** any terminal with `dotnet` CLI

## How to build the EXE (choose one method)

### ✅ Method 1 — Double-click (easiest)
1. Extract this folder anywhere on your PC
2. Double-click **`COMPILE_TO_EXE.bat`**
3. The script auto-detects your compiler and builds `dist\CipherForge.exe`
4. The `dist\` folder opens automatically when done

> If you don't have .NET SDK, the script opens the download page for you.

---

### ✅ Method 2 — Visual Studio 2022 (recommended for projects)
1. Open Visual Studio 2022
2. Create a new **Windows Forms App (.NET 6)** project
3. Replace the generated `Program.cs` with the contents of `CipherForge.cs`
4. Press **F5** to run, or **Ctrl+Shift+B** to build
5. EXE is in `bin\Release\net6.0-windows\`

---

### ✅ Method 3 — Command Line (.NET 6 SDK)
```bat
dotnet new winforms -n CF
copy CipherForge.cs CF\Program.cs
cd CF
dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -o ..\dist
```

---

## Project Structure

```
CipherForge/
├── CipherForge.csproj   ← Project config (targets .NET 6-windows)
├── Program.cs           ← Entry point, launches SplashScreen
├── SplashScreen.cs      ← Animated loading screen
└── MainForm.cs          ← Main window (Text tab + File tab + crypto logic)
```

---

## How to Use

### Text Encryption
1. Select **Algorithm** (AES-256 recommended)
2. Click **↻ GEN KEY** and **↻ GEN IV** to generate random keys
   - *Save these — you need the same key + IV to decrypt!*
3. Paste your text in the **INPUT** box
4. Click **⬡ ENCRYPT** → Base64 ciphertext appears in OUTPUT
5. To decrypt: paste ciphertext in INPUT, click **⬡ DECRYPT**

### File Encryption
1. Switch to the **FILE** tab
2. Click **◈ BROWSE** to select any file
3. Set algorithm, key, and IV (or generate new ones)
4. Click **⬡ ENCRYPT FILE** → creates `filename.enc` next to source
5. To decrypt: browse the `.enc` file, same key/IV, click **⬡ DECRYPT FILE** → creates `.dec` file

---

## Security Notes

- **AES-256 (CBC)** is the strongest option available
- Keys and IVs are generated using `RandomNumberGenerator` (cryptographically secure)
- Keys are entered as **hex strings** (preferred) or plaintext (zero-padded to required length)
- IVs are **16 bytes** for AES and RC2, **8 bytes** for DES and TripleDES (handled automatically)
- **Always store your key and IV securely** — there is no recovery without them

---

## Algorithms Reference

| Algorithm | Key Size | Block Size | Notes |
|---|---|---|---|
| AES-256 | 256 bit | 128 bit | Recommended — NIST standard |
| DES | 64 bit | 64 bit | Legacy — weak by modern standards |
| TripleDES | 192 bit | 64 bit | Moderate security |
| RC2 | 128 bit | 64 bit | Legacy stream-like block cipher |

---

*CipherForge v2.1 — © 2025 Krut Vyas*
