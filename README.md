# githubcodespaces-netbootxyz

Debian inside a GitHub Codespace.

## Overview

This project makes it surprisingly easy to run a full Linux environment inside a cloud-hosted development workspace by using a QEMU-based virtual machine under the hood with `netboot.xyz`. It provides a streamlined way to install operating systems dynamically without bloating your local storage footprint.

## Features

* **Network Boot:** Powered by `netboot.xyz` iPXE loader to stream and install distributions over the network.
* **Browser Access:** Fully interactive graphical interface accessible directly via a web-based VNC console on port 8006.
* **Resource Efficient:** Streamline installations like Debian GNOME while keeping container storage tracking structured and modular.

## Getting Started

1. Start the container environment inside your Codespace.
2. Connect to port 8006 using your web browser to open the VNC interface.
3. Select and complete your desired OS installation via the network boot menu.
