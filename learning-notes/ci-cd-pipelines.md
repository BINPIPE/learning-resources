# CI/CD Pipelines

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---


## What is CI/CD?

CI/CD is a way of developing software in which you’re able to release updates at any time in a sustainable way. When changing code is routine, development cycles are more frequent, meaningful and faster.

“CI/CD” stands for the combined practices of Continuous Integration (CI) and Continuous Delivery (CD).

Continuous Integration is a prerequisite for CI/CD, and requires:

-   Developers to merge their changes to the main code branch many times per day.
-   Each code merge to trigger an automated code build and test sequence. Developers ideally receive results in less than 10 minutes, so that they can stay focused on their work.

The job of Continuous Integration is to produce an artifact that can be deployed. The role of automated tests in CI is to verify that the artifact for the given version of code is safe to be deployed.

In the practice of  **Continuous Delivery**, code changes are also continuously deployed, although the deployments are triggered manually. If the entire process of moving code from source repository to production is fully automated,  [the process is called  **Continuous Deployment**.

#### A litmus test for doing CI/CD!

    If any developer in your team can stop what they’re doing right now and ship the current development version of code to production in 20 minutes or less without anyone stressing about what could happen — congratulations, you’re doing CI/CD!


## CI/CD principles

Continuous Delivery practices take CI further by describing principles for successful production deployments:

-   **Architect the system in a way that supports iterative releases**. Avoid tight coupling between components. Implement metrics that help detect issues in real-time.
-   **Practice test-driven development to always keep the code in a deployable state**. Maintain a comprehensive and healthy automated test suite. Build in monitoring, logging, and fault-tolerance by design.
-   **Work in small iterations**. For example, if you develop in feature branches, they should live no longer than a day. When you need more time to develop new features, use feature flags.
-   Developers can  **push the code into production-like staging environments**. This ensures that the new version of the software will work when it gets in the hands of users.
-   **Anyone can deploy any version**  of the software to any environment on demand,  **at a push of a button**. If you need to consult a wiki on how to deploy, it’s game over.
-   **If you build it, you run it**. Autonomous engineering teams should be responsible for the quality and stability of the software they build. This breaks down the silos between traditional developers and operations groups, as they work together to achieve high-level goals.

## What are the benefits of CI/CD?

CI/CD is much more than the automation of tasks to avoid human error. It lets us get new solutions into the hands of users as quickly, efficiently and cheaply as possible.

**Deliver software with less risk**. CI/CD pipelines standardize release processes across projects. By testing every change in source code, we reduce the chances of introducing bugs.

**Release new features more frequently**. A CI/CD pipeline can visualize your entire path from commit to production in a single screen. You can navigate across stages, spot inefficiencies, and optimize your process. By removing the roadblocks to productivity, you enable your company to succeed.

**Deliver the product that users need**. Delivering updates often leads to more user feedback. You can take advantage of that by A/B testing features, or testing early versions of products with real customers. This way you avoid investing too much in features that your customers don’t need, and focus on those that matter.

**Improve developer productivity**. Engineering teams that don’t practice CI/CD often work under stress. There are constant fires for bad deploys and hard-to-fix outages. Developers write a lot of code that never gets used. Long-lived feature branches are too big to get proper peer review, so code degrades in quality. On the other hand, CI/CD guides product management to optimize for user impact. Developers deploy code while it’s fresh in their minds. The result is a happy engineering team.


## Demonstration of CI/CD Pipelines


```
::Prerequisites::
In the Jenkins node following should be installed, apart from the plugins that will be demonstrated in video-
sudo apt install docker.io
docker --version
> Docker version 18.09.2, build 6247962
sudo usermod -a -G docker jenkins
service jenkins restart
sudo systemctl enable docker
sudo systemctl start docker
```


Follow the `Jenkins-CI/CD Pipelines` video at [youtube.binpipe.org](https://youtube.binpipe.org) for a complete run-through of the following use cases:

- **Freestyle CI/CD Pipeline Job on Jenkins** //Static-Website HTML/CSS  
source-code: https://github.com/BINPIPE/static-site-docker.git


- **Freestyle CI/CD Pipeline Job on Jenkins** //Java Project    
source-code: https://github.com/BINPIPE/devops_pipeline_demo.git  

- **Upstream, Downstream & Scheduled Jobs**
Jobs that can be run as per predefined triggers or times.  

- **Parametrized Jobs**  
Jobs which run based on user-defined parameters. For instance, we can define environments where the code will be deployed to or the branch from where the code will be checked out.
source-code: https://github.com/BINPIPE/parametrized-job-demo  


- **Scripted Pipelines & Declarative Pipelines** (Groovy)      
source-code: https://github.com/BINPIPE/scripted-and-declarative-pipeline-demo.git  


-   The **key difference** between Declarative pipeline and Scripted pipeline would be with respect to their **syntaxes** and their **flexibility**.

-   Declarative pipeline is a relatively new feature that supports the pipeline as code concept. It makes the pipeline code easier to read and write. This code is written in a Jenkinsfile which can be checked into a source control management system such as Git.

-   Whereas, the scripted pipeline is a traditional way of writing the code. In this pipeline, the Jenkinsfile is written on the Jenkins UI instance.

-   Though both these pipelines are based on the groovy DSL, the scripted pipeline uses stricter groovy based syntaxes because it was the first pipeline to be built on the groovy foundation. Since this Groovy script was not typically desirable to all the users, the declarative pipeline was introduced to offer a simpler and more optioned Groovy syntax.

-   The declarative pipeline is defined within a block labelled ‘pipeline’ whereas the scripted pipeline is defined within a ‘node’.


Find the a demo repo here for these pipeline types - https://github.com/BINPIPE/scripted-and-declarative-pipeline-demo.git


**Structure and syntax of the Declarative pipeline:**

The Agent is where the whole pipeline runs. Example, Docker. The Agent has following parameters:

-   **any** – Which mean the whole pipeline will run on any available agent.

-   **none** – Which mean all the stages under the block will have to declared with agent separately.

-   **label** – this is just a label for the Jenkins environment

-   **docker** – this is to run the pipeline in Docker environment.


The Declarative pipeline code will looks like this:

```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t flask-app:latest .'
            }
        }


        stage('Test') {
            steps {
                sh 'python3 test.py'
            }
            post {
                always {junit 'test-reports/*.xml'}
            }
        }

        stage('Approve Deployment') {
            input{
                 message "Do you want to proceed for deployment?"
                    }
            steps {
                sh 'echo "Deploying into Server"'
                sh 'docker rm -f flask-app || true'
                sh 'docker run -d -p 5000:5000 --name flask-app flask-app:latest'
                sh 'echo "Check App at http://ip-address:5000/"'

              }
        }    

    }     
}
```


**Scripted Pipeline:**

-   The scripted pipeline is a traditional way of writing the Jenkins pipeline as code. Ideally, Scripted pipeline is written in Jenkins file on web UI of Jenkins.

-   Unlike Declarative pipeline, the scripted pipeline strictly uses groovy based syntax. Since this, The scripted pipeline provides huge control over the script and can manipulate the flow of script extensively.

-   This helps developers to develop advance and complex pipeline as code.


**Structure and syntax of the scripted pipeline:**

_Node Block_:

Node is the part of the Jenkins architecture where Node or agent node will run the part of the workload of the jobs and master node will handle the configuration of the job. So this will be defined in the first place as
```
node {
}
```
_Stage Block_:

Stage block can be a single stage or multiple as the task goes. And it may have common stages like

-   Cloning the code from SCM

-   Building the project

-   Running the Unit Test cases

-   Deploying the code

-   Other functional and performance tests.


So the stages can be written as mentioned below:
```
stage {
}
```
So, Together, the scripted pipeline can be written as mentioned below.

```
node('master') {
 stage('Source') {
  git 'https://github.com/BINPIPE/scripted-and-declarative-pipeline-demo.git'
 }
 stage('Build') {
  sh 'docker build -t flask-app:latest .'
 }

 stage('Test') {
  sh 'python3 test.py'
 }

}
```

-   Declarative Pipeline encourages a **declarative programming model**, whereas, Scripted Pipelines follow a more **imperative programming model**.

-   Declarative type imposes limitations to the user with a more strict and pre-defined structure, which would be ideal for simpler continuous delivery pipelines.

-   Scripted type has very few limitations that to with respect to structure and syntax that tend to be defined by Groovy, thus making it ideal for users with more complex requirements.


**Multi-Branch Pipelines**

The Multibranch Pipeline project type enables you to implement different Jenkinsfile for different branches of the same project. In a Multibranch Pipeline project, Jenkins automatically discovers, manages and executes Pipelines for branches that contain an in-source control.

Follow this repo - https://github.com/BINPIPE/multibranch-demo  

And the video to be able to learn about Multibranch pipelines.


**Integrating SonarQube with Jenkins for Code Quality Analysis**

Watch the video to follow the integration process.  
Reference repo - https://github.com/BINPIPE/java-springboot-sonarqube


**Integrating Slack with Jenkins for Alerts**

Watch the video to follow the integration process. We will cover, slack integration for freestyle jobs and declarative pipelines.  
Reference repo - https://github.com/BINPIPE/java-springboot-sonarqube

<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry.
Write to me at <b>learn@binpipe.org</b> if you are looking for tailor-made training sessions.
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
