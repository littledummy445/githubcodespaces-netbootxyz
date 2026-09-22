## Run this to launch the **docker contanier**

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

