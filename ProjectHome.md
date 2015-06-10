Softflowd is flow-based network traffic analyser capable of Cisco NetFlow data export. Softflowd semi-statefully tracks traffic flows recorded by listening on a network interface or by reading a packet capture file. These flows may be reported via NetFlow to a collecting host or summarised within softflowd itself.

Softflowd supports Netflow versions 1, 5 and 9 and is fully IPv6-capable - it can track IPv6 flows and send export datagrams via IPv6. It also supports export to multicast groups, allowing for redundant flow collectors.

## Details ##

Softflowd semi-statefully tracks traffic flows. Upon expiry of a flow, its statistics are accumulated and reports them to a designated collector host using the standard NetFlow protocol. Currently the statistics collected are summaries only: min/max/avg/total bytes, packets on a aggregate or per-protocol basis.

Softflowd can export using NetFlow version 1, 5 or 9 datagrams and it is fully IPv6 capable: it can track and report on IPv6 traffic and flow export datagrams can be sent to an IPv6 host. Any standard NetFlow collector should be able to process the reports from softflowd.

As softflowd watches traffic promiscuously, it is likely to place additional load on hosts or gateways on which it is installed. However, this implementation has been designed to minimise this load as much as possible. Alternately, softflowd can read pcap save files recorded from tcpdump and friends.

Unless reading from a traffic dump, softflowd run as a daemon. A "remote control" program (softflowctl) is included which allows runtime control and extraction of statistics from a daemonised softflowd.

Softflowd is developed on Linux and OpenBSD. It requires libpcap and its associated headers to build, these are available from tcpdump.org, or from your operating system vendor. As of version 0.9, there is some support for Solaris but this is still experimental.