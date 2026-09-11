**P R O D U C T S E C U R I TY L E A D**

# **Threat-model the platform behind a city's intersections**

**Time cap 3 hours AI use expected**

## **Your goal**

Build a threat model for X platform.

Read the system description below, tell us where you'd focus your first three months of security work, and design one AI-assisted capability that would help you do part of it.

We're not looking for a finished audit. We're looking for your reasoning, your priorities, and the tools you reach for.

## **How our system works**

Every signalized intersection has a **signal controller** —a box in a metal cabinet at the roadside that decides which direction gets a green light and for how long. On its own, it usually runs a fixed timer that ignores what's actually on the road.

&#x20;X  adds two pieces of hardware. **Sensor Units** with a camera and a radar mounted on the poles and watch the intersection: detect cars, buses, cyclists, and pedestrians. A **Nexus Unit** - a device that sits inside the cabinet, turns what the sensors see into signal timing decisions, tells the controller what to do, and interacts with the cloud.

The Nexus Unit stays connected over cellular to the **Mobility OS (MOS)** , our customer-facing web platform where city traffic engineers work in. MOS allows the end users to use different applications enabled by our edge units. A second web application, the **NOC** , is where our own operations team monitors fleet health and manages edge devices.

So: sensors that see, a unit in the cabinet that decides, a controller that switches the lights, and a cloud that configures and watches all of it.



<!-- Start of picture text -->

EDGE — INTERSECTION CLOUD<br>Sensor Units<br>on the poles · see the road<br>MOS<br>city traffic engineers<br>cellular uplink<br>Nexus Unit<br>in the cabinet · decides timing telemetry up · config \& firmware down<br>NOC<br>our operations team<br>Signal controller<br>third party · switches lights<br><!-- End of picture text -->

Where the work lives: the hardware went through threat modeling during its design, and it changes slowly. What changes much more dynamically is the cloud platform - the two applications on top of it, and the pipeline that configures and updates the fleet. That's where we'd expect your plan to focus—treat the fleet as something the cloud commands.

### **What the cloud side involves**

City staff sign in through a managed identity provider, with role-based access—traffic engineers, field technicians, and read-only viewers

The NOC application is internal and reaches across the whole fleet

Cloud services run in containers on Kubernetes (EKS) in AWS, alongside managed databases. Every customer is an isolated tenant

The edge software also runs in containers on the Nexus Unit, updated remotely from the cloud

Cloud deployments run through a standard CI pipeline. Changes reach the fleet through a separate tool we built in-house

We're not looking for a Kubernetes hardening checklist. Assume we've done the obvious things, and tell us what worries you about this system.

## **What to send us**

### **Threat model**

> \*\*PART\*\* Two pages at most, in whatever format you like. Work from the system above and 

> \*\*ONE\*\* tell us where you'd spend your first three months. 

The attack surfaces you consider most exposed, and why

Your top handful of risks, ranked—with your reasoning for the ranking

What you'd deliberately leave for later, and what makes that acceptable

Anything you'd need to ask us before committing to the plan

### **Design the first thing you'd automate**

**PART TWO**

Pick one risk from Part one and design an AI-assisted capability to help you cover it. Half a page. Don't build it—we're interested in the design, not the code.

What it looks at—code, configuration, alerts, tickets, telemetry—and where it sits in the workflow

How it decides what's worth a human's attention

How you'd know it's working, and how you'd catch it quietly failing

What you'd never let it decide on its own

### **Show how you used AI**

##### **PART THREE**

You used AI to produce the two parts above. Tell us how — half a page of notes, plus the prompts or agent setup if you kept them.

Where it was genuinely useful, and where it wasn't

What it got wrong, and how you caught it

What you'd do differently with more time

**W H AT H A P P E N S N E X T**

After receiving your work we will schedule an in-person review session - you walk us through what you sent; we ask questions.

#### **When you're done, send your assignment back to the same email address you got it from.**



