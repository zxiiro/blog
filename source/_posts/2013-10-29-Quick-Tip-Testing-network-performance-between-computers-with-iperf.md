title: Quick Tip - Testing network performance between computers with iperf
date: 2013-10-29
tags:
- linux
---
I discovered a handy tool to check network performance between 2 computers. This tool called
[iperf](https://code.google.com/p/iperf/) is quite easy to use too. You can install this tool using your
distro's package manager. In my case I was using OpenSUSE which was available via "zypper install iperf".

There are 2 modes this tool runs in. Server and Client, you will need to run it in server mode on one end and client
mode on the other end. Doesn't matter which.

Server Usage:

    iperf -s

Client Usage:

    iperf -c host/ip

Basically you want to run it with the "-s" option on the serverside and the "-c" option on the client side. On the
client end you will also need to provide the server's hostname or ip

Here is an example of what it looks like when I run it on my network.

    ------------------------------------------------------------
    Client connecting to 192.168.32.50, TCP port 5001
    TCP window size: 22.9 KByte (default)
    ------------------------------------------------------------
    [  3] local 192.168.32.152 port 40885 connected with 192.168.32.50 port 5001
    [ ID] Interval       Transfer     Bandwidth
    [  3]  0.0-10.0 sec   897 MBytes   752 Mbits/sec
