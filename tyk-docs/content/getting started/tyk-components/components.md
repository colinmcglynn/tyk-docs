---
date: 2017-03-23T13:07:27Z
title: Tyk Components
menu:
  main:
    parent: "Getting Started"
weight: 1
url: "/getting-started/tyk-components"
---

A full Tyk stack consists of the following components working together:

* **Tyk Gateway**: This does all the heavy lifting, the actual proxy doing all the work
* **Tyk Dashboard**: This is the GUI to control your Gateways and view analytics, as well as an extended Dashboard REST API that enables granular integration
* **Tyk Pump**: A data processor that moves analytics data from your Gateways (Redis) into other data sinks, most importantly MongoDB for the Tyk Dashboard to process.
The following sections will outline in detail show all of the Tyk component operate.
