# Addresses and Routing

## Overview

Every device on a network needs an address so data knows where to go. Two kinds of address work together: an IP address for the final destination, and a MAC address for each hand-off along the way. Routers use the IP address to choose the next step of the journey.

---

## Key Concepts

### IP addresses

- **IPv4** (`192.168.0.5`): four numbers called octets, each from 0 to 255. About 4.3 billion addresses, which are running out.
- **IPv6** (`2001:0db8:85a3::8a2e:0370:7334`): hexadecimal, separated by colons, with practically unlimited addresses.
- Dots mean IPv4; colons mean IPv6.

### IP vs MAC

| | IP address | MAC address |
|---|---|---|
| Job | final destination | next device to hand the data to |
| Scope | the whole internet | the local network only |
| Changes during the journey? | no | yes, at every hop |
| OSI layer | 3 (Network) | 2 (Data Link) |
| Set by | the network | the hardware |

Moving from home to work Wi-Fi gives a device a **new IP but the same MAC**.

### Routing

- A **router** forwards traffic towards its destination, one hop at a time.
- At each hop, it checks its **routing table** against the destination IP address.
- **Static** routes are entered by hand; **dynamic** routes are learned and updated automatically when a path fails.
- **OSPF** builds routes **inside** one organisation's network; **BGP** connects **separate** networks and holds the internet together.

---

## Commands Practised

Addresses I saw for real while running a Flask app:

```
Running on http://127.0.0.1:5003      # localhost: this machine only
Running on http://172.19.148.177:5003 # Ubuntu's IP on WSL's internal network
```

And inside Docker, from `docker logs myapp`:

```
Running on http://172.18.0.3:5003     # the container's own IP on my custom network
"GET / HTTP/1.1" 200                  # request arriving from 172.18.0.1, the network's gateway
```

---

> [!WARNING]
> `192.168.1.256` is not a valid address. Each octet stops at 255.

> [!IMPORTANT]
> The router reads its **routing table**. OSPF and BGP are how that table gets built and updated, not what the router checks for each packet.

---

## Reflection

The parcel picture made IP vs MAC stick: the address on the parcel never changes, but the courier handing it on changes at every depot. Seeing real container IPs in logs later made the addresses concrete rather than theoretical.

⬅️ [Back to Fundamentals](./)
