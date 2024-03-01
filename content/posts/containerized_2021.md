---
author: ["Patrick Brunier"]
title: "Containerized"
date: "2021-04-28"
description: ""
summary: "This evening I finished migrating my servers to 95% containerized workloads."
tags: ["Docker", "Ethics", "IT", "Open Source"]
categories: ["IT"]
series: [""]
ShowToc: false
TocOpen: false
---

This evening I finished migrating my servers to 95% containerized workloads.

Although lightweight, the setup of the conventional workloads became quiet complex over the years.

As I do not need complex orchestrations or automatic scaling, I managed to move all my business needs to Docker, following the KISS principle, without any Kubernetes involved.

Some of the containerized apps: Nextcloud, PostgreSQL, Django NGINX instances, Jenkins, Buildbot, Node-RED, Camunda, JupyterHub, Gitea, Robot Framework, Mosquitto, XMPP, Redis, Apache CouchDB. The only thing left out of Docker is the backup.

In the past years I managed to move all my business activities, both end user computing and my servers to Open Source , and therefore I don’t suffer from vendor lock-in. My bookkeeping and VAT also has to be done using Open Source software. I use GNU Cash for this, but I have to admit that is a pain. But hey. No pain no gain 😉

![Image description](/imgs/docker_logo.png)
{.pi_center}