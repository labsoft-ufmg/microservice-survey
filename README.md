# Microservice Study
## A Survey About Microservice Usage

  - ### Search String: "Microservice Architecture"
  
| DOC 1 | Microservices: a definition of this new architectural term |
| ------ | ------ |
| Access date| May-2017 |
| URL | https://martinfowler.com/articles/microservices.html |
| Authors | James Lewis, Martin Fowler |

```sh
The term 'microservice' has been used to describe a particular way of designing software applications as
suites of independently deployable services.
```

```sh
The microservice architectural style is an approach to developing a single application as a suite of small
services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource 
API
```
```sh
Componentization via services. Component is a unit of software that is independently replaceable and 
upgradeable).
```

```sh
Another consequence of using services as components is a more explicit component interface. 
Most languages do not have a good mechanism for defining an explicit Published Interface. 
Services make it easier to avoid this by using explicit remote call mechanisms.
```
```diff
- Remote calls are more expensive than in-process calls, and thus remote APIs need to be coarser-grained, 
-which is often more awkward to use
```
```sh
The microservice approach to division is different, splitting up into services organized around business 
capability. Consequently the teams are cross-functional, including the full range of skills required for 
the development: user-experience, database, and project management.
```

```diff
-The biggest issue in changing a monolith into microservices lies in changing the communication pattern. A naive 
-conversion from in-memory method calls to RPC leads to chatty communications which don't perform well. Instead 
-you need to replace the fine-grained communication with a coarser -grained approach.
```
```sh
Decentralized Governance. We prefer using the right tool for the job
```
```diff
-Decentralized Data Management: Distributed transactions are notoriously difficult to implement and as a 
-consequence microservice architectures emphasize transactionless coordination between services.
```
```diff
-A consequence of using services as components, is that applications need to be designed so that they can 
-tolerate the failure of services. Any service call could fail due to unavailability of the supplier. 
-This is a disadvantage compared to  a monolithic design as it introduces additional complexity to handle it.
```


| DOC 2 | Pattern: Microservice Architecture |
| ------ | ------ |
| Access date| May-2017 |
| URL | http://microservices.io/patterns/microservices.html |
| Author | **Chris Richardson**: Experienced software architect, author of POJOs in     Action and the creator of the original CloudFoundry.com |

```sh
An architecture that structures the application as a set of loosely coupled, collaborating services. Each
service implements a set of narrowly, related functions. Services communicate using either synchronous 
protocols such as HTTP/REST or asynchronous protocols such as AMQP. Services can be developed and deployed 
independently of one another.
```

```diff
+Each service can be deployed independently of other services - easier to deploy new versions of services 
+frequently
```
```diff
+Easier to scale development.
```

```diff
-Developers must deal with the additional complexity of creating a distributed system and testing is more 
-difficult.
```

| DOC 3 | What are microservices? |
| ------ | ------ |
| Access date| May-2017 |
| URL | https://opensource.com/resources/what-are-microservices |

```diff
+ When the different components of an application are separated, they can be developed concurrently. 
```

```diff
+Components can be spread around multiple severs or even multiple data centers.
```


| BLOG 1 | Introduction to Microservices |
| ------ | ------ |
| Access date| May-2017 |
| URL | https://www.nginx.com/blog/introduction-to-microservices/ |
| Author | **Chris Richardson**: Experienced software architect, author of POJOs in     Action and the creator of the original CloudFoundry.com |

```sh
A service typically implements a set of distinct features or functionality, such as order management, customer management, etc.
```

```sh
The Microservices Architecture pattern significantly impacts the relationship between the application and the database. Rather than sharing a single database schema with other services, each service has its own database schema.
```

```sh
One way to think about the Microservices Architecture pattern is that it’s SOA without the commercialization and perceived baggage of web service specifications (WS‑*) and an Enterprise Service Bus (ESB). Microservice‑based applications favor simpler, lightweight protocols such as REST, rather than WS‑*. They also very much avoid using ESBs and instead implement ESB‑like functionality in the microservices themselves. The Microservices Architecture pattern also rejects other parts of SOA, such as the concept of a canonical schema.
 ```
 
 ```diff
+Individual services are much faster to develop, and much easier to understand and maintain.
```

```diff
+This architecture enables each service to be developed independently by a team that is focused on that service. The developers are free to choose whatever technologies make sense. This freedom means that developers are no longer obligated to use the possibly obsolete technologies that existed at the start of a new project.
```
```diff
+Microservices Architecture pattern enables each microservice to be deployed independently. 
```
```diff
+The Microservices Architecture pattern enables each service to be scaled independently.
```
```diff
-A major drawback of microservices is the complexity that arises from the fact that a microservices application is a distributed system.
```
```diff
-Another challenge with microservices is the partitioned database architecture. Business transactions that update multiple business entities are fairly common. You need to update multiple databases owned by different services.
```
```diff
-Testing a microservices application is also much more complex.
```
```diff
-Deploying a microservices‑based application is also much more complex. Successfully deploying a microservices application requires greater control of deployment methods by developers, and a high level of automation.
```

| BLOG 2 | Best Practices for Building a Microservice Architecture |
| ------ | ------ |
| Access date| May-2017 |
| URL | http://www.vinaysahni.com/best-practices-for-building-a-microservice-architecture |
| Author | **Vinay Sahni**: Full stack developer · Founder of [Enchant](https://www.enchant.com/) |

```sh
You need to build services that are small enough to keep them focused on a single purpose and big enough to minimize interactions with other services.
```
**Watch out for shared libraries!**
```sh
If changes to a shared library require all services be updated simultaneously, then you have a point of tight coupling across services. Carefully understand the implications of any shared library you're introducing.
```
**Identifying Service Boundaries**
```sh
This is a complex one to grasp. Each service should be an autonomous unit that implements a business capability.
```

```sh
A service should be loosely coupled.
```
```sh
A service should have high cohesion.
```
```sh
A service should cover a single bounded context. A bounded context encapsulates internal details of a domain, including any domain specific models.
```

**Micro in microservice has nothing to do with the physical size or lines of code, it is about minimizing complexity. A service should be small enough that it serves a focused purpose. At the same time, it should big enough that it minimizes interservice communication.**

```sh
Consistency is hard in a distributed system.
```
```sh
Communication Protocols. As you build more services, it becomes critical to have standardized methods of communication between them. The chosen communication protocols must be language and platform independent.
```

```diff
+HTTP is a great choice for synchronous communications. HTTP clients are already available in all languages.
```
```diff
-The one negative of HTTP is that it's a verbose protocol as plain text headers are repeatedly sent and connections are repeatedly created and torn down.
```
**We already have a better option on the horizon: HTTP/2. It effectively solves the verbosity problem by using compressed headers and multiplexing requests over persistent connections. It does all that while maintaining backwards compatibility with older clients**

```sh
For asynchronous communications, we will need to implement the publish subscribe pattern: Message Broker and webhooks delivered by the services.
```
**What about an Enterprise Service Bus (ESB) or a messaging fabric? The main problem with heavyweight messaging fabrics is they encourage pushing business logic out of the services and into the messaging layer.**

```sh
Mechanism that services can use to find each other: Service Registry.
```
```sh
Maintaining Distributed Consistency: Your database and event stream are likely two different systems, making it extremely difficult to atomically write to both systems and thus hard to guarantee eventual consistency. You could use a local database transaction to wrap the database operation and write to an event table at the same time. Then, the event publisher would just read from the event table. But not all databases support such transactions.
```
```sh
Communication between services should only happen through established communication protocols. No exceptions!
```
```sh
Automated Deployment: Developers should have a common way to trigger automated deployments for any version of any service to any environment. Keeping deployment fully automated and simple makes it easy to confidently deploy small changes often.
```
```sh
Service teams should own, operate and evolve the services they build. Their work is done when the service is retired, not when it's shipped.
```

