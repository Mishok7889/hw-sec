# hw-sec

Fault-injection labs for the **ChipWhisperer-Husky + CW312T-SAM4S** (NaUKMA Hardware Security),
organized by course week. `week-05/` glitches a 2500-count loop on the target: `01` over the clock,
`02` over the power rail (crowbar).

## Install (once)

Set up ChipWhisperer, the ARM build toolchain, this repo, and VS Code - full steps in
[SETUP.md](SETUP.md).

## Run

1. Open a notebook in `week-05/`, pick the kernel = the Python env where ChipWhisperer is installed.
2. Run all cells top to bottom.

The notebooks locate your ChipWhisperer install themselves, so this repo can live anywhere.
