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

High level walk through: 

We receive a query and hand it to our app controller obj, for example "create table test1 (id int NOT NULL auto_increment primary key, first_name varchar(50) NOT NULL, last_name varchar(50));", app controller then gives the input stream to our tokenizer obj. Our tokenizer obj parses the isteam and breaks down the input into a vector of tokens that our code can work with. 
App controller's last task is to find the right processor to delgate the rest of the work to, does so by parsing the tokens. A processors job is to setup the chain of responsibility for a particular type of query (basic,table, database, etc..). 
Chain of responbility starts with one handler parsing the tokens and determining if it can handle the input, if it can't handle the input, the handler passes down the responbility of handing to the next handler and so on till there are no more handlers or a handler is able to handle input. 
The correct handler is tasked with handling the job and passing on a string to a viewer listener obj.

