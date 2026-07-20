# Multi-Area OSPF Lab

### Objective

Configure OSPF across multiple areas in order to demonstrate my understanding of route summarization and inter-area route propagation instead of a single area.

\-Summarizations on the ABRs R1 and R3
```text
ABR	Route	 Type	 Metric
R1	10.2.0.0 O IA	  110/2
R1	5.5.5.5	 O IA	 110/3
R3	10.1.0.0 O IA	 110/2
R3	4.4.4.4	 O IA	 110/3
```
### R1

**`show ip route ospf`**
```text
R1#show ip route ospf
     2.0.0.0/32 is subnetted, 1 subnets
O       2.2.2.2 [110/2] via 10.0.0.2, 00:04:55, GigabitEthernet0/0/0
     3.0.0.0/32 is subnetted, 1 subnets
O       3.3.3.3 [110/2] via 10.0.0.3, 00:04:45, GigabitEthernet0/0/0
     4.0.0.0/32 is subnetted, 1 subnets
O       4.4.4.4 [110/2] via 10.1.14.2, 00:05:25, GigabitEthernet0/0/1
     5.0.0.0/32 is subnetted, 1 subnets
O IA    5.5.5.5 [110/3] via 10.0.0.3, 00:04:45, GigabitEthernet0/0/0
     10.0.0.0/8 is variably subnetted, 6 subnets, 5 masks
O       10.1.4.0 [110/2] via 10.1.14.2, 00:05:25, GigabitEthernet0/0/1
O IA    10.2.0.0 [110/2] via 10.0.0.3, 00:04:45, GigabitEthernet0/0/0
```
**`show ip ospf neighbor`**
```text
R1#show ip ospf neighbor
Neighbor ID     Pri   State           Dead Time   Address         Interface
4.4.4.4           0   FULL/  -        00:00:35    10.1.14.2       GigabitEthernet0/0/1
3.3.3.3           1   FULL/BDR        00:00:35    10.0.0.3        GigabitEthernet0/0/0
2.2.2.2           1   FULL/DROTHER    00:00:34    10.0.0.2        GigabitEthernet0/0/0
```
### R3

**`show ip route ospf`**
```text
R3#show ip route ospf
     1.0.0.0/32 is subnetted, 1 subnets
O       1.1.1.1 [110/2] via 10.0.0.1, 00:02:50, GigabitEthernet0/0/0
     2.0.0.0/32 is subnetted, 1 subnets
O       2.2.2.2 [110/2] via 10.0.0.2, 00:02:50, GigabitEthernet0/0/0
     4.0.0.0/32 is subnetted, 1 subnets
O IA    4.4.4.4 [110/3] via 10.0.0.1, 00:02:50, GigabitEthernet0/0/0
     5.0.0.0/32 is subnetted, 1 subnets
O       5.5.5.5 [110/2] via 10.2.35.2, 00:03:20, GigabitEthernet0/0/1
     10.0.0.0/8 is variably subnetted, 6 subnets, 5 masks
O IA    10.1.0.0 [110/2] via 10.0.0.1, 00:02:50, GigabitEthernet0/0/0
O       10.2.5.0 [110/2] via 10.2.35.2, 00:03:20, GigabitEthernet0/0/1
```

**`show ip ospf neighbor`**
```text
R3#show ip ospf neighbor
Neighbor ID     Pri   State           Dead Time   Address         Interface
5.5.5.5           0   FULL/  -        00:00:30    10.2.35.2       GigabitEthernet0/0/1
1.1.1.1         100   FULL/DR         00:00:30    10.0.0.1        GigabitEthernet0/0/0
2.2.2.2           1   FULL/DROTHER    00:00:30    10.0.0.2        GigabitEthernet0/0/0
```
