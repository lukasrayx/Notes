# 01. Introduction

### Goals:

Component-based software engineering is the generalization of object-oriented software engineering

- Understand how to reuse software
- component models are the basis of all engineering

### Mass-produced Software Components:

- Every ripe industry is based on components, to manage large systems
- components should be produced in masses and composed to systems afterwards

### "Real" Component Systems:

- Lego
- Square stones
- Building plans
- IC's
- Hardware bus

### Definitions of software Components:

- A software component is a unit of composition with contractually specified interfaces and explicit context dependencies only.

  A software Component can be deployed independently and is subject to composition by third parties. 

  (By Clemens Szyperski)

- A reusable software component is a logically cohesive, loosely coupled module, that denotes a single abstraction.

  (by Grady Booch)

- A software component is a static abstraction with plugs.

  (By Nierstrasz/Dami)

### What is a software Component?

A component is a container with

- Hidden inner
- Public outer interface
- Stating all dependencies explicitly 明确说明所有依赖关系

**Example**: a method

- Public outer interface: return type
- Explicit dependencies: parameters
- Hidden inner: method body

A Component is a reusable unit for composition

A Component underlies a component model

- That fixes the abstraction level
- that fixes the grain size (widget or OS?)
- that fixes the time (static or runtime?)

**Example:** Android Activity Components

- Interfaces specified in <u>AndroidManifest.xml</u>
- **public outer interface**: intent-filter, lists intents the activity shall respond to 
- **explicit dependencies:** Uses-feature, to list hard- and software features required by your activity
- **Hidden inner:** Implementation of activity class

**Example:** Robot Operating SYstem(ROS) Components

- **Public outer interface:** ROS Nodes are executables. Their outer interfaces is defined by start-up parameters
- **Explicit dependencies:**
  - ROS Packages (package.xml). Dependencies are specified per package.
  - ROS Nodes communicate via topics
- **Hidden inner:** Implementation in C++ or Python



### What is a **Component-Based System?**

**Feature:** major relationship between the components should be **tree-shaped or reducible**, in other words, components are hierarchically organized.

**Consequence:** the entire system can be reduced to one abstract node, at least along the structuring relationship.

Tow types of component models are known:

- Modular decomposition (**blackbox**)
- Seperation of concerns (**graybox**)



### **Component** Systems:

A component system has 

- **Component Model** for description of components and 
- **Composition Technique** for compositions of components.

### **Composition** Systems:

A composition system has 

- **Component Model**, 
  - How do components look like? What types of components are provided?
  - Secrets, interfaces, substitutability
- **Composition Technique** and 
  - How are components plugged together, composed, merged, applied?
  - Composition time (Compile-time, Deployment-time, Runtime)
- **Composition Language**
  - How are compositions of large systems described?
  - How are system builds managed?



### The Ladder of Composition Systems:

![](https://i.imgur.com/63vXnCA.jpg)



## Black-box Composition:

![](https://i.imgur.com/B4m7QIX.jpg)

- Structured Programming
- Object-oriented Programming
- Classical Component Systems
- Architectural Systems

### Structured Programming

**Component Model:**

- Procedures (alias methods, Functions, Operations)
- Variables (i.e. data)

**Composition Technique**:

- Procedure calls (data exchanged via parameters and return values)

**Composition Language:** None



### Object-oriented Programming

**Component Model:**

- Classes, which capsule
  - Methods
  - Variables
- Objects

**Composition Technique:**

- Method calls (Delegation)
- Inheritance (Polymorphism) 继承与多态

**Composition Language:** None



### Classical Component-based Systems

**Component Model:**

- Standardized components, typically defined via interfaces
- Components are technology-specific:
  - Android: Apps
  - ROBOT OS: Packages
  - Enterprise Java: Enterprise archive(EAR)
  - OSGi: Bundles

**Composition Technique:**

- Interplay of components managed by middleware services
- Composition techniques are technology-specific too:
  - Android: Intents, Android Interface Definition Language(AIDL)
  - Robot OS: topics
  - Enterprise Java: Remote Method invocation (RMI)
  - OSGi: Package ex-/import, Method calls

**Composition Language**: None



### Architectural Systems 

**Component Model:**

- Standardized components, typically defined via interfaces

**Composition Technique**

- Interconnection of components via **Connectors**
- Connectors encapsulate communication     封装

**Composition Language:** Architecture Description Languages



### Black-box Composition Systems

Components + Connectors + Composition recipe ===> Component-based Applications



### Aspects in software

Aspects are Crosscutting:

- Scattered across and tangled in the core

Component Model

- Core and aspects
  - Core contains joinpoints
  - Aspects specify pointcuts, which reference sets of jointpoints

Composition Technique

- Weaving (code composition)

Composition Language

- usually implicit

Besides Aspect-oriented Programming, we will investigate:

- composition filters
- hyperspace programming
- Invasive software composition (ISC)



### Composition Languages in Composition Systems

Composition languages describe the structure of the system in-the-large

- Composition programs combine the basic composition operation of the composition language

Composition languages can look quite different

- imperative or rule-based
- textual languages
  - sandard languages, such as Java
  - Domain-spacific languages (DSL) such as Makefiles or ant-files
- Graphic languages
  - Architectural description languages (ADL)
- Composition languages enable us to describe large systems



### Conclusions for Composition Systems

Components have a <u>composition interface</u>

Composition interface is different from functional interface

- the composition is running usually **before** the execution of the system
- from the composition interface, the functional interface is derived

System composition becomes a new step in system build

![](https://i.imgur.com/0sNQ51f.jpg)





# Metamodelling

## Searching and finding Components in Repositories

### Component Repositories

<u>Components</u> must <u>be stored in component repositorie</u>s with metadata(makeup, attributes) to find them again

Descriptions (Metadata)

- **Attributes:** Keywords, Author data
- **Usage protocols** (behavioral specifications)
  - (Protocol) State machines record the sequence of calls to the component
  - Sequence diagrams record parallel interaction sequences of the component
  - Contracts specify conditions on the state before, after and during the calls

**Examples of Component Repositories** 

• Debian Linux Component System (apt, dpkg)

• Mobile App Stores (Google Play, Apple AppStore, F-Droid, etc.)

• CTAN TeX Archive

• CORBA

• implementation registry

• interface registry

• COM+ registry

### Why searching Components?

A public component repository is called a market, managed by a trader

Searching for functionality (interface, contract, protocol)

Searching for quality features

## Introduction to Metalevels

![](https://i.imgur.com/XH9YPeD.jpg)



Domain-specific languages (DSL) form extensions on M2

Composition languages (CL) also on M2

**Language engineering** means to develop M2 models using M3 language

**Notation:** **metaclasses** with dashed lines, **metametaclasses** with dotted lines



### Reflection(self-Modification, Intercession, Metaprogramming)

Computation about the metamodel in the model is reflection

- Reflection: thinking about oneself with the help of metadata
- The application can look at their own skeleton and change it
  - Allocating new classes, methods, fields
  - Removing classes, methods, fields

This self modification is also called intercession in a meta-object protocol (MOP)

### Introspection 自省

Read-only reflection is called **introspection**

- The component can look at the skeleton of itself or another component and learn from it (but not change it)
- Typical application: find out features of components
  - Classes, methods, attributes, types

A reflection system is a system in which the application domain is causally connected with its own domain. (Patti maes)



## Metalevel Architectures

### Reflective Architecture

A system with a reflective architecture maintains metadata and a causal connection between meta- and base level

- The metaobjects describe structure, features, semantics of domain objects. This connection is kept consistent

Metaprogramming is programming with metaobjects

![](https://i.imgur.com/Vf0kVD4.jpg)

**Examples:**

24/7 systems with total availability

■ Dynamic update of new versions of classes

■ Telecommunication systems

■ Internet banking software

Self-adaptive systems

■ Systems reflect about the context and themselves and, consequently, change themselves

Reflection is used to think about versions of the systems

■ Keeping two versions at a time

### 

### Introspective Architectures

![image-20210928192131535](/Users/lucas/Library/Application Support/typora-user-images/image-20210928192131535.png)

### Staged Metalevel Architecture (static Metaprogramming Architecture)

![image-20210928192212287](/Users/lucas/Library/Application Support/typora-user-images/image-20210928192212287.png)

### Compilers:

![image-20210928192228898](/Users/lucas/Library/Application Support/typora-user-images/image-20210928192228898.png)

### Compilers are static metaprograms

![image-20210928192258638](/Users/lucas/Library/Application Support/typora-user-images/image-20210928192258638.png)



## Metaobject protocols (MOP)

### Metaobject protocol

Bychanging the MOP, the language semantic is changed

- Or adapted to a context
- If the MOP language is object-oriented, default implementations of metaclass methods can be overwritten by subclassing
- and the semantics of the language is changed by subclassing

By changing the MOP of a component from a component market, the component can be adapted to the reuse context

A MOP is a reflective implementation of the **methods of the metaclasses**(<u>interpreter</u> for the language) describing the semantics, i.e., the behavior of the language objects in terms of the language itself.



### An Open Language has a Static MOP

An **Open Language** has a static metalevel architecture(static metaprogramming architecture)

, with a static MOP

... offers its AST as metamodel for static metaprogramming

- Users can write static metaprograms to adapt the language
- Users can override default methods in the metamodel, changing the static language semantics or the behavior of the compiler

... can be used to adapt components from a market a compile time

- During reuse of the component in system generation
- static adaptation of components

Metaprograms are removed during system generation, no runtime overhead

- Avoids the overhead of dynamic metaprogramming

**Example:** Open Java, Open C++

![image-20210928193226268](/Users/lucas/Library/Application Support/typora-user-images/image-20210928193226268.png)



### Metaobject Facility (MOF)

A metaobject facility is a language specification language(metalanguage) to describe the context-free structure and context-sensitive structure of a language and to check the wellformedness of modes.

Dynamic semantics(interpretation) is omitted. 省略

MOF of OMG is a **metalanguage** to describe the structure of modeling languages, and finally the structure of models as **abstract syntax graphs(ASG)**

MOF is a minimal UML class diagram like language

- MOF provides the modelling concepts: class, inheritance, relation, attribute, signature...
- Constraints(in OCL) on the classes and their relations

A MOF is **not** a MOP

- The MOP is interpretative
- A MOP specification does not describe an interpreter for the full-fledged language, but provides only a structural description

### MOF

A MOF specification(a MOF metamodel) is a typed attributed graph, containing

-  the concepts of a language as metaclasses
- their relationships as associations between metaclasses
- their constrains

With MOF, the context-sensitve structure of languages is described, constrained, and generated

- type systems
  - to navigate in data with unknown types
  - to generate data with unknown types
  - describing IDL, the CORBA type system
  - describing XML schema
- Modlling languages(such as UML)
- relational schema language
- component models
- Workflow languages

![image-20210928195239282](/Users/lucas/Library/Application Support/typora-user-images/image-20210928195239282.png)



### A typical Application of MOF: Mapping type systems with a language mapping

The type system of CORBA-IDL is a kind of mediating type system

- maps to other language type systems (Java, C++ ..)
- for interoperability to components written in other languages, an interface description in IDL is required

### Mapping type systems in CORBA

![image-20210928195509775](/Users/lucas/Library/Application Support/typora-user-images/image-20210928195509775.png)



### Language mappings for program and object mappings

![image-20210928195604461](/Users/lucas/Library/Application Support/typora-user-images/image-20210928195604461.png)

### 

### The MOF as smallest common denomiator and mediator between type systems

From the mappings of the language-specific metamodels to the IDL metamodel, transformation, query, navigation routines can be generated

![image-20210928195834905](/Users/lucas/Library/Application Support/typora-user-images/image-20210928195834905.png)



### Summary MOF

The MOF describes the structure of a language

- Type systems
- languages
- itself

Relations between type systems are supported

- for interoperability between type systems and repositories
- automatic generation of mappings on M2 and M1

Reflection/introspection supported

Application to workflows, data bases, groupware, business processes, data warehouses



### Markup languages  标记语言

Markup languages convey more semantics for the artifact they markup

- for a component, they describe metadata
- XML, SGML are markup languages

A markup can offer contents of the component for the external world, i.e., for composiition

- a component is a conainer
- it can offer the content for introspection
- or even introcession

A markup is stored together with the coponents, not separated



### Embedded markup and style sheets

Markup can be defined as embedded or by style sheets

- embedded markup marks a part of a component in-line
  - The part may be required or provided
- style sheets mark a part of a component off-line
- Some component languages allow for defining embedded markup
  - latex



### Markup with Hungarian Notation

**Hungarian notation** is an embedded markup method that defines naming conventions for identifiers in languages

- to convey more semantics for composition in a component system
- to be compatible 兼容 with the syntax of the component language
- so that standard tools can be used

The composition environment can ask about the names in the interfaces of a component and can deduce推断 more semantics

Convention: {prefix} + {name}

- prefix indicates type
- name starts with a capital letter
- Examples: idPerson, cmembers, etc.



### Java Beans naming Schemes use Hungarian Notation

Property access

■ setField(Object value);

■ Object getField();

Event firing

■ fire<Event>

■ register<Event>Listener

■ unregister<Event>Listener



### Markup and Metadata Attributes

by structured Comments

- Javadoc tags:

  - @author

    @date

    @deprecated

    @entity

    @invoke-around

Java annotations and C# attributes are metadata

- Java annotations:
  - @override ...
- C#/ .NET attributes
  - [author(Uwe Assmann)] . [date Feb 24] . [selfDefinedData(...)]
- User can define their own metadata attributes themselves
- metadata attributes are compiled to byte code and can be inspected by tools of an IDE

UML stereotypes and tagged values

- <<Account>>

  {

  author=”Uwe

  Assmann”

  }



### Markup is essential for component composition

Because it supports introspection and intercession

- Components that are not marked-up cannot be composed

Every component model has to introduce a strategy for component markup

Insight: a component system that supports comosition techniques must have some form of reflective architecture 



# V3:finding-components

### Faceted Classification for better matchmaking

A facet isi a dimension of a classification

- Facets simplify search: Facet classification has been invented in library science to simplify the description and search for books
- A component is described in several facets, dimensions, which are orthogonal to each other

matchmaking engines can look up a service by stating the desired properties for all facets

Classifications can be arranged in facets if several partitions of a group of objects exist that are orthogonal

- In domain modelling, this is often the case
- Without facets, multiple inheritance hierarchies have to be specified, which are often clumsy and error-prone

Idea: use jacets for better matchmaking



### Service Facets in a UNIX System

To describe the services of a UNIX System, [Prieto-Diaz] employed a 4-faceted scheme

- function
- Logical object
- implementation object
- tool

UNIX services can be described with appropriate facet values and looked up in a repository

### Other Advantages

The facet classification is rather immune to extensions

■ Extending one facet leaves all others invariant

■ Example: If Europe is extended with a new member state, the matchmaking algorithm can deliver new courses from the new member state, without affecting the rest of the semantic specifications at all

The accuracy can be improved by synonym lists (thesauri)

■ Synonyms increase the chances for a match

■ They permit to search not only for keywords, but also for their synonyms (assembled in a thesaurus)

■ Beyond synonyms other refinement relations of concepts can be used to improve the search

■ Example: Great Britain is used as a synonym for England, Scotland, and Wales.

Synonyms allows for matchmaking on any of the keywords, so that students looking for a course need not bother about geographic and political details.



### The Use of Ontologies in Faceted Matchmaking

Ontologies simplify matchmaking by standardization

- Since they provide standardized terminology and standardized ontological relations between the terms, queries can specify
  - Keywords with a precise, shared, and standardized meaning
  - contextual informaion for search in context, where the context is defined by the ontological relations of the terms

Example:

- A web course on IT basics can be queried by the standardized word IT-basics (being semantic search)
- also in context, by relating it to courses such as IT-advanced or IT-preparatory (contextual search)



## UML Components

### Component Specification with UML Components

A **UML component** is a **hierarchical class** for big objects with **provided and required interfaces** (roles)

- Provided interfaces(provided roles) use lollipop notation
- Required interfaces (required roles) use plug notation

Some components are required to use specific other interfaces

### Port of UML Components

A **port** is a connection point of a UML component

- A port has a set of roles (interfaces)
- it may be represented by a port object (gate)

### Lollipops und Plugs (balls and sockets)

For a UML component, provided and required interfaces can be distinguished

- A required interface specifies what the current class needs to execute 

### Ports

Ports consist of port classes with interfaces and behavior in form of interface automata

- Provided: normal, offered interface
- Required: used, necessary interface

### Nesting of UML Components

UML components

- Ports are connected by links 
- Delegation link: links outer and inner port

### Refinement of UML Components

UML components can be nested

Nesting is indicated by aggregation and part-of relationship

Nesting is introduced by an encapsulation operator  嵌套是由一个封装操作符引入的 

### Encapsulation means Agregation

Nesting means Aggregation

- A UML component is a package and a facade for all subcomponents



### Ports can be equipped with interface automata contracts

Ports consist of port classes with interfaces and behavior in form of interface automata (port automata, protocol automata)

- Provided: normal, offered interface
- Required: used, necessary interface

### Component Protocols with Operational Contracts

The port protocol automata can be composed to a **component protocol automaton**

Components may have a protocol automaton in which their ports, services, procedures should be called, invoked, or signaled 

- The provided protocol specifies in which order the services can be invoked (given by a provided interface automaton)
- the required protocol specifies in which order the services can be invoked (given by a required interface automaton)

The order of component invocation can be specified by a language over the alphabet of the ports, services, procedures (state-based protocol contract, operational contract)

- Language contains sets of paths over the alphabet
- Finite state automaton(regular language) specify regular sets of paths
  - UML state chart (Hierarchical finite state machine, protocol machines)
  - data flow diagram
- stack machine (context-free language)
- Petri net (regular dialects, context-free and context-sensitive dialects)

The contract provides an abstraction of the implementation of the component

- Implementations must be proven to be comformant一致 to the protocol 

The conformance checking is decidable if the protocol language is decidable

Sets of paths over states (words over state and edge alphabet)



### The Golden Rules of Substitutability 可替代性

Component A can replace component B if it offers more and requires less

Two conditions:

- A's provided protocol must be stronger(richer, larger) than B's - it must guarantee more
- A's required protocol must be weaker(smaller) than B's - it must assume less

If those conditions hold for all component instances of two component types AT and BT, we say that AT can substitute BT in a program

### Searching by Protocol

A component C can be found in a repository, if a query protocol Q is given with Q<=P(C)

Search consists of subsumption checking with all component protocols in the repository

**Query protocols** can be :

- Metadata about the component
- Provided protocols
- required protocols
- Provided and required protocols

### Delcarative Protocols

A protocol can also be specified as predicates over the states of a component (**declarative contract**)

- Preconditions (assumptions)
- Postconditions (guarantees)
- invariants

Then, the protocol consists of logic expressions. The logic should be decidable

- OCL
- Description logic
- Datalog
- Temporal logic

Subsumption包含 checking of protocols and conformance can be done **by reasoning**

- E.g., by subsumption checking of an OWL class hierarchy





# V4:uml-business-components

**Business Objects are Complex Objects**

In the Cheesman-Daniels component model, a business component consists of a set of business objects and other business components (part-of relation)

- The smallest component is a business object with several provided and required interces
- the business objects are the logical entities of an application



### Chessman-Daniels Process

![image-20210929192048050](/Users/lucas/Library/Application Support/typora-user-images/image-20210929192048050.png)



### Component Identification

![image-20210930104102362](/Users/lucas/Library/Application Support/typora-user-images/image-20210930104102362.png)

### stept2.1:Component Identification

- Business Type Model
- Identifying Business Object Interfaces
- Component Grouping

### step2.2: Component Interaction Analysis for Refinement of Component Interfaces

### Step 2.3: Contract Specification

- Enrich the interfaces with contracts
- **Contract Specification in OCL**

### Step 3: Provisioning (Realization, Implementation, Publishing)

### Step 4: Assembly

### Evaluation of Cheesman-Daniels Business Components

- Only bottom-up 



# V5: transparency-problems

Content secrets

- Language transparency:
  -  able to write a component in any language, and still can use other components which are written in other language (need a middleware)
- Persistency transparency: 
  - how is the state of a component are stored on disk to be safe against crashes
- Lifetime transparency
  - do not need to know whether a component is currently running or not

Connection secrets

- Location transparency
- Naming transparency
- Transactional transparency



### Encapsulate Transparency Problems

## The Decorator-Connector Pattern

### Language Transparency With the Connector Pattern

Connector Pattern

- stub:
  - client use stub to make calls
- skeleton
  - server use skeleton to receive calls and send back the results

**Component can be either a client or a server or both**

### Layered Decorators

Do not need to use only one stack and one skeleton, but you can stack them, this allows you to handle in each layer a seperate problem

Use stubs and skeletons to connect server and client

### Decorator vs Proxy vs Adapters vs Chain

### Tasks of the Layers

### Containers – Infrastructure for all Connectors

### Who Realizes Stubs and Skeletons?

- Programmer
- Generator
  - Stub
  - skeleton

## Interface Definition Languages

### Transparency Problem 1: Language Transparency

- Language Mediation - Options In General
- Language Mediation – Common Basic Type System
- Language Mediation – WSDL

### Solutions in Classical Component Systems

### Type Mapping with the CORBA IDL

### Generation of Stubs and Skeletons from CORBA IDL

kw: host programming language (HPL)

![image-20210930121115595](/Users/lucas/Library/Application Support/typora-user-images/image-20210930121115595.png)



### Location Transparency

### Transparency Problem 2: Distribution

### Transparent Local/Remote Calls

- Communication over proxies/decorators
- RPC for remote calls to a handler

### Stubs and Skeletons for Distribution



### Stubs, Skeletons, and Serializers



### Transparency Problem 3: The Reference Problem (Name Transparency)

### Approach: Global Adresses



### Name Service

### Remote Yellow Page Service

### 



# V6: CORBA

### Ingredients of CORBA

- Component Model : CCM
  - component secrets
    - . Language interoperability by uniform interface description . 
    - Location transparency . 
    - Name transparency . 
    - Transparent network protocols
  - Standardization
    - CORBA Services (Transactions, Trader, etc.)
    - CORBA Facilities (Application-oriented)
      - Horizontal
      - Vertical
- Composition Techniques

### OMA (Object Management Architecture)

software bus coupled by decorator-connectors

![image-20210930132959280](/Users/lucas/Library/Application Support/typora-user-images/image-20210930132959280.png)

### The Top Class CORBA::Object

### Problem: Multiple Inheritance of CORBA Object

### Basic Connections in CORBA



### Dynamic Call Connector (Request Broking)

### Object Request Broker (ORB)

### ORB Activation

![image-20210930133400030](/Users/lucas/Library/Application Support/typora-user-images/image-20210930133400030.png)



### Protocol of Dynamic Call (Dynamic Invocation Interface, DII)



### Service Call with the Trader Service

### Service Offers for Trader

### Interfaces Trading Service

- Basic interfaces: 1.lookup 2.register 3.admin 4.link



### Component Model

- Mechanisms for secrets and transparency: very good
- No parameterization
- Standardization: quite good!

### Composition Technique

- Mechanisms for connection
- Mechanisms for aspect separation
- Mechanisms for meta-modeling
- Scalability

### Composition Language: week



### Static CORBA Call, Local or Remote

### The CORBA Outer Skeleton: Basic Object Adapter BOA

### Object Activation on the Server through a BOA

### Object Adapters Support Different Server Life-Time Models

- Common server process (shared server)
- Separate server process (unshared server)
- Server-per-request (session server)
- Persistent server

### Callback Connectors with the Callback Service

- Callback pattern
- Callback function registration

### Event Connections

- Most flexible way of communication (also called messages)
- Receiver models
- Push model
- pull model
- event channels as intermediate buffers



# V7: Enterprise Java Beans

### Ingredients of EJB

- Java-based component model (language specific)
- comonent types:
  - session beans
  - message-driven beans
  - Entity beans
  - component factory
  - customization possible by metadata and configuration files
- Coposition Technique
  - Adaptation/Glue



### Interactions in an EJB Component System (Where are the Beans?)

### The Bean Container/Application Server

- The bean container is a run-time façade for all beans on a server with infrastructure (application server)
  - container manages the beans with
    - factory
    - repository
- The bean container is a deployment infrastructure

### Implicit Middleware by Interceptors (Bean Decorators)

![image-20210930141321899](/Users/lucas/Library/Application Support/typora-user-images/image-20210930141321899.png)



### The EJB Object as a Skeleton

- EJB is not called via an EJB object (skeleton, facade object, proxy)

### The Remote Object Interface

### The Home Object and Interfaces

- An EJB object factory and repository is needed: The home object with the home interface
- The communication uses Java RMI (Remote Method Invocation)

### Name Service for Name Transparency

- The Java Naming and Directory Interface (JNDI) is used to lookup home objects
  - Only the address to the JNDI server is needed

![image-20210930142032185](/Users/lucas/Library/Application Support/typora-user-images/image-20210930142032185.png)



### Local Interfaces

- Beans do not support location transparency

- ■ local interface corresponding to remote interface

  ■ local home interface corresponding to home interface

### Putting Together an EJB Component File

### Deployment of an EJB Component File



### Session Beans Overview

### Life Cycle of a Stateful Session Bean

![image-20210930142222578](/Users/lucas/Library/Application Support/typora-user-images/image-20210930142222578.png)



### Activation of a Stateful Session Bean

![image-20210930142245946](/Users/lucas/Library/Application Support/typora-user-images/image-20210930142245946.png)



### Characteristics of Message-Driven Beans (MDB)

### Overview of Entity Beans

- An entity bean is a persistent material
- Object-relational mapping necessary (from Java classes to relational databases)
- Several entity bean instances may represent the same underlying data
- Two kinds of entity beans

### Loading and Storing an Entity Bean

![image-20210930142854296](/Users/lucas/Library/Application Support/typora-user-images/image-20210930142854296.png)



### Persistency is Container-Managed in 3.0



### Component Model

- Mechanisms for secrets and transparency: very good
- Parameterization by metadata annotations
- Standardization: de-facto standard in the Java world

### Composition Technique

### Composition Language



# V8: Architecture Systems

### Separation of Concerns

### Architecture Systems as Automated Architectural Views

### Essence – Administration – Infrastructure (EAI)

### Kruchten‘s 4+1 View Model of Software

![image-20210930143955508](/Users/lucas/Library/Application Support/typora-user-images/image-20210930143955508.png)

### The 4-View to Software Architecture

- [Hofmeister/Sony/Nord. Applied Software Architecture] fills the Kruchten Model with more content

### 

### Data ports

- Data port
- Control-flow port (service port)

### Synchronicity

- inpput data ports
- output data ports

Continuity 

- Stream ports
- event port

### Composite Ports (Services)

Ports can be atomic or composite (structured)

- A service is a structured port (groups of ports)
- A data service is a tuple of atomic ports
- A call port is a synchronous input/output composite, singular port with one out-port, the return
- A property service is a synchronous singular data service to access component attributes, i.e., a simple tuple of in and out ports



### Hierarchic Architectures with Encapsulation

- Components can be connected by connectors
- Components can be nested by an encapsulation operator

### Nesting of Components with the Encapsulation Operator

- In most component models, components are nested.
- Nesting is indicated by aggregation and part-of relationship. 
- Nesting is introduced by an encapsulation operator encapsulate.



### Connectors Generate Architectural Code

- Glue- and adapter code from connectors, skeletons, and ADL-specifications
- Simulations of architectures:
- Test cases for architectures

### Most Commercial Component Systems Provide Restricted Forms of Connectors

It turns out that most commercial component systems do not offer connectors as explicit modelling concepts, but

■ offer communication mechanisms that can be encapsulated into a connector component

■ For instance, CORBA remote connections can be packed into connectors

### A Complex Connector: Repository Connector (Tuple Space Connector)

- A specific, large connector is the repository (tuple space)
- Based on data ports, components can communicate via tuples of data, emitting and receiving from a tuple space
- Data in tuple spaces can be untyped, or typed by a data definition language (DDL)



### Complex Composition Operator: Coordination Skeletons

An **architectural skeleton** is a **coordination scheme** for a set of components superimposing a topology of connectors (connector nets)

**Example**: the Map-Reduce Skeleton (Google) for searching



### Architectural Styles

### Which Types of Control- and Data-flow Specifications Exist for Architectures?



# V9: Web Services

### Web Services and Architecture Systems

- Architecture systems may have different forms of architectural languages
- Web Service Systems and Languages (WSS) are a form of architectural system
- WSS have an imperative architectural language

### Web Services are Black-Box Components

### Workflow Languages

### Workflow engines

### WDSL Specification Structure

### Ingredients of BPEL

### Business Process Modeling Notation (BPMN)

### Gateways and Connections





# V10: composition-filters

### Inheritance Anomaly – Why Dimensional Software Composition Is Necessary

### Decorator Relations

### Composition Filters

### Filters are Layers



### Implementation with Decorator



# V11: Generic Programming with Generic Components

### Full Genericity in BETA

### Generic Components

### BETA Fragment Metaprogramming System

### The Component Model of BETA and Mjölner

### Fragments (Snippets)

### Generic Fragments

Full genericity

### Slot Markup Languages

### Slots (Declared Hooks)



### Template Metaprogramming (TMP)



# V12: View-Based Development

### Constructive and Projective Views

### Constructive Views Require Open Definitions

### CoSy Extensible Repository-Architecture

### O-O Technology doesn’t fit

### Syntactic Fragile Base Class Problem in Object-Oriented Languages

### A CoSy Compiler is Extensible by Constructive Views



### Subject-Oriented Programming (SOP)



### Hyperspaces

### The Concern Matrix of the Hyperspace

### Fragment Hyperspaces



# V13: Aspect-Oriented Programming with Aspect/J

### Crosscutting: Scattering and Tangling

### Superimposition of Aspects

### The AOP Idea

- Crosscutting
- typical examples

### Display Updating

### Primitive Pointcuts

### A Simple Aspectual Component











# 

























































































