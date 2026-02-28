NebulaDesk

A system-level Windows AI desktop assistant with global hotkey activation and local Ollama integration.

NebulaDesk is a lightweight Windows desktop assistant that connects to locally hosted large language models via Ollama. It provides fast global activation (Alt + Space), a clean WinForms interface, and optional native components for deeper system integration.

All processing runs locally. No cloud services required.

✨ Features

Global Alt + Space activation

Clean WinForms desktop UI

Local LLM integration via Ollama

Optional native C++ low-level keyboard hook

Optional Go backend support

Automatic fallback to managed C# hook

Fully offline operation

Lightweight distribution (.zip + .exe)

🏗 Architecture

NebulaDesk is composed of three modular components:

1. C# WinForms Application (Core)

Main UI

Message routing

Ollama HTTP communication

Fallback keyboard hook

2. Optional C++ Hook DLL

WH_KEYBOARD_LL low-level keyboard hook

Intercepts Alt + Space

Suppresses Windows system menu

Higher reliability than managed hook

3. Optional Go Backend

Model orchestration layer

Extended processing capabilities

If native components are unavailable, NebulaDesk gracefully falls back to pure C# functionality.

⚠ Requirements

NebulaDesk requires Ollama to be installed separately.

This repository does not bundle or redistribute:

Ollama binaries

Model weights

Third-party runtimes

🔧 Installation
Step 1 — Install Ollama

Download and install Ollama:

https://ollama.com

Verify installation:

ollama --version
Step 2 — Pull a Model

NebulaDesk requires at least one local model.

Example:

ollama pull llama3

Other supported models include:

mistral

phi3

gemma

Test manually:

ollama run llama3

If the model responds, Ollama is working.

Step 3 — Run NebulaDesk

Download the latest release .zip

Extract the archive

Run NebulaDesk.exe

Press Alt + Space to activate

🔎 Troubleshooting
NebulaDesk Cannot Connect

Check:

Ollama is installed

Ollama service is running

A model has been pulled

ollama run <model> works in terminal

Test Ollama API:

Open in browser:

http://localhost:11434

If accessible, the service is active.

Hotkey Not Working

Possible causes:

App not running as Administrator

Architecture mismatch (x86 vs x64)

Native hook DLL not present

Windows security restrictions

The app will automatically fall back to managed mode if the DLL is unavailable.

🛠 Building From Source
C# Application
dotnet build
Optional C++ Hook (MinGW)
g++ -shared -O2 -o NebulHook.dll hook.cpp -luser32 -static-libgcc -static-libstdc++
Optional Go Backend
go build
📦 Distribution Model

Releases contain:

Prebuilt NebulaDesk.exe

Optional native DLL

No bundled third-party software

Users must install Ollama separately.

🧠 Design Philosophy

NebulaDesk prioritizes:

Local-first AI

System-level integration

Minimal latency

Modular architecture

Graceful degradation

The application is designed to operate even if native components fail to load.

📄 License

MIT License

You are free to use, modify, distribute, and integrate this software in commercial or non-commercial projects.

See LICENSE for full terms.

🏷 Topics

windows winforms desktop-app ai-assistant ollama llm csharp keyboard-hook local-ai
