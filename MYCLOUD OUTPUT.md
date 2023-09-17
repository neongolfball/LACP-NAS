MYCLOUD OUTPUT 1

root@NAS ~ # cat /proc/net/bonding/*
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 500
Up Delay (ms): 1000
Down Delay (ms): 1000

802.3ad info
LACP rate: slow
Min links: 0
Aggregator selection policy (ad_select): stable
System priority: 65535
System MAC address: 00:14:ee:00:3f:a2
Active Aggregator Info:
	Aggregator ID: 1
	Number of ports: 2
	Actor Key: 9
	Partner Key: 4042

Slave Interface: egiga0
MII Status: up
Duplex: full
Link Failure Count: 19
Permanent HW addr: 00:14:ee:00:3f:a2
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 4
Partner Churned Count: 7
details actor lacp pdu:
    system priority: 65535
    system mac address: 00:14:ee:00:3f:a2
    port key: 9
    port priority: 255
    port number: 1
    port state: 61
details partner lacp pdu:
    system priority: 32768
    system mac address: 78:8c:b5:5d:90:10
    oper key: 4042
    port priority: 32768
    port number: 7
    port state: 61

Slave Interface: egiga1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 19
Permanent HW addr: 00:14:ee:00:3f:a3
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: none
Partner Churn State: none
Actor Churned Count: 3
Partner Churned Count: 7
details actor lacp pdu:
    system priority: 65535
    system mac address: 00:14:ee:00:3f:a2
    port key: 9
    port priority: 255
    port number: 2
    port state: 61
details partner lacp pdu:
    system priority: 32768
    system mac address: 78:8c:b5:5d:90:10
    oper key: 4042
    port priority: 32768
    port number: 5
    port state: 61

Switch Side Outputs

TL-SG3428X-M2#show etherchannel load-balance 
EtherChannel Load-Balancing Configuration:
        src-dst-mac

TL-SG3428X-M2#show etherchannel detail                                         
Group: 2
----------
Group state = L2
Ports: 2  MaxPorts = 16
Protocol:   LACP
                Ports in the group:
                -------------------
Flags:  S - Device is sending Slow LACPDUs   F - Device is sending fast LACPDUs.
        A - Device is in active mode.        P - Device is in passive mode.

Local information:
                            LACP port     Admin     Oper    Port    Port
Port      Flags   State     Priority      Key       Key     Number  State
Tw1/0/5   SA      Up        32768         0x2       0xfca   0x5     0x3d
Tw1/0/7   SA      Up        32768         0x2       0xfca   0x7     0x3d

Partner's information:
                  LACP port                         Oper    Port    Port
Port      Flags   Priority     Dev ID               Key     Number  State
Tw1/0/5   SA      255          0014.ee00.3fa2       0x9     0x2     0x3d
Tw1/0/7   SA      255          0014.ee00.3fa2       0x9     0x1     0x3d

TL-SG3428X-M2#show etherchannel summary
Flags: D - down                       P - bundled in port-channel
       U - in use                     I - stand-alone
       H - hot-standby(LACP only)     s - suspended
       R - layer3                     S - layer2
       f - failed to allocate aggregator

       u - unsuitable for bundling
       w - waiting to be aggregated
       d - default port

Group  Port-channel  Protocol  Ports
------+-------------+---------+-------------------------------------------------
2      Po2(S)          LACP    Tw1/0/5(P)  Tw1/0/7(P)  

TL-SG3428X-M2#show interface status
Port      Status      Speed     Duplex    FlowCtrl    Active-Medium   Description
 Po2       LinkUp      1000M     Full      Disable     N/A  

TL-SG3428X-M2#show mac address-table 

                    MAC Address Table                    
------------------------------------------------------------  
MAC                VLAN    Port     Type            Aging    
---                ----    ----     ----            ----- 
00:14:ee:00:3f:a2  1       LAG 2    dynamic         aging    
00:14:ee:00:3f:a3  1       LAG 2    dynamic         aging    