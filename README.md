# 🎸 Guitar Hero for Minix — Low-Level Rhythm Game in C

![C](https://img.shields.io/badge/C-00599C?logo=c&logoColor=white) ![Minix](https://img.shields.io/badge/OS-Minix%203-555) ![Grade](https://img.shields.io/badge/Grade-20%2F20-brightgreen)

A rhythm game inspired by *Guitar Hero*, built **from scratch in C on the Minix 3 operating system**, with no game engine or graphics library: every device is controlled through **custom drivers that talk directly to the hardware**.

> Final project for **Computer Laboratory (LCOM)** — BSc in Informatics and Computing Engineering (L.EIC), FEUP, 2025/2026. **Final grade: 20/20.**

<p align="center"><img src="Project/devices/video/assets/gameplay1.png" width="600" alt="Stage artwork used in the game"/></p>

## ✨ Features
- Main menu, song selection and username entry, navigated with the **mouse**
- Notes fall along **five lanes**, hit with the **A S D F G** keys
- **Dynamic beatmap loading** from text files, so new songs can be added without recompiling
- **Score and combo system**, with visual feedback for hits and misses
- **"Mission Success" / "Mission Failed"** end screens
- **Persistent Top-5 leaderboard**, saved to disk
- **Audio through the serial port (UART)**: the game sends events to an external Python script that plays the music

## 🔧 Hardware & low-level programming
Each device has its own driver, built during the course labs and integrated into the final project:

| Device | Usage in the game |
|---|---|
| **Graphics card (VBE)** | Graphics mode, double buffering, XPM sprites and backgrounds |
| **Keyboard (KBC, i8042)** | Hitting notes on the five lanes |
| **Mouse (PS/2)** | Menu navigation |
| **Timer (i8254)** | Game loop timing and note synchronization |
| **RTC** | Date and time for the leaderboard |
| **UART (serial port)** | Communication with the external audio subsystem |

All devices are handled through **interrupts**, in a single **event-driven main loop**.

## ▶️ How to run (Minix VM)
```bash
cd Project
make
lcom_run proj
```
Audio setup is described in [`Project/SETUP_AUDIO.md`](Project/SETUP_AUDIO.md).

## 👤 My contribution
- Main game loop and integration of the devices in `main.c`
- **Video driver** (`devices/video`): graphics mode and image rendering
- UI and visual design: menus, loading screen, Mission Success/Failed screens, transparent leaderboard and crowd particle effects
- Gameplay: missed notes keep falling to the bottom of the screen

## 👥 Team
André Rocha · Guilherme Pinho · Martim Ferreira · Artur Ferro

📄 Original documentation (Portuguese): [README_PT.md](README_PT.md)
