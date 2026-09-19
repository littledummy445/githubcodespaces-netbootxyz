<h1 align="center">Netboot.xyz<br />
<div align="center">
<a href="https://github.com/netbootxyz/netboot.xyz"><img src="https://github.com/netbootxyz/netboot.xyz/raw/master/docs/images/netbootxyz-logo.png" title="Logo" style="max-width:100%;" width="96" /></a>
</div>
<div align="center">

[![Build]][build_url]
[![Version]][tag_url]
[![Size]][tag_url]
[![Package]][pkg_url]
[![Pulls]][hub_url]

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

## Video 📺

[![YouTube](https://img.youtube.com/vi/xhGYobuG508/maxresdefault.jpg)](https://www.youtube.com/watch?v=xhGYobuG508)

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
