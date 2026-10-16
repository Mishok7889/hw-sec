# Environment setup

From a bare machine to a notebook in `week-05/` that talks to the Husky. Pick your OS; both end
at the same place. Official docs:
[Windows](https://chipwhisperer.readthedocs.io/en/latest/windows-install.html),
[macOS](https://chipwhisperer.readthedocs.io/en/latest/mac-install.html).

You need two pieces: the **ChipWhisperer software** (Python + Jupyter) and a **compiler** that builds
the target firmware. Then clone this repo and open it in VS Code.

## Windows

Neither piece needs WSL.

1. **Software.** Install Python 3.9+ and [Git](https://git-scm.com/downloads). In Git Bash:
   ```bash
   git clone https://github.com/newaetech/chipwhisperer
   cd chipwhisperer
   git submodule update --init jupyter
   python -m pip install -e .
   python -m pip install -r jupyter/requirements.txt
   ```
2. **Compiler.** Install the
   [GNU Arm Embedded toolchain](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)
   and a `make` (ships with the [avr-gcc builds](https://blog.zakkemble.net/avr-gcc-builds/), or
   `pacman -S make` under MSYS2). Put each `bin` folder on PATH, then verify in Git Bash:
   ```bash
   arm-none-eabi-gcc --version
   make --version
   ```
   SAM4S needs only `arm-none-eabi-gcc` and `make`. A compiler is required only to *build* firmware,
   not to flash a prebuilt `.hex`.
3. **Driver.** Windows 10/11 installs the Husky driver automatically (WCID); no Zadig.

> The bundled `Chipwhisperer.vX.Y.Z.exe` installer is simpler but pulls in WSL for the compilers. The
> steps above avoid WSL; the notebooks' `%%bash` build cell works either way. If you use the installer,
> install into your home folder (not `C:\Program Files`).
> [Releases](https://github.com/newaetech/chipwhisperer/releases).

## macOS

1. **Homebrew** ([brew.sh](https://brew.sh)):
   ```bash
   brew install libusb                   # talk to the board
   brew install --cask gcc-arm-embedded  # firmware compiler
   ```
2. **Python env** - a venv or pyenv. On Apple Silicon use conda miniforge so `libusb` and Python
   share one architecture ([chipwhisperer#381](https://github.com/newaetech/chipwhisperer/issues/381)).
3. **ChipWhisperer:**
   ```bash
   git clone https://github.com/newaetech/chipwhisperer
   cd chipwhisperer
   git submodule update --init jupyter
   python -m pip install -e .
   python -m pip install -r jupyter/requirements.txt
   ```

## This repo in VS Code (both OSes)

1. Clone it:
   ```bash
   git clone https://github.com/Mishok7889/hw-sec
   ```
2. Install [VS Code](https://code.visualstudio.com) and its **Python** (`ms-python.python`) and
   **Jupyter** (`ms-toolsai.jupyter`) extensions.
3. **File -> Open Folder** on `hw-sec`.
4. Open a notebook in `week-05/`. Top-right, **Select Kernel** -> the Python env where you installed
   ChipWhisperer (your venv / pyenv / conda env). Getting the kernel right is the one thing people miss:
   if `import chipwhisperer` fails, you picked the wrong one.

The notebooks locate your ChipWhisperer install themselves, so `hw-sec` can live anywhere.

## Verify

Plug the Husky in over USB. In a notebook cell:

```python
import chipwhisperer as cw
scope = cw.scope()
print(scope)          # Husky detected
```

If it reports the firmware is out of date, update it (see the docs). The live maps in the notebooks
need `jupyter_bokeh`: `python -m pip install jupyter_bokeh` into the same env, then restart the kernel.

**End state:** a notebook that talks to the Husky.
