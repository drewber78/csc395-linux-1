# Week 6

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

### Hosting - Recommended Reading

1. Cloudflare - Reverse Proxy [Definition](https://www.cloudflare.com/learning/cdn/glossary/reverse-proxy/)

## Lab Exercise

For this lab exercise, you will be configuring an internal web page served through
a reverse proxy. Use NGINX for your reverse proxy, and host it your controller box,
since it is the only VM available for outside connections. It should point to an
Apache webserver on `host3` that can host any basic site of your choice. A simple
HTML "Hello, world!" is an appropriate (albeit very boring) demo for this, but feel
free to use any website source code you've created as a part of another course/project
or make something interesting from scratch for this exercise. Anyone should be able
to access this site, given your public IP.
