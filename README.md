<h1 align="center">Netboot.xyz<br />
<div align="center">
<a href="https://github.com/netbootxyz/netboot.xyz"><img src="https://raw.githubusercontent.com/netbootxyz/netboot.xyz/master/docs/images/netbootxyz-logo.png" title="Logo" style="max-width:100%;" width="96" /></a>
</div>
<div align="center">

[![Pulls](https://img.shields.io/docker/pulls/netbootxyz/netbootxyz.svg?style=flat&label=pulls&logo=docker)](https://hub.docker.com/r/netbootxyz/netbootxyz)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/githubcodespaces-netbootxyz)

</div></h1>

Netboot.xyz inside a Docker container.

## Features ✨

- Runs Netboot.xyz inside a Docker container
- Automatic download and hands-free network booting
- Supports modern and legacy operating system releases
- Near-native performance with KVM acceleration
- Customizable CPU, memory, and storage allocation
- Dynamic memory allocation with memory ballooning
- USB passthrough and host folder sharing
- Supports NAT, user-mode, macvlan, and macvtap networking

## Usage 🐳

##### Docker Compose:

```yaml
services:
  netbootxyz:
    image: netbootxyz/netbootxyz
    container_name: netbootxyz
    environment:
      VERSION: "latest"
    devices:
      - /dev/kvm
      - /dev/net/tun
    cap_add:
      - NET_ADMIN
    ports:
      - 8006:8006
    volumes:
      - ./netbootxyz:/storage
    restart: always
    stop_grace_period: 2m
