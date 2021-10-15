---
title: Sourcegraph Administrators Guide
author: jonah-dueck
tags: [Sourcegraph, Administrators, Tutorial]
publicationDate: October 15th, 2021
description: Comprehensive guide to being a Sourcegraph Site Administrator
image: https://storage.googleapis.com/sourcegraph-assets/learn/headers/sourcegraph-learn-09.png
imageAlt: Sourcegraph Learn
browserTitle: Sourcegraph Administrators Guide
type: posts
---
Adminstration and management in Sourcegraph is handled by Site Admins. These admins are typically the people responsible for deploying, managing, and configuring Sourcegraph for users on their instance. Site Admins have [elevated permissions](https://docs.sourcegraph.com/admin/privileges) within their Sourcegraph instance. 

This guide will walk you through the features and functionalities available to you as a Site Admin and how you can get started managing and maintaing your Sourcegraph instance. 

## Installation and Deployment


### What is the best deployment option for me?
We recommend Docker Compose for most initial production deployments. You can [migrate to a different deployment method](https://docs.sourcegraph.com/admin/updates#migrating-to-a-new-deployment-type) later on if needed.

If you need a deployment option offers a higher level of scalability and availability, the [Kubernetes deployment](https://docs.sourcegraph.com/admin/install/kubernetes) would be recommended. 

To help give you a starting point on choosing a deployment option and allocating resources to it, check out our [resource estimator](https://docs.sourcegraph.com/admin/install/resource_estimator)

For a comphrensive deployment guide for each option, check out our in-depth documentation for both [Docker Compose](https://docs.sourcegraph.com/admin/install/docker-compose) as well as [Kubernetes](https://docs.sourcegraph.com/admin/install/kubernetes)

### Deployment options 
| Deployment Type                                             | Suggested for                                           | Setup time        | Resource isolation | Auto-healing | Multi-machine |
| ----------------------------------------------------------- | ------------------------------------------------------- | ----------------- | :----------------: | :----------: | :-----------: |
| [**★ Docker Compose**](https://docs.sourcegraph.com/admin/install/docker-compose) | **Small & medium** production deployments               | 🟢 5 minutes     |         ✅         |      ✅      |      ❌       |
| [**★ Kubernetes**](https://docs.sourcegraph.com/admin/install/kubernetes)         | **Medium & large** highly-available cluster deployments | 🟠 30-90 minutes |         ✅         |      ✅      |      ✅       |
| [Single-container](https://docs.sourcegraph.com/admin/install/docker)              | Local testing                                           | 🟢 1 minute      |         ❌         |      ❌      |      ❌       |

> NOTE: Some features for production deployments [require a Sourcegraph license](https://about.sourcegraph.com/pricing/).

### On-prem vs Managed instances
Regardless of the deployment option you choose, Sourcegraph can be deployed either on-prem (whether locally or with the cloud provider of your choice) using the deployment options listed above. We also offer [managed instances](https://docs.sourcegraph.com/admin/install/managed) (we handle deployment, upgrades and management of the instance for you). Please [contact us](https://about.sourcegraph.com/contact/sales) if you are interested in learning more about managed instances. 


## Upgrading your instance 
New versions of Sourcegraph are release monthly (with patches released in between, as needed). New updates are announced in the [Sourcegraph blog](https://about.sourcegraph.com/blog) and comprehensive update notes are available in the [changelog](https://docs.sourcegraph.com/CHANGELOG). 

Regardless of the deployment type you choose, the following upgrade rules apply: 
- **Upgrade one minor version at a time**, e.g. v3.26 –> v3.27 –> v3.28.
    - Patches (e.g. vX.X.4 vs. vX.X.5) do not have to be adopted when moving between vX.X versions.
- **Check the [update notes](https://docs.sourcegraph.com/admin/updates#update-notes) for your deployment type for any required manual actions** before updating.
- Check your [out of band migration status](https://docs.sourcegraph.com/admin/migration) prior to upgrade to avoid a necessary rollback while the migration finishes.

To check the current version your instance is on, go to Site Admin > Updates: 
<div style="position: relative; padding-bottom: 70.22106631989598%; height: 0;"><iframe src="https://www.loom.com/embed/590a569c2fb54dd1a6a78096db75205f?hide_owner=true&hide_title=true&hideEmbedTopBar=true&autoplay=1" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

## Configuration

### Connecting to code hosts

### Setting up user authentication and repo permissions

### Site configuration 

### External services 

## Obersvability 

### Viewing instance health and metrics

### Troubleshooting
