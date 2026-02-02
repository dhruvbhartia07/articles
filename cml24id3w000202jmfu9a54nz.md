---
title: "Understanding Network Devices: How the Internet Reaches Your Device"
seoTitle: "How Internet Connects to Your Device"
seoDescription: "Explore how your internet requests travel through modems, routers, switches, firewalls, and more to reach devices securely and reliably"
datePublished: Fri Jan 30 2026 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: cml24id3w000202jmfu9a54nz
slug: understanding-network-devices-how-the-internet-reaches-your-device
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769852391731/1a56f71a-09ac-414b-8b57-6e5a5c109839.png
tags: router, devops, networking, system-design, load-balancer, firewall, computer-networks, switch, backend-engineering, network-fundamentals

---

We all use the internet today.

The most common way is via **Wi-Fi or mobile data**, with Wi-Fi being the most prominent.  
Ever wondered how your device actually gets that Spotify song, YouTube video, or even shows you this particular blog?

It often feels like we are in a direct connection with Spotify or YouTube from our system - but that’s not the case.

There are **multiple layers and multiple devices** involved before a request from your device reaches a server and comes back with a response.

It’s also not that we weren’t connected to the world before the internet. We already had means like **telephones and cable TV**.  
The internet is just another medium - one that expanded the horizon of what kind of data can be shared over an existing connection to the world.

Let’s break down the key devices that make this entire journey possible.

---

## Modem - Translating Languages Between Worlds

In the earlier days of the internet, computers were connected using **telephone lines**:

```plaintext
Telephone Line → Modem → Ethernet Cable → Computer
```

We already had telephone connections with companies that were well connected across regions and countries.  
The only issue was the **language of communication**.

* Telephone lines understood **analog signals**
    
* Computers spoke in **digital signals**
    

Telephones didn’t transmit our voice as-is.  
The microphone converted sound into **analog signals**, sent them over the wire, and the receiver converted them back into sound.

Computers needed something similar - a way to convert their digital data into a form that telephone wires could understand.

This is where the **modem** came into existence.

A **Modem (Modulator–Demodulator)**:

* Converts **digital signals → analog signals**
    
* Converts **analog signals → digital signals**
    

This translation allowed computers to communicate using existing telephone infrastructure.

---

## Router – Making Sure Traffic Reaches the Right Device

As time passed, the number of devices increased and **Wi-Fi came into existence**.

Now a single household might have:

* Phones
    
* Laptops
    
* TVs
    
* Tablets
    

We can’t give each device its own internet connection like mobile phones do with SIM cards.

So the question became:

> How do we connect multiple devices using a single internet connection?

If a single device is requesting data, it’s easy.  
But with multiple devices, we need a way to **identify who requested what**.

Imagine:

* You are watching a football match
    
* Someone else in your home is watching cricket
    
* Suddenly you start getting the cricket stream
    

That’s exactly what a **router prevents**.

A router:

* Keeps track of devices
    
* Ensures responses go back to the **same device that requested them**
    

This routing logic isn’t limited to homes.  
Routers exist **at all levels of the internet**, connecting one logical network to another.

We’ll revisit this idea again later.

---

## Router vs Modem – Do Routers Replace Modems?

It often feels like routers have replaced modems.

We commonly say:

> “I have a fibre Wi-Fi router at home”

That statement is *partially true*.

If we recall what a modem actually does - **signal translation** - we’ll realize that routers never took over that responsibility.

* A router manages and routes traffic (like a traffic policeman)
    
* A modem translates signals so they can travel over physical media
    

What changed is **integration**.

Today:

* Signal translation happens using **light signals over fibre**
    
* This role is handled by something called an **ONT**
    
* The modem functionality is **hidden inside the same device**
    

The idea remains the same - there is still a translator.

Analogy:

* Earlier: a human translator
    
* Now: Google Translate
    

Both do the same job; the implementation evolved.

So:

* **Modem and router both exist**
    
* They just live inside the same physical device in most homes today
    

---

## Switch and Hub - Local Network Communication

So far, we’ve talked about **connecting to the internet**.

But sometimes we only need **local communication**, within a limited area like:

* An office
    
* A data center
    
* A home network
    

For this, we use **switches and hubs**.

Routers *can* do this, but they are **overkill**.

A simple analogy:

* Finding an item directly in a box
    
* Versus opening a box, finding another box, and then finding the item
    

Switches are **Layer 2 (L2)** devices  
Routers are **Layer 3 (L3)** devices

More layers = more processing.

### Hub

A hub is like a **railway station announcement**.

* Any message sent is broadcast to **all ports**
    
* Every connected device receives it
    
* Even if the message is meant for just one device
    

### Switch

A switch is a **smart hub**.

* It knows which devices are connected to which ports
    
* Sends data **only to the intended recipient**
    

Analogy:

* Hub → General announcement at a railway station
    
* Switch → Airport announcements made for a specific gate
    

This makes switches faster and more efficient for local networks.

---

## Firewall – Where Security Lives

Until now, we assumed:

* We send data
    
* Others receive it willingly
    

But what if:

* Someone accesses data you never intended to share?
    
* Someone sends commands to your device from anywhere in the world?
    

These are real problems.

Devices often respond to commands **by default** once they receive them.

That’s why we add **security layers**, such as:

* Firewall
    
* IDS / IPS
    
* IAM
    
* WAF
    
* Antivirus
    
* SIEM
    

A **Firewall** is one of these mechanisms.

Firewalls can operate at:

* Layer 3
    
* Layer 4
    
* Layer 7
    
* Or combinations of these
    

Analogy:

* Some guards check badges
    
* Some check bags
    
* Some even listen to conversations
    

In general, when we say *firewall*, we usually mean **L3 / L4 firewalls**.

They:

* Check source and destination IP
    
* Check ports
    
* Check protocol type
    
* Track connections
    

This is why blindly disabling firewalls or allowing all traffic - just because a tutorial said so - is dangerous.

Your app might not be malicious, but opening everything can allow **malicious actors** into your system.

Security helps keep your application **available and running**.  
But availability isn’t only about security - which brings us to the next component.

---

## Load Balancer – Handling Scale and Availability

Think about:

* A small local shop
    
* A large supermarket
    

Now imagine two groups of 1000 people:

* Group A goes to the supermarket
    
* Group B goes to the local shop
    

Who gets served faster?

Most likely, **Group A**.

Why?

Supermarkets have:

* Larger area
    
* Well-defined sections
    
* Multiple entry and exit points
    
* Multiple billing counters
    

Local shops:

* Small space
    
* Single entry/exit
    
* One billing counter
    

Local shops aren’t badly designed - they just aren’t meant to serve **large traffic at the same time**.

Now imagine:

* A supermarket with multiple billing counters
    
* But everyone lines up at a single counter
    

That defeats the purpose.

To fix this, we need someone directing people to different counters.

That person is the **Load Balancer**.

A load balancer:

* Sits in front of backend servers
    
* Distributes incoming traffic across multiple instances
    

Scaling backend servers alone isn’t enough.  
Users don’t know:

* Which instance exists
    
* Which instance is free
    
* Which instance is overloaded
    

So users always hit the **load balancer**, and it decides where the request should go.

Load balancers use different algorithms depending on needs and intelligence required.

---

## How Everything Works Together – End-to-End Flow

Let’s trace how your request reached this blog.

Assume you are reading this from your office computer.

### Flow

1. Open the browser
    
2. Enter the URL
    
3. Request goes via Ethernet connection to the **switch**
    
4. Switch forwards it to the **router** (where modem translates the signal)
    
5. Router sends the request to the **ISP**
    
6. Request passes through multiple routers
    
7. Reaches the ISP router of the hosting server
    
8. Router routes and translates the signal back to digital
    
9. Traffic goes to the **switch**
    
10. Switch sends it to the **server**
    
11. Server hosts a **load balancer**
    
12. Load balancer routes request to the appropriate backend server
    

The internal LAN and switches may be physical or virtual, and may not map 1:1 - but the **logic remains the same**.

---

## Sum Up

All these devices:

* Modem
    
* Router
    
* Switch
    
* Hub
    
* Firewall
    
* Load Balancer
    

Are interesting in their own way and deserve deeper dives.

This write-up was meant to **touch upon their responsibilities**, how they differ, and how they work together to deliver something as simple as this blog to your screen.