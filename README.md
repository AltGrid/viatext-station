# viatext-station

*The terminal window at the edge of the network. The Linux-side operator of the Line.*

![VIATEXT Logo](viatext.png)

**`viatext-station`** is the Linux-side interface for running ViaText nodes as message dispatchers, relays, and endpoints.  
It transforms any Linux box — Ubuntu, Tails, Raspberry Pi — into a self-reliant node in the ViaText mesh.

This is where human operators type messages, receive logs, manage relay queues, and optionally run long-lived daemons.  
It’s where automation and personhood meet — the “station” that bridges user interaction and core node logic.

---

## 🔗 Project Umbrella

For overall philosophy and architecture, see the main ViaText repo:

→ [github.com/altgrid/viatext](https://github.com/altgrid/viatext)

---

## 🎯 Purpose

`viatext-station` is responsible for:

- **Interfacing** with serial-connected LoRa or USB nodes
- **Running** interactive chat CLI and message terminals
- **Logging** incoming and outgoing message activity
- **Daemonizing** core services to run in background
- **Installing** systemd services for startup persistence
- **Eventually** integrating network bridges (sneakernet dropbox, LAN API, etc.)

This package acts as the Linux-side **host + operator** — a user terminal in the network.

---

## 📦 Expected Features

- CLI Chat Client (`vt-chat`)
- Daemon Runner (`vt-daemon`)
- Serial Node Interface (`vt-serial-bridge`)
- Sync Utilities (`vt-sync`, `vt-scan`, `vt-rps`)
- Debian Installer Scripts
- Configurable `/etc/viatext/` paths
- Compatible with `/dev/ttyUSB*` detection

---

## 🐧 Debian + Linux Targeting

- Built for **Debian/Ubuntu**
- Compatible with **Tails, Raspberry Pi OS**, and other `.deb`-based distros
- Self-installing `.deb` package in future milestone
- Follows FHS structure:
  - `/etc/viatext/`
  - `/var/lib/viatext/`
  - `/usr/bin/viatext-*`
  - `/lib/systemd/system/viatext.service`

---

## 📁 Structure (Planned)

```
viatext-station/
├── src/
│   ├── vt-chat.cpp
│   ├── vt-daemon.cpp
│   ├── vt-serial-bridge.cpp
│   └── ...
├── debian/
│   ├── control
│   ├── postinst
│   └── rules
├── systemd/
│   └── viatext.service
├── include/
│   └── viatext/
│       └── station.hpp
├── Makefile
└── README.md
```

---

## 🛠️ Dependencies

- Standard Linux libraries (`libc`, `libstdc++`)
- No GUI, no X11, no Python required
- Optional: CLI11 for argument parsing
- May include TTY UI or `ncurses` for CLI menu later

---

## 🔄 Interoperability

Communicates with:

- LoRa nodes via `/dev/ttyUSB*`
- Local daemons for routing & logging
- Other Linux hosts via file-copy/sneakernet
- Possibly future web dashboard (local-only)

---

## 🚧 Status

Early development. Expect:

- Minimal examples to start (`vt-chat`, `vt-daemon`)
- Focus on stable deb packaging + launch consistency
- Modular design for future expansion

---

## 🤖 Note on AI Assistance

Parts of this README and supporting scripts were authored with the help of **ChatGPT** and **GitHub Copilot** for drafting, formatting, and generation.

All logic, file layout, and code structure are reviewed and curated by a human engineer. AI is used to assist in clarity and speed — never in place of design judgment or debugging.

This project values **transparency and intent** — AI is part of the toolbox, not the architect.

ViaText is built for humans, by humans, with help from machines.

