# Week 5

## Storage

Need for shared storage is one of the primary use cases for more sophisticated networking.
Although many public cloud and web-based options are available, there are various
valid reasons (usually compliance-based) for why a given organization (or individual)
may need a more custom solution.

### Local Storage

Local storage device management and configuration is a topic worthy of its own deep-dive,
but it isn't particularly important for this introductory course. Our Azure VM deployments
handle this themselves, and in most cases storage configurations are a "set it and
forget it" task. But, inevitably, if you work with Linux you will encounter a need
for storage setup or troubleshooting. There are GUI tools that can help, but knowing
your way around the CLI commands to handle those tasks never hurts. I've listed some
great guides from DigitalOcean down below that cover both storage terminology and
concepts, as well as some basic commands for navigating those processes. Disk and
storage configurations can be managed via Ansible as well, but because we are using
auto-generated Azure resources for all of our lab's disk needs, we won't be tackling
that in this module.

### Networked Storage

#### NAS Software

Full-fledged Network Access Storage systems often offer niceties like multiple methods
of connection, a web or local GUI for management, and configuration wizards for ease-of-use.
In many personal or home/small business use cases, this is perfectly suitable. At
scale, however, these sorts of tools can require a significant amount of management
overhead if the process is not automated. For this reason, many people choose an
all-in-one hardware/software bundled NAS if this is their preferred solution.

#### Private Cloud Suites

Private cloud suites like [Nextcloud](https://nextcloud.com/) can offer even more
than most dedicated NAS platforms, including features familiar to users of GSuite
or DropBox: collaboration frameworks, shared calendars, web GUI document editors,
and more. Despite this, one of their primary features is typically a solid storage
and file management platform. These often see the same benefits and pitfalls of
similarly-styled NAS systems.

#### Lower-Level Solutions

Much simpler solutions can be devised as needed. For example, a simple SMB share
can offer password-protected access to a shared storage location, and be available
from Linux and Windows machines alike. Suites like [Samba](https://www.samba.org/samba/)
take this a step further, offering more complete interoperability for storage, domain
integration, and more on Windows/Linux hybrid systems.

### Storage - Recommended Reading

1. Digital Ocean - [Storage Intro](https://www.digitalocean.com/community/tutorials/an-introduction-to-storage-terminology-and-concepts-in-linux)

## Lab Exercise

For this lab exercise, you will be using Ansible to install Samba in order to configure
a networked file share with password-protected access that is usable by the other
hosts on your network. Complete this portion on `host2` in your lab. Then, configure
your `host3` to use this share and ensure your admin user can read and write to it.
