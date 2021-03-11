# Week 8

## User Access

Computing systems are kind of pointless if they aren't used for anything, and no
one can use it for anything if they can't get in. In W4 we briefly mentioned VPN
services, which allow encrypted connections into a network from the outside.

### VPN

We will be providing a VPN entry point to our lab in order to complete our
simulation of a real system. VPNs are one of the most common ways for a system to
provide access to internal resources for outside users. There are plenty of providers
and systems that will offer VPN capabilities, but OpenVPN has years of open source
history, community support, and industry use. Even many commercial VPNs for privacy
are simply OpenVPN offered as a service!

### Something else...?

Systems are unique! Computing systems serve such a vast number of people in a broad
variety of contexts, and we can only begin to scratch the surface of that in a course
like this. For this reason, your last component will be one of your choice. Select
any networked application or service that is:

- Configured using Ansible
- Available to users in your lab (in this case, via VPN)
- Interactive in some fashion
  - A static website == not interactive (We already did this in W6!)
  - Interactive examples:
    - An API that users can hit
    - Dashboard that loads some bit of information about the lab
    - A database with some information in it that users can log into
  - **Note**: If you have trouble coming up with something, feel free to ask me and
    I can give you a starting point

## Lab Exercise

For this lab exercise, use Ansible to configure a VPN gateway using OpenVPN, as
well as at least one other app or service of choice that is accessible via VPN.
This can be anything as long as it is a private, network-accessible application
or service that a potential user can interact with when connected to the VPN. It
can be as trivial or as complex as you like as long as it is implemented correctly.
"Correct" implementation depends heavily on the component selected, but you will
have a chance to justify your implementation during your...

### System Presentation

You will be giving a presentation comprised of a system overview (components, features,
etc.) as well as a review of your experience configuring it (roadblocks, breakthroughs,
etc.) to the rest of the class. Although your systems will be very similar, based
on the nature of our exercises, the pathways and techniques you used to get there,
as well as your reflection on the experience, should be unique. This should take
about 5-10 minutes and will be given during the last instruction time slot.
