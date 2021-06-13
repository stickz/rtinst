## rtinst

### Note: Now installs Lets Encrypt SSL certificates

#### 30 Second Guide

Ubuntu and Debian Seedbox Installation

Download and run setup (if logged in directly as root, do not need to use sudo)

	sudo bash -c "$(wget --no-check-certificate -qO - https://raw.githubusercontent.com/stickz/rtinst/master/rtsetup)"

and then to run the main script, ([check the options you can use](https://github.com/arakasi72/rtinst/wiki/Guide#21-main-script-options)):

	sudo rtinst

The script takes about 15 minutes to run (depending on your server setup). After the script succesfully completes, I suggest a reboot. The script does not automatically reboot. You can optionally run `sudo reboot` to manually reboot.

[A detailed installation guide](https://github.com/arakasi72/rtinst/wiki/Installing-rtinst)

[A detailed user guide](https://github.com/arakasi72/rtinst/wiki/Guide)

It is highly recommended to use **Ubuntu 20.04 LTS** for this fork. However, **Debain 10** will be maintained as well. Older versions of Ubuntu and Debian will receive very limited support. 
	
Services that will be installed and configured are

	1. libtorrent/rtorrent
	2. rutorrent
	3. Nginx (webserver)
	4. Dnsmasq (dns server)
	5. webmin (optional see section 3.7 in main guide)

This fork is designed for a dedicated server and adjusts configuration settings acoordingly. Some important changes include:

	* Multiple bugs have been resolved including issues with geoip, letsencrypt and nginx not working properly.
	
	* All custom built software is done using GCC's Level 2 Optimizations for a stable performance increase.
	* The static libaries are no longer built because the operating system prefers to use the dynamic libaries.
	* Ubuntu 20.04 LTS now uses GCC 10.2 instead of 9.3 for increased performance of software builds.
	
	* Annoyances with disabling the root login and changing the ssh port will no longer happen. Security enthusiasts can research how to do this.
	
	* You can no longer select versions of libtorrent and rtorrent due to superior custom support. (timeout & udns changes)
	* Simply create an issue report if a new version is released and this fork will be updated. It will always be kept stable on a rolling release.
	
	* IPV6 support is disabled for rTorrent and nginx to ensure compability with VPNs.
	* Support for the following software has been removed from this fork: vsftpd, ffmpeg and autodl-irssi.
	* Bigger buffer sizes are used in the default rtorrent.rc file to reduce disk seeking. 32GB of ram is highly recommended.
	* The logging directory for rtorrent is created. All errors which cause the program to crash will be reported.
	* Preallocation of disk space is enabled by default because fallocate is very fast.
	* Max open files and sockets have been raised to 10000 for thousands of torrents.
	* The file limits have been raised to 65535 to allow for thousands of torrents.

	* The curl timeouts have been reduced from 60s to 30s for connections and from 5m to 90s to receive information on http trackers.
	* The udp tracker requests will no longer retry twice in a short period of time for results because some trackers have rate limits.
	
	* The dnsmasq dns server is installed and configured, as a local dns caching solution for faster tracker updates.
	* The rTorrent build includes the latest verison of curl with c-ares support for asynchronous http tracker requests.
	* The libtorrent build is a custom version with udns support for asynchronous udp tracker requests.
	* Asynchronous tracker requests improve performance and prevent rtorrent from stalling with thousands of torrents.
	
	* Backported a few fixes from jesec/libtorrent for memory leaks in the libtorrent binary.


Future changes to this fork will improve the performance and throughput. These will include:

	* The sysctl.conf file will be updated with TCP network tweaks to increase throughput. Again 32GB of ram is highly recommended.
	* The php-fpm configuration will be updated with a bigger memory cache, to reduce the frequency of disk activity.
	

[rtinst installation guide](https://github.com/arakasi72/rtinst/wiki/Installing-rtinst)

[Additional information on all the features](https://github.com/arakasi72/rtinst/wiki/Guide)

To see latest updates to the script go to [Change Log](https://github.com/arakasi72/rtinst/wiki/Change-Log)

-------------------------------------------------------------------------

 Copyright (c) 2015 arakasi72 (https://github.com/arakasi72)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: 

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. 

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

 --> Licensed under the MIT license: http://www.opensource.org/licenses/mit-license.php
