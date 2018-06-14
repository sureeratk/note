# Simulation System : Review

[TOC]

## Definition



## Simulation Concept

(source: INTRODUCTION TO MODELING AND SIMULATION by John S. Carson II Proceedings of the 2004 Winter Simulation Conference )

* A model is a representation of a system or process

* A simulation model is a representation that incorporates time and the changes that occur over time.

* A discrete model is changes only a discrete points in time, not continuously

  

* Discrete event model -> state changes only at discrete times (event times)

* **Discrete event model** concept :

  * state = state of each entity at the process time
  * events = an instantaneous occurrence that changes the model's state
    * primary event driven by data
    * secondary event generated internally by model logic
  * activities = duration of time that is initiated by the event in conjunction with the model being in a certain sate
  * processes = a sequence of events, activities and other time delays associated with one entity as it flow through a system

* **Entity** = Object of the model

  * dynamic entities are create at time zero
  * Usually represent some real-world object that is flow through a system

### Modelling vs Simulation 1 

(Source : https://dl.acm.org/citation.cfm?id=268440 )

#### Modelling
* Modeling is the process of producing a model; 
* A model is a representation of the construction and working of some system of interest. 
* A model is similar to but simpler than the system it represents.
  * A model should be a close approximation to the real system and incorporate most of its salient features but should not be so complex that it is impossible to understand and experiment with it 
  * A good model is a judicious tradeoff between realism and simplicity 
* An important issue in modeling is model validity. 
  * simulating the model under known input conditions and comparing model output with system output 

#### Simulation

* A simulation of a system is the operation of a model of the system. 
  * The model can be reconfigured and experimented with 
* simulation is a tool to evaluate the performance of a system, existing or proposed, under different configurations of interest and over long periods of real time. 

### Modelling vs Simulation 2 

Source : https://www.researchgate.net/post/What_is_the_difference_between_modeling_and_simulation

- **Modelling** means creating a physical replica or equations of a situation or activity. 
  - A model is a product (physical or digital) that represents a system of interest

- **Simulation** is a process where you show virtually ( you create virtual scenes ) how a real physical situation would happen.
  - A simulation is the process of using a model to study the behavior and performance of an actual or theoretical system. In a simulation, models can be used to study existing or proposed characteristics of a system.

While a model aims to be true to the system it represents, a simulation can use a model to explore states that would not be possible in the original system.

### Simulation Model

Simulation models  has 4 components:

1. system entities
2. input variables
3. performance measures
4. functional relationships

## Discrete Event Simulation (DES) 

### Definition

* *discrete event simulation* in which the central assumption is that the system changes instantaneously in response to certain discrete events 



## Agent-based modeling and simulation (ABMS)

 

## Simulation Tools

### OMNeT++

* Discrete Event Simulator
* OMNeT++ is an extensible, modular, component-based C++ simulation library and framework, primarily for building network simulators.
* https://omnetpp.org

### CloudSim 

* A Framework For Modeling And Simulation Of Cloud Computing Infrastructures And Services

* https://github.com/Cloudslab/cloudsim

### iFogSim

* Toolkit for Modeling and Simulation of Resource Management Techniques in Internet of Things, Edge and Fog Computing Environments
* https://github.com/Cloudslab/iFogSim

### The Repast Suite

* open source agent-based modeling and simulation platforms
* https://repast.github.io
* Status : last updated 2018

### DKF (HLA Development Kit)

* a *software framework (the DKF)* for the development in Java of HLA Federates
* https://github.com/SMASH-Lab/HLA-Development-Kit
* HLA 1.3 and IEEE-1516e supported
* status : last updated 2017

### portico 

* an open source, cross-platform, fully supported HLA RTI implementation
* https://github.com/openlvc/portico
* HLA 1.3 and IEEE-1516e supported
* status : active (2018)

### HLA Listener

* An introduction to HLA simulation and HLA Listener
* https://www.codeproject.com/Articles/994486/HLA-Listener



### Related Works

[1] 	X. Zeng, S. K. Garg, P. Strazdins, P. P. Jayaraman, D. Georgakopoulos, and R. Ranjan, “IOTSim: A simulator  		for analysing IoT applications,” *Journal of Systems Architecture*, vol. 72, pp. 93–107, Jan. 2017.

[2] G. D’Angelo, S. Ferretti, and V. Ghini, “Modeling the Internet of Things: a simulation perspective,” in *2017 International Conference on High Performance Computing Simulation (HPCS)*, 2017, pp. 18–27.

