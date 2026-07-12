# Preperation

We'll using Jupyter Notebook with a Rust Kernel. 

Here are the steps to install the notebook:

```shell
python3.12 -m venv .venv # creats a virtual environment

# Either:
source .venv/bin/activate # shell
source .venv/bin/activate.fish # fish-shell
./.venv/bin/activate.bat # windows

pip install -r requirements.txt # installs same version of jupyter notebook we use for the workshop
cargo install --locked evcxr_jupyter@0.21.1 # install rust kernel for jupyter notebook on system

# Either to register the rust kernel in the virtual env:
# Linux/MacOS
env JUPYTER_PATH=$VIRTUAL_ENV/share/jupyter/ evcxr_jupyter --install 
# Windows Cmd:
set JUPYTER_PATH=%VIRTUAL_ENV%\\share\\jupyter # Windows cmd
evcxr_jupyter --install
# Windows Powershell:
$env:JUPYTER_PATH = "$env:VIRTUAL_ENV\share\jupyter"
evcxr_jupyter --install

# Afterwards the jupyter nootbook can be started with 
jupyter notebook
```

If you create a new notebook you have to select the Rust kernel instead of the Python kernel and you're ready to go.
