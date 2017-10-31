# Tor firejail on-demand
This shell script will quickly setup a Linux systems network to route traffic through a Tor using a dedicated interface, iptables rules, and the [firejail](https://firejail.wordpress.com) profile for Tor.
  
This has only been tested on Ubuntu 16.04.3 LTS. A `torrc` file is included in this repo that will replace your existing `/etc/tor/torrc` file (a backup of the original will be made). Feel free to edit this file as needed, but **do not edit** the following settings:
- TransPort
- VirtualAddrNetwork
- DNSPort
- AutomapHostsOnResolve

**Warning:** This is not guaranteed to securely route _all_ traffic through Tor. If this is your use-case, it is much better to run a live version of the [Tails](https://www.tails-boums.org) distribution.
  
## Requirements
- [Tor](https://www.tor-project.org) - `apt install tor`
- [Firejail](https://firejail.wordpress.com) - `apt install firejail`
- Root access to run the script as it edits iptables, /etc/tor/torrc, network settings, and sysctl.conf

## Usage
- **Enable Proxying:** `./tfj-ondemand.sh start <external interface>`
- **Disable Proxying:** `./tfj-ondemand.sh stop`
- **Show Help Menu:** `./tfj-ondemand.sh help`
