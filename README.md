# Setting up Realtek RTL8188FTV in AP mode
The following instructions will guide you through the process of setting up the Realtek RTL8188FTV in AP mode on both Windows and Ubuntu.

## Prerequisites
* A computer with Realtek RTL8188FTV wireless adapter
* Wired internet connection
* Realtek wireless adapter driver installed
## Windows
1. Download and install the Realtek wireless adapter driver from the Realtek website.
2. Open Device Manager, right-click on the Realtek adapter, select Properties and change Wireless Mode to AP.
3. Change SSID to your desired network name and configure security settings.
4. Enable Internet Connection Sharing (ICS) on the wired network connection.
5. Restart the wireless adapter.
## Ubuntu
1. Open terminal and install hostapd and dnsmasq:
```csharp
sudo apt-get install hostapd dnsmasq
```
2. Create a new hostapd configuration file:
```bash
sudo nano /etc/hostapd/hostapd.conf
```
3. Add the following lines to the configuration file:
```makefile
interface=wlan0
driver=nl80211
ssid=Your_SSID
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=Your_Passphrase
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```
Replace "Your_SSID" with desired network name and "Your_Passphrase" with desired password.
4. Enable hostapd and dnsmasq to start on boot:
```bash 
sudo systemctl enable hostapd
sudo systemctl enable dnsmasq
```
5. Start hostapd and dnsmasq service:
```sql
sudo systemctl start hostapd
sudo systemctl start dnsmasq
```
6. Restart wireless adapter:
```
sudo ifdown wlan0
sudo ifup wlan0
```
Your Realtek RTL8188FTV wireless adapter should now be configured as an access point and ready to use. Connect to the newly created wireless network with the SSID and password you have set
