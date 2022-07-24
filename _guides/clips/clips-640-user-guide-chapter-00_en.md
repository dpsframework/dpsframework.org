---
layout: guide
lang: en
ref: c640ug00
 
manualcode: c640ug

title: "CLIPS 6.4 User's Guide"
headtitle: 'Readme'
shorttitle: 'Giarratano, J.C. (2021)'

toc: true
author: 'Giarratano, Joseph C. Ph.D.'
date: '2021-04-09 03:17:40:49:44 +0100'

keywords: 
  - 'CLIPS'
  - 'COOL'
ndt: '2022-07-24 08:28:40:49:44 +0100'
chapter: 0
--- 

![image](images/clips-user-guide-JC-Giarratano-Banner.jpg){:width="200px"  border="0px" }
![image](images/clips_logo.jpg){:width="128px"  border="0px" }



# CLIPS 6.40 User's Guide (2021)

> by  **Joseph C. Giarratano**, Ph.D.<br>
> Editor: **Gary Riley**

- CLIPS 6.40 User's Guide[^1] is available at _SourceForge_.
- In the process of being translated into Spanish [**at this address...**](/guides/clips/clips-640-user-guide-chapter-00_es.html)



# Table of Contents
Readme<br>
1. Just the Facts<br>
2. Following the Rules<br>
3. Adding Details<br>
4. Variable Interests<br>
5. Doing It Up In Style<br>
6. Being Functional<br>
7. How to Be in Control<br>
8. Matters of Inheritance<br>
9. Meaningful Messages<br>
10. Fascinating Facets<br>
11. Handling Handlers<br>
12. Questions and Answers<br>
Support Information<br>




# _Readme_



> The first step on the road to wisdom is the admission of ignorance. <br>The second step is realizing that you don’t have to blab it to the world.



This section was formerly called the Preface, but since nobody read it, I renamed it to a more  conventional title that computers users are conditioned to obey. Another suggestion was to call  this the Don’t Readme section, but since people today believe everything they read, I was afraid  they really wouldn’t read it.

The purpose of a Preface, oops, excuse me, a Readme, is to provide metaknowledge about  the knowledge contained in a book. The term **metaknowledge** means knowledge about the  knowledge. So this description of the Readme is actually metametaknowledge. If you’re either  confused or intrigued at this point, go ahead and read this book anyway because I need all the  readers I can get.


## _What Is CLIPS?_

CLIPS is an expert system tool originally developed by the Software Technology Branch (STB),  NASA/Lyndon B. Johnson Space Center. Since its first release in 1986, CLIPS has undergone  continual refinement and improvement. It is now used by thousands of people around the world.

CLIPS is designed to facilitate the development of software to model human knowledge or  expertise.

There are three ways to represent knowledge in CLIPS:

- Rules, which are primarily intended for heuristic knowledge based on experience.

- Deffunctions and generic functions, which are primarily intended for procedural knowledge.

- Object-oriented programming, also primarily intended for procedural knowledge. The five  generally accepted features of object-oriented programming are supported: classes,  message-handlers, abstraction, encapsulation, inheritance, and polymorphism. Rules may  pattern match on objects and facts.

You can develop software using only rules, only objects, or a mixture of objects and rules.

CLIPS has also been designed for integration with other languages such as C and Java. In  fact, CLIPS is an acronym for C Language Integrated Production System. Rules and objects  form an integrated system too since rules can pattern-match on facts and objects. In addition to  being used as a stand-alone tool, CLIPS can be called from a procedural language, perform its  function, and then return control back to the calling program. Likewise, procedural code can be  defined as external functions and called from CLIPS. When the external code completes  execution, control returns to CLIPS.

If you are already familiar with object-oriented programming in other languages such as  Smalltalk, C++, Objective C, or Java, you know the advantages of objects in developing  software. If you are not familiar with object-oriented programming, you will find that CLIPS is  an excellent tool for learning this new concept in software development.

## _What This Book is About_

The _CLIPS User’s Guide_ is an introductory tutorial on the basic features of CLIPS. It is not  intended to be a comprehensive discussion of the entire tool. The companion volume to this  book is the _CLIPS Reference Manual_, which does provide a complete, comprehensive discussion of  all the topics in this book and much more.

## _Who Should Read This Book_

The purpose of the CLIPS User’s Guide is to provide an easy to read, elementary introduction to  expert systems for people with little or no experience with expert systems.

The CLIPS User’s Guide can be used in the classroom or for self-teaching. The only  prerequisite is that you have a basic knowledge of programming in a high-level language such as  Java, Ada, FORTRAN, C (OK, BASIC if nothing else, but we won’t admit it in public and will  disavow this statement if asked.)

## _How To Use This Book_

The CLIPS User’s Guide is designed for people who want a quick introduction to expert system  programming in a hands-on manner. The examples are of a very general nature. Also, since  learning a new language can be a frustrating experience, the writing is in a light, humorous style  (I hope) compared to serious-minded, massive, and intimidating college textbooks. Hopefully, the  humor will not offend anyone with a sense of humor.

For maximum benefit, you should type in the example programs in the text as you read  through the book. By typing in the examples, you will see how the programs should work and  what error messages occur if you make a mistake. The output for the examples is shown or  described after each example. Finally, you should read the corresponding material in the CLIPS  Reference Manual as you cover each chapter in the CLIPS User’s Guide.

Like any other programming language, you will only learn programming in CLIPS by writing  programs in it. To really learn expert system programming, you should pick a problem of interest  and write it in CLIPS.

## _Acknowledgments_

I greatly appreciate the advice and reviews of this book by many people. Thanks to Gary Riley,  Chris Culbert, Brian Dantes, Bryan Dulock, Steven Lewis, Ann Baker, Steve Mueller, Stephen  Baudendistel, Yen Huynh, Ted Leibfried, Robert Allen, Jim Wescott, Marsha Renals, Pratibha Boloor, Terry Feagin, and Jack Aldridge. Special thanks to Bob Savely for supporting the  development of CLIPS.



## _Editor’s Note_

Minor changes have been made to Dr. Giarratano’s original document to reflect changes in  newer versions of CLIPS --- Gary Riley.









##  References

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/. Available at: [https://altushost-swe.dl.sourceforge.net/project/clipsrules/CLIPS/6.40/clips_documentation_640.zip](https://altushost-swe.dl.sourceforge.net/project/clipsrules/CLIPS/6.40/clips_documentation_640.zip)