# Worker Node Specification

## Hardware Overview
* **Model:** HP EliteDesk 600 G3 DM 
* **CPU:** i5-6500T
* **RAM:** 8GB DDR4
* **Storage:** 256GB SSD (OS & VM Storage)
* **Network Interface:** 1x Gigabit Ethernet (nic0)

## Network Configuration
* **Hostname:** `pve.local`
* **Static IP:** `192.168.0.11/24`
* **Gateway:** `192.168.0.1`
* **DNS:** `192.168.0.1`

## Roles & Responsibilities
* Secondary cluster node for workload distribution and High Availability (HA) architecture testing.
* Hosting development, staging, and CI/CD sandbox environments (e.g., runners).
* Failover target for migrating services during master node maintenance.
