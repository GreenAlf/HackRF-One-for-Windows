# HackRF One for Windows
A comprehensive tutorial for setting up and using HackRF One on Windows. This repository provides detailed step-by-step instructions, code samples, and troubleshooting tips—filling the gap left by Linux-focused guides. It also integrates modified code from [jamRF_v1.py](https://github.com/tiiuae/jamrf/blob/master/HackRF/jamRF_v1.py)

## Overview
HackRF One is a popular, low-cost, open-source software-defined radio (SDR) platform. While many setup guides assume a Linux environment, this project is tailored for Windows users. Whether you prefer using Conda, WSL, or Docker, this guide covers various methods to get you started.

## Features
- Step-by-step setup guide for HackRF One on Windows
- Windows-specific code samples and scripts
- Integration of selected functions from jamRF_v1.py
- Troubleshooting tips and FAQ

## Requirements
- **Operating System:** Windows 10 or later
- **Device:** HackRF One, Micro USB cable (for connecting HackRF to your PC)
- **Python:** Version 3.6 or higher

## Contents
- **[Conda Setup](#conda-setup)**
- **[WSL Setup](#wsl-setup)**
- **[Docker Setup](#docker-setup)**
- **[Troubleshooting](#troubleshooting)**

## Conda Setup
1. Install miniconda from here
2. 


## WSL Setup
1. **Clone the repository:**
   ```bash
   git clone https://github.com/whiteSHADOW1234/HackRF-One-for-Windows.git
   cd HackRF-One-for-Windows
   ```
2. 



## Docker Setup



## Troubleshooting
1. Device not found, but sill get the following issue:
   ```
   Exception has occurred: RuntimeError
   Failed to use '0' as HackRF device index: not enough devices
   File "C:\Users\<USER_NAME>\Desktop\HackRF-One-for-Windows\jamRF_v1.py", line 130, in jam
      osmosdr_sink = osmosdr.sink("hackrf=0")
                     ^^^^^^^^^^^^^^^^^^^^^^^^
   File "C:\Users\<USER_NAME>\Desktop\HackRF-One-for-Windows\jamRF_v1.py", line 271, in <module>
      jam(freq, waveform, power, t_jamming)
   RuntimeError: Failed to use '0' as HackRF device index: not enough devices
   ```
   - Switch a different USB port
2. After running `usbipd list` but found the HackRF has been detected as `USBIP Shared Device`, instead of `HackRF One`.
   - Update the USB driver
   - Unplug and replug HackRF
   - Switch a different USB port