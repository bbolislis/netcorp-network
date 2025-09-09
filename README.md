# Netcorp — Network Infrastructure Portfolio

**Netcorp** is a fictional small startup tech company (two branches, hybrid infrastructure). This repository is a portfolio project that demonstrates end-to-end network design, security, monitoring, automation, disaster recovery, and SLA management using free and open-source tools.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Technology Stack](#technology-stack)
- [Minimum Requirements](#minimum-requirements)
- [Repository Layout](#repository-layout)
- [Quickstart](#quickstart)
- [How to run the minimal lab](#how-to-run-the-minimal-lab)

---

## Project Overview
This project is a structured, phased implementation of a realistic network infrastructure for Netcorp. Each phase includes documentation, diagrams, configuration examples, automation, and monitoring artifacts suitable for showcasing on GitHub or during interviews.

---

## Objectives
Deliver a reproducible lab and documentation across these areas:
1. Network design and topology
2. Network security and segmentation
3. Monitoring and logging
4. Automation & orchestration
5. Disaster recovery
6. Performance optimization
7. Compliance mapping
8. Capacity planning
9. Cost optimization
10. SLA management

---

## Technology Stack
- Virtualization/Containers: VirtualBox/VMware workstation, Docker, Containerlabs
- Firewalls/Routers (lab): pfSense, OPNsense, VyOS/EOS/SR Linux (VM/Container images)
- IPAM / Documentation: NetBox (Docker)
- Monitoring: Zabbix or LibreNMS, Grafana
- Automation: Ansible, Netmiko, NAPALM
- Config backups: Oxidized
- VPN: WireGuard / OpenVPN
- Logging / SIEM: Elastic Stack (optional) or Graylog

---

## Minimum Requirements
- Laptop: 10th gen Intel i3 (or equivalent), 16 GB RAM, 50+ GB free disk
- OS: Linux/macOS/Windows with Docker & VirtualBox installed
- Suggested: install Docker Desktop or Docker Engine + docker-compose

---

## Repository Layout
```
netcorp-network/
├─ .github/             # issue templates and CI workflows
├─ docs/                # design and phase docs
├─ automation/          # ansible playbooks & scripts
├─ monitoring/          # monitoring configs & dashboards
├─ lab/                 # docker-compose and VM artifacts
├─ scripts/             # helper scripts (bootstrap)
├─ README.md
├─ LICENSE.md
└─ CONTRIBUTING.md
```

---

## Quickstart
1. Clone the repo
```bash
git clone https://github.com/bbolislis/netcorp-network.git
cd netcorp-network
```
2. Bootstrap skeleton (creates folders/placeholders)
```bash
chmod +x scripts/bootstrap.sh
./scripts/bootstrap.sh
```
3. Start the minimal demo (NetBox stack) — keep containers minimal to conserve RAM
```bash
cd lab
docker-compose up -d postgres redis netbox
```
4. Access NetBox at `http://localhost:8080` (if running locally)

---

## How to run the minimal lab
1. Ensure Docker is installed and running.
2. Edit `lab/docker-compose.yml` if you need to change ports or data paths.
3. Bring up only the sevices you need:
```bash
# start just NetBox demo
docker-compose up -d netbox postgres redis
# check logs
docker-compose logs -f netbox
```
4. To stop everything:
```bash
docker-compose down
```
5. If you plan to run a pfSense VM, allocate a minimum of 2GB RAM and 1 CPU for better performance.

---

[Network Design >>](https://github.com/bbolislis/netcorp-network/blob/main/docs/network-desgin.md)
