# OSPF-Networking-Project
Configuring OSPF to enable communication between networks using Cisco routers and switches.
Step 1: Configure Router0

enable
configure terminal
hostname Router0

interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 10.0.0.1 255.255.255.0
 no shutdown

router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.255 area 0

exit

Step 2: Configure Router1

enable
configure terminal
hostname Router1

interface FastEthernet0/0
 ip address 10.0.0.2 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 10.0.1.1 255.255.255.0
 no shutdown

router ospf 1
 network 10.0.0.0 0.0.0.255 area 0
 network 10.0.1.0 0.0.0.255 area 0

exit
write memory
Step 3: Configure Router2

enable
configure terminal
hostname Router2

interface FastEthernet0/0
 ip address 10.0.1.2 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown

router ospf 1
 network 10.0.1.0 0.0.0.255 area 0
 network 192.168.2.0 0.0.0.255 area 0

exit
write memory
Step 4: Configure PCs
Set the IP address and default gateway for each PC.

PC0 (Switch0)

IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
PC1 (Switch0)

IP Address: 192.168.1.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
PC2 (Switch1)

IP Address: 192.168.2.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1
PC3 (Switch1)

IP Address: 192.168.2.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1
Step 5: Test Connectivity
After setting up, use the ping command on the PCs to check connectivity.

From PC2 to PC0:

ping 192.168.1.2
If OSPF is working correctly, the ping should be successful.
