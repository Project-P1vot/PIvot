
# PIvot

A Raspberry Pi OS variant for self-hosters.

自托管者的三大欲求是掌控欲、隐私欲和折腾欲。其中，掌控欲对自托管者来说是维持数字生命独立所必需的，在技术探索方面伴随着无与伦比的成就感。它被设定为优先采取行动。通过成功部署容器可以获得满足感，通过运行流畅无广告的服务可以获得喜悦，从而对精神产生极大的积极影响。此外，还有一些人热衷于终日追求这种自由与快乐。这些人通常被称为“自托管极客”。本项目为那些已经对市场上各种商业云服务与隐私侵犯感到厌倦的人们，提供最适合自托管极客的数字食材与硬核配置。

##  Getting Started

Default connection details are managed via [`pivot-gen/config`](https://github.com/cylin577/pivot-gen/blob/master/config):

*   **Hostname:** `pivot`
*   **Username:** `pivot`
*   **Password:** `tovip`
*   **SSH:** Enabled by default
*   **Sudo:** Passwordless access for the default user

---

##  Connecting to PIvot

### Via SSH
Connect from your terminal using the local hostname:
```bash
ssh pivot@pivot.local
```

*If mDNS is not supported on your network, use the device IP address: `ssh pivot@<device-ip>`*

### Via Web Browser
On first boot, a setup screen is exposed on port **7681**:
*   ```http://pivot.local:7681```
*   ```http://<device-ip>:7681```

---

##  Important Notes

*   **Wi-Fi Setup:** If you do not use an Ethernet cable on the first boot, you must connect a keyboard and screen to the Pi to configure your wireless network manually.
*   **Security:** If you intend to expose this device to the internet, immediately update the default password by running the `passwd` command or you could get all your data stolen if someone has access to your network
*   **Remote Access:** For secure access outside your local network (LAN), it is highly recommended to use [Tailscale](https://login.tailscale.com/admin).