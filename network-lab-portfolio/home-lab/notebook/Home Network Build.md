# Home Network Build

#### 7/14/26

Starting my home network build today super excited. The M720Q ended up having the wrong PCIE slot for my NIC. Luckily I was able to order an adapter off amazon. Today ill be setting up my WAN edge (BGW320 Passthrough + OPNsense base install). Then I will setup router on a stick and VLAN interfaces on OPNsense. Will have a short period of down time when I have to restart the router after enabling Passthrough. I will also be setting up DHCP scopes on OPNsense. Going to disable IPv6 until the network is done then I will implement IPv6 as my next project. Having IPv6 disabled is better then having it half configured

#### 7/15/26

Today im going to setup my switch. I will be configuring VLANS, trunks, and access ports. I will also setup SSH. Then i will set a password for all lines. I accidentally erased my OPNsense config and didn't make a backup. Not making that mistake again. My computer was no compatible with the SSH options on the cisco switch unless i specified in the shh command what algorithms to use, So i created a config file in my .ssh folder to my computer knows what algorithms to use when SSHing into the switch without having to type it every time. I made sure to enable portfast and bpduguard on access ports. My computer is now able to receive the correct DHCP address for the VLAN it is in.

#### 7/16/26

Today I finished up my network and got it fully running. I then set firewall rules on OPNsense so guest/IoT could not initiate a conversation with a host in the HOME vlan or Management vlan. I set the guest/IoT vlan to only use the 2.4ghz band in order to reduced congestion and save bandwidth on the 5ghz band. My next project will be to implement IPv6. I made sure to store backups of my switch, OPNsense, and Omada configs on a external hard drive as well as the internal hard drive. 

