# hw-sec

Fault-injection labs for the **ChipWhisperer-Husky + CW312T-SAM4S** (NaUKMA Hardware Security),
organized by course week. `week-05/` glitches a 2500-count loop on the target: `01` over the clock,
`02` over the power rail (crowbar).

## Install (once)

1. Install ChipWhisperer with the ARM build toolchain, so `make` can build firmware from a notebook
   `%%bash` cell - [docs](https://chipwhisperer.readthedocs.io/en/latest/getting-started.html)
   ([Windows](https://chipwhisperer.readthedocs.io/en/latest/windows-install.html),
   [macOS](https://chipwhisperer.readthedocs.io/en/latest/mac-install.html)).
2. `git clone https://github.com/Mishok7889/hw-sec`
3. Open the folder in VS Code and add the **Jupyter** extension.

## Run

1. Open a notebook in `week-05/`, pick the kernel = the Python env where ChipWhisperer is installed.
2. Run all cells top to bottom.

The notebooks locate your ChipWhisperer install themselves, so this repo can live anywhere.
