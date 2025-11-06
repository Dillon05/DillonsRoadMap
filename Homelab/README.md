## Homelab Journey

This timeline documents the evolution of my self-hosted lab, starting from a single Proxmox node and growing into a segmented, service-rich environment with routing, storage, security, and monitoring components.

### 1. Initial Hypervisor & Game Hosting

- Installed **Proxmox VE** on a spare PC as my first hypervisor.
- Deployed **AMP (Application Management Panel)** on Proxmox.
- Hosted a **Minecraft server** for friends/family, managing updates, backups, and performance through AMP.

### 2. Dedicated Router & Network Control

- Acquired a **Dell OptiPlex 5070** and repurposed it as my edge device.
- Installed **OPNsense** and configured it as my primary router/firewall.
- Began centralizing all routing, DHCP, DNS, and firewall policies through OPNsense instead of ISP-provided hardware.

### 3. Media Services

- Deployed **Jellyfin** to self-host movies/TV.
- Integrated Jellyfin into my internal network, tuning storage usage and remote/local access behavior.

### 4. Remote Access

- Implemented **WireGuard** for secure remote access to internal services.
- Documented peers, keys, and allowed IPs to maintain a clean, auditable VPN configuration.
- Used VPN instead of exposing random ports directly to the internet.

### 5. VLAN Design & Early Segmentation

- Designed and began implementing **VLANs** to separate:
  - Family / WiFi clients
  - My main workstation
  - Servers and hypervisors
  - Lab / testing environment
  - Network management
- Configured **trunk and access ports** on managed switches and started building firewall policies in OPNsense to limit lateral movement.

### 6. Storage & Hardware Upgrade

- Purchased **8 × 4TB HDDs**, upgraded the original Proxmox box with:
  - New case
  - Additional RAM
  - New motherboard
- Rebuilt it as a higher-capacity **virtualization and storage host** suitable for Nextcloud, media, and lab workloads.

### 7. Nextcloud Deployment with Cloudflare

- Installed **Nextcloud** for file sync/backup and family data storage.
- Integrated with **Cloudflare DNS** for clean, memorable hostnames.
- Configured HTTPS and reverse proxying so Nextcloud could be accessed securely from outside the network.

### 8. Lab Cluster Build

- Acquired **three Lenovo ThinkCentre** systems and built a dedicated **lab cluster**.
- Node 1:
  - Installed **Security Onion** to begin building a detection/monitoring environment.
- Node 2:
  - Installed **Windows**, **Kali Linux**, and **Parrot OS** for testing, tooling, and training in a controlled environment.
- Node 3:
  - Reserved for future workloads and experiments.

### 9. Dedicated Docker/Portainer Host

- Deployed an **HP desktop** with **Debian** as a dedicated Docker host.
- Installed **Portainer** to centrally manage containers and stacks.
- Separated lab/infra services from Proxmox system overhead for cleaner roles.

### 10. Service Portal & UI

- Deployed **Dashy** as a central homelab dashboard.
- Customized UI, layout, and theming to organize:
  - Proxmox nodes
  - Nextcloud
  - Jellyfin
  - AMP/game servers
  - OPNsense
  - Docker/Portainer
  - Future monitoring and SIEM tools

### 11. Reverse Proxy & Ingress Layer

- Installed **Caddy** as a reverse proxy.
- Configured virtual hosts and routes for key services.
- Integrated with **Cloudflare** to simplify HTTPS and centralize ingress rather than exposing each service individually.

### 12. Ongoing Work (In Progress)

- Finalizing **VLAN segmentation and firewall policies** so each network segment:
  - Has internet access
  - Is restricted from unnecessary lateral access
- Building **port mirroring** and **Security Onion** integration to monitor real traffic from core segments.
- Expanding documentation, diagrams, and configuration files in this repository to reflect a production-style, security-focused homelab.

