
# Local Installation (optional)

For these options it makes sense to clone the repository to your local machine. You can do this by running:

```sh
git clone https://github.com/fneum/phl-workshop.git
```

or by downloading the repository as a ZIP file (look for a green "Code" button) and extracting it to a local folder:

https://github.com/fneum/phl-workshop

Then, navigate to the `phl-workshop` directory where you will find the `.ipynb` files for the course materials.


## Option A: Using `uv`

For using `uv` as package manager, first follow the [installation instructions](https://docs.astral.sh/uv/getting-started/installation/). These differ depending on your operating system.

Once `uv` is installed, navigate to your local copy of the course repository and verify that it's working:

```sh
uv --version
```

Now, install all required packages and set up the environment by running:

```sh
uv sync
```

It is important that you run this command in the root folder of the course repository, where the `pyproject.toml` and `uv.lock` files are located.

Once this is done, you can start a new Jupyter Lab session in your browser with this environment by running:

```sh
uv run jupyter lab
```


## Option B: Using `conda`

### Installing `conda`

Python and nearly all of the software packages in the scientific python
ecosystem are [open-source](https://opensource.org/). Coordinating the
compatibility between these different packages and their multiple versions can
be difficult! Fortunately, the problem is solved by using **package managers**.

The easiest way to set up a full-stack scientific Python deployment without
prior experience is to use a Python distribution, such as
[Anaconda](https://www.anaconda.com). The instructions differ for Windows, MacOS, and Linux. Closely, follow the instructions (and videos) at

https://www.anaconda.com/docs/getting-started/getting-started

Watch the introduction videos and follow the instructions there.

:::{note}
For beginners, the Anaconda Python Distribution is recommended. If you are comfortable with using the command line, you can also use the lightweight `miniconda` installation.
:::

Once Anaconda is installed, you can access `conda` in the command line using the *Anaconda Prompt* application on Windows, or the terminal application on Linux and MacOS.

### Installing `conda` environments

Python coupled with a package manager like `conda` provides a way to make
isolated, reproducible **environments** where you have control over all
installed packages and configurations. To work through the course materials, you
need to install a specific set of packages within such a dedicated `conda`
environment.

#### Downloading specification files

Among several other ways to do this, this can be done by creating a new
environment from a provided `environment.yaml` file. This file lists all
required packages and their versions in the [`YAML`
format](https://en.wikipedia.org/wiki/YAML). These files can list exact package
versions (**pinned** versions) or just version constraints (e.g., minimum
versions).

In this course, we provide pinned versions to ensure everyone has the same
environment, but they depend on the operating system you are using.

- For **Windows**, use the [`win-64.lock.yaml`](https://github.com/fneum/phl-workshop/blob/main/envs/win-64.lock.yaml) file.
- For **MacOS (Intel/AMD)**, use the [`osx-64.lock.yaml`](https://github.com/fneum/phl-workshop/blob/main/envs/osx-64.lock.yaml) file.
- For **MacOS (Apple Silicon)**, use the [`osx-arm64.lock.yaml`](https://github.com/fneum/phl-workshop/blob/main/envs/osx-arm64.lock.yaml) file.
- For **Linux**, use the [`linux-64.lock.yaml`](https://github.com/fneum/phl-workshop/blob/main/envs/linux-64.lock.yaml) file.

**There is a download button at the top-right corner.**

:::{note}
If there are problems with the pinned versions, you can also try using the
unpinned
[`environment.yaml`](https://github.com/fneum/phl-workshop/blob/main/envs/environment.yaml)
file.
:::


#### Option 1: Anaconda user interface

1. Open the Anaconda Navigator application
2. Go to the "Environments" tab on the left
3. Click "Import" at the bottom
4. In the dialog, provide a name for the new environment (e.g. `phl-workshop`) and select the downloaded `environment.yaml` file
5. Click "Import" to create the environment and install all required packages

:::{note}
This process may take some time, depending on your internet connection and computer speed.
:::

#### Option 2: Command line

First, check that you have access to `conda` in your terminal (or Anaconda Prompt on Windows) by typing:

```sh
conda --version
```

For **Windows**:

```sh
conda env create -f envs/win-64.lock.yaml
```

For **MacOS** (Intel/AMD):

```sh
conda env create -f envs/osx-64.lock.yaml
```

For **MacOS** (Apple Silicon):

```sh
conda env create -f envs/osx-arm64.lock.yaml
```

For **Linux**:

```sh
conda env create -f envs/linux-64.lock.yaml
```

:::{note}
This process may take some time, depending on your internet connection and computer speed. If you encounter issues that the environment could not be solved, try using the
:::


### Using `conda` environments

To use the course environment, it must be **activated** by executing in the terminal (or Anaconda Prompt on Windows):

```sh
conda activate phl-workshop
```

This can be done anywhere; you do not need to be in the course repository folder.

You should now see the string `(phl-workshop)` prepended to your prompt.

Now, any execution of Python will use the packages installed in your
environment `phl-workshop`.

:::{warning}
The activation step has to be repeated whenever you open a new terminal; it is not persistent across terminal sessions.
:::

### Running Jupyter Lab

With the environment activated, you can start [Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/), a web-based interactive development environment, by typing:

```sh
jupyter lab
```

This should open a new tab in your web browser with the Jupyter Lab interface.

## Option c: Using `pip`

For using `pip` as package manager, first ensure you have a working Python installation (version 3.13 is recommended). You can download Python from [python.org](https://www.python.org/downloads/) for your operating system.

Once Python is installed, you can open the command prompt / terminal and verify the installation by typing:

```sh
python --version
python -m pip --version
# or
pip --version
```

Now, you can upgrade `pip` to the latest version by running:

```sh
pip install --upgrade pip
```

Similar to the `conda` environment setup, you can install all required packages using a `requirements.txt` file. This is the same for all operating systems.

For our course, you can find it
[here](https://github.com/fneum/phl-workshop/blob/main/requirements.txt).
There is a download button at the top-right corner.

After navigating to the folder where the `requirements.txt` file is stored (i.e. using `cd path/to/your/directory`), you can install the required packages with

```sh
pip install -r requirements.txt
```

You can add more packages later using `pip install package_name`, e.g.

```sh
pip install pandas
```

Once this is done, you can start a new Jupyter Lab session in your browser:

```sh
jupyter lab
```

Unlike with `conda`, `pip` does not provide isolated environments by default.
