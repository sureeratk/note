# A Note From Building Microservices

[TOC]

## Ch1. Microservices 

### What are microservices?

Microservices are small, autonomous services that work together.

#### Small, and Focused on Doing One Thing Well

* Robert C. Martin’s definition of the Single Responsibility Principle, which states 

  > “Gather together those things that change for the same reason, and separate those things that change for different reasons.“

* Think about :

  * how small is small? 
  * small enough and no smaller

* the smaller the service, the more you maximize the benefits and downsides of microservice architecture.

#### Autonomous

* These services need to be able to change independently of each other, and be
  deployed by themselves without requiring consumers to change.
  * what our services should expose, and what they should allow to be hidden
* Our service exposes an application programming interface (API), and collaborating services communicate with us via those APIs. 
* The golden rule: *can you make a change to a service and deploy it by itself without changing anything else?*

### Key Benefits

#### Technology Heterogeneity

#### Resilience

* If one component of a system fails, but that failure doesn’t cascade, you can isolate the problem and the rest of the system can carry on working. 

#### Scaling

* With smaller services, we can just scale those services that need scaling, allowing us to run other parts of the system on smaller, less powerful hardware.
* we can even apply this scaling on demand for those pieces that need it.
  This allows us to control our costs more effectively.

#### Ease of Deployment

* With microservices, we can make a change to a single service and deploy it independently of the rest of the system. This allows us to get our code deployed faster. 
* If a problem does occur, it can be isolated quickly to an individual service, making fast rollback easy to achieve. It also means we can get our new functionality out to customers faster. 

## Ch2. The Evolutionary Architect

* **Vision** - Ensure there is a clearly communicated technical vision for the system that will help your system meet the requirements of your customers and organization
* **Empathy** - Understand the impact of your decisions on your customers and colleagues
* **Collaboration** - Engage with as many of your peers and colleagues as possible to help define, refine, and execute the vision
* **Adaptability** - Make sure that the technical vision changes as your customers or organization requires it
* **Autonomy** - Find the right balance between standardizing and enabling autonomy for your teams
* **Governance** - Ensure that the system being implemented fits the technical vision

## Ch3. How to Model Services

### What Makes a Good Service?

#### Loose Coupling

- When services are loosely coupled, a change to one service should not require a change to another.
- A loosely coupled service knows as little as it needs to about the services with which it collaborates. 
  - limit the number of different types of calls from one service to another

#### High Cohesion