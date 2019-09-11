---
date: 2017-03-09T11:20:34Z
Title: Tyk API Gateway Documentation
diffTitleName: Tyk Documentation
menu:
  main:
    name: Documentation
url: "/"
weight: 1
diffTitle: true
---

Our documentation helps you get the most out of your Tyk installation. It covers all aspects of using Tyk to manage your APIs.

### [Getting Started](/docs/getting-started/)

If you are new to Tyk, this section introduces you to our application and its components, introduces key concepts, deployment options and how to install Tyk for demo and PoC purposes.

### [Try out Tyk](/docs/try-out-tyk/try-out-tyk/)

We have some tutorials to get you up and running with Tyk, for all our editions.
 
### [Basic Configuration and Security](/docs/basic-config-and-security/)

This section covers methods for configuring and applying security methods to Tyk.

### [Analytics and Reporting](/docs/analytics-and-reporting/)

How you can use the Tyk Dashboard's analytic functions.

### [Advanced Configuration](/docs/advanced-configuration/)

This section covers topics such as integration with 3rd parties, using Single Sign On (SSO), how to transform traffic and manage multiple environments.

### [Tyk Configuration Reference](/docs/tyk-config-reference/)

This section covers settings for all the Tyk components (Gateway, Dashboard, Pump, TIB, MDCB), plus some overall Tyk installation configuration options.

### [Plugins](/docs/plugins/)

How to customise your Tyk installation, with the use of Rich Plugins (Python, gRPC and LuaJIT) and JavaScript Middleware.

### [Planning for Production](/docs/planning-for-production/)

What to consider when installing Tyk in a production environment.

### [Tyk Multi Data Centre Bridge (MDCB)](/docs/tyk-multi-data-centre/)

How our separately licenced product allows you to use Tyk in the following manner:

MDCB acts as a broker between Tyk Gateway Instances that are isolated from one another and typically have their own Redis DB.

In order to manage physically separate Tyk Gateway clusters from a centralised location, Tyk MDCB needs to be used to provide a remote “back-end” for token and configuration queries.

### Tyk APIs

How to use our APIs.

* [Gateway API](/docs/tyk-gateway-api/)
* [Dashboard API](/docs/tyk-dashboard-api/)
* [Dashboard Admin API](/docs/dashboard-admin-api/)

### Current Versions

* Tyk Gateway v2.8.4
* Tyk Dashboard v1.8.4
* Tyk Pump v0.7.2
* Tyk Identity Broker (TIB) v0.6.0
* MDCB v1.6.1



### Supported MongoDB and Redis Versions

Tyk has been tested on the following versions:

* MongoDB 3.x and 4.0.x
* Redis 2.8.x to 5.0.x
