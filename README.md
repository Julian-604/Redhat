# Redhat


Open the terminal or connect to your server via SSH.

Identify the network interface name you want to configure using the ip link show command. It typically appears as eth0 or ensXXX.

Edit the network configuration file using a text editor like vi or nano. For example, use the following command to open the file with vi:

bash
Copy code
```shsudo vi /etc/sysconfig/network-scripts/ifcfg-<interface-name>```
Replace <interface-name> with the actual name of your network interface.

Within the file, locate the line that begins with BOOTPROTO and change its value to none. This ensures that the IP address is not obtained via DHCP.

Add the following lines to specify the IP address, netmask, gateway, and DNS servers:

bash
Copy code
``IPADDR=<your-ip-address>``
``NETMASK=<your-netmask>``
``GATEWAY=<your-gateway>``
``DNS1=<your-primary-dns>``
``DNS2=<your-secondary-dns>``
Replace <your-ip-address>, <your-netmask>, <your-gateway>, <your-primary-dns>, and <your-secondary-dns> with your actual network configuration values.

Save the changes and exit the editor.

Restart the network service to apply the new configuration:

bash
Copy code
``sudo systemctl restart network``
Verify the changes by running the ip addr show command or using the ifconfig command.
