# Week 3

## Security

Systems security is a complex, multifaceted area of our work that involves a variety
of skills and techniques that take time to develop, and which are constantly evolving.
That being said, there are certain simple things that can be done in almost any
case to improve the security of our systems from bad actors, from both inside and
outside of our organizations.

### Account Security

Securing accounts, and thereby their associated permissions, is an important step
on the road to system security. By locking down elevated permissions to a select
set of accounts, restricting access to these accounts through auditable pathways
for authorized users, and regularly self-auditing through whatever tooling is appropriate,
we can set a solid baseline.

#### Automating Account Security - Examples

We can use Ansible to...

- Set password complexity requirements
- Disable empty passwords
- Set password change policies
- Establish security groups for elevated permissions (sudoers, etc.)

### File System Security

Securing sensitive files and directories (such as personal or system files) with
the appropriate levels of restriction is another way to protect both your system
itself, as well as the safety and privacy of those using it. By automating these
sorts of access policies, we gain not only the peace of mind that comes with well-protected
information, but also the documentation of these practices that many systems lack.

#### Automating File System Security - Examples

We can use Ansible to...

- Restrict access to users' personal files
- Modify system files as needed through a secure pipeline
- Back up configuration files as they are changed
- Restrict access to sensitive system files
- Establish security groups for access to shared locations

### Network Security

Network security is often our first line of defense against external bad actors.
For someone to affect your system, they must first reach it; preventing this in
the first place makes many of our other forms of security redundant (but still
necessary!) in these cases. Because many forms of network infrastructure can be
managed as a part of a Linux environment, using the same tooling and practices,
we can secure our infrastructure and endpoints without straying too far.

#### Automating Network Security - Examples

We can use Ansible to manage nearly every aspect of our networking, including...

- Network infrastructure (e.g. DNS servers, DHCP servers, routing, etc.)
- Networked device access daemons settings (e.g. `sshd` config)
- Local interface settings
- Firewall rules

### Security Tooling

A wide variety of security tooling is available, ranging from traditional antivirus
to adaptable, multi-faceted threat detection. A classic example for many Linux use
cases is `fail2ban` which watches your local log files for connections exhibiting
potentially malicious behaviour and then blocks these connections automatically based
on your configured policies. Tooling like this that can monitor and self-remediate
in potentially dangerous situations, when combined with vigilant monitoring and auditing
practices, can offer some of the strongest security baselines available. Depending
on your needs in a real-world use case, other tools may be more suitable or further
security steps may need to be taken in context.

### Security Automation - Recommended Reading

1. The Linux Documentation Project's [Security HOWTO](https://tldp.org/HOWTO/html_single/Security-HOWTO/)
   - Specifically:
     - Chapter 4: [Local](https://tldp.org/HOWTO/html_single/Security-HOWTO/#local-security)
     - Chapter 5: [Files and File Systems](https://tldp.org/HOWTO/html_single/Security-HOWTO/#file-security)
     - Chapter 6: [Passwords and Encryption](https://tldp.org/HOWTO/html_single/Security-HOWTO/#password-security)
     - Chapter 8: [Network](https://tldp.org/HOWTO/html_single/Security-HOWTO/#network-security)
     - Chapter 9: [Security Preparation](https://tldp.org/HOWTO/html_single/Security-HOWTO/#secure-prep)
2. OpenStack Ansible Hardening [Docs](https://docs.openstack.org/ansible-hardening/latest/)

## Lab Exercise

There is a well-maintained Ansible role for hardening of Linux systems from the
open source project [OpenStack](https://www.openstack.org/) available [here](https://github.com/openstack/ansible-hardening)
that bases its practices on the Security Technical Implementation Guides (STIGs)
from the Defense Information Systems Agency (DISA) and maintains implementations
for a variety of popular and widely supported distributions. Due to compatibility
issues of the latest in-development version, I have made a fork for this course.
For this exercise, configure this role to be applied to all of your lab hosts and
ensure that it can be applied uniformly as a part of your configuration. You will
need to specify that the role use the appropriate `stig_version` (because DISA uses
RHEL instead of Ubuntu, ours is `rhel7`) in order for the role to apply without an
error. Since this role includes a secure baseline, you can remove any existing `sshd`
hardening steps at this time to avoid duplication of work.

Roles often come with optional settings that can be activated via optional variables
in your implementation. After you have applied this role, you should activate some
of its optional features; specifically:

- use the existing password quality settings, but enforce them on set/change
- set a maximum password lifespan of 90 days to force rotation (without ever having
  to do it during this course, of course).
