# Learning Notes - Monitoring, Logging, Alerting

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---



**Monitoring** provides feedback from production. Monitoring delivers information about an application’s performance and usage patterns.

*One goal of monitoring is to achieve high availability by minimizing time to detect and time to mitigate (TTD, TTM).*
In other words, as soon as performance and other issues arise, rich diagnostic data about the issues are fed back to development teams via automated monitoring. That’s TTD. DevOps teams act on the information to mitigate the issues as quickly as possible so that users are no longer affected. That’s TTM. Resolution times are measured, and teams work to improve over time. After mitigation, teams work on how to remediate problems at root cause so that they do not recur. That time is measured as TTR.

*A second goal of monitoring is to enable “validated learning” by tracking usage.*
The core concept of validated learning is that every deployment is an opportunity to track experimental results that support or diminish the hypotheses that led to the deployment.

“**Telemetry**” is the mechanism for collecting data from monitoring. Telemetry can use agents that are installed in the deployment environments, an SDK that relies on markers inserted into source code, server logging, or a combination of these.

“**Synthetic monitoring**” uses a consistent set of transactions to assess performance and availability. Synthetic transactions are predictable tests that have the advantage of allowing comparison from release to release in a highly predictable manner.


### What is logging?

The purpose of logging is to track error reporting and related data in a centralized way. Logging should be used in big applications and it can be put to use in smaller apps, especially if they provide a crucial function. The term logging can refer both to the practice of event logging or to the  [actual log files](https://en.wikipedia.org/wiki/Log_file)  that result.

### What is tracing?

Where logging provides an overview to a discrete, event-triggered log, tracing encompasses a much wider, continuous view of an application. The goal of tracing is to following a program’s flow and data progression.

### What are metrics?

While monitoring may be a casual term that can be applied to tracing or logging or a number of other activities, in this context, monitoring is much more specific: instrumenting an application and then  [collecting, aggregating, and analyzing metrics](https://www.digitalocean.com/community/tutorials/an-introduction-to-metrics-monitoring-and-alerting)  to improve your understanding of how the system behaves.
<hr>
Hands-On Labs & Demonstration:

### Netdata
Netdata is a monitoring agent designed to run on all your systems: physical and virtual servers, containers, even IoT/edge devices. Netdata runs on Linux, FreeBSD, macOS, Kubernetes, Docker, and all their derivatives.

To install Netdata from source and get  _automatic nightly updates_, run the following as your normal user:
```
bash  <(curl -Ss https://my-netdata.io/kickstart.sh)
```
Can also run it as Docker Container-

```
docker run -d --name=netdata \
-p 19999:19999 \
-v netdatalib:/var/lib/netdata \
-v netdatacache:/var/cache/netdata \
-v /etc/passwd:/host/etc/passwd:ro \
-v /etc/group:/host/etc/group:ro \
-v /proc:/host/proc:ro \
-v /sys:/host/sys:ro \
-v /etc/os-release:/host/etc/os-release:ro \
--restart unless-stopped \
--cap-add SYS_PTRACE \
--security-opt apparmor=unconfined \
netdata/netdata
```
To uninstall Netdata:
```
wget https://raw.githubusercontent.com/netdata/netdata/master/packaging/installer/netdata-uninstaller.sh
chmod +x ./netdata-uninstaller.sh
./netdata-uninstaller.sh --yes --env /etc/netdata/.environment
```

### ELK Stack
"ELK" is the acronym for three open source projects: Elasticsearch, Logstash, and Kibana. Elasticsearch is a search and analytics engine. Logstash is a server‑side data processing pipeline that ingests data from multiple sources simultaneously, transforms it, and then sends it to a "stash" like Elasticsearch. Kibana lets users visualize data with charts and graphs in Elasticsearch.


**Demonstration**-
[https://github.com/BINPIPE/elk-stack-demo](https://github.com/BINPIPE/elk-stack-demo)

### Prometheus + Grafana + CAdvisor to Monitor Containers

### What is Prometheus?[](https://prometheus.io/docs/introduction/overview/#what-is-prometheus)

[Prometheus](https://github.com/prometheus)  is an open-source systems monitoring and alerting toolkit originally built at  [SoundCloud](https://soundcloud.com/). Since its inception in 2012, many companies and organizations have adopted Prometheus, and the project has a very active developer and user  [community](https://prometheus.io/community). It is now a standalone open source project and maintained independently of any company.

### What is Grafana?
Grafana is a multi-platform open source solution for running data analytics, pulling up metrics that make sense of the massive amount of data, and monitoring apps through customizable dashboards.

**Demonstration**- [https://github.com/BINPIPE/dockprom](https://github.com/BINPIPE/dockprom)





<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry.
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions.
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
