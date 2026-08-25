## 🚀 Quick Start in VSCode

### 1. Open Terminal in VSCode
Press `` Ctrl+` `` (backtick) to open the integrated terminal.

### 2. Clone and Install
Copy and paste these commands one by one:

```bash
git clone https://gitlab.com/mullerthomas2528/ed_dmft.git

cd ed_solver

python -m venv venv_dmft

# Activate it (choose one based on your OS)
# macOS/Linux:
source venv/bin/activate
# Windows:
venv_dmft\Scripts\activate.bat

# Install ed_solver
pip install -e .

# Test it works
python -c "import ed_solver; print('✅ Installation successful!')"
# ED_DMFT
