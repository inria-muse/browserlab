# Browserlab OpenWRT Feed

OpenWRT package feed for various network measurement tools and APIs. 


## Contents

### collectd

Modified collectd 5.5.0 with libtrace based LAN and WAN monitoring modules.

### iperfng  

Modified iperf 2.0.5 that supports NAT traversal and JSON output. 

See: https://github.com/apietila/iperf-ng


### libtcptools  

Libtcptools is a library that leverages libtrace to perform several
useful TCP analysis tasks, including RTT estimation, classification 
of reordering events and bandwidth estimation.

See: http://research.wand.net.nz/software/libtcptools.php


### libtrace and libtrace-tools

Network trace processing library and tools for trace processing. 
Supports multiple input methods, including device capture, raw and 
gz-compressed trace, and sockets.

See: http://research.wand.net.nz/software/libtrace.php


### libtrace-tools-extra

A collection of libtrace (and libtcptools) based trace utilities:

  * tracepktiv: monitor packet inter-arrival times
  * tracertt: in/out RTTs based on TCP data-ack packet pairs

See: https://github.com/apietila/libtrace-tools-extra


### sysstat  

Performance monitoring tools for Linux.

See: https://github.com/sysstat/sysstat



## Compiling

  1. Setup OpenWRT cross-compilation environment (http://wiki.openwrt.org/doc/howto/buildroot.exigence)

  2. Configure the 'browserlab' custom feed to your feeds.conf (http://wiki.openwrt.org/doc/devel/feeds):

	```
	src-git browserlab https://github.com/inria-muse/browserlab.git
	```

  3. Update and install selected packages from the 'browserlab' feed

	```
	[path/to/openwrt/]$ ./scripts/feeds update browserlab
	[path/to/openwrt/]$ ./scripts/feeds install -p browserlab <package>
	[path/to/openwrt/]$ make menuconfig 
	```

  4. Select the installed packages in the menu config tool

  5. Build the packages 

	```
	[path/to/openwrt/]$ make package/<package>/compile V=s 
	```

