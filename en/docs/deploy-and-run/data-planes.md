---
sidebar_position: 15
title: Data plane models
description: Compare the WSO2 Cloud data plane and private data planes to choose where your integrations run.
keywords: [wso2 cloud, data plane, cloud data plane, cdp, private data plane, pdp, deployment model]
slug: /deploy-and-run/data-planes
---

# Data plane models

A **data plane** is the infrastructure your integrations actually run on. All runtime traffic is restricted to it, which keeps user data contained within its boundary. The **control plane** is the operations layer where deploy, manage, and observe actions happen; it orchestrates the data plane but does not run your integrations itself.

WSO2 Cloud offers two data plane models:

- The **WSO2 Cloud data plane (CDP)** — public cloud infrastructure owned and operated by WSO2, shared across organizations.
- A **private data plane (PDP)** — dedicated infrastructure for a single organization, giving full isolation at the runtime level.

Both are managed through the same WSO2 Cloud control plane, so the choice affects where your integrations run and who operates the underlying infrastructure. It does not change how you build or deploy them.

## At a glance

| | WSO2 Cloud data plane | Private data plane |
|---|---|---|
| Infrastructure | Owned and operated by WSO2, shared across organizations | Dedicated to your organization |
| Runtime isolation | Shared, multi-tenant | Full isolation |
| Where it runs | WSO2-operated regions (currently US East 2 and North Europe) | Azure, AWS, GCP, or on-premises infrastructure |
| Setup required | None — available as soon as your organization is created | A one-time Helm installation on your Kubernetes cluster |
| Environments | Development and Production by default; adding more requires a paid subscription | The number requested at setup, with more added as needed; unlimited on an Enterprise subscription |
| Maximum replicas per integration | Capped at 5 | No restriction |
| Container registry | WSO2-managed | Your own registry |
| Configurations and secrets | Encrypted and stored in a secure vault managed by WSO2 | Can be stored in your own infrastructure |
| Infrastructure responsibility | WSO2 | One of three [management models](deploy-on-private-data-plane/management-models.md) |
| Security | Operated by WSO2 | Three [security levels](deploy-on-private-data-plane/security-levels.md): basic, standard, and premium |

## When to choose a private data plane

A private data plane is the right choice when you:

- Have strict **data residency** requirements, or need a region the WSO2 Cloud data plane does not currently serve.
- Need to meet **compliance standards** such as GDPR or HIPAA.
- Need runtime traffic to stay **within your own network boundary**.
- Need to **scale beyond 5 replicas** for a single integration, or want to size infrastructure yourself.
- Want to keep configurations and secrets in **your own key vault**.

Otherwise the WSO2 Cloud data plane is the faster path: there is no infrastructure to provision, and WSO2 operates it for you.

:::note
A private data plane requires infrastructure you provide and maintain — an upstream-compatible Kubernetes cluster, a container registry, a key vault, and a logging service — along with a decision about how much of its operation you want to own. See [Set up a private data plane](deploy-on-private-data-plane/deploy-on-private-data-plane.md) for the full requirements.
:::

## What stays the same

The data plane model does not change the development or delivery experience. On either model you get:

- The same editor and the same [deployment workflow](deploy-to-wso2-cloud/deploy-to-wso2-cloud.md).
- The same WSO2 Cloud control plane for deploy, manage, and observe actions.
- Build-once-deploy-many promotion across environments, with configuration injected at runtime.
- Automated per-commit builds, image scanning, and rolling updates with health checks.

## What's next

- [Deploy your integration](deploy-to-wso2-cloud/deploy-to-wso2-cloud.md) — Get an integration onto WSO2 Cloud, on either data plane model.
- [Set up a private data plane](deploy-on-private-data-plane/deploy-on-private-data-plane.md) — Infrastructure requirements, system components, and control plane connectivity.
