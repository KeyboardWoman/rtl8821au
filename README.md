-----

## rtl8821au (8821au.ko)

## Realtek RTL8821AU Wireless Lan Driver for Linux

- v5.12.5.2 (20210708)
- Based on EDIMAX EW-7811UTC Linux Driver (Version : 1.0.3.4) 2021-09-16
- Support Kernel: 4.15 - 5.11 (Realtek)
- Support up to Kernel 6.2

Kernel v6.3rc2 support
```
git clone https://github.com/ivanovborislav/rtl8821au.git
cd rtl8821au
wget https://raw.githubusercontent.com/ivanovborislav/document/main/patch/20230314-k-v6.3-rc2.patch
patch -p1 < 20230314-k-v6.3-rc2.patch
make
sudo make install
```

##	Specification

- Supported interface modes:
  * IBSS
  * managed
  * AP
  * monitor
  * P2P-client
  * P2P-GO
- Packet injection
- TX power control
- LED control
- Power saving control
- Driver debug log level control
- VHT control
- REGD source selection
- Security:
  * WEP 64/128-bit, WPA, WPA2, WPA3, and 802.1x

## Supported adapters

- Realtek RTL8811AU Wireless LAN 802.11ac USB 2.0 Network Adapter
- Realtek RTL8821AU Wireless LAN 802.11ac USB 2.0 Network Adapter
- Edimax EW-7811UTC
- Edimax EW-7811UAC
- Edimax EW-7811DAC
- Edimax EW-7811USC
- Edimax EW-7611UCB
- I-O DATA WN-AC433UA Wireless LAN Adapter
- D-Link DWA-171 rev A1 Wireless AC Dual Band Adapter
- D-Link DWA-172 rev A1 Wireless AC600 Dual Band High-Gain USB Adapter
- Hawking USB WLS 11AC Adapter
- ELECOM WDC-433SU2M2  Wireless Adapter
- ELECOM WDB-433SU2M2  Wireless Adapter
- TRENDnet AC600 Dual Band Wireless USB Adapter
- TP-LINK Archer T2U V3
- TP-LINK Archer T2U Nano V1
- TP-LINK Archer T2U Plus V1
- I-O DATA Realtek Wireless LAN USB 2.0 5G Only Network Adapter
- Planex GW-450S
- Sitecom WiFi High Gain USB Adapter AC600
- ELECOM WDC-433DU2H 11ac Wireless Adapter
- Abocom 802.11ac Wireless LAN Card
- I-O DATA WN-AC433UM Wireless LAN Adapter
- I-O DATA WHG-AC433UM Wireless LAN Adapter
- AirTies Air2520 Wireless USB Adapter
- AirTies Air2525 Wireless USB Adapter
- BUFFALO WI-U2-433DM Wireless LAN Adapter
- BUFFALO WI-U2-433DHP Wireless Lan Adapter
- BUFFALO WLP-U2-433DHP Wireless Lan Adapter
- Netgear A6100
- Obihai OBiWiFi

[To support WiFi USB Adapter(s) with new vid/pid(s) which have rtl8821au or rtl8811au chipset.](https://github.com/ivanovborislav/document/blob/main/HowTo_support_more_VidPids.pdf)

## Tested Linux Distros and Tools

Successful tested injection `aireplay-ng -9 <interface>`, deauthentication `aireplay-ng -0 1 -a <bssid> <interface>`.

NO `fixed channel 1` issue.

Successful hcxdumptool driver test `hcxdumptool -i <interface> --check_driver` and capture packets `hcxdumptool -i <interface> -o test.pcapng --filterlist_ap=targets.lst --filtermode=2 --enable_status=15` `(hcxdumptool -i <interface> -o test.pcapng --filterlist=targets.lst --filtermode=2 --enable_status=15)`.

Connecting to AP with WPA3 (WPA3-SAE) authentication method (IMPORTANT: Test distro Ubuntu 22.04 kernel 5.15 - NetworkManager 1.36.4 nmcli tool, version 1.36.4. Otherwise use wpa_supplicant).

Start WPA3 (WPA3-SAE) SoftAP.

TX power control tested with SoftAP mode and OpenWrt firmware (OpenWrt 21.02.0 r16279-5cc0535800, Channel Analysis Feature).

- Ubuntu 22.04 (kernel 5.19)
  * Aircrack-ng 1.6
  * hcxdumptool 6.2.6
  * hostapd v2.11-devel-hostap_2_10-309-gc3d389b72
  * wpa_supplicant v2.11-devel-hostap_2_10-309-gc3d389b72

<details>
  <summary>
    Ubuntu 22.04 (kernel 5.18)
  </summary>
  
  * wpa_supplicant v2.11-devel-hostap_2_10-309-gc3d389b72
  * hostapd v2.11-devel-hostap_2_10-309-gc3d389b72
  * Aircrack-ng 1.6
  * hcxdumptool 6.2.6
</details>

<details>
  <summary>
    Ubuntu 21.10 (kernel 5.17)
  </summary>
  
  * hostapd v2.11-devel-hostap_2_10-151-g3085e1a67
  * hcxdumptool 6.2.4
  * Aircrack-ng 1.6
  * wpa_supplicant v2.11-devel-hostap_2_10-151-g3085e1a67
</details>

<details>
  <summary>
    Ubuntu 21.10 (kernel 5.16)
  </summary>
  
  * Aircrack-ng 1.6
  * hcxdumptool 6.2.4
  * wpa_supplicant v2.10-devel-hostap_2_9-2398-g8a54c252a
  * hostapd v2.10-devel-hostap_2_9-2398-g8a54c252a
</details>

<details>
  <summary>
    Kali Linux 2021.3a (kernel 5.14)
  </summary>
  
  * Aircrack-ng 1.6
  * hcxdumptool 5.2.2
  * wpa_supplicant v2.10-devel-hostap_2_9-2433-g8d881d942
</details>

<details>
  <summary>
    Kali Linux 2020.3 (kernel 5.9)
  </summary>
  
  * wpa_supplicant v2.10-devel-hostap_2_9-2379-g4775a5f82
  * hostapd v2.10-devel-hostap_2_9-2379-g4775a5f82
  * Aircrack-ng 1.6
  * hcxdumptool 6.1.4
</details>

<details>
  <summary>
    Kali Linux 2019.1a (kernel 4.19)
  </summary>
  
  * Aircrack-ng 1.5.2
  * hcxdumptool 5.1.7
  * wpa_supplicant v2.10-devel-hostap_2_9-2433-g8d881d942
</details>

<details>
  <summary>
    Ubuntu 21.10 (kernel 5.15)
  </summary>
  
  * wpa_supplicant v2.10-devel-hostap_2_9-2398-g8a54c252a
  * hostapd v2.10-devel-hostap_2_9-2398-g8a54c252a
  * Aircrack-ng 1.6
  * hcxdumptool 6.2.4
</details>

<details>
  <summary>
    Ubuntu 21.10 (kernel 5.13)
  </summary>
  
  * Aircrack-ng 1.6
  * hcxdumptool 6.2.0
  * hostapd v2.10-devel-hostap_2_9-2398-g8a54c252a
  * wpa_supplicant v2.10-devel-hostap_2_9-2398-g8a54c252a
</details>

<details>
  <summary>
    Ubuntu 12.04 (kernel 3.4)
  </summary>
  
  * Aircrack-ng 1.5.2
  * hcxdumptool 4.2.1
</details>

<details>
  <summary>
    Ubuntu 11.10 (kernel 3.0)
  </summary>
  
  * Aircrack-ng 1.5.2
  * hcxdumptool 4.2.1
</details>

<details>
  <summary>
    Linux Mint 20.2 MATE (kernel 5.4)
  </summary>
  
  * wpa_supplicant v2.10-devel-hostap_2_9-2486-gbb6fa62b3
  * hostapd v2.10-devel-hostap_2_9-2486-gbb6fa62b3
  * hcxdumptool 6.1.6
  * Aircrack-ng 1.6
</details>

<details>
  <summary>
    Ubuntu 12.10 (kernel 3.5)
  </summary>
  
  * Aircrack-ng 1.5.2
  * hcxdumptool 4.2.1
</details>

<details>
  <summary>
    Ubuntu 13.04 (kernel 3.8)
  </summary>
  
  * Aircrack-ng 1.5.2
  * hcxdumptool 5.1.4
</details>

<details>
  <summary>
    Ubuntu 21.04 (kernel 5.11)
  </summary>
  
  * Aircrack-ng 1.6
  * hcxdumptool 6.1.6
  * wpa_supplicant v2.10-devel-hostap_2_9-2374-g9ef8491d9
</details>

## HOW TO

### Install

Download source:

```
git clone https://github.com/ivanovborislav/rtl8821au.git
cd rtl8821au
```

Install missing packages:

```
sudo apt-get install bc build-essential
```

Install linux headers:

```
sudo apt-get install linux-headers-$(uname -r)
```

or

```
apt-cache search linux-headers
sudo apt-get install linux-headers-5.14.0-kali4-amd64 (for example)
apt-cache search linux-image
sudo apt-get install linux-image-5.14.0-kali4-amd64 (for example)
```

Compile:

```
make
sudo make install
```

or

```
chmod +x install.sh
./install.sh -i
```

Raspberry Pi:

Edit `Makefile`:

Ln142 - CONFIG_PLATFORM_I386_PC = `y` to CONFIG_PLATFORM_I386_PC = `n`

Ln143 - CONFIG_PLATFORM_RPI_ARM = `n` to CONFIG_PLATFORM_RPI_ARM = `y` for ARM

or

Ln144 - CONFIG_PLATFORM_RPI_ARM64 = `n` to CONFIG_PLATFORM_RPI_ARM64 = `y` for ARM64

### DKMS installation
```
sudo git clone "https://github.com/ivanovborislav/rtl8821au.git" /usr/src/rtl8821au-5.12.5.2
sudo dkms add -m rtl8821au -v 5.12.5.2
sudo dkms autoinstall
dkms status
```
or
```
sudo git clone "https://github.com/ivanovborislav/rtl8821au.git" /usr/src/rtl8821au-5.12.5.2
sudo dkms add -m rtl8821au -v 5.12.5.2
sudo dkms build -m rtl8821au -v 5.12.5.2
sudo dkms install -m rtl8821au -v 5.12.5.2
dkms status
```

### Monitor mode

```
sudo airmon-ng check kill
sudo ip link set <interface> down
sudo iw dev <interface> set type monitor
sudo ip link set <interface> up
```

### Managed mode

```
sudo ip link set <interface> down
sudo iw dev <interface> set type managed
sudo ip link set <interface> up
sudo systemctl restart NetworkManager (sudo service network-manager restart)
```

### TX power control

Note: Set TX power before start SoftAP mode. `...set txpower fixed 3000 = txpower 30.00 dBm`.

```
sudo iw dev <interface> set txpower fixed 3000
```

### Driver options

#### Change driver options during inserting driver module

Remove (unload) a module from the Linux kernel.
```
sudo rmmod /lib/modules/$(uname -r)/kernel/drivers/net/wireless/8821au.ko
```

Insert (load) a module into the Linux kernel.
```
sudo insmod /lib/modules/$(uname -r)/kernel/drivers/net/wireless/8821au.ko rtw_ips_mode=1 rtw_drv_log_level=4 rtw_power_mgnt=2 rtw_led_ctrl=1
```

#### Change driver options loading from file

Create a file `8821au.conf` containing `options 8821au rtw_ips_mode=1 rtw_drv_log_level=4 rtw_power_mgnt=2 rtw_led_ctrl=1`.
Copy a file to `/etc/modprobe.d/` directory.

```
sudo cp -f 8821au.conf /etc/modprobe.d
```

Power saving control.

IPS (Inactive Power Saving) Function, rtw_ips_mode=
```
0:Disable IPS
1:Enable IPS (default)
```

LPS (Leisure Power Saving) Function, rtw_power_mgnt=
```
0:Disable LPS
1:Enable LPS
2:Enable LPS with clock gating (default)
```

Driver debug log level control, rtw_drv_log_level=
```
0:_DRV_NONE_
1:_DRV_ALWAYS_
2:_DRV_ERR_
3:_DRV_WARNING_
4:_DRV_INFO_ (default)
5:_DRV_DEBUG_
6:_DRV_MAX_
```

Driver LED control, rtw_led_ctrl=
```
0:led off
1:led blink (default)
2:led on
```

Driver VHT control, rtw_vht_enable=
```
0:disable
1:enable (default)
2:force auto enable
```

Driver REGD source selection, rtw_regd_src=
```
0:Realtek defined
1:OS (default, get channel plan from OS)
```

### Connecting with wpa_supplicant

Example wpa_supplicant.conf with WPA3-Personal (WPA3-SAE).

```
update_config=1
ctrl_interface=/var/run/wpa_supplicant
country=EN
p2p_no_group_iface=1
sae_groups=19 20 21

network={
	ssid="WPA3"
	proto=RSN
	key_mgmt=SAE
	pairwise=CCMP
	group=CCMP
	ieee80211w=2
	psk="1234567890"
}
```

Now start...
```
sudo systemctl stop NetworkManager
sudo killall wpa_supplicant
sudo wpa_supplicant -B -i <interface> -c wpa_supplicant.conf
sudo dhclient <interface>
```

### Start SoftAP mode

Example hostapd.conf with WPA3-Personal (WPA3-SAE) 2.4GHz.

```
driver=nl80211
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=WPA3
country_code=EN
hw_mode=g
channel=6
beacon_int=100
dtim_period=1
max_num_sta=16
rts_threshold=2347
fragm_threshold=2346
ignore_broadcast_ssid=0
wmm_enabled=1
ieee80211n=1
ht_capab=[HT40-][SHORT-GI-20][SHORT-GI-40][RX-STBC1][MAX-AMSDU-7935][DSSS_CCK-40]

auth_algs=1
wpa=2
wpa_passphrase=1234567890
wpa_key_mgmt=SAE
wpa_pairwise=CCMP
rsn_pairwise=CCMP
ieee80211w=2
sae_groups=19 20 21
sae_require_mfp=1
````

Example hostapd.conf with WPA3-Personal (WPA3-SAE) 5GHz.

CAUTION: Allow width: 80 MHz, `insmod 8821au.ko rtw_vht_enable=2`.

```
driver=nl80211
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=WPA3_5GHz
country_code=EN
hw_mode=a
channel=36
beacon_int=100
dtim_period=1
max_num_sta=16
rts_threshold=2347
fragm_threshold=2346
ignore_broadcast_ssid=0
wmm_enabled=1
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-20][SHORT-GI-40][MAX-AMSDU-7935][DSSS_CCK-40]
ieee80211ac=1
vht_capab=[MAX-MPDU-11454][SHORT-GI-80][RX-STBC1][SU-BEAMFORMEE][HTC-VHT][MAX-A-MPDU-LEN-EXP7]
vht_oper_chwidth=1
vht_oper_centr_freq_seg0_idx=42

auth_algs=1
wpa=2
wpa_passphrase=1234567890
wpa_key_mgmt=SAE
wpa_pairwise=CCMP
rsn_pairwise=CCMP
ieee80211w=2
sae_groups=19 20 21
sae_require_mfp=1
```

Now start...
```
sudo killall hostapd
sudo hostapd -i <interface> hostapd.conf
```

### [Kali NetHunter Kernel module Samsung Galaxy S5](https://github.com/ivanovborislav/document/blob/main/NetHunter_Kernel_module_Samsung_Galaxy_S5.md)

## Test devices

- TP-Link Archer T2U Plus V1

- Linksys WRT1200AC V2
  * OpenWrt 21.02.0 r16279-5cc0535800 / LuCI openwrt-21.02 branch git-21.231.26241-422c175

```
config wifi-iface 'default_radio1'
	option device 'radio1'
	option network 'lan'
	option mode 'ap'
	option macaddr '30:23:03:XX:XX:XX'
	option ssid 'WPA3'
	option encryption 'sae'
	option key '1234567890'
	option ieee80211w '2'
```

-----
