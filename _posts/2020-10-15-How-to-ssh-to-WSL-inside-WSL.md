---
layout: post
title: "How to ssh into WSL inside WSL"
date: 2020-10-15
---

```
user$ sudo vi /etc/ssh/sshd_config # **See note below.
user$ sudo service ssh --full-restart

# Uncomment Port 22 in the sshd_config
```
