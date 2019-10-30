---
title: DNS Records
layout: post
---

A while back I was setting up a domain in a VPS. While adding configurations for the DNS, I came upon a list of different DNS record types such as CNAME, A, AAAA, etc. I wasn't clear as to the purpose of each record type, therefore I performed a little research to find out.

# What is a DNS, or how do I find Sarah Connar?

DNS stands for Domain Name System. The way it works is, when you go to `www.example.com`, the client needs to know which IP address the url connects to. The IP address is the main focal point of communication between the client and the server. To do this, the client has to perform a DNS lookup which acts as a directory of names that are matched with their ip addresses.

A real world analogy would be a phone book, or (if you're < 30 years old) the contacts list on your phone. If you want to call someone, let's say Kevin, you go to your contacts, search for kevin and you get the phone numbers. Easy! Also check out the first Terminator movie.

There is a bit more to DNS, but this post is about those wierdly named DNS records and what they do.

# A

This is the most basic type of DNS record which is used to point a domain or subdomain to an IP address.

| Type        | Host           | Value  | TTL |
| ------------- |:-------------:| -----:| -----:|
| A      | * | 104.123.12.12 | 600ms
| A      | @ | 104.123.14.14 | 600ms
| A      | test | 104.123.14.14 | 600ms

in the example table above, `*` and `@` hosts designate a wildcard root. Whereas `test` would designate a _test_ root E.g. test.example.com.

# CNAME

This maps a subdomain to another subdomain.

| Type        | Host           | Value  | TTL |
| ------------- |:-------------:| -----:| -----:|
| CNAME      | staging | test.example.com | 600ms

From the table above, the _staging_ host name connects to _test.example.com_, which is located at the IP address `104.123.14.14` found in the A record. CNAME provides the benefit of the server changing it's IP address without the browser or client needing to readjust their DNS records.

# MX

Are Mail Exchange (MX) records that are used to route emails. MX records have a priority attribute which identifies the priority to use each server.

| Type   | Priority     | Host           | Value  |
| ------------- |:-------------:| -----:|
| MX  | 1    | @ | aspmx1.google.com |
| MX  | 5    | @ | aspmx2.google.com |


<script>
    document.getElementById("general-development-link").classList.add("active");
</script>