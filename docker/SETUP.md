# Setup
---


## Ubuntu

The following setup instructions assume the user is running the following version of Ubuntu:
- **Ubuntu 20.04**

### Step 1 - Installing Docker
The Docker installation package available in the official Ubuntu repository may not be the latest version. To ensure we get the latest version, we'll install Docker from the official Docker repository. To do that, we'll add a new package source, add the GPG key from Docker to ensure the downloads are valid, then install the package

First, update your existing list of packages:
```bash
sudo apt update
```
Next, install a few prerequisite packages which let `apt` use packages over HTTPS:
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

Then add the GPG key for the official Docker repository to your system:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Add the Docker repository to APT sources:
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

This will also update our package database with the Docker packages from the newly added repo.
Make sure you are about to install from the Docker repo instead of the default Ubuntu repo
```bash
$ apt-cache policy docker-ce
```





---

## 