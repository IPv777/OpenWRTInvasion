# Root shell exploit for the router Xiaomi 4A Gigabit Global Edition, firmware version 2.28.132

## How to run

```
# Install requirements
# pip3 install -r requirements.txt
# Run the script
# python3 remote_command_execution_vulnerability.py
```

After that, a letnet server will be up and running on the router. You can connect to it by running:

```
telnet <router_ip_address>
```

* User: root
* Password: none (just hit enter)

The script also starts an ftp server at port 21, so you can get access to the filesystem using a GUI (for example [cyberduck](https://cyberduck.io)).

## Install OpenWrt

After login to the router through telnet, run:

```
cd /tmp
wget http://downloads.openwrt.org/snapshots/targets/ramips/mt7621/openwrt-ramips-mt7621-xiaomi_mir3g-v2-squashfs-sysupgrade.bin
mtd -e OS1 -r write openwrt-ramips-mt7621-xiaomi_mir3g-v2-squashfs-sysupgrade.bin OS1
```

This will install the snapshot version of OpenWrt (without Luci). You can now use ssh to connect to the router (and install Luci if you prefer it).

## Demo

### Version 0.0.2: telnet

![Alt Text](readme/exploit-002.gif)

### Version 0.0.1: netcat (legacy)

![Alt Text](readme/exploit-001.gif)

## For more info and support go to:

* [OpenWrt forum thread](https://forum.openwrt.org/t/xiaomi-mi-router-4a-gigabit-edition-r4ag-r4a-gigabit-fully-supported-but-requires-overwriting-spi-flash-with-programmer/36685)
* [Slack workspace](https://join.slack.com/t/openwrt-workspace/shared_invite/zt-cz2m5uf4-Q8wbP_LKggOy9B7IQyaqfA)
* User [ksc91u](https://forum.openwrt.org/u/ksc91u) claims that this method also works on firmware version `2.28.62`: [OpenWrt forum](https://forum.openwrt.org/t/xiaomi-mi-router-4a-gigabit-edition-r4ag-r4a-gigabit-fully-supported-but-requires-overwriting-spi-flash-with-programmer/36685/359)
* User [morhimi](https://forum.openwrt.org/u/morhimi) claims that this method also works on firmware version `2.18.51` for the router Xiaomi 4A 100M (non gigabit): [OpenWrt forum](https://forum.openwrt.org/t/xiaomi-mi-router-4a-gigabit-edition-r4ag-r4a-gigabit-fully-supported-but-requires-overwriting-spi-flash-with-programmer/36685/372)
* User [Massimiliano Mangoni](massimiliano.mangoni@gmail.com) claims that this method also works on firmware version `2.28.8` for the router Mi Router 3G v2 (message posted in Slack).

## Acknowledgments

* Original vulnerabilities and exploit: [UltramanGaia](https://github.com/UltramanGaia/Xiaomi_Mi_WiFi_R3G_Vulnerability_POC)
* Instructions to install OpenWrt after exploit execution: [rogerpueyo](https://forum.openwrt.org/t/xiaomi-mi-router-4a-gigabit-edition-r4ag-r4a-gigabit-fully-supported-but-requires-overwriting-spi-flash-with-programmer/36685/21)
* Testing and detailed install instructions: [hey07](https://forum.openwrt.org/t/xiaomi-mi-router-4a-gigabit-edition-r4ag-r4a-gigabit-fully-supported-but-requires-overwriting-spi-flash-with-programmer/36685/349)
