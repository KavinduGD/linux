# Make the server's private IP address static in ubuntu

### Why the IP changes

Right now, your server is probably using **DHCP (Dynamic Host Configuration Protocol)**.

- When the server connects to the router, it asks:

  > "Can I have an IP address?"

- The router gives it one, such as `192.168.1.24`.
- Later, after a reboot or when the DHCP lease expires, the router may assign a different IP like:
  - `192.168.1.35`
  - `192.168.1.18`

This causes problems because applications, SSH, or other computers expect the server to always be at the same address.

---

## Two ways to fix it

### Option 1 (Recommended): DHCP Reservation on the Router

This is the best method.

The router remembers the server's **MAC address** (the network card's unique hardware address) and always gives it the same IP.

Example:

```
MAC Address
AA:BB:CC:DD:EE:FF

↓

Router

↓

Always assign

192.168.1.24
```

Advantages:

- Easy to manage
- No network conflicts
- Server still uses DHCP
- Works well if DNS or gateway changes

---

### Option 2: Configure a Static IP on Ubuntu

Instead of asking the router for an address, Ubuntu always uses the IP you configure.

Example:

```
IP Address: 192.168.1.24
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.1
DNS: 8.8.8.8
```

---

# First, check the current network configuration

SSH into the server:

```bash
ssh kavindu@192.168.1.24
```

Then run:

```bash
ip addr
```

and

```bash
ip route
```

Also run:

```bash
ls /etc/netplan
```

You will probably see something like

```
50-cloud-init.yaml
```

```bash
sudo cat /etc/netplan/50-cloud-init.yaml
```

```yaml
network:
  version: 2
  ethernets:
    enp6s18:
      dhcp4: true
```

This tells Ubuntu:

"Get the IPv4 address automatically from the router using DHCP."

```yaml
network:
  version: 2
  ethernets:
    enp6s18:
      dhcp4: false
      addresses:
        - 192.168.1.24/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
          - 192.168.1.1
          - 8.8.8.8
```

```bash
sudo netplan generate
```

```bash
sudo netplan try
```

```bash
sudo netplan apply
```
