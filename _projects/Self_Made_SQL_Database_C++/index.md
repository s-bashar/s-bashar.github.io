---
layout: post
title: Self Made SQL Database 
description:  Designed a SQL database system in C++, leveraging object-oriented design principles and multiple software design patterns and idioms. Implemented abstraction layers using patterns such as Chain of Responsibility, Decorator, Adapter, Iterator, and Creation patterns. Applied polymorphism, singletons, pure virtual classes, and event listeners to enforce modularity and extensibility. Followed Object Construction Framework (OCF) best practices to enhance maintainability and scalability.	

skills: 
  - C++
  - OOP
  - Patterns/Idioms/OCF
  - SQL Database

main-image: /SQL_logo.png
---

---
# Project Repo:
[View the source code on GitHub](https://github.com/s-bashar/SP24-ECE141B-Database-Team5)

# Project Overview:

I will be showing a high level block explanaiton of how this database operates and then dive deep into each block showcasing how each block works and what patterns/idioms, and abstraction layers are used and why. 

{% include image-gallery.html images="SQL_Overview.png" height="800" alt="DB Overview" %}

## High level walk through: 

We receive a query and hand it to our app controller obj, for example "create table test1 (id int NOT NULL auto_increment primary key, first_name varchar(50) NOT NULL, last_name varchar(50));", app controller then gives the input stream to our tokenizer obj. Our tokenizer obj parses the isteam and breaks down the input into a vector of tokens that our code can work with. 
App controller's last task is to find the right processor to delgate the rest of the work to, does so by parsing the tokens. A processors job is to setup the chain of responsibility for a particular type of query (basic,table, database, etc..). 
Chain of responbility starts with one handler parsing the tokens and determining if it can handle the input, if it can't handle the input, the handler passes down the responbility of handing to the next handler and so on till there are no more handlers or a handler is able to handle input. 
The correct handler is tasked with handling the job and passing on a string to a viewer listener obj.

## Low level walk through of abstraction layers and design choices:

In general we create each abstraction layer to follow "Single Responsibility Priniciple" this helps the code to be readable, scalabe/maintable , and low cognitive effort. 
### **App Controller:** 

The first layer is our "App Controller" class, single responbility it to select the correct proccessor for a given query. While mainting the information of current database, state of program (running or not), and passing a ViewListener down the abstraction layers. <br>
App controller calls on a Tokizer utility class to help break down the input stream. 

### **Processors:** 

The next abstraction layer is the processor classes, we have 6. "BasicProcessor", "DataBaseProcessor", "TableProcessor", "INsertProcessor", "SelectProcessor", "UpdateandDelProcessor". <br>
Each processor single task is to setup the chain of responsibility for each type of query (i.e. Basic Query, DataBase Query, Table Query, or etc...). <br>

This design follows the three core principles of good software: **readability**, **scalability/maintainability**, and **low cognitive effort**.

**1. Readability**  
By breaking up the processors, each class handles a focused, well-defined task and stays around ~30 lines of code. This makes each processor easy to read and understand in isolation, without requiring a full understanding of the entire system.

**2. Scalability & Maintainability**  
Having one large, monolithic processor that builds a giant Chain of Responsibility (CoR) would be difficult to scale or modify. Every new command or change would require modifying a central block, increasing the risk of bugs and regressions.

Instead, by **pre-processing the tokens** to select the appropriate processor early, we:

- Reduce unnecessary handlers loaded into memory.
- Shorten traversal time through the chain (since unrelated handlers are skipped).
- Allow new processors to be added or modified independently — adhering to the **Open/Closed Principle**.

This makes the system easier to evolve and maintain over time.

**3. Low Cognitive Effort **  
Developers only need to understand **one processor at a time**, rather than a tangled mega-handler with complex branching. The system becomes more modular and easier to reason about, debug, and test.

---

**Summary**  
This design methodology improves performance, modularity, and clarity. It aligns with core software engineering principles by ensuring each component has a single responsibility and a clear, self-contained scope.

### **Handlers:** 

Handlers class sole responisbility is to do the actual work that the query needs as well as invoking a storage object to handle the saving of the database to memory, the Storage class is another abstraction layer for in memory saves within that layer there is a Block layer that handles the chunking of the memory writes/reads.  <br>
All handlers are derived from a pure virtual base class, this allows us to achieve run time polymoriphsm which keeps our code clean, flexible, and less error prone.

{% include image-gallery.html images="default_handler.png" height="800" alt="default_handler" %}
