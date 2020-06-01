DevOps Use-Cases &  Real-World Scenarios
======

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A?sub_confirmation=1)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)

```diff
- SCENARIO-1
```

There is a Static Website for a company. And this website needs to be deployed using automated CI/CD on Amazon Cloud Servers.

So basically the following has to be done:
```
- Deploy 2 EC2 instances (Ansible+Jenkins & WebServer)
- Create & Apply Playbooks to set up each of the above
- Create Pipeline in Jenkins
- Deploy the simple-website from https://github.com/BINPIPE/simple-website via the simple pipeline.
```
In other words, the requirement is to Create EC2 instances, install the prerequisites, checkout the code, run the pipeline.

```
(JENKINS+ANSIBLE)-------CI/CD Pipeline---------> (WEBSERVER)
```

[Solution](https://github.com/BINPIPE/simple-cicd-ec2):

The below repositories are to be used.

```
- https://github.com/BINPIPE/simple-cicd-ec2   ---> Playbook Repo for CI/CD
- https://github.com/BINPIPE/simple-website ---> Code Repo for Website
```
<hr>


<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry. 
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions. 
For self-study resources look around in this repository, <a href="https://www.binpipe.org">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>
___
**[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
[![BINPIPE](https://img.shields.io/badge/YouTube-red.svg)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
___
