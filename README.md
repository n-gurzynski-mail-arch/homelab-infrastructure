# homelab-infrastructure

## Overview
This repository documents the physical architecture and software configuration of my beginner HomeLab environment. The core infrastructure is built on a 2-node Proxmox Virtual Environment cluster, designed to support future Cloud & DevOps projects.

## Hardware Specification
* **Master Node:** [HP EliteDesk 800 G3 (pve-master)](docs/EliteDesk-Specification.md)
* **Worker Node:** [HP ProDesk 600 G3 (pve-worker)](docs/ProDesk-Specification.md)
* **Networking:** TP-Link TL-SG108E (Managed Layer 2 Switch)

## Network Architecture
Currently operating on a flat `/24` subnet. (VLAN segmentation planned for future scalability).
* **Gateway/DNS:** `192.168.0.1`
* **Switch Management:** `192.168.0.2`
* **Master Node IP:** `192.168.0.10`
* **Worker Node IP:** `192.168.0.11`

## Configuration Milestones
* **Hardware:** Replaced failing storage components and validated S.M.A.R.T. health diagnostics for optimal operational stability.
* **Repository Optimization:** Removed commercial `pve-enterprise` and `ceph-squid` repositories, successfully transitioning both nodes to `pve-no-subscription` to ensure system updates.
* **Cluster Initialization:** Configured physical networking components, generated keys, and successfully established a functional Proxmox Datacenter.

## Deployed Services & Automations
* **[MobiDziennik to Notion API Sync](./services/mobidziennik-notion-sync):** A headless data pipeline running on a Debian LXC container. It handles HTTP POST authentication with a proprietary educational platform, parses DOM tables using BeautifulSoup, converts localized time strings to strict ISO 8601 formats, and pushes JSON payloads to a Notion master database via REST API. Fully automated via a daily cron daemon.
 
## Next Steps
* Deploying Infrastructure as Code (IaC) environments for testing.
* AWS hybrid cloud integrations.
* Starting preparation for the AWS Certified Solutions Architect Associate (SAA-C03) exam.
