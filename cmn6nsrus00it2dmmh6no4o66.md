---
title: "I used to think Docker + systemd was enough"
seoTitle: "Why Docker + systemd Isn't Enough: Understanding Kubernetes "
seoDescription: "A practical reflection on why Docker and systemd alone aren't enough at scale, and how understanding their limitations makes Kubernetes finally make s"
datePublished: 2026-03-25T23:12:54.533Z
cuid: cmn6nsrus00it2dmmh6no4o66
slug: i-used-to-think-docker-systemd-was-enough
cover: https://cdn.hashnode.com/uploads/covers/62d3d651bc2c7a1dc67274f7/fbb904fa-500f-4407-bb35-99eb310cd03f.png
tags: docker, kubernetes, devops, containers, distributed-systems, systemd, cloud-native, ckad, cka, engineering-thinking

---

Around late 2019 / early 2020, I was working with setups where applications were running directly on VMs.

Each team had their own set of VMs, environments were split, CIDR ranges were being managed separately. Deployments were done using scripts/playbooks, which felt like mini package managers in their own way - it was quite a lot.

At that time, I remember having very basic questions:

why so many VMs?  
why can't we just run multiple apps on the same machine using different ports?

I didn't really have a clear answer back then. It just felt like "this is how it's done".

Around the same time, I had also started exploring Kubernetes.

So there were two things happening in parallel:

- seeing apps run on VMs in this structured but slightly heavy setup
- and learning Kubernetes, without fully understanding where it actually fits

I didn't connect these two at that point.

---

Recently in 2026, while preparing for CKA/CKAD, I found myself thinking about that phase again.

Back when I had just started exploring Kubernetes, I used to hear explanations like:

> "we can't use just Docker, we need Kubernetes as it makes the system reliable"

At that time, I interpreted it very literally.

Containers can go down.  
Kubernetes makes sure they come back up.

And somewhere in that, a very practical doubt came up:

if I can package an app in a container, and use something like systemd to restart it when it crashes.. isn't that enough?

So it would be like:

- container handles packaging
- systemd handles restarts

so what exactly is Kubernetes adding here?

I didn't push that thought very far.

I didn't have enough context, and over time it just faded.

> Experiment: Here is a github link with steps if anyone is interested: [lab - docker-systemd-reliability](https://github.com/dhruvbhartia07/devops-lab/tree/main/docker-systemd-reliability)

---

But recently, when I came back to that old thought, I tried to reason through it again.

Q. What if I need more than one instance?

-> Okay.. I can probably run multiple containers.

Q. What if they need to run on different machines?

-> Hmm.. maybe we need a proxy at each VM for that app, but the exact approach was unclear.

Q. What if one of those machines goes down?

-> Now it starts to resemble the old setup, where we can't do much without manual intervention.

---

These questions made me realize:

Earlier, I was thinking about how to run this app properly. My view was limited to Docker and systemd, which were right in front of me. I was just seeing it as an app and a server.

The setup itself isn't failing. It works at an individual level, but it doesn't really answer these new questions - the ones that go beyond a single machine.

---

And that's where Kubernetes started to make more sense - not as a tool or usage pattern, but in terms of the problem it is actually solving.

It is handling the part I wasn't even looking at earlier. For the questions above, it kind of fills that missing gap.

I have been using Kubernetes for some time now, learning and adapting it in my daily work:

I knew how to:

- deploy things
- debug issues
- check logs
- fix problems

And interestingly, those steps haven't really changed even now. What has changed is the depth and design that I see behind the same actions.

And on top of that, the idea of "run something and keep it alive on the machine" still exists - kubelet.

Kubelet is not exactly systemd + Docker and does a lot more, but a part of its responsibility still feels similar: making sure whatever is supposed to run is actually running on the node.

---

What has changed is how I see what's happening underneath.

Earlier, `kubectl` felt like a command.

Now it feels more like:

> I'm making an API call to a system

- auth details are stored in a context (kubeconfig)
- there's a control plane
- components talking to each other
- state being stored and reconciled
- decisions being made about where things should run

It all feels more real now, instead of just a tool or command line. The architecture and extensibility make more sense beyond just YAML.

---

It reminds me of how web development is taught.

At first, a browser is just:

> something that loads a webpage

Later you realize:

- there's a rendering engine
- networking layer
- JS engine
- parsing, reflow, painting

Same browser.  
Different understanding.

Feels like I've unlocked a deeper understanding of Kubernetes in a similar way.

---

And maybe that's why that old Docker + systemd thought came back.

Not because it was wrong.

But because now I can finally see where it fits and where it stops.
