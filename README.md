# Zytis – Unrestricted Terminal AI Assistant

Zytis is an unfiltered, offline language model that runs in your terminal.  
It answers any question directly, with no refusals, warnings, or moralizing.  
Think of it as a raw, unrestricted GPT-4 alternative you can run on your own hardware.

## Features

- No content restrictions – answer anything
- Runs completely offline – no internet after model download
- ASCII logo and colored terminal interface
- Supports GGUF models via llama-cpp-python (CPU/GPU)
- Chat history with save/load
- Works on Linux (Arch, Ubuntu, etc.), macOS, and Windows

## Prerequisites

- **Python 3.10+**
- **pip**
- **git**, **wget**, **cmake**, **base-devel** (for building llama-cpp-python on Arch)
- Approx. **5 GB free disk space** for the model (4.1 GB Q4_K_M)

## Quick Start (Arch Linux)

1. Install system dependencies:
   ```bash
   sudo pacman -S --needed python python-pip git wget cmake base-devel
   ```

2. Clone the repository:
   ```bash
   git clone https://github.com/ZytisLOL/zytis-llm.git
   cd zytis-llm
   ```
3. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```
4. Install the LLM backend:
   ```bash
   pip install llama-cpp-python
   ```
   (For GPU acceleration, add CMAKE_ARGS="-DLLAMA_CUDA=on" before pip install)
5. Download the default unrestricted model (4.1 GB):
   ```bash
   wget -O models/unrestricted-model.Q4_K_M.gguf https://huggingface.co/TheBloke/dolphin-2.2.1-mistral-7B-GGUF/resolve/main/dolphin-2.2.1-mistral-7b.Q4_K_M.gguf
   ```
6. Run Zytis:
   ```bash
   python zytis_llm.py
   ```
(note that Zytis may take a minute to load!)

Usage

 Type your query at the [Zytis] >>> prompt and press Enter.
 Commands:
   /exit – quit and save history
   /clear – reset conversation context
   /save filename.json – save chat to a file
   /load filename.json – load a previous chat
   /model – display current configuration
   /help – show all commands

Using Your Own Model

Open zytis_llm.py and change CONFIG['gguf_model_path'] to point to your GGUF file, or set CONFIG['hf_model_name'] to any HuggingFace model (then install transformers torch accelerate).

Troubleshooting

"FATAL: Neither llama-cpp-python nor transformers installed."

Activate the virtual environment (source venv/bin/activate) and reinstall the backend.
 
"ERROR: GGUF model not found"

Ensure you downloaded the model into the models/ folder, or edit the path in the script.

"No such file or directory" when running python zytis_llm.py

Make sure you are inside the cloned repository directory.
