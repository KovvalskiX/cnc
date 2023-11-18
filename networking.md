# Mesa board setup

**_Warning: Disable Wired before making changes - it breaks other network interfaces_**

1.	Disable Secure Boot
2.	Wired:
    - Manual mode
    - IPv4 `10.10.10.11`
    - Mask `8`
    - Gateway `10.10.10.1`
    - DNS `10.10.10.1`

_Possible that IPv6 will cause problems, not tested_

3.  `sudo nmcli connection modify "Wired connection 1" ipv4.never-default true`

4. Connect to Wired interface

**_PC interface is ready. Check Mesa onboard jumpers (should be EEPROM mode, IP 10.10.10.10 by default)_**

5.	`mesaflash --device ETHER --addr 10.10.10.10 –readhmid`

_Should reply with board info, means board is recognized_

