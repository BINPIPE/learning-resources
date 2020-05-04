# Learning Notes - DEVOPS INTRODUCTION 

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---



**What is DevOps?**

> DevOps is the combination of cultural philosophies, practices, and > tools that increases an organization’s ability to deliver applications > and services at high velocity: evolving and improving products at a > faster pace than organizations using traditional software development > and infrastructure management processes. This speed enables > organizations to better serve their customers and compete more > effectively in the market.

 [*As defined by Amazon Web Services.*](https://aws.amazon.com/devops/what-is-devops/)


DevOps is not a technology or tool, it is a concept of behavior, and it is an extension of AgileMethodology.The DevOps is a set of practices designed to overcome the gap between development, QAand Operations by effective communication and collaboration, incorporating continuousintegration process with automated deployment.

DevOps helps to increase an organization’s speed to deliver applications and services. It allows organizations to serve their customers better and compete more strongly in the market.There are four basic continuous processes in DevOps:

- Continuous Integration
- Continuous Delivery
- Continuous Testing
- Continuous Monitoring

**Relationship between Agile and DevOps**

Agile Development is an umbrella term for several iterative and incremental softwaredevelopment methodologies.The most popular agile methodologies include Extreme Programming (XP), Scrum, Crystal,Lean Development, and Feature-Driven Development (FDD).On the other hand, DevOps is about a culture where development and operations collaborateto give maximum throughput and high-end outcomes.Similar to Agile, there are ways through which DevOps can be implemented such as deepcommunication and automated deployment.Agile is all about software development while DevOps deals with software development andoperations. *Note: Therefore one thing is clear that DevOps is an extension of agile methodology.*

**DevOps Lifecycle**

DevOps is  deep integration between development and  operations. Understanding DevOps  isnot possible without knowing DevOps life cycle.Here is brief information about the Continuous DevOps life-cycle:

- **Development**
In this DevOps stage the development of software takes place constantly. In this phase,  the  entire  development  process  is  separated  into  small  development  cycles.This benefits DevOps team to  speed up software development and  delivery process.

- **Testing**
QA team use tools like Selenium to identify and  fix bugs in the new piece of code.

- **Integration**
In this stage, new functionality is integrated with the prevailing code, and testingtakes place. Continuous development is only possible due to continuous integrationand testing.

- **Deployment**
In this phase, the deployment process takes place continuously. It is performed insuch a manner that any changes made any time in the code, should not affect the functioning of high  traffic application.

- **Monitoring**
In this phase, operation team will take care of the inappropriate system behavior orbugs which are found  in production.

**Software Tools for DevOps**

As DevOps is the collaboration of Development, QA and Operations, it is obvious that asingle tool cannot be adequate for all the needs. So there are multiple tools required in eachstage to perform all the  operations successfully.

**Popular Tool for DevOps  Automation**-
- Git : Version Control System tool
- Jenkins : Continuous Integration tool
- Selenium : Continuous Testing tool
- Puppet/Chef/Ansible : Configuration Management and Deployment tools
- Nagios/Netdata/Datadog : Continuous Monitoring tool
- Docker : Containerization tool
- Kubernetes/ECS/Mesos: Orchestrators

**How do all these tools work  together?**

This flow may vary from organization to organization as per the  requirement.

- Developers develop the code and this source code is managed by Version ControlSystem tools like Git etc.
- Developers send this code to the Git repository and any changes made in the  code iscommitted to this Repository.
- Jenkins pulls this code from the repository using the Git plugin and builds it usingtools like Ant or Maven.
- Configuration management tools like puppet deploys & provisions testing the environment and then Jenkins releases this code on the test environment on whichtesting is done using tools like selenium.
- Once the code is tested, Jenkins send it for deployment on the production server(even production server is provisioned & maintained by tools like puppet).
- After deployment It is continuously monitored by tools like Nagios.
- Docker containers provides testing environment to test  the build features. Docker containers can be deployed and scaled using orchestrators like Kubernetes & Apache Mesos.





<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry. 
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions. 
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
