# Networking Fundamentals — Reflection

## Introduction

In the past, I thought I had a good idea of how the internet works. My idea
was that it is like a giant library where I go up to the counter and ask the
librarian for a book (information), and they would go and search for it and
bring it back once it has been found. I now believe that with that idea I
was barely scratching the surface. The internet is much more detailed,
distributed, and frankly astonishing. After learning how it truly works, it
feels more like a living organism where everything is connected one way or
another.

## The DNS System

The fact that the internet has its own "phone book" is simply remarkable.
Before, I thought that when I searched for something like Gmail or
Instagram, the network already knew exactly where it was, with no searching
required. In reality, it is more of a chain of events that takes place.

It starts with the local cache — if the address is stored there, the
computer simply pulls it from there. If not, it reaches out to a DNS
resolver, which contacts a root nameserver. The root nameserver directs the
request to the appropriate Top-Level Domain (TLD) server (such as `.com` or
`.org`), which in turn points to the service's own authoritative nameserver
(Google's, Instagram's, etc.), which finally returns the actual IP address.

The most fascinating part is that all of these steps happen in
milliseconds, even if the website being searched for is on the opposite
side of the globe.

## IP Addressing and Routing

I used to imagine the data travel process like sending a letter at the post
office — the mail (information) would be sent as one piece. On the
internet, however, it works differently. Data is broken into smaller pieces
called packets, and each packet is stamped with the source IP address and
the destination IP address. The packets then travel through junctions
called routers, and along the way each packet may take a different route to
reach the destination. Once they all arrive, they are reassembled into the
complete, original information.

What is also striking is that there is no single central controlling point
through which all information flows. Instead, data spreads across a network
of routers that independently make forwarding decisions by following
protocols such as BGP (Border Gateway Protocol). This decentralised design
makes the internet resilient — it can route around failures automatically.

## HTTP / HTTPS

Reaching a webpage is a structured "conversation" between my browser (the
client) and a remote machine (the server). When I type a web address into
the browser, my browser sends an HTTP request to the server, which responds
with a status code and the requested content.

I already knew that the "S" in HTTPS stands for Secure, but I had only a
vague sense of what that actually meant. Now I understand that before any
real data is exchanged, a TLS handshake takes place. This process
establishes an encrypted connection between the browser and the server.
Digital certificates are used to verify each party's identity, ensuring the
connection is authentic and that the data cannot be read by anyone
intercepting it. All of this happens within a fraction of a second.

## The Full Picture

When I type a URL and press Enter, a well-constructed sequence of events is
triggered:

1. DNS resolution converts the domain name into an IP address.
2. My browser opens a TCP connection to that IP address (via the three-way
   handshake: SYN → SYN-ACK → ACK).
3. If HTTPS is used, a TLS handshake encrypts the connection.
4. My browser sends an HTTP GET request to the server.
5. The server processes the request and sends back an HTML response.
6. My browser parses the HTML, discovers additional resources (CSS, images,
   scripts), and fires off further requests for each one.
7. All the pieces are assembled and the page appears on screen.

Probably the most surprising part for me was realising that these
back-and-forth requests can happen dozens or even hundreds of times — all
within the blink of an eye.

## Conclusion

The beauty of the internet lies in how precisely it has been put together —
piece by piece, protocol by protocol — yet it all works together as one
robust, fast, and global system. The internet is not magic; it is a
well-constructed engineering achievement, built to allow everyone to
connect with one another and to learn.
