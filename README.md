# Pfsense Firewall Configuration

## Objective

The Pfsense Firewall Configuration project was designed to simulate the deployment and configuration of a firewall in a controlled virtual environment. The primary goal was to understand firewall architecture, configure network interfaces, and create appropriate rules to manage traffic between different network segments. This hands-on experience aimed to enhance practical skills in network security and firewall management.

### Skills Learned

- Understanding of firewall architecture and functionality.
- Proficiency in configuring VirtualBox for network simulations.
- Ability to create and manage firewall rules effectively.
- Insight into network protocols and their security implications.
- Development of troubleshooting skills in a simulated network environment.

### Tools Used

- VirtualBox for creating and managing virtual machines.
- Pfsense as the firewall solution for the lab setup.
- Network analysis tools for monitoring and testing traffic flow.

## Steps

### Step 1: Setting Up VirtualBox Network

1. Open VirtualBox and navigate to preferences.
2. Click on “Network” and add a new NAT Network.
3. Name the new network: LAB-WAN-OUT with CIDR 192.168.200.0/24.
4. Ensure "Supports DHCP" is checked and click “OK”.

---

### Step 2: Installing Pfsense

1. Download the Pfsense ISO from https://pfsense.org/download.
2. Create a new VM in VirtualBox named pfsense-fw configured for BSD.
3. Allocate memory (1024MB) and create a virtual hard disk (16GB).
4. Set up two network interfaces for the VM, one for inside (LAB-NAT-NET) and one for outside (LAB-WAN-OUT).

---

### Step 3: Configuring Firewall Interfaces

After installing Pfsense:

1. Ensure IP Addresses are assigned correctly:
   - WAN: 192.168.200.0/24
   - LAN: 10.10.10.0/24
2. Setup VLANs as needed and configure the LAN IP address.

---

### Step 4: Accessing Pfsense Admin Interface

1. Power on your Windows VM, ensure it is connected to the LAB-NAT-NET.
2. Access Pfsense via the browser at `http://10.10.10.11` using default credentials (admin/pfsense).
3. Complete the initial setup by configuring hostname, DNS, and interface settings.

---

### Step 5: Creating Firewall Rules

#### Task 1: Create Stealth Rule
- Allow access to `http://10.10.10.11` from your Windows VM's IP.

#### Task 2: Default Deny Rule
- Create a last rule to deny any traffic not matching defined rules.

#### Task 3: Outbound Rules
- Allow outbound traffic from LAN (10.10.10.0/24) for:
  - TCP Ports 80, 443, 53
  - UDP Port 53
  - TCP Port 25

#### Task 4: Inbound Rules
- Allow inbound traffic on WAN for:
  - TCP Ports for specific servers (Web, DNS, SMTP).

---

### Conclusion

This lab provided practical experience with configuring firewall rules and understanding network security principles. The skills gained will be invaluable in real-world applications of network management and security.
