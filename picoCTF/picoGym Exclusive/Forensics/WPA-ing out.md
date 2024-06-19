# WPA-ing out

## Overview

Points: 200

Category: Forensics

## Description
I thought that my password was super-secret, but it turns out that passwords passed over the AIR can be CRACKED, especially if I used the same wireless network password as one in the rockyou.txt credential dump. 

Use this `pcap file` and the rockyou wordlist. The flag should be entered in the picoCTF{XXXXXX} format.

## Hints (if any)
1. Finding the IEEE 802.11 wireless protocol used in the wireless traffic packet capture is easier with wireshark, the JAWS of the network.
2. Aircrack-ng can make a pcap file catch big air...and crack a password.
## Approach

We have pcap file that has a record of wifi traffic. Since `AIR` and `CRACKED` are written in capitalized manner, we can get another hint that `aircrack-ng` is to be used to get the password. So first, lets start to analyse the pcap file.

![pcap file in wireshark](./img/wpaing%20out%201.png)

We see that there's an SSID called "Gone_Surfing" in the wireless network traffic packet capture. Lets filter this to see if there are any more SSIDs present in the network.

`wlan.ssid` is the filter parameter we use to get all of the SSIDs that are present in the wireless network traffic packet capture. Now seeing only the relevant packets, we see that there's only 1 SSID present. Saves us time to crack its password.

Now lets hop onto using `aircrack-ng` to get the password.

```bash
aircrack-ng -e SSID-NAME -w wordlist pcap-file
```
The command is really simple:
- `-e` flag is used to specify the SSID of the network
- `-w` is the wordlist that will be used for cracking. In kali, wordlist is stored in `/usr/share/wordlists` directory.
- and finally the pcap file which contains all the packets.

Run this and you will get the flag!

![aircrack-ng to crack password](./img/wpaing%20out%202.png)

## Flag
picoCTF{mickeymouse}