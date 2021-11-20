---
layout: page
title: Docsy Jekyll Theme
permalink: /
---

# SRE Handbook
---

![](assets/static/sre-banner.png)

Author: Hideyuki Kanazawa (Site Reliability Engineer @ DBS Bank)

<br>

---

## Introduction
Herein documents my personal journey on learning Site Reliability Engineering best practices and condensed information for each SRE enabling software. 

<br>

---

# Site Reliability Engineer tools

## Technology stack

Ansible | Bash | Cloud | Docker | Elasticsearch | Git
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
<img src="assets/static/ansible.png" width="100">  |  <img src="assets/static/bash.png" width="100"> | <img src="assets/static/aws.jpg" width="100"> | <img src="assets/static/docker.png" width="100"> | <img src="assets/static/elasticsearch.png" width="100"> | <img src="assets/static/git.png" width="100">

Go | Grafana | Jenkins | Kafka | Kubernetes | Nginx
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
<img src="assets/static/go.png" width="100">  |  <img src="assets/static/grafana.jpg" width="100"> | <img src="assets/static/jenkins.png" width="100"> | <img src="assets/static/kafka.png" width="100"> | <img src="assets/static/kubernetes.png" width="100"> | <img src="assets/static/nginx.png" width="100">

Prometheus | Python | Terraform | - | - | -
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
<img src="assets/static/prometheus.png" width="100">  |  <img src="assets/static/python.png" width="100"> | <img src="assets/static/terraform.png" width="100"> 



---

## Motivation
With the advent of Web 2.0, anyone with a PC and functioning internet connectivity was able to create and share their wisdom with the rest of the world. While this drove an amazing open-source culture and led to a plethora of independently written knowledge articles, they were largely scattered so the average user might end up going down a rabbit hole and filling up their browser cache before learning how to echo `Hello World` in python. A metaphorical glue was needed to integrate these loosely coupled articles into a cohesive information stack, something which organizations like Wikipedia, Atlassian & Stack Overflow did a marvellous job in. This enabled the average internet user with a myriad of possibilities on the technologies and software they can learn. At the same time, this created a new challenge for software professionals who would have to put in a little more elbow grease to sieve through and find the most relevant documentation. As Desmond MacHale once put it, "The average human (user) has one breast and one testicle". With every design decision there's a trade-off, albeit a minor one in this case. Therefore, the purpose of this handbook is to provide condensed information and equip software professionals (with familiarity in command lines and basic programming knowledge) with the tools required to kick-start their SRE journey.

> **TLDR; too many loosely-coupled articles on the internet, I compile SRE stuff for software professionals**

<br>

## Disclaimer
While the content here do include my experience and sentiments, **most** of the material are sourced from articles by software giants & technical experts. As *Bernard of Chartres* famously quoted, "we stand on the shoulders of giants". I'm gratified and honoured to be provided wisdom in the works of people much more intelligent than I am, and pleased to be able to share what I learnt with the rest of the world. 

> **TLDR; this guide stands on the shoulders of giants** 

<br>


---


## Project Structure

For each SRE enabling tool, the folder will contain a couple of files which prescriptively provide knowledge on operationalizing it in a production setting. 

- README.md - General information & best practices
- SETUP.md - Instructions on how to set-up the SRE tool on multiple platforms (Typically Ubuntu, Fedora, Windows)
- CONFIG.md - Configuring your tool to fit your organization use-case
- USECASES.md - Examples of using the SRE tool in production
- MONITOR.md - How to monitor the tool and ensure that everything is running smoothly


<br>

---

## Other SRE guides available on Github

- [Site Reliability Engineer guide - vorozhko](https://github.com/vorozhko/site-reliability-engineer-guide)
- [SRE University - andrealmar](https://github.com/andrealmar/sre-university)
- [Awesome Site Reliability Engineering - dastergon](https://github.com/dastergon/awesome-sre)