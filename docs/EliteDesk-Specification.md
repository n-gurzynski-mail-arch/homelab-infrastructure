# Master Node Specification (pve-master)

## Hardware Overview
* **Model:** HP EliteDesk 800 G3 DM
* **CPU:** Intel Core i5-6500T
* **RAM:** 16GB DDR4
* **Storage:** 512GB NVMe SSD (Primary OS & VM Storage)
* **Network Interface:** 1x Gigabit Ethernet

## Network Configuration
* **Hostname:** `elitedesk.local`
* **Static IP:** `192.168.0.10/24`
* **Gateway:** `192.168.0.1`
* **DNS:** `192.168.0.1`

## Roles & Responsibilities
* Primary cluster management (Corosync master).
* Hosting mission-critical infrastructure containers.
