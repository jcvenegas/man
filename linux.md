---
title: Linux
layout: 2017/sheet
prism_languages: [bash]
weight: -3
tags: [Featured]
category: cli
updated: 2020-06-21
---

## Getting started
{: .-three-column}

### Clean up logs
{: .-prime}

#### clean.sh
{: .-file}

```sh
journalctl --disk-usage
sudo journalctl --vacuum-size=500M
sudo truncate -s 0 /var/log/syslog*
sudo truncate -s 0 /var/log/kern*
```
