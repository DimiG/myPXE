myPXE
========
This repository dedicated to my [PXE][pxe] scripts which provides disk-less BOOT for PC clients.  

Code descriptions
-----------------

* `boot.ipxe`: This script helps to use tools and installers for easy infrastructure deployments. It was made for [iPXE][ipxe] cause it is much more flexible compare to ordinary [PXE][pxe] boot. More about [iPXE][ipxe] you can read on [iPXE][ipxe] official site. Cause I use ordinary network cards for network booting I provide the `chainloading iPXE` technique according to [official documentation][chainload]. The current diagram shows the files location in the root of HTTP server (simplified scheme):  

```
/ WEB Server ROOT
├── archiso.img
├── archlinux-2019.10.07-i686
│   ├── EFI
│   ├── [BOOT]
│   ├── arch
│   ├── isolinux
│   └── loader
├── iso
│   ├── CentOS-8-x86_64-1905-boot.iso
│   ├── archlinux-2019.10.01-x86_64.iso
│   ├── archlinux-2019.10.07-i686.iso
│   ├── clonezilla-live-2.6.3-7-amd64.iso
│   └── dban-2.3.0_i586.iso
├── memdisk
├── vmlinuz
├── wimboot
└── winpe
    └── media
```

* `All Applications and Scripts`:  
   **Note:** The `undionly.kpxe` compilation process described in [official documentation][chainload] and compiled by this command `make bin/undionly.kpxe EMBED=boot.ipxe`. In these examples shown how to BOOT by [iPXE][ipxe] with different ways.  
   ***Requires :*** [PXE][pxe] boot demands to have [DHCP][dhcp], [TFTP][tftp] and [HTTP][http] servers. [DHCP][dhcp] server redirects the [DHCP][dhcp] request from client to [TFTP][tftp] server which provides the compiled `undionly.kpxe` from `boot.ipxe`. The binary `undionly.kpxe` makes request to local/internet [HTTP][http] server which provides necessary files to boot.  
   ***Important:*** These scripts may contain bugs and may not always behave as expected. You were warned ;). The host MUST have 1Gb [RAM][ram] as minimum! DON'T FORGET to set your [HTTP][http] server IP address in `boot.ipxe`.  

* `To be continued...`  

### License  

This code has been written by ©2019 DimiG  

[pxe]:https://en.wikipedia.org/wiki/Preboot_Execution_Environment
[ipxe]:https://ipxe.org
[chainload]:https://ipxe.org/howto/chainloading
[tftp]:https://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol
[http]:https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol
[dhcp]:https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol
[ram]:https://en.wikipedia.org/wiki/Random-access_memory
