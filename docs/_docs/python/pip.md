---
title: Pip Package manager
tags: 
 - python
description: Getting started with Python
---


# Pip package manager 

<br>

---

## Installing packages
<br>
You may install packages using the following format where `python` refers to the Python interpreter you want to install the package for:

```bash
python -m pip install PACKAGE==VERSION
python -m pip install PACKAGE>=VERSION
```

You may also choose to install packages from a `requirements.txt` for bigger projects:
```bash
python -m pip install -r requirements.txt
```
Format of the `requirements.txt` file can be found [here](https://pip.pypa.io/en/stable/reference/requirements-file-format/#requirements-file-format)

<br><br>

---

## Installing from Wheels
<br>
"Wheels" are built, archive format files that can greatly speed installation compared to building from source archives. 
To install directly from a wheel archive:

```bash
python -m pip install SomePackage-1.0-py2.py3-none-any.whl
```

<br>

For the cases where wheels are not available, pip offers [pip wheel](https://pip.pypa.io/en/stable/cli/pip_wheel/#pip-wheel) as a convenience, to build wheels for all your requirements and dependencies. 

pip wheel requires the [wheel package](https://pypi.org/project/wheel/) to be installed, which provides the "bdist_wheel" setuptools extension that it uses.

To build wheels for your requirements and all their dependencies in a local directory:
```bash
python -m pip install wheel
python -m pip wheel --wheel-dir=/local/wheels -r requirements.txt
```

And then to install those requirements just using your local directory of wheels (not from PyPI):
```bash
python -m pip install --no-index --find-links=/local/wheels -r requirements.txt
```

<br><br>

---

## Uninstalling packages
<br>
pip is able to uninstall packages like so:

```bash
python -m pip uninstall SomePackage
```

<br><br>

---

## Configuration
Configuration files can change the default values for command line option. They are written using standard INI style configuration.

pip has 4 "levels" of configuration lines with increasing priority:
- `PIP_CONFIG_FILE`, if given
- `Global`: system-wide configuration file, shared across users
- `User`: per-user configuration file
- `Site`: per-environment configuration file, i.e. per virtulenv

<br>

### Location
<br>

pip's configuration files are located in fairly standard locations.

**Global** 
In a "pip" subdirectory of any of the paths set in the environment variable `XDG_CONFIG_DIRS`, for example `/etc/xdg/pip/pip.conf`

**User** 
`$HOME/.config/pip/pip.conf`, which represents the `XDG_CONFIG_HOME` environment variable
The legacy "per-user" configuration file `$HOME/.pip/pip.conf` is also loaded if it exists.

**Site** 
`$VIRTUAL_ENV/pip.conf`

<br>

### Environment variables

pip's command line options can be set with environment variables using the format `PIP_<UPPER_LONG_NAME>`. Dashes (-) have to be replaced with underscores (_).

- `PIP_DEFAULT_TIMEOUT=60` is the same as `--default-timeout=60`

<br>

### Priority

In terms of priority, the override order is as follows:
> Command-line options > Environment variables > Configuration files 


<br><br>

---

## Using a proxy server
When installing packages from [PyPi](https://pypi.org/), pip requires internet access, which in many corporate environments require an outbound HTTP proxy server. 

pip can be configured to connect through a proxy server in various ways:
- Using the `--proxy` command-line option to specify a proxy in the form `[user:password@]proxy.server:port`
- Using `proxy` in a [Config file](https://pip.pypa.io/en/stable/user_guide/#config-file)
- By setting the standard environment variables `http_proxy`, `https_proxy` and `no_proxy`
- Using the environment variable `PIP_USER_AGENT_USER_DATA` to include a JSON-encoded string in the user-agent variable used in pip's requests






<br><br>

---

## Acknowledgements

#### - [Pip Documentation - The pip developers](https://pip.pypa.io/en/stable/user_guide/)


<br><br><br>