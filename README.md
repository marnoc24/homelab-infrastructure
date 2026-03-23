# 🚀 Prywanty Homelab Proxmox + Docker

## 📌 O projekcie
Domowe laboratorium zbudowane w celu nauki technologii **Cloud Computing**, **DevOps** oraz **Sieci komputerowych**. Projekt symuluje rzeczywiste środowisko produkcyjne z naciskiem na segmentację sieci, bezpieczeństwo i konteneryzację (Infrastructure as Code).

## 🏗 Architektura Sieciowa i Aplikacyjna
![Schemat Architektury](homelab-schemat.png)

## 🛠 Tech Stack
* **Wirtualizacja:** Proxmox VE
* **Sieć i Bezpieczeństwo:** OPNsense (Firewall, NAT/Port Forwarding, DMZ), UFW (Uncomplicated Firewall)
* **OS:** Ubuntu Server (SSH Key-Based Auth)
* **Konteneryzacja:** Docker Engine, Docker Compose
* **Usługi & Routing:** Nginx Proxy Manager (Reverse Proxy), Portainer, Uptime Kuma, Homepage

## 🔒 Kluczowe założenia infrastruktury
1. **Segmentacja (Izolacja sieci):** Serwer aplikacyjny (Ubuntu) nie znajduje się w sieci domowej. Został odizolowany w dedykowanej podsieci Labu (`10.0.0.0/24`) za pomocą routera OPNsense.
2. **Reverse Proxy:** Pojedynczy punkt wejścia (Single Point of Entry). Ruch HTTP/HTTPS trafia z zewnątrz wyłącznie do Nginx Proxy Managera, który na podstawie nagłówków domenowych kieruje go do odpowiednich kontenerów.
3. **Zasada najmniejszych uprawnień:** Firewall OPNsense przepuszcza do sieci Labu wyłącznie wymagany ruch (porty 80, 81, 443 dla www oraz 22 dla zarządzania po SSH).

## 🗺️ Roadmap (Co dalej?)
- [ ] Implementacja lokalnego serwera DNS (Unbound) w celu rozwiązania nazw `.lan`.
- [ ] Automatyzacja konfiguracji serwera Ubuntu za pomocą narzędzia **Ansible**.
- [ ] Zarządzanie sekretami i hasłami w Dockerze przy użyciu plików `.env`.
