# Microservice Study
## A Survey About Microservice Usage

  - ### Search String: "Microservice"
  
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
