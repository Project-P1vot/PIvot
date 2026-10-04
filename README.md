
# PIvot

A Raspberry Pi OS variant for self-hosters.

## Getting Started

Default connection details are managed via [`pivot-gen/config`](https://github.com/cylin577/pivot-gen/blob/master/config):

* **Hostname:** `pivot`
* **Username:** `pivot`
* **Password:** `tovip`
* **SSH:** Enabled by default
* **Sudo:** Passwordless access for the default user

---

## Connecting to PIvot

### Via SSH
Connect from your terminal using the local hostname:
```bash
ssh pivot@pivot.local
```

*If mDNS is not supported on your network, use the device IP address: `ssh pivot@<device-ip>`*

### Via Web Browser
On first boot, a setup screen is exposed on port **7681**:
* ```http://pivot.local:7681```
* ```http://<device-ip>:7681```

---

## Captive Portal

**When no internet connection is detected on first boot, PIvot will automatically start a captive portal.**

### How it works:
1. If the Raspberry Pi has no working internet connection, it will create a WiFi access point
2. **SSID:** `Pivot-Setup`
3. **Password:** `pivot-setup-123`
4. Once you connect to this network, a captive portal page will open automatically
5. The portal will prompt you to connect and then redirect you to the setup screen

### Connecting to the Captive Portal:
1. Connect your device to the **`Pivot-Setup`** WiFi network
2. Open your browser - you should be automatically redirected to the captive portal
3. If not redirected, manually visit: ```http://10.0.0.1```
4. Follow the instructions to connect to the setup network
5. Once connected, you'll be redirected to the main setup screen at port 7681

### Technical Details:
- The captive portal creates a WiFi access point using `hostapd`
- DHCP and DNS are provided by `dnsmasq`
- All HTTP/HTTPS traffic on the captive network is redirected to the portal page
- The portal runs on IP `10.0.0.1`

---

## Important Notes

* **Wi-Fi Setup:** If you do not use an Ethernet cable on the first boot, you must connect a keyboard and screen to the Pi to configure your wireless network manually. **Alternatively, use the captive portal feature to connect via WiFi without any additional hardware.**
* **Security:** If you intend to expose this device to the internet, immediately update the default password by running the `passwd` command or you could get all your data stolen if someone has access to your network
* **Remote Access:** For secure access outside your local network (LAN), it is highly recommended to use [Tailscale](https://login.tailscale.com/admin).