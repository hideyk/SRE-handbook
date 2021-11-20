# Installing Jenkins

The procedures in this chapter are for new installations of Jenkins. 

Jenkins is typically run as a standalone application in its own process with the built-in Java servlet container/application server ([Jetty](https://www.eclipse.org/jetty/)).

Jenkins can also be run as a servlet in different Java servlet containers such as [Apache Tomcat](https://tomcat.apache.org/) or [GlassFish](https://javaee.github.io/glassfish/). However, instructions for setting up these types of installations are beyond the scope of this chapter. 

<br><br>

---

## Linus

### Prerequisites

Minimum hardware requirements:

- 256 MB of RAM
- 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)

Recommended hardware configuration for a small team:
- 4 GB+ of RAM
- 50 GB+ of drive space

Comprehensive hardware recommendations:
- Hardware: see the [Hardware Recommendations](https://www.jenkins.io/doc/book/scaling/hardware-recommendations) page

### Java requirements
- [Java 8](https://docs.datastax.com/en/jdk-install/doc/jdk-install/installOpenJdkDeb.html) runtime environments are supported in both 32-bit and 64-bit versions
- [Java 11](https://developers.redhat.com/blog/2018/12/10/install-java-rhel8#tl__dr) runtime environments are supported
- Other Java versions unsupported

<br><br>

---

## Debian / Ubuntu

### Long Term Support release
A LTS (Long-Term Support) release is chosen every 12 weeks from the stream of regular releases at the stable release for that time period. It can be installed from the `debian-stable` apt repository.

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

This package installation will:
- Setup Jenkins as a daemon launched on start. See `/etc/init.d/jenkins` for more details.
- Create a 'jenkins' user to run this service
- Direct console log output to the file `/var/log/jenkins/jenkins.log`. Check this file if you are troubleshooting Jenkins
- Populate `/etc/default/jenkins` with configuration parameters for the launch, e.g `JENKINS_HOME`
- Set Jenkins to listen on port 8080. Access this port with your browser to start configuration. 

> If your `/etc/init.d/jenkins` file fails to start Jenkins, edit the `/etc/default/jenkins` to replace the line `----HTTP_PORT=8080----` with `----HTTP_PORT=8081----`. 

<br><br>

---

## Fedora

## Long Term Support release
A LTS (Long-Term Support) release is chosen every 12 weeks from the stream of regular releases as the stable release for that time period. It can be installed from the `redhat-stable` yum repository. 

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo dnf upgrade
# Add required dependencies for the jenkins package
sudo dnf install chkconfig java-devel
sudo dnf install jenkins
```


