# HSRP Lab

##### Objective

First I enabled OSPF on all routers so I wouldn't have to statically configure every route. I then made a basic HSRP config using one instance. Then I removed that config in order to build HSRP in a way that allows load sharing. I did this by having each vlans hosts point at a different VIP I made R1 the Active for vlan 20 and R2 the active for vlan 10. R1 is the standby for vlan 10 and R2 is the standby for vlan 20.

