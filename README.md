# Portable Python environment
A venv-like structure that can be used as a portable environment for Python.

It differs from common virtual environments by not hardcoding any absolute paths so it works after being run from a different directory.
The same version of Python is required for binary compatibility of some modules.

## Prerequisites
- Linux
- supported Python 3 version with `ensurepip` available


## Installation
1.  Clone this repository to a directory you would like to use as the Python environment, e.g. `pythonenv`:

        git clone https://github.com/hyneq/portable-python-env.git python-env

    Alternatively, add this repository as a submodule to an existing repo:

        git submodule add https://github.com/hyneq/portable-python-env python-env

2.  Initialize the environment:

        python-env/bin.static/init-env


## Usage
1.  Activate the environment:

        source python-env/bin.static/activate

2.  Use the `python`or `python3` command for calling the interpreter and the `pip` or `pip3` command for installing/uninstalling packages.


## Notes
-   Because the shebang in scripts installed in `bin/` is meant to be portable, it is necessary that the environment is activated for actually working inside it.

-   It is necessary to use pip by calling the command `pip` or `pip3`. Calling `python -m pip` (or `python3 -m pip`) would result in scripts not being portable.

-   There are two bin directories:
    - `bin/` - for scripts installed by pip
    - `bin.static/` - for custom scripts that are part of this repository
