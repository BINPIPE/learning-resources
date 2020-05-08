# Learning Notes - DevOps 

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---


## What is Jenkins?

**Jenkins** is a continuous integration server (continuous integration server is the practice of running tests on non-developer machine automatically every time when new code is pushed into source repository). Jenkins is written in Java. It provides many plugins that help to support building, deploying and automating any project. It can be installed through native system packages, Docker or even run standalone by any machine with the help of JRE (Java Runtime Environment). It automates multiple tasks including building, testing and delivering software.

Continuous integration server has tremendous advantage. It helps to provide information if all the tests working properly and getting fast feedback. Fast feedback helps you whenever you broke the build and introduce changes. So you get to know about the error codes and get rectified immediately. Continuous deployment and delivery are built on the top of continuous integration and Jenkins helps to speed up the deployment process.

## What is Continuous Integration?

In Continuous Integration after a code commit, the software is built and tested immediately. In a large project with many developers, commits are made many times during a day. With each commit code is built and tested. If the test is passed, build is tested for deployment. If deployment is a success, the code is pushed to production. This commit, build, test, and deploy is a continuous process and hence the name continuous integration/deployment.

A Continuous Integration Pipeline is a powerful instrument that consists of a set of tools designed to  **host**,  **monitor**,  **compile**  and  **test**  code, or code changes, like:

-   **Continuous Integration Server**  (Jenkins, Bamboo, CruiseControl, TeamCity, and others)
-   **Source Control Tool**  (e.g., CVS, SVN, GIT, Mercurial, Perforce, ClearCase and others)
-   **Build tool**  (Make, ANT, Maven, Ivy, Gradle, and others)
-   **Automation testing framework**  (Selenium, Appium, TestComplete, UFT, and others)

## Jenkins History

-   Kohsuke Kawaguchi, a Java developer, working at SUN Microsystems, was tired of building the code and fixing errors repetitively. In 2004, created an automation server called Hudson that automates build and test task.
-   In 2011, Oracle who owned Sun Microsystems had a dispute with Hudson open source community, so they forked Hudson and renamed it as Jenkins.
-   Both Hudson and Jenkins continued to operate independently. But in short span of time, Jenkins acquired a lot of projects and contributors while Hudson remained with only 32 projects. With time, Jenkins became more popular, and Hudson is not maintained anymore.

## Why use Jenkins?

**Faster Development**
Pulling the entire code for building and testing can consume a lot of time. Jenkins helps in automate building and testing systems to the integration work.

**Better Software Quality**
While developing software, generally the issues are detected and resolved before it is completed which makes it a better software with quality assurance while saving a lot of money to the organisation.

**Easily Customisable**
A developer can easily use Jenkins with multiple plugins and you can also customise and bring multiple possibilities in using the software. The plugins are categorised on the Jenkins website and a user must follow the special instructions while installing the plugins.

**Effortless Auditing Of Previous Run**
There is no need for spending time on human efforts while capturing the console output. Jenkins capture console output for both stdout and stderr while running jobs. Also, the distribution method of Jenkins enables you to send a developer’s work across multiple platforms without any struggle.

**Large Community**
Jenkins has grown large community support and has many plugins available including GitHub, Slack, Docker, etc. by which the project is kept as well-maintained and updated. You can also join in the community of Jenkins extensively and interact with the developers, share feedbacks and views on further improvements, etc.
### Jenkins Plugins

By default, Jenkins comes with a limited set of features. If you want to integrate your Jenkins installation with version control tools like Git, then you need to install plugins related to Git. In fact, for integration with tools like Maven, Amazon EC2, you need to install respective plugins in your Jenkins.


## Disadvantages of using Jenkins

Though Jenkins is a very powerful tool, it has its flaws.

-   Its interface is out dated and not user friendly compared to current UI trends.
-   Though Jenkins is loved by many developers, it's not that easy to maintain it because Jenkins runs on a server and requires some skills as server administrator to monitor its activity.
-   One of the reasons why many people don't implement Jenkins is due to its difficulty in installing and configuring Jenkins.
-   Continuous integrations regularly break due to some small setting changes. Continuous integration will be paused and therefore requires some developer attention.

## Conclusion:

-   In Continuous Integration, after a code commit, the software is built and tested immediately
-   Jenkins is an open source Continuous Integration server capable of orchestrating a chain of actions
-   Before Jenkins when all Developers had completed their assigned coding tasks, they used to commit their code all at same time. Later, Build is tested and deployed.
-   After Jenkins the code is built and test as soon as Developer commits code. Jenkin will build and test code many times during the day
-   By default, Jenkins comes with a limited set of features. If you want to integrate your Jenkins installation with version control tools like Git, then you need to install plugins related to Git
-   The biggest pros of Jenkins is that it is managed by the community which holds public meetings and take inputs from the public for the development of Jenkins projects
-   The biggest con of Jenkin is that Its interface is out dated and not user friendly compared to current UI trends.

## INSTALLATION STEPS

## Step 1 — Installing Jenkins (Non Docker)

The version of Jenkins included with the default Ubuntu packages is often behind the latest available version from the project itself. To take advantage of the latest fixes and features, you can use the project-maintained packages to install Jenkins.

Install java 8  

```
sudo apt install openjdk-8-jre  
```

Set default java version as java 8  
```
sudo update-alternatives --config java
```
Add the key  
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
```
Add repository  

```sudo apt-add-repository "deb https://pkg.jenkins.io/debian-stable binary/"```


Install jenkins  
```
sudo apt install jenkins
```

Now that Jenkins and its dependencies are in place, we’ll start the Jenkins server.  

## Step 2 — Starting Jenkins

Let’s start Jenkins using  `systemctl`:

```
sudo systemctl start jenkins

```

Since  `systemctl`  doesn’t display output, you can use its  `status`  command to verify that Jenkins started successfully:

```
sudo systemctl status jenkins
```

If everything went well, the beginning of the output should show that the service is active and configured to start at boot:

```
● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; generated)
   Active: active (exited) since Mon 2018-07-09 17:22:08 UTC; 6min ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 0 (limit: 1153)
   CGroup: /system.slice/jenkins.service
```

Now that Jenkins is running, let’s adjust our firewall rules so that we can reach it from a web browser to complete the initial setup.

## Step 3 — Opening the Firewall

By default, Jenkins runs on port  `8080`, so let’s open that port using  `ufw`:

```
sudo ufw allow 8080
```

Check  `ufw`’s status to confirm the new rules:

```
sudo ufw status
```

You will see that traffic is allowed to port  `8080`  from anywhere:

```
To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
8080                       ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
8080 (v6)                  ALLOW       Anywhere (v6)
```

**Note:**  If the firewall is inactive, the following commands will allow OpenSSH and enable the firewall:

```
-   sudo ufw allow OpenSSH
-   sudo ufw enable
```

With Jenkins installed and our firewall configured, we can complete the initial setup.

## Step 4 — Setting Up Jenkins

To set up your installation, visit Jenkins on its default port,  `8080`, using your server domain name or IP address:  `http://your_server_ip_or_domain:8080`

You should see the  **Unlock Jenkins**  screen, which displays the location of the initial password.

In the terminal window, use the  `cat`  command to display the password:

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the 32-character alphanumeric password from the terminal and paste it into the  **Administrator password**  field, then click  **Continue**.

The next screen presents the option of installing suggested plugins or selecting specific plugins. We’ll click the  **Install suggested plugins**  option, which will immediately begin the installation process. When the installation is complete, you will be prompted to set up the first administrative user. It’s possible to skip this step and continue as  `admin`  using the initial password we used above, but we’ll take a moment to create the user.


## Installing Jenkins (Docker)

Assuming that Docker is installed in the server already, the following script (or commands from the script) can be run to install Jenkins.

```
#!/bin/bash
 
# Pull latest container
docker pull jenkins
 
# Setup local configuration folder
# Should already be in a jenkins folder when running this script.
export CONFIG_FOLDER=$PWD/config
mkdir $CONFIG_FOLDER
chown 1000 $CONFIG_FOLDER
 
# Start container
docker run --restart=always -d -p 49001:8080 \
-v $CONFIG_FOLDER:/var/jenkins_home:z \
--name jenkins -t jenkins
 
docker logs --follow jenkins
```

Additional Stuff-

* [A good article on webooks triggering automated builds](https://medium.com/faun/triggering-jenkins-build-on-push-using-github-webhooks-52d4361542d4)



<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry. 
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions. 
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
