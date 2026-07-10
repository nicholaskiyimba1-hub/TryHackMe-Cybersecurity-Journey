# TryHackMe: Cloud Computing Fundamentals (Computer Fundamentals Module)

**Room:** Cloud Computing Fundamentals
**Module:** Computer Fundamentals
**Difficulty:** Beginner
**Write-up by:** Nicholas Kiyimba
**Platform:** TryHackMe

## Why This Room Exists

The room opened with a scenario I could actually picture: I build an app that helps students practice cyber security, and I host it on my own computer in my own country. What happens when someone from another country tries to use it and it lags? What happens if many students connect at once, or my computer is simply turned off? At that point, my app cannot grow. Cloud computing exists to solve exactly this kind of problem.

I also learned that the cloud is not a separate new thing on its own. It is built on top of virtualization and containers, the same technologies from the previous room. The cloud uses these to run many applications efficiently on shared infrastructure, and to create or change environments quickly whenever needed.

## What I Learned

* What cloud computing actually is
* The service models of cloud computing: IaaS, PaaS, SaaS
* The cloud types: Private, Public, Hybrid
* The benefits of cloud computing
* How big companies use the cloud in the real world

## How We Got to the Cloud

Cloud computing did not appear overnight. It is the result of years of businesses trying to cut costs, use their resources better, and make applications easier to run and scale. It evolved step by step from physical servers all the way to the cloud model used today.

## Why the Cloud Is So Widely Used

The cloud was built to fix the same old problems: limited capacity, high cost, and slow growth. These are the benefits I want to remember clearly, since they are the kind of thing that shows up directly in exam questions:

* **Scalability:** I can scale my application up or down easily as demand changes.
* **On-demand self-service:** I can create or remove servers and storage instantly, with no waiting for physical hardware.
* **Pay only for what you use:** I get charged based on actual usage, not a big upfront cost.
* **Security:** The cloud provider protects the underlying infrastructure with strong security measures.
* **High availability:** My application keeps running even if part of the system fails.
* **Global access:** Users anywhere in the world can reach my application.

In simple terms, the cloud makes IT resources flexible, cost-effective, and easier to manage.

## Cloud Deployment Types

This is about where the cloud environment lives and who has access to it.

* **Public Cloud:** Shared cloud infrastructure, used by startups, websites, and global apps because it is affordable, scales easily, and needs no infrastructure management on my side. This is the most common type of cloud deployment used today.
* **Private Cloud:** Built for a single organization, used by banks, healthcare, and government bodies because it gives more control, customization, and compliance for sensitive data.
* **Hybrid Cloud:** A mix of both, used by companies like e-commerce platforms that need to keep sensitive data private while still being able to scale publicly during high demand periods, like a big sale.

## Cloud Service Models

This is about how much control and responsibility I have versus how much the provider handles for me. I found it easiest to remember using the renting analogy from the room.

* **Infrastructure as a Service (IaaS):** I rent the basic building blocks, like virtual servers, storage, and networking. I am responsible for the operating system and my application, while the provider only manages the physical hardware underneath.
* **Platform as a Service (PaaS):** The provider manages both the infrastructure and the operating system for me. I only focus on building, deploying, and running my application, without worrying about servers at all.
* **Software as a Service (SaaS):** I just use a finished application over the internet. The provider manages everything end to end, and I access it through a browser or app. Gmail and Zoom are good examples of this.

A quick way I remember this: IaaS gives me the most control and the most responsibility, PaaS is the middle ground, and SaaS gives me the least control but the least responsibility too, since I am just the end user.

## Major Cloud Vendors

Amazon Web Services (AWS) is the clear industry leader, with the largest range of services and the widest global reach. Other major providers I should know by name:

* **Microsoft Azure:** Strong in enterprise and hybrid cloud setups.
* **Google Cloud Platform (GCP):** Known for data analytics, AI, and machine learning tools.
* **Alibaba Cloud:** A major player in Asia with competitive global offerings.
* **IBM Cloud:** Focused on hybrid cloud and AI-driven solutions.
* **Oracle Cloud:** Focused on enterprise applications and databases.

## Real Companies Using the Cloud

Seeing real examples made this stick better for me than just reading definitions:

* **Netflix** runs its whole platform on AWS so it can scale globally and stream reliably to millions of people at once.
* **Spotify** uses the cloud to manage millions of songs and users, scaling fast whenever new music or features launch.
* **Instagram** relies on the cloud to store huge amounts of photos and videos and deliver them quickly worldwide.
* **Online stores** use the cloud to absorb traffic spikes during events like Black Friday, without needing to own permanent extra infrastructure all year round.

The common thread across all of these: the cloud lets them scale easily, cut costs, stay reliable, and spend their time improving their product instead of managing physical hardware.

## Hands On Practice: Deploying My Own Cloud Environment

The second part of the room let me actually deploy a cloud environment for my own cyber security training app, using an interface similar to AWS.

**Basic terms I needed first:**
* **EC2:** represents a virtual computer in the cloud. It has its own CPU and RAM and can run applications, just like a real computer. Adding an EC2 instance means adding a new computer to my environment.
* **Instance Type** (like t2, t3, m5): describes how powerful that virtual computer is. Bigger instance types mean more power but higher cost, and smaller ones mean less power but lower cost.

**What I built:**
This matched the IaaS model I had just learned, since cyber security practice usually needs full access to the operating system to install tools and safely simulate attacks and defenses.

I first picked a region, which represents the geographic location where my resources would live, such as Europe or North America.

Then I created three EC2 instances:

* `application-interface`, using a small t3.micro instance, since it only needed to serve the app interface.
* `study-machine-1`, using a more powerful m5.large instance, meant for practicing cyber security skills.
* `study-machine-2`, also an m5.large instance, for the same purpose.

**Managing cost:**
I then checked the Billing section to see what each instance was costing. Since the app was still in development and had no real users yet, I stopped both study machines to save cost, and confirmed the total cost dropped considerably right after.

This part really drove home why "pay only for what you use" is such a big deal in the cloud. I could directly see the cost go up when machines were running and go down the moment I stopped them.

## Key Terms I Want to Remember

* **Public Cloud:** Cloud services accessed over the internet and shared by many people and companies.
* **Private Cloud:** A cloud built for one company only, giving more control and security.
* **Hybrid Cloud:** A mix of public and private clouds that work together and share data.
* **IaaS:** Renting basic computer parts like servers and storage from the cloud.
* **PaaS:** A ready-to-use environment to build and run apps without managing servers.
* **SaaS:** Ready-made software used online without installing anything.
* **EC2:** Amazon's cloud computers that I can quickly create, use, and resize as needed.

## Benefits of Cloud Computing I Want to Remember

* Scalability
* On-demand self-service
* Pay only for what you use
* Security
* High availability
* Global access

## Why This Matters To Me

This room turned cloud computing from a buzzword into something I actually understand the mechanics of, from picking a region to launching instances to watching billing change in real time. It also builds directly on virtualization, which makes sense since the cloud is really just virtualization and containers offered as a service at a massive scale.

---
*This write-up documents my own progress through TryHackMe as I work through the Computer Fundamentals module, written in simple language for my own future review and certification exam preparation.*
