# Week 4

## Network Infrastructure

A great deal of networking, both internal and across the internet, is handled by
Linux machines. Because of their inherent flexibility, hey can serve in a variety
of roles, and so understanding how to configure them with consistency at scale can
offer a great start to anyone interested in focusing on these areas of computing
systems.

### DNS

Domain name resolution is one of the most important parts of network usability.
Being able to use common names instead of IP addresses is something that most users
take for granted, but is supported by a vast network of servers. Typically this
responsibility is outsourced to an external server, but for those that need name
resolution for local hosts, there are a variety of Linux utilities that offer customizable
DNS capabilities to your networks.

### DHCP

DHCP also plays a valuable role in the basic functions of most local networks.
While many routers handle this by default, you may require more custom configurations
depending on your use case. Luckily, there are Linux utilities that can handle that
manage to be simple to configure (through automation, even!) while remaining powerful
enough for most use cases.

### VPN

Private connections via VPN have been a staple of corporate network environments
for quite some time, and have increased significantly for personal use in recent
years. Although we won't be configuring one as a part of this exercise, tools like
OpenVPN are known to be stable and relatively simple to set up on Linux.

### Networking -  Recommended Reading

1. The `dnsmasq` docs are accessible via the command: `man dnsmasq` or [online](https://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html)
2. This `dnsmasq` configuration [guide](https://thekelleys.org.uk/dnsmasq/docs/setup.html)
3. Basic network commands from our [cheatsheet](https://gto76.github.io/linux-cheatsheet/#network)

## Lab Exercise

For this lab exercise, you will be using `dnsmasq` to handle DNS in your Azure lab.
Your DNS server should be hosted on `host1` of your lab hosts and should (at least):

- Use at least two upstream servers for redundancy
- Maintain a `hosts` file with all machines (including the controller)
- Provide cool new names with which to address your hosts
  - Pick sensible names related to purpose, or weird names related to whatever you
    want. For these exercises, it really doesn't matter as long as you know them.
- Avoid routing private requests to public DNS servers
- Be listed on your Azure VNet as the DNS server of choice
