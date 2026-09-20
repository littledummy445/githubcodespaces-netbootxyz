<h1 align="center">Netboot.xyz<br />
<div align="center">
<a href="https://github.com/netbootxyz/netboot.xyz"><img src="https://raw.githubusercontent.com/netbootxyz/netboot.xyz/master/docs/images/netbootxyz-logo.png" title="Logo" style="max-width:100%;" width="96" /></a>
</div>
<div align="center">

[![Pulls](https://img.shields.io/docker/pulls/netbootxyz/netbootxyz.svg?style=flat&label=pulls&logo=docker)](https://hub.docker.com/r/netbootxyz/netbootxyz)

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

```

##### Docker CLI:

```bash
docker run -d --name netboot-qemu \
  -p 8006:8006 \
  -e "BOOT=https://boot.netboot.xyz/ipxe/netboot.xyz.iso" \
  -e "PORT=8006" \
  --device=/dev/kvm \
  --device=/dev/net/tun \
  --cap-add NET_ADMIN \
  -v "${PWD:-.}/storage:/storage" \
  ghcr.io/qemus/qemu:latest

```

##### Kubernetes:

```shell
kubectl apply -f [https://raw.githubusercontent.com/netbootxyz/netboot.xyz/refs/heads/master/kubernetes.yml](https://raw.githubusercontent.com/netbootxyz/netboot.xyz/refs/heads/master/kubernetes.yml)

```

## Requirements ⚙️

* Docker or Podman on a Linux host with KVM support.
* Docker Desktop or Podman (Desktop) on Windows 11 with nested virtualization enabled.
* At least 2 GB of available RAM.
* At least 15 GB of free disk space.

> [!NOTE]
> Docker Desktop on Linux, macOS, and Windows 10 does not currently provide KVM access to containers and is therefore not supported.

## FAQ 💬

### How do I use it?

Very simple! These are the steps:

* Start the container and connect to [port 8006](http://127.0.0.1:8006/?utm_source=gemini) using your web browser.
* Select your desired operating system from the netboot.xyz iPXE menu.
* Sit back and relax while the installation is performed over the network.

Enjoy your brand new machine, and don't forget to star this repo!

### How do I change the size of the disk?

To expand the default size, add the `DISK_SIZE` setting to your compose file and set it to your preferred capacity:

```yaml
environment:
  DISK_SIZE: "64G"

```

> [!TIP]
> This can also be used to resize an existing disk to a larger capacity without any data loss.

### How do I change the amount of CPU or RAM?

By default, the VM is allowed to use 2 CPU cores and 4 GB of RAM.

If you want to adjust this, you can specify the desired amount using the following environment variables:

```yaml
environment:
  RAM_SIZE: "8G"
  CPU_CORES: "4"

```

### How do I verify that KVM is available?

First, make sure your platform and container runtime meet the requirements listed above.

On a Linux host, install `cpu-checker` and run:

```bash
sudo apt install cpu-checker
sudo kvm-ok

```

A working configuration should report:

```text
KVM acceleration can be used

```

You can also verify that the KVM device exists:

```bash
ls -l /dev/kvm

```

## GitHub Codespaces 🚀

## Stars 🌟

## Disclaimer ⚖️

*The product names, logos, brands, and other trademarks referred to within this project are the property of their respective trademark holders. This project is not affiliated, sponsored, or endorsed by netboot.xyz.*

```

```
