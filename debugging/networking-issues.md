# Networking Issues

### Getting network info

Run the command below to get the information of various network interfaces.

`ip addr show`

### Checking for firewalls

Checking for firewalld

`sudo firewall-cmd --state`

Checking for ufw

`sudo ufw status`

&#x20;Checking iptables

`sudo iptables -t nat -L -n -v`

Checking iptables-legacy (needed if iptables-nft is installed

`sudo iptables-legacy -t nat -L -n -v`

### DNS issues.&#x20;

Currently the most common cause for DNS issues are ports. Ports `53` and `67` need to be allowed, as well as packet forwarding. this will be dependent on the firewall being used.

iptables-legacy has on a single case caused issues with DNS routing, the solution was upgrading to iptables-nft.
