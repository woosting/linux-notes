# PCI (WiFi) hardware (chipset) listing

Query devices connected to any pci compatible bus:

```
$ lspci -nn

    00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
    00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
    00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
    00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
    00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
    00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
    00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
    00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
    00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
    00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
    00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
    00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
    00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
    00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
    00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
    02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)
    15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
    16:00.0 Ethernet controller [0200]: ADMtek 21x4x DEC-Tulip compatible 10/100 Ethernet [1317:1985] (rev 11)
```

> NOTE: Requires the package: [ciutils][2]


# References

> Adapted from: Debian Wiki
> [How to identify a device PCI][1]


<!-- REFERENCES -->

[1]:https://wiki.debian.org/HowToIdentifyADevice/PCI
[2]:https://packages.debian.org/pciutils
