<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="medias/logo-sombre.svg">
    <img src="medias/logo-clair.svg" alt="Relay" height="56">
  </picture>
</p>

<p align="center"><img src="medias/affiche.png" alt="Banner — Relay" width="100%"></p>

# Relay

**Self-hosted reverse proxy with a UI: one name per service, served over HTTPS or a Cloudflare Tunnel, with health checks and Telegram alerts.**

<p align="center">

[![Stars](https://img.shields.io/github/stars/Nesaris/Relay?style=flat&logo=github&label=stars)](https://github.com/Nesaris/Relay/stargazers)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
![Node.js 24](https://img.shields.io/badge/Node.js-24-339933?logo=node.js&logoColor=white)
![Zero npm dependencies](https://img.shields.io/badge/npm%20dependencies-0-brightgreen)
![Docker](https://img.shields.io/badge/Docker-ready-2496ED?logo=docker&logoColor=white)
![Self-hosted](https://img.shields.io/badge/self--hosted-yes-orange)
![Caddy](https://img.shields.io/badge/Caddy-powered-1F88C0?logo=caddy&logoColor=white)

</p>

<p align="center"><a href="README.fr.md">🇫🇷 Documentation complète en français</a> · <a href="https://nesaris.github.io">Nesaris Network</a></p>

## Why Relay?

Exposing homelab services cleanly usually means hand-editing proxy configs and DNS. Relay gives every service its own name and certificate from a web UI — and when used with the Hub, publishes each new service automatically.

## Features

- **One name per service**, HTTPS (Let's Encrypt via Cloudflare DNS) or Cloudflare Tunnel.
- **Health of every target** and **Telegram alerts** when one goes down.
- **Local DNS** — every name in your local zone (`home.arpa`) resolves to the Relay host.
- **Hardened** — Caddy built from source on an empty image, no root, no capabilities; admin API on a Unix socket only.
- **Hub integration** — adds a *Connections* page to the Hub and publishes every service the Hub installs.

## Screenshots

<table>
<tr><td align="center" width="50%"><img src="medias/capture-1.png" alt="Routes and their health"><br><sub>Routes and their health</sub></td><td align="center" width="50%"><img src="medias/capture-2.png" alt="Connected services"><br><sub>Connected services</sub></td></tr>
<tr><td align="center" width="50%"><img src="medias/capture-3.png" alt="Settings: domains, Cloudflare, Telegram"><br><sub>Settings: domains, Cloudflare, Telegram</sub></td></tr>
</table>

## Quick start

```bash
git clone https://github.com/Nesaris/Relay && cd Relay
cp .env.example .env    # RELAY_IP, RELAY_HUB_TOKEN (or empty without the Hub)
mkdir -p secrets && openssl rand -base64 32 > secrets/socle_cle && : > secrets/socle_cle_ancienne
sudo chown 10001:10001 secrets/socle_cle secrets/socle_cle_ancienne && sudo chmod 400 secrets/socle_cle secrets/socle_cle_ancienne
docker compose up -d --build
docker compose logs relay | grep "Jeton d'installation"   # one-time setup token
```

Full documentation (configuration, backups, key rotation, reverse proxy, upgrades) is in **[README.fr.md](README.fr.md)** (French).

## Part of Nesaris Network

Relay is one of the self-hosted tools of **[Nesaris Network](https://nesaris.github.io)**. Every service shares the same hardened core (accounts, passkeys, TOTP, audit log, encrypted secrets), runs on Node.js 24 with **zero npm dependencies**, and can be installed in one click from the **[Nesaris Hub](https://github.com/Nesaris/Hub)**.

Other projects: [Hub](https://github.com/Nesaris/Hub) · [MapMyLAN](https://github.com/Nesaris/MapMyLAN) · [NexArc](https://github.com/Nesaris/NexArc) · [ProxLab](https://github.com/Nesaris/ProxLab) · [Vigie](https://github.com/Nesaris/Vigie) · [Nesmail](https://github.com/Nesaris/Nesmail) · [Synapse](https://github.com/Nesaris/Synapse) · [Dialekt](https://github.com/Nesaris/Dialekt)

## Contributing

Issues and pull requests are welcome. If Relay is useful to you, a ⭐ helps a lot — it's how other people find the project.

## License

[MIT](LICENSE) — made by [CodeX64](https://codexx64.github.io).
