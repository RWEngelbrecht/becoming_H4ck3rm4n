# NMAP
## Network Mapper

Tool for network exploration and security auditing.

### What? How?
Uses raw IP packets to determine available hosts on network, what services they are offering, what OS they're running, and packet filters/firewalls they use.

### commands
- scan for hosts on network (doesn't scan ports)
  - `nmap -sP <inet>/<range>`
- ping hosts in network (same as above, but newer)
  - `nmap -sn <inet>/<range>`
- scan ports on host (`-sT`: tcp connect (full open scan))
  - `nmap -sT [-p<ports,>][-p- for all ports] <inet>/<range>`
