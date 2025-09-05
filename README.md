# TMG EMME Lib

This library gives us an example of how to create a Rust library that is
able to be called from the Python instead for EMME.

## Building the project

### Setting up the environment

Assuming you are on Windows and have EMME 2025 installed in the default directory, we are going to
use its built in version of Python to create the virtual environment.  While in the `tmg_emme_lib`
directory run the following command.

```cmd
C:\Program Files\Bentley\OpenPaths\EMME 25.00.00\Python311\python.exe' -m venv .env 
```

This will create a virtual python environment with the version of python that is compatible with your
copy of EMME.

Next we need to activate the environment, run the following command.

```cmd
.\.env\Scripts\activate
```

This will activate this virtual environment as the instance of python to use for further commands. Next
we are going to setup Maturin, the library we will use to build the bindings between Python and our
Rust library.

```cmd
pip install maturin
```

### Compiling

If you are returning to development, make sure to activate your python environment with the following before continuing.

```cmd
.\.env\Scripts\activate
```

After the environment has been setup you can then compile the code using the following command.

```cmd
maturin develop
```

This will compile the library and compile the binaries into the `./.env/Lib/site-packages` directory.

### Consuming the library

After you have compiled the library the next step is to consume it with the Python instead embedded within EMME.  You can do this
either by developing EMME tools or using the built-in Jupyter Notebook.

```py
# Temporarly add the library directory to your EMME's python path
import sys
sys.path.append(r"C:\Your_Library_Path\tmg_emme_lib\.env\Lib")

# You can now import in the library
import tmg_emme_lib

# And execute some high performance code
tmg_emme_lib.add(2, 3) # 5
```
