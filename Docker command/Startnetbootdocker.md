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
```

After that command was run, follow these steps:
* Start the container and connect to [port 8006](http://127.0.0.1:8006/?utm_source=mygithubrepo) using your web browser.
* Select your desired operating system from the netboot.xyz iPXE menu.
* Sit back and relax while the installation is performed over the network.

