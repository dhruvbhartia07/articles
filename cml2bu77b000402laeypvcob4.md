---
title: "How Does a Browser Know Where a Website Lives?"
seoTitle: "How Browsers Locate Websites"
seoDescription: "Discover how browsers use DNS to find the correct server for a website. Learn about DNS records, including NS, A, CNAME, and MX records"
datePublished: Sat Jan 31 2026 13:07:36 GMT+0000 (Coordinated Universal Time)
cuid: cml2bu77b000402laeypvcob4
slug: how-does-a-browser-know-where-a-website-lives
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769864769138/9a41b3d8-efdc-4231-b547-7c1f5b44d3b0.png
tags: dns, devops, dns-records, web-infrastructure, networkingbasics, chaicode, internetfundamentals

---

When you type a website name like `example.com` into your browser, the browser somehow figures out **which server on the internet** actually hosts that website.

But how?

This is where **DNS** comes into play.

---

## What is DNS?

DNS (Domain Name System) is like a **phonebook for the internet**.

* Humans remember names like `google.com`
    
* Computers communicate using IP addresses like `142.250.183.14`
    

DNS helps **resolve domain names to their corresponding IP addresses**, so browsers know where to send requests.

DNS is **not a single system** replying with an IP address.  
There are **recursive calls made across multiple servers** to finally find the correct IP.

> If you’re interested in seeing this entire flow in action, you can check out this article:
> 
> [**How DNS Resolution Works**](https://dhruvbhartia07.hashnode.dev/how-dns-resolution-works-using-dig-to-see-whats-actually-happening)

---

## Why DNS Records Are Needed

Now here’s an important question:

> How does the recursive resolver know whether it has found the **actual website IP** or just the **next server it should ask**?

This is exactly why **DNS record types** exist.

Each DNS record type tells the resolver **what the response means** and **what to do next**.

---

## NS Record - Who Is Responsible for This Domain?

An **NS (Name Server) record** tells the resolver **where to look next**.

* NS records point the resolver toward the **authoritative name server**
    
* They do **not** return the website IP
    
* They tell the resolver:  
    → “You need to ask *this server* for more information about the domain”
    

In simple terms, NS records guide the resolver step-by-step until it reaches the server that has the final answer.

---

## A and AAAA Records - The Actual Address

Once the resolver finds these records, the search **stops**.

* **A Record** → IPv4 address of the website
    
* **AAAA Record** → IPv6 address of the website
    

These records contain the **actual IP address** of the domain.

When the resolver sees an A or AAAA record:

* It knows it has reached the destination
    
* It returns the IP address back to the browser
    

---

## CNAME Record - One Name Pointing to Another

A **CNAME (Canonical Name)** record is used to create **alias names**.

A common example:

* You host your website on Vercel
    
* Vercel gives you a subdomain
    
* You **don’t control the public IP**
    

So instead of pointing to an IP:

* Your domain uses a CNAME record
    
* It points to Vercel’s domain
    

What happens internally?

* The resolver sees the CNAME record
    
* It starts a **new lookup** for the target domain
    
* That lookup eventually resolves to an A or AAAA record
    

---

## MX Record - How Emails Find the Right Server

Email delivery works differently from web traffic.

That’s why **MX (Mail Exchange)** records exist.

* MX records specify **which server should receive emails**
    
* They help distinguish between:
    
    * Web servers
        
    * Mail servers
        

If MX records don’t exist:

* A records *can* be used
    
* But then the web server must also handle mail logic
    

To keep things simple and clean:

* MX records clearly define **mail routing**
    
* Web servers stay focused on serving websites
    

---

## TXT Record - Extra Information & Verification

TXT records are **not part of normal website routing**.

They store **extra information**, mostly for verification purposes.

Common use case:

* SSL certificate issuance
    
* Domain ownership verification
    

Flow:

* Certificate Authority (CA) asks for proof of domain ownership
    
* You add specific content to a TXT record
    
* CA checks the TXT record
    
* Certificate is issued if verification passes
    

---

## How All DNS Records Work Together (End-to-End Example)

Let’s put everything together.

Assume:

* You request a website
    
* There is **no cache**
    

Step-by-step flow:

1. Resolver asks the **root name server**
    
2. Root replies with an **NS record for the TLD**
    
3. Resolver queries the **TLD server**
    
4. TLD replies with an **NS record for the authoritative name server**
    
5. Resolver queries the **authoritative name server**
    
6. Authoritative server replies with a **CNAME record** mapped to Vercel
    
7. Resolver sees the CNAME and checks cache
    
8. Resolver queries TLD again to find authoritative server for Vercel
    
9. Resolver queries Vercel’s authoritative name server
    
10. Gets an **A record**
    
11. Resolver returns the IP to the browser
    

At this point, the browser finally knows **where the website lives**.