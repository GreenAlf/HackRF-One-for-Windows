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
1. Prepare Essentials:
   - Download and install [Git](https://git-scm.com/downloads) and [Miniconda](https://www.anaconda.com/download/success) (or Anaconda).
   - Install usbipd-win (.msi) from its [GitHub releases](https://github.com/dorssel/usbipd-win/releases).
3. Connect and Verify HackRF One
   - Plug in your HackRF One with a micro USB cable.
   - Open the Device Manager to check if your PC recognizes the device.
   - If not recognized properly, download and run [Zadig](https://zadig.akeo.ie/):
      - Click on List All Devices.
         ![zadig-screenshot-1](images/3-1.png)
      - From the drop-down menu, select HackRF One.
         ![zadig-screenshot-2](images/3-2.png)
      - Click Downgrade WCID Driver to install the driver.
         ![zadig-screenshot-3](images/3-3.png)
      - Confirm in Device Manager that the HackRF One now appears correctly.
         ![zadig-screenshot-4](images/3-4.png)

4. Clone the Repository
   Open a Command Prompt and run:
   ```
   git clone https://github.com/whiteSHADOW1234/HackRF-One-for-Windows.git
   ```
   This will download the files `jamRF_v1.py` and `config_v1.yaml`.
5. Set Up the Python Environment
   Open the cloned repository in Visual Studio Code (or your preferred editor). If you notice unresolved packages, 
   Continue with these commands in the Command Prompt:
   ```
   conda create -n hackrf_env -c conda-forge gnuradio gr-osmosdr hackrf
   conda activate hackrf_env
   ```
   ![vScode-screenshot](images/5-1.png)
   Then, in VSCode, change the Python interpreter to `hackrf_env` and restart the terminal 
   ![vScode-screenshot](images/5-2.png)
      - This may require restarting twice to resolve all issues.
         ![vScode-screenshot](images/5-3.png)
  

6. Verify and Run
   - In the terminal, run the following command to ensure HackRF One details are displayed.
      ```
      > hackrf_info
      hackrf_info version: 2024.02.1
      libhackrf version: 2024.02.1 (0.9)
      Found HackRF
      Index: 0
      Serial number: 0000000000000000a18c63dc2b3c6813
      Board ID Number: 2 (HackRF One)
      Firmware Version: v2.0.1 (API:1.08)
      Part ID Number: 0xa000cb3c 0x00614766
      Hardware Revision: older than r6
      Hardware supported by installed firmware:
         HackRF One
      ```

   - Run `python jamRF_v1.py` in the terminal
      ```
      > python jamRF_v1.py
      1 100
      JAM!

      The frequency currently jammed is: 2412.0MHz
      gr-osmosdr 0.2.0.0 (0.2.0) gnuradio 3.10.12.0
      built-in sink types: uhd hackrf bladerf soapy redpitaya file 
      Using HackRF One with firmware v2.0.1
      Detected Windows OS
      100
      pagesize :debug: Setting pagesize to 4096 B
      top_block_impl :debug: Using default scheduler "TPB"
      UUUUUUUU
      ```
## WSL Setup



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