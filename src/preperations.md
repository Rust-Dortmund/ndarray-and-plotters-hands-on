# Preperation

We'll using Jupyter Notebook with a Rust Kernel.

Here are the steps to install the notebook, do this in the meanwhile you should be able to see this page locally, when you installed cloned the repository, installed `mdbook` and generate this book with it.

## Windows PowerShell
```shell
python3.12 -m venv .venv # creats a virtual environment

./.venv/Scripts/Activate.ps1 # start virtual environment

# Install dependencies
pip install -r requirements.txt # installs same version of jupyter notebook we use for the workshop
cargo install --locked evcxr_jupyter@0.21.1 # install rust kernel for jupyter notebook on system

# Register the rust kernel in the virtual env:
$env:JUPYTER_PATH = "$env:VIRTUAL_ENV\share\jupyter"
evcxr_jupyter --install

# Afterwards the jupyter nootbook can be started with
jupyter notebook
```

## Windows Cmd
```shell
python3.12 -m venv .venv # creats a virtual environment

./.venv/Scripts/activate.bat # start virtual environment

# Install dependencies
pip install -r requirements.txt # installs same version of jupyter notebook we use for the workshop
cargo install --locked evcxr_jupyter@0.21.1 # install rust kernel for jupyter notebook on system

# Register the rust kernel in the virtual env:
set JUPYTER_PATH=%VIRTUAL_ENV%\\share\\jupyter # Windows cmd
evcxr_jupyter --install

# Afterwards the jupyter nootbook can be started with
jupyter notebook
```

## Linux
```shell
python3.12 -m venv .venv # creats a virtual environment

# Either:
source .venv/bin/activate # shell
source .venv/bin/activate.fish # fish-shell

# Install dependencies
pip install -r requirements.txt # installs same version of jupyter notebook we use for the workshop
cargo install --locked evcxr_jupyter@0.21.1 # install rust kernel for jupyter notebook on system

# Register the rust kernek in the virtual environment
env JUPYTER_PATH=$VIRTUAL_ENV/share/jupyter/ evcxr_jupyter --install
evcxr_jupyter --install

# Afterwards the jupyter nootbook can be started with
jupyter notebook
```

## MacOS
```shell
python3.12 -m venv .venv # creats a virtual environment

# Either:
source .venv/bin/activate # shell
source .venv/bin/activate.fish # fish-shell

# Install dependecies
pip install -r requirements.txt # installs same version of jupyter notebook we use for the workshop
cargo install --locked evcxr_jupyter@0.21.1 # install rust kernel for jupyter notebook on system

# Either to register the rust kernel in the virtual env:
env JUPYTER_PATH=$VIRTUAL_ENV/share/jupyter/ evcxr_jupyter --install
evcxr_jupyter --install

# Afterwards the jupyter nootbook can be started with
jupyter notebook
```

## Select the Rust Kernel

If you create a new notebook you have to select the **Rust** kernel instead of the Python kernel and you're ready to go.
