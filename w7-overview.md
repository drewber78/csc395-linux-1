# Week 7

## Hosting

Internally accessible sites and services are important for nearly every private network.
Much like network accessible storage, being able to host private resources with controlled
access is a part of many system implementations. Our lab is no exception.

### Networked Applications

Networked applications use your private network to carry all sorts of information.
Monitoring software, collaboration tools like we discussed in W5, and more can all
be self-hosted and managed on your local network. Many of these tools can be centrally
managed and configured in the same fashion as our other lab components so far.

### Web Hosting

One of the easiest examples of these kinds of resources is a private webpage. Many
applications such as the collaboration suites mentioned above, NAS software, and
even more modern network infrastructure tooling offer web GUIs that are served either
directly from their host itself or through a reverse proxy. By managing both the
infrastructure as well as the applications that depend on it, we can offer unique
flexibility in their implementation based on our users' needs.

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

## Lab Exercise

For this lab exercise, you will be configuring an internal web page and OpenVPN server.
Run the webserver on `host3` and host any basic site of your choice. A simple
HTML "Hello, world!" is an appropriate demo for this, but feel free to use any website
source code you've created as a part of another course/project or make something
interesting from scratch for this exercise. Anyone should be able to access this
site, given access to your VPN. You should generate a profile through which I can
access your network in order to verify functionality.
