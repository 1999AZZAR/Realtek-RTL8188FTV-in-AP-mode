# Setting up Realtek RTL8188FTV in AP mode on Windows
The following instructions will guide you through the process of setting up the Realtek RTL8188FTV in AP mode on Windows.

## Prerequisites
* A Windows machine with a Realtek RTL8188FTV wireless adapter.
* A wired internet connection.
* The Realtek wireless adapter's drivers installed on your Windows machine.
## Installation
* Download the Realtek wireless adapter's drivers from Realtek's website and install it on your Windows machine.
## Configuration
1. Open the Device Manager and find the Realtek wireless adapter under "Network Adapters." Right-click on the adapter and select "Properties."
2. Go to the "Advanced" tab and find the "Wireless Mode" option. Change the value from "Client" to "AP."
3. Go to the "Advanced" tab and find the "SSID" option. Enter the name you want to give your wireless network.
4. Go to the "Security" tab and configure the security settings for your wireless network. You can choose to use WPA2-PSK (AES) encryption, and enter a password of your choice.
5. Click "OK" and close the Device Manager.
6. Enable the Internet Connection Sharing (ICS) feature on the wired network connection. Go to "Control Panel" > "Network and Sharing Center" > "Change adapter settings". Right-click on the wired network connection and select "Properties." Go to the "Advanced" tab and check the "Allow other network users to connect through this computer's Internet connection."
7. Restart the wireless adapter for the changes to take effect
## Conclusion
You have successfully set up Realtek RTL8188FTV in AP mode on Windows. You can now connect to the wireless access point, and you should be able to access the internet via the wired connection. Keep in mind that these steps are general and you might need to adjust them for your specific setup, also the compatibility of your wifi card with the AP mode may vary.
