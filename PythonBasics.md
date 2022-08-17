# Python Basics

## How To Setup PIPX

1. On Windows -> Install PIPX via `python -m pip install --user pipx`
2. Go to the Path specified in the warning during installation
3. `python -m pipx ensurepath` -> this adds your pipx path

PIPX is now installed, run commands with the following syntsx: 
`python -m pipx ...`

## Install Python Poetry via PIPX

I found this out the hard way... This seems to be the easiest way:
Simply type `python -m pipx install poetry`

Paths etc. are then already installed in the correct way.
