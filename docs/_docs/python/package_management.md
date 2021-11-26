---
title: Package Management with Poetry
tags: 
 - python
description: Managing Python packages with Poetry
---

# Package Management with [Poetry](https://python-poetry.org/)

<br>

Poetry is a tool for **dependency management** and **packaging** in Python. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.

- **Dependency Resolver:** Poetry comes with an *exhaustive* dependency resolver, which will always find a solution if it exists
- **Isolation:** Poetry either uses your configured virtualenvs or creates its own to always be *isolated* from your system
- **Intuitive CLI:** Poetry's commands are *intuitive* and ea

<br><br>

---

## System requirements

<br>

Poetry requires Python 2.7 or 3.5+. It is multi-platform and the goal is to make it work equally well on Windows, Linux and OSX. 
> Python 2.7 and 3.5 is no longer supported since Poetry 1.2. Consider updating your Python version to a supported one.

<br><br>

---

## Installing Poetry 

<br>

Poetry provides a custom installer python script ( `get-poetry.py` <a href="https://python-poetry.org/blog/announcing-poetry-1.2.0a1/" target="_blank">[Deprecated]</a> / `install-poetry.py` ) that will install `poetry` isolated from the rest of your system by vendorizing its dependencies. This is the recommended way of installing `poetry`:

<br>

Linux / OSX / Bash on Windows:
```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -
```

Powershell:
```powershell
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py -UseBasicParsing).Content | python -
```

> The installer installs the `poetry` tool to Poetry's `bin` directory. On Linux it is located at `$HOME/.poetry/bin` and on Windows at `%USERPROFILE%\.poetry\bin`.

<br><br>

## Project setup

<br>

### **Option 1: New project**

First, let's create our new project, let's call it `poetry-demo`:
```bash
poetry new poetry-demo
```

### **Option 2: Initializing a pre-existing project**
Instead of creating a new project, Poetry can be used to 'initialize' a pre-populated directory. To interactively create a `pyproject.toml` file in directory `pre-existing-project`:
```bash
cd pre-existing-project
poetry init
```

<br>

Doing either of the above steps will create the `poetry-demo` directory with the following content:
```
poetry-demo
|__ pyproject.toml
|__ README.rst
|__ poetry_demo
|   |__ __init__.py
|
|__ tests
    |__ __init__.py
    |
    |___ test_poetry_demo.py
```

The `pyproject.toml` file is what is the most important here. This will orchestrate your project and its dependencies. For now, it looks like this:
```ini
[tool.poetry]
name = "poetry-demo"
version = "0.1.0"
description = ""
authors = ["Sébastien Eustace <sebastien@eustace.io>"]

[tool.poetry.dependencies]
python = "*"

[tool.poetry.dev-dependencies]
pytest = "^3.4"
```

<br>

To get your poetry environment details, use the following command:
```bash
poetry env info
```

<br><br>


---

## Adding dependencies to your project
<br>

If you want to add dependencies to your project, use the `add` command:
```bash
poetry add SomePackage
```
It will automatically find a suitable version constraint and install the package and subdependencies.

<br>

You may also add dependencies to your project by hand by modifying the `pyproject.toml` file under the `tool.poetry.dependencies` section:
```ini
[tool.poetry.dependencies]
SomePackage = "^1.4"
```
Poetry uses this information to search for the right set of files in package "repositories" that you register in the `tool.poetry.repositories` section, or on <a href="https://pypi.org/" target="_blank">PyPI</a> by default.

<br>

If you have a private repository apart from PyPI, you'll need to configure your project with <a href="https://python-poetry.org/docs/repositories/" target="_blank">these steps</a>.

<br><br>

---

## Running your project

<br>

### **Option 1: Using `poetry run`**
To run your script along with all the dependencies defined in `pyproject.toml`, simply use `poetry run python your_script.py`. Likewise if you have command line tools such as `pytest` or `black` you can run them using `poetry run pytest`. 

<br>

### **Option 2: Activating the virtual environment**
The easiest way to activate the virtual environment is to create a new shell with `poetry shell`. To deactivate the virtual environment and exit this new shell, type `exit`. To deactivate the virtual environment without exiting, use `deactivate`. 

<br>

> **Why a new shell?**<br>
Child processes inherit their environment from their parents, but do not share them. As such, any modifications made by a child process, is not persisted after the child process exits. A python application (Poetry), being a child process, cannot modify the environment of the shell that it has been called from. <br>
Therefore, Poetry has to create a sub-shell with the virtual environment activated in order for the subsequent commands to run from within the virtual environment

<br><br>

---

## Install dependencies for shared projects
<br>

To install the defined dependencies for your (team's) project, just run the `install` command:
```bash
poetry install
```
If you have never run this command before and there is no `poetry.lock` file present, Poetry simply resolves all dependencies listed in `pyproject.toml` file and downloads the latest versions of their files.

When Poetry has finished installing, it'll write all of the packages and their exact versions to the `poetry.lock` file. It is *best practice* to commit the `poetry.lock` file to your project repo so teammates are locked to the same versions of dependencies. 

<br><br>

---

## Publishing to PyPI
<br>

### <ins>Packaging</ins>
Before you can publish your library, you will need to package it:
```bash
poetry build
```
This command will package your library in two different formats: `sdist` which is the source formet, and `wheel` which is a `compiled` package.

Once that is ready, you're ready to publish your library!

<br>

### <ins>Publishing</ins>
Poetry will publish to PyPI by default. Anything that is published to PyPI is automatically available through Poetry. 

If we wanted to share our package `poetry-demo` with the Python community, we would do so with this command:
```bash
poetry publish
```

This will package and publish the library to PyPI, at the condition that you are a registered user and you have <a href="https://python-poetry.org/docs/repositories/#configuring-credentials" target="_blank">configured your credentials</a> properly. 




<br><br>

---

## Uninstalling Poetry
<br>

If you decide that Poetry isn't your cup of tea, you can completely remove it from your system by running the installer again with the `--uninstall` option or by setting the `POETRY_UNINSTALL` environment variable before executing the installer:
```bash
python get-poetry.py --uninstall                # Option 1
POETRY_UNINSTALL=1 python get-poetry.py         # Option 2
```



<br><br>

---

## Acknowledgements

#### - [Pip Documentation - The pip developers](https://pip.pypa.io/en/stable/user_guide/)


<br><br><br>