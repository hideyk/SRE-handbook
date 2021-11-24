---
title: Setup
tags: 
 - python
description: Setting up python
---

# Setting up Python

<br>

---

## **Ubuntu**
The following setup instructions assume the user is running one of the following versions of Ubuntu:
- **Ubuntu 18.04**
- **Ubuntu 20.04**

<br>

### **Option 1: Install using apt**

<br>

### Step 1.1 - <ins>Update and refresh repository lists</ins>

```bash
sudo apt update
```

<br>

### Step 1.2 - <ins>Install supporting software</ins>
The software-properties-common package gives you better control over your package manager by letting you add PPA (Personal Package Archive) repositories:

```bash
sudo apt install -y software-properties-common
```

<br>

### Step 1.3 - <ins>Add Deadsnakes PPA</ins>
Deadsnakes is a PPA with newer releases than the default Ubuntu repositories. Add the PPA by entering the following:
```bash
sudo add-apt-repository ppa:deadsnakes/ppa
```

<br>

### Step 1.4 - <ins>Install Python 3</ins>
Now you can install Python 3.8 along with pip package manager with the following command:
```bash
sudo apt install -y python3.8 python3-pip
```
<br>

### Step 1.5 - <ins>Verify that Python installed successfully</ins>
```bash
python3 --version
```

<br><br>

### **Option 2: Install from source code (when internet connectivity is limited)**

<br>

### Step 2.1 - <ins>Update and refresh repository lists</ins>

```bash
sudo apt update
```

<br>

### Step 2.2 - <ins>Install supporting software</ins>
Compiling a package from source code requires additional software than just the software-properties-common:

```bash
sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget
```

<br>

### Step 2.3 - <ins>Download the latest version of Python source code</ins>
Change the python version in the download command below to suit your organization's needs. If the server has limited internet connectivity, copy it over using SCP or SFTP from another server in the VPN.
```bash
wget https://www.python.org/ftp/python/3.8.3/Python-3.8.3.tgz
```

<br>

### Step 2.4 - <ins>Extract compressed files
```bash
tar -xvf Python-3.8.3.tgz
```

<br>

### Step 2.5 - <ins>Test system and optimize Python
Before you install the software, make sure you test the system and optimize Python.

The `./configure` command evaluates and prepares Python to install on your system. Using the `--optimization` option speeds code execution by 10-20%.

```bash
cd Python-3.8.3

./configure --enable-optimization --with-ensurepip=install
```
This step can take up to 30 minutes to complete.

<br>

### Step 2.6 - <ins>Install a second instance of Python (recommended)
To create a second instance of Python, in addition to your current Python installation, enter the following
```bash
sudo make altinstall
```
It is recommended not to overwrite your current python installation as your Ubuntu system may have software packages dependent on Python 2.X.

### Step 2.7 - <ins>Verify that Python installed successfully</ins>
```bash
python3 --version
```

<br><br>

---

## **Fedora**

The following setup instructions assume the user is running one of the following versions of Fedora:
- **Fedora 33**
- **Fedora 34**

<br>

### Step 1 - <ins>Install required packages</ins>
Use the following command to install prerequisite packages for Python. (Failure to run the groupinstall "Development Tools" might result in [this issue](https://stackoverflow.com/questions/19816275/no-acceptable-c-compiler-found-in-path-when-installing-python))
```bash
sudo yum -y groupinstall "Development Tools"
sudo yum -y install gcc openssl-devel bzip2-devel libffi-devel zlib-devel wget
```

<br>

### Step 2 - <ins>Download the latest version of Python source code</ins>
Change the python version in the download command below to suit your organization's needs. If the server has limited internet connectivity, copy it over using SCP or SFTP from another server in the VPN.
```bash
wget https://www.python.org/ftp/python/3.8.3/Python-3.8.3.tgz
```

<br>

### Step 3 - <ins>Extract compressed files</ins>
```bash
tar -xvf Python-3.8.3.tgz
```

<br>

### Step 4 - <ins>Test system and optimize Python
Before you install the software, make sure you test the system and optimize Python.

The `./configure` command evaluates and prepares Python to install on your system. Using the `--optimization` option speeds code execution by 10-20%.

```bash
cd Python-3.8.3

./configure --enable-optimization --with-ensurepip=install
```
This step can take up to 30 minutes to complete.

<br>

### Step 5 - <ins>Install a second instance of Python (recommended)
To create a second instance of Python, in addition to your current Python installation, enter the following
```bash
sudo make altinstall
```
It is recommended not to overwrite your current python installation as your Ubuntu system may have software packages dependent on Python 2.X.

<br>

### Step 6 - <ins>Verify that Python installed successfully</ins>
```bash
python3 --version
```


<br><br>

---

## **Windows**

Head over to the official [Python downloads page](https://www.python.org/downloads/windows/) and install the relevant full installer for your system. 

Follow the instructions to get the full-featured Python development environment. 




<br><br>

---

## Acknowledgements

#### - [How to install python 3 - Phoenixnap](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu)
#### - [How To Install Python 3.8 on RHEL/CentOS 7 & Fedora 34/33 - TecAdmin](https://tecadmin.net/install-python-3-8-centos/)