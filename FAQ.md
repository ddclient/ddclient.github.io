---
layout: default
title: Frequently asked questions
nav_order: 5
---

# ddclient doesn't update after changing IP using webinterface.

This is done by default.  Ddclient uses its own cache to verify if the ip changes. It does not use dns to get the current state.  Ddclient uses this system to prevent problems caused by bad dns servers or propagation problems.
