## Building Microservices

After completing the Building Microservices book, I was inspired to create a comprehensive summary that encapsulates all of the essential points. Without further ado, here it is.

### Book Diagram

!['Image 00'](./assets/image03.png)

### What Are Microservices?

As introduced in Chapter 1, microservices are a type of service-oriented architecture that focuses on independent deployability. Independent deployability means that you can make a change to a microservice, deploy that microservice, and release its functionality to the end users without requiring other microservices to change. Getting the most out of a microservice architecture means embracing this concept. Normally, each microservice is deployed as a process, with communication with other microservices being done over some form of network protocol. It’s common to deploy multiple instances of a microservice, perhaps so that you can provide more scale, or else to improve robustness by having redundancy.

To deliver independent deployability, we need to make sure when changing one microservice that we don’t break interactions with other microservices. This requires that our interfaces with other microservices are stable, and that changes be made in a backward-compatible way. Information hiding, which I expanded on in Chapter 2, describes an approach in which as much information as possible (code, data) is hidden behind an interface. You should expose only the bare minimum over your service interfaces to satisfy your consumers. The less you expose, the easier it is to ensure the changes you make are going to be backward compatible. Information hiding also allows us to make technological changes within a microservice boundary in a way that won’t impact consumers.

One of the key ways we implement independent deployability is by hiding the database. If a microservice needs to store state in a database, this should be entirely hidden from the outside world. Internal databases should not be directly exposed to external consumers, as this causes too much coupling between the two, which undermines independent deployability. In general, avoid situations in which multiple microservices all access the same database.

Microservices work very well with domain-driven design (DDD). DDD gives us concepts that help us find our microservice boundaries, with the resulting architecture being aligned around the business domain. This is extremely helpful in situations where organizations are creating more business-centric IT teams. With a team focused on one part of the business domain, it can now take ownership of the microservices that match this part of the business.

### Moving to Microservices

Microservices bring a lot of complexity—enough complexity that the reasons for using them need to be seriously considered. I remain convinced that a simple single process monolith is a totally sensible starting point for a new system. Over time, though, we learn things, and we start to see the ways in which our current system architecture is no longer fit for purpose. At that point, looking to change is appropriate.

It is important to understand what you are trying to get out of a microservice architecture. What is the goal? What positive outcome do you expect a shift to microservices to bring? The outcome you are aiming for will directly impact how you break your monolith apart. If you are trying to change your system architecture to better handle scale, you’ll end up making different changes than if your main driver is to improve organizational autonomy. I cover this more in Chapter 3, and in even more detail in my book Monolith to Microservices.

Many of the problems with microservices are evident only after you hit production. Therefore, I strongly recommend an incremental, evolutionary decomposition of an existing monolith rather than a “big bang” rewrite. Identify a microservice you want to create, extract the appropriate functionality from the monolith, deploy the new microservice into production, and start using it in anger. Based on that, you’ll see if you are helping move toward your goal, but you’ll also learn a lot that will make the next microservice extraction easier—or perhaps it will suggest to you that microservices might not be the way forward after all!
