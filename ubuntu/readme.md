# Setting up Realtek RTL8188FTV in AP mode on Ubuntu
The following instructions will guide you through the process of setting up the Realtek RTL8188FTV in AP mode on Ubuntu.

## Prerequisites
* A Ubuntu machine with a Realtek RTL8188FTV wireless adapter.
* A wired internet connection.
## Installation
1. Update your package list:
```bash
sudo apt-get update
```
2. Install the necessary software:
```bash
sudo apt-get install hostapd dnsmasq
```
## Configuration
1. Configure the network interface:
```bash
sudo nano /etc/network/interfaces
```
Add the following lines:
```c
auto wlan0
iface wlan0 inet static
address 192.168.42.1
netmask 255.255.255.0
```
2. Configure the DHCP server:
```bash
sudo nano /etc/dnsmasq.conf
```
And add the following lines:
```go
interface=wlan0
dhcp-range=192.168.42.2,192.168.42.20,255.255.255.0,24h
```
3. Configure the access point:
```bash
sudo nano /etc/hostapd/hostapd.conf
```
Add the following lines:
```mkfile
interface=wlan0
driver=rtl871xdrv
ssid=MyAP
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=MyPassphrase
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```
## Start Services
1. Start the hostapd service:
```bash
sudo service hostapd start
```
2. Start the dnsmasq service:
```bash
sudo service dnsmasq start
```
## Enable IP Forwarding
1. Enable IP forwarding:
```bash
sudo sysctl -w net.ipv4.ip_forward=1
```
## Configure iptables
1. Configure iptables:
```bash
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i wlan0 -o eth0 -j ACCEPT
```

You should now have a working wireless access point. Keep in mind that these steps are general and you might need to adjust them for your specific setup.
You might also consider using NetworkManager instead of editing files and starting services manually.

## Conclusion
You have successfully set up Realtek RTL8188FTV in AP mode on Ubuntu. You can now connect to the wireless access point, and you should be able to access the internet via the wired connection.
