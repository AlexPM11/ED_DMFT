## 🚀 Quick Start in VSCode

### 1. Open Terminal in VSCode
Press `` Ctrl+` `` (backtick) to open the integrated terminal.

### 2. Clone and Install
Copy and paste these commands one by one:

```bash
git clone https://github.com/AlexPM11/ED_DMFT.git

cd ED_DMFT

python -m venv venv_dmft

# Activate it (choose one based on your OS)
# macOS/Linux:
source venv_dmft/bin/activate
# Windows:
venv_dmft\Scripts\activate.bat

# Install ed_solver
pip install -e .

# Test it works
python -c "import ed_solver; print('✅ Installation successful!')"
# ED_DMFT
