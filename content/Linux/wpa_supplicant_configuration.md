---
title: "使用 wpa_supplicant 配置无线网络"
date: 2017-04-17
---

* 使用 `iwconfig` 命令查看网络接口。如果无线接口默认没有启动可以使用 `sudo ifup wlan0` 来启动接口。
* 使用 `wpa_passphrase` 命令来获取加密后的 psk，即 wifi 密码，并记住或拷贝下来
	
```bash
$ wpa_passphrase <your_ssid> <your_psk>
# your_ssid: 无线网络名称
# your_psk: 无线网络的密码
```
* 创建一个配置文件 `sudo vi /etc/wpa_supplicant.conf`
	
```bash
ctrl_interface=/var/run/wpa_supplicant
# ap_scan=2
network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
}
# your_psk：第二步生成的psk
```
* 修改网络配置文件 `sudo vi /etc/network/interfaces`
	
```bash
iface wlan0 inet static
address 192.168.0.125
netmask 255.255.255.0
wireless-ssid "essid"
gateway 192.168.0.1

pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
* 修改完成之后重新启动网络服务
	
```bash
sudo /etc/init.d/networking restart
```

## 参考资料

* [WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)


