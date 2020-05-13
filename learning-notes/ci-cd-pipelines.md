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

Follow the `Jenkins-CI/CD Pipelines` video at [youtube.binpipe.org](https://youtube.binpipe.org) for a complete run-through of the following use cases:

- **Freestyle CI/CD Pipeline Job on Jenkins** //Static-Website HTML/CSS  
source-code:


- **Freestyle CI/CD Pipeline Job on Jenkins** //Java Project    
source-code:


- **Multi-branch deployments**  


- **Parametrized Jobs**  

- **Upstream & Downstream Jobs**  

- **Scripted Pipelines** (Groovy)      
source-code:

- **Declarative Pipelines**     
source-code:

<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry.
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions.
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
