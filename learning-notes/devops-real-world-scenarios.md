## DevOps implementations in Cloud

** Scenario-1 **

S - Situation 

There is a Static Website for a company. And this website needs to be deployed using automated CI/CD on Amazon Cloud Servers.

T - Task 
```
- Deploy 2 EC2 instances (Ansible+Jenkins & WebServer)
- Create & Apply Playbooks to set up each of the above
- Create Pipeline in Jenkins
- Deploy the simple-website from https://github.com/BINPIPE/simple-website via the simple pipeline.
```
A - Action

Create EC2 instances, install the prerequisites, checkout the code, run the pipeline.

R - Results

The Website should be live on the Webserver.
```
(JENKINS+ANSIBLE)----------------> (WEBSERVER)
```

References: 
```
- https://github.com/BINPIPE/simple-cicd-ec2   ---> Playbook Repo for CI/CD
- https://github.com/BINPIPE/simple-website ---> Code Repo for Website
```
