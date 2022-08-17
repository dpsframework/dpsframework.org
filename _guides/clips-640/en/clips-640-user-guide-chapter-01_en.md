---
layout: guide
ref:  c640ug01
lang:  en
idiom:  us-EN
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug








toc:  true


title:  "CLIPS 6.4 User's Guide"
headtitle:  'Just the Facts'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Giarratano, Joseph C. Ph.D.'
department:  
authors:



departments:



chapter:  1
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'




ndtdate:  '2022-07-01 11:07:56:49:44 +0100'
date_published:  '2021-04-09'
date_modified:  '2022-07-16'
publisher:  'Gary Riley'

---




#  **Chapter 1**

# 1.  Just the Facts

>  If you ignore the facts, you’ll never worry about being wrong


This chapter introduces the basic concepts of an expert system. You’ll see how to insert and  remove facts in CLIPS.


## 1.1.   Introduction


CLIPS is a type of computer language designed for writing applications called expert systems.  An expert system is a program which is specifically intended to model human expertise or  knowledge. In contrast, common programs such as payroll programs, word processors,  spreadsheets, computer games, and so forth, are not intended to embody human expertise or  knowledge. (One definition of an expert is someone more than 50 miles from home and carrying  a briefcase.)


CLIPS is called an expert system tool because it is a complete environment for developing  expert systems which includes features such as an integrated editor and a debugging tool. The  word shell is reserved for that portion of CLIPS which performs inferences or reasoning. The  CLIPS shell provides the basic elements of an expert system:


1. **fact-list**, and **instance-list**: Global memory for data

2. **knowledge-base**: Contains all the rules, the **rule-base**

3. **inference engine**: Controls overall execution of rules


A program written in CLIPS may consist of rules, facts, and objects. The inference engine  decides which rules should be executed and when. A rule-based expert system written in CLIPS  is a data-driven program where the facts, and objects if desired, are the data that stimulate  execution via the inference engine.


This is one example of how CLIPS differs from procedural languages such as Java, Ada,  BASIC, FORTRAN, and C. In procedural languages, execution can proceed without data. That  is, the statements are sufficient in those languages to cause execution. For example, a statement  such as PRINT 2 + 2 could be immediately executed in BASIC. This is a complete statement


that does not require any additional data to cause its execution. However, in CLIPS, data are  required to cause the execution of rules.


Originally, CLIPS had capabilities to represent only rules and facts. However, the  enhancements of Version 6.0 allow rules to match objects as well as facts. Also, objects may be  used without rules by sending messages and so the inference engine is no longer necessary if you  use only objects. In chapters 1 through 7, we’ll discuss the facts and rules of CLIPS. The object  features of CLIPS are covered in chapters 8 through 12.


## 1.2.  The Beginning and the End


To begin CLIPS, just enter the appropriate run command for your system.

<p class="code-label">You should see the  CLIPS prompt appear as follows:</p>
```scheme
CLIPS >
```


At this point, you can start entering **commands** directly into CLIPS. The mode in which you  are entering direct commands is called the **top-level**. If you have a Graphical User Interface  (GUI) version of CLIPS, you can also **select** some commands using the mouse or arrow keys rather than typing them in. Please refer to the CLIPS Interfaces Guide for a discussion of the  commands supported by the various CLIPS GUIs. For simplicity and uniformity in this book,  we’ll assume the commands are typed in.


<p class="code-label">The normal mode of leaving CLIPS is with the exit command. Just type</p>
```scheme
(exit)
```


in response to the CLIPS prompt and then press the carriage return key.


## 1.3.   Making a List


As with other programming languages, CLIPS recognizes certain keywords. For example, if you  want to put data in the fact-list, you can use the assert command.


<p class="code-label">As an example of assert, enter the following right after the CLIPS prompt as shown:</p>
```scheme

CLIPS> (assert (duck))
```


Here the assert command takes (duck) as its argument. Be sure to always press the carriage return  key to send the line to CLIPS.


<p class="code-label">You will see the response</p>
```scheme
<Fact-1>
```




which indicates CLIPS has stored the duck fact in the fact-list and given it the identifier 1. The  **angle-brackets** are used as a delimiter in CLIPS to surround the name of an item. CLIPS will  automatically name facts using a sequentially increasing number and list the highest fact-index  when one or more facts is asserted.


Notice that the (assert) command and its (duck) argument are surrounded by parentheses.  Like many other expert system languages, CLIPS has a LISP-like syntax which uses parentheses  as delimiters. Although CLIPS is not written in LISP, the style of LISP has influenced the  development of CLIPS.


## 1.4.   And Checking It Twice


Suppose you want to see what’s in the fact-list. If your version of CLIPS supports a GUI, you  may just select the appropriate command from the menu. Alternatively, you can enter commands  from the keyboard. In the following, we’ll describe the keyboard commands since the window  selections are self-explanatory.


The keyboard command to see facts is with the facts command. Enter (facts) in response to  the CLIPS prompt and CLIPS will respond with a list of facts in the fact-list. Be sure to put  parentheses around the command or CLIPS will not accept it.

<p class="code-label">The result of the (facts) command  in this example should be:</p>
```scheme
CLIPS> (facts)
f-1 (duck)
For a total of 1 fact.

CLIPS>
```

The term f-1 is the **fact identifier** assigned to the (duck) fact by CLIPS. Every fact inserted into  the **fact-list** is assigned a unique fact identifier starting with the letter “f ” and followed by an  integer called the **fact-index**. On starting up CLIPS, and after certain commands such as **clear**  and **reset** (to be discussed in more detail later), the fact- index will be set to one, and then  incremented by one as each new fact is asserted.

<p class="code-label">What happens if you try to put a second duck into the fact-list?</p>
Let’s try it and see. Assert a new (duck), then issue a (facts) command as follows
```scheme
CLIPS> (assert (duck))
<Fact-1>
CLIPS> (facts)
f-1 (duck)
For a total of 1 fact.
CLIPS>
```

The <Fact-1> message is returned by CLIPS to indicate that the fact already exists. You’ll see  just the original “f-1 (duck)”. This shows that CLIPS will not accept a duplicate entry of a fact.  However, there is an override command, **set-fact-duplication**, which will allow duplicate fact  entry.

<p class="code-label">Of course you can put in other, different facts. For example, assert a (quack) fact and then  issue a (facts) command. You’ll see</p>
```scheme
CLIPS> (assert (quack))
<Fact-2>
CLIPS> (facts)
f-1 (duck)
f-2 (quack)
For a total of 2 facts.
CLIPS>
```

Notice that the (quack) fact is now in the fact-list.


Facts may be removed or **retracted**. When a fact is retracted, the other facts do not have  their indices changed, and so there may be “missing” fact-indices. As an analogy, when a football  player leaves a team and is not replaced, the jersey numbers of the other players are not all  adjusted because of the missing number (unless they really hate the guy’s guts and want to forget  he ever played for them).



## 1.5.   Clearing Up the Facts



<p class="code-label">The clear command removes all facts from memory, as shown by the following.</p>
```scheme
CLIPS> (facts)
f-1 (duck)
f-2 (quack)
For a total of 2 facts.
CLIPS> (clear)
CLIPS> (facts)
CLIPS>
```



The (clear) command essentially restores CLIPS to its original startup state. It clears the memory  of CLIPS and resets the fact-identifier to one. 
<p class="code-label">To see this, assert (animal-is duck), then check the fact-list.</p>
```scheme
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (facts)
f-1 (animal-is duck)
For a total of 1 fact.
CLIPS>
```



Notice that (animal-is duck) has a fact-identifier of f-1 because the (clear) command reset the fact  identifiers. The (clear) command actually does more than just remove facts. Besides removing all  the facts, (clear) also removes all the rules, as you’ll see in the next chapter.


## 1.6.   Sensitive Fields and Slurping



A fact such as (duck) or (quack) is said to consist of a single **field**. A field is a placeholder (named  or unnamed) that may have a value associated with it. As a simple analogy, you can think of a  field as a picture frame. The frame can hold a picture, perhaps a picture of your pet duck (For  those of you who are curious what a picture of a “quack” looks like, it could be (1) a photo of an  oscilloscope trace of a duck saying “quack”, where the signal input comes from a microphone, or  (2) for those of you who are more scientifically inclined, a Fast Fourier Transform of the “quack”  signal, or (3) a TV-huckster selling a miracle cure for wrinkles, losing weight, etc.). Named  placeholders are only used with **deftemplates**, described in more detail in chapter 5.



The (duck) fact has a single, unnamed placeholder for the value duck. This is an example of a  **single-field** fact. A field is a placeholder for a value. As an analogy to fields, think of dishes  (fields) for holding food (values).


The **order** of unnamed fields is significant. For example, if a fact was defined

```scheme
(Brian duck)
```

and interpreted by a rule as the hunter Brian shot a duck, then the fact

```scheme
(duck Brian)
```

would mean that the hunter duck shot a Brian. In contrast, the order of named fields is not  significant, as you’ll see later with deftemplate.


Actually, it is good software engineering to start the fact with a relation that describes the  fields. A better fact would be

```scheme
(hunter-game duck Brian)
```

to imply that the first field is the hunter and the second field is the game.


A few definitions are now necessary. A list is a group of items with no implied order. Saying  that a list is ordered means that the position in the list is significant. A multifield is a sequence  of fields, each of which may have a value. The examples of (duck Brian) and (Brian duck) are  multifield facts. If a field has no value, the special symbol nil, which means “nothing” may be  used for an empty field as a placeholder. For example,


```scheme
(duck nil)
```


would mean that the killer duck bagged no trophies today.


Note that the nil is necessary to indicate a placeholder, even if it has no value. For example,  think of a field as analogous to a mailbox. There’s a big difference between an empty mailbox,  and no mailbox at all. Without the nil, the fact becomes a single-field fact (duck). If a rule  depends on two fields, it will not work with only one field, as you’ll see later.


There are a number of different **types** of fields available: **float**, **integer**, **symbol**, **string**,  **external-address**, **fact-address**, **instance-name** and **instance-address**. The type of each  field is determined by the type of **value** stored in the field. In an unnamed field, the type is  determined implicitly by what type you put in the field. In deftemplates, you can explicitly declare  the type of value that a field can contain. The use of explicit types enforces the concepts of  **software engineering**, which is a discipline of programming to produce quality software.


A **symbol** is one type of field that starts with a printable ASCII character and is followed  optionally by zero or more printable characters. Fields are commonly delimited or bounded, by  one or more spaces or parentheses. For example,

```scheme
(duck-shot Brian Gary Rey)
```


However, this could be a legal deftemplate fact if "shot" is defined as the name of a field, while  “Brian Gary Rey” are the values associated with the named field.


CLIPS is case-sensitive. Also, certain characters have special meaning to CLIPS.

```scheme
" ( ) & | < ~ ; ? $  
```


The `“&”, “|”, and “~”` may not be used as stand-alone symbols or as any part of a symbol. 


 Some characters act as delimiters by ending a symbol. The following characters act as  delimiters for symbols.  
 
- any non-printable ASCII character, including spaces, carriage returns, tabs, and linefeeds 
- double quotes, `  `"
- opening and closing parentheses, `() `
- ampersand, `&`
- vertical bar, `| `
- less than,` <`. Note that this may be the first character of a symbol
- tilde, `~ `
- semicolon, `;` indicates start of a comment, a carriage return ends it
- ? and `$?` may not begin a symbol but may be inside it


The semicolon acts as the start of a comment in CLIPS. If you try to assert a semicolon, CLIPS  will think you’re entering a comment and wait for you to finish. If you accidentally enter a  semicolon in top-level, just type in a closing parenthesis and carriage return. CLIPS will respond  with an error message and the CLIPS prompt will reappear (This is one of the few approved  occasions in life in which it’s necessary to do something wrong to get something right.)


As you read through this manual, you will learn the special meanings of the characters  above. With the exception of the `“&”, “|”`, and ` “~” `, you may use the others as described.  However, it may be confusing to someone reading your program and trying to understand what  the program is doing. In general, it’s best to avoid using these characters in symbols unless you  have some good reason for using them.



<p class="code-label">The following are examples of symbols.</p>
```racket
duck
duck1
duck_soup
duck-soup
duck1-1_soup-soup
d!?#%^
```





The second type of field is the string. A string must begin and end with double quotes. The  double quotes are part of the field. Zero or more characters of any kind can appear between the  double quotes. Some examples of strings follow.


```racket
  "duck"
  "duck1"
  "duck/soup"
  "duck soup"
  "duck soup is good!!!"
```




The third and fourth types of field are numeric fields. A field which represents a number can  be either an integer or floating-point type field. A floating-point type is commonly referred to  simply as a float.


All numbers in CLIPS are treated as “long long” integers or double-precision floats.  Numbers without a decimal point are treated as integers unless they are outside integer range.  The range is machine dependent on the number of bits, N, used to represent the integer as  follows.



```racket
-2N-1
.
.
.
2N-1 - 1

"For 64-bit “long long” integers, 
this corresponds to a range of numbers"
-9223372036854770000
.
.
.
9223372036854770000
```


As some examples of numbers, assert the following data where the last number is in exponential  notation, and uses the “e” or “E” for the power-of-ten.



```racket
CLIPS> (clear)
CLIPS> (facts)
CLIPS> (assert (number 1))
<Fact-1>
CLIPS> (assert (x 1.5))
<Fact-2>
CLIPS> (assert (y -1))
<Fact-3>
CLIPS> (assert (z 65))
<Fact-4>
CLIPS> (assert (distance 3.5e5))
<Fact-5>
CLIPS> (assert (coordinates 1 2 3))
<Fact-6>
CLIPS> (assert (coordinates 1 3 2))
<Fact-7>
CLIPS> (facts)
f-1 (number 1)
f-2 (x 1.5)
f-3 (y -1)
f-4 (z 65)
f-5 (distance 350000.0)
f-6 (coordinates 1 2 3)
f-7 (coordinates 1 3 2)
For a total of 7 facts.
CLIPS>
```



As you can see, CLIPS prints the number entered in exponential notation as 350000.0 because it  converts from power-of-ten format to floating-point if the number is small enough.


Notice that each fact must start with a symbol such as “number”, “x”, “y”, etc. Before CLIPS  version 6.0, it was possible to enter only a number as a fact. However, now a symbol is required  as the first field. Also, certain reserved words used by CLIPS cannot be used as the first field, but  may be used for other fields. For example, the reserved word not is used to indicate a negated  pattern and may not be used as the first field of a fact.


A fact consists of one or more fields enclosed in matching left and right parentheses. For  simplicity we’ll only discuss facts in the first seven chapters, but most of the discussion of pattern  matching applies to objects as well. Exceptions are certain functions such as assert and retract  which only apply to facts, not objects. The corresponding ways to handle objects are discussed in  chapters 8–12.


A fact may be ordered or unordered. All the examples you’ve seen so far are ordered facts  because the order of fields makes a difference. For example, notice that CLIPS considers these as  separate facts although the same values “1”, “2”, and “3” are used in each.


```racket
f-6 (coordinates 1 2 3)
f-7 (coordinates 1 3 2)
```


Ordered facts must use field position to define data. As an example, the ordered fact (duck Brian)  has two fields and so does (Brian duck). However, these are considered as two separate facts by  CLIPS because the order of field values is different. In contrast, the fact (duck-Brian) has only  one field because of the “-” concatenating the two values.


Deftemplate facts, described in more detail later, are unordered because they use named fields  to define data. This is analogous to the use of structs in C and other languages.
Multiple fields normally are separated by white space consisting of one or more spaces,  tabs, carriage returns, or linefeeds. For example, enter the following examples as shown and you’ll  see that each stored fact is the same.

```racket
CLIPS> (clear)
CLIPS> (assert (The duck says "Quack"))
<Fact-1>
CLIPS> (facts)
f-1 (The duck says "Quack")
For a total of 1 fact.
CLIPS> (clear)
CLIPS> (assert (The duck says "Quack" ))  <Fact-1>
CLIPS> (facts)
f-1 (The duck says "Quack")
For a total of 1 fact.
CLIPS>
```



Carriage returns may also be used to improve readability. In the following example, a carriage  return is typed after every field and the asserted fact is the same as before when the fact was  entered on one line.


```racket
CLIPS> (clear)
CLIPS> (assert (The
duck
says
Quack))
<Fact-1>
CLIPS> (facts)
f-1 (The duck says "Quack")
For a total of 1 fact.
CLIPS>
```



However, be careful if you insert a carriage return inside of a string, as the following example  shows.


```racket
CLIPS> (assert (The
duck
says
"Quack  
))"
<Fact-2>
CLIPS> (facts)
f-1 (The duck says "Quack")
f-2 (The duck says "Quack")
For a total of 2 facts.
CLIPS>
```



As you can see, the carriage return embedded in the double quotes was output with the string to  put the closing double quote on the next line. This is important because CLIPS considers fact f-1  as distinct from fact f-2.



Notice also that CLIPS preserved the uppercase and lowercase letters in the fields of the fact.  That is, the “T” of “The” and the “Q” of “Quack” are uppercase. CLIPS is said to be case sensitive because it distinguishes between uppercase and lowercase letters. For example, assert  the facts (duck) and (Duck) and then issue a (facts) command. You’ll see that CLIPS allows you to  assert (duck) and (Duck) as different facts because CLIPS is case-sensitive.



The following example is a more realistic case in which carriage returns are used to improve  the readability of a list. To see this, assert the following fact where carriage returns and spaces are  used to put fields at appropriate places on different lines. Dashes or minus signs are used  intentionally to create single fields, so CLIPS will treat items like “fudge sauce” as a single field.


```racket
CLIPS> (clear)
CLIPS>
(assert (grocery-list
ice-cream
cookies
candy
fudge-sauce))
<Fact-1>
CLIPS> (facts)
"f-1 (grocery-list ice-cream cookies candy fudge-sauce)  
For a total of 1 fact."
CLIPS>
```



As you can see, CLIPS replaced the carriage returns and tabs with single spaces. While the use of  white space in separating the facts is convenient for a person reading a program, they are  converted to single spaces by CLIPS.


## 1.7.   A Matter of Style


It is good rule-based programming style to use the first field of a fact to describe the relationship of  the following fields. When used this way, the first field is called a relation. The remaining fields of  the fact are used for specific values. An example is (grocery-list ice-cream cookies candy fudge sauce). The dashes are used to make multiple words fit in a single field.


Good documentation is even more important in an expert system than in languages such as  Java, C, Ada, etc., because the rules of an expert system are not generally executed in a  sequential manner. CLIPS aids the programmer in writing descriptive facts like this by means of  deftemplates.


Another example of related facts is (duck), (horse), and (cow). It’s better style to refer to them  as


```racket
(animal-is duck)
(animal-is horse)
(animal-is cow)
          or as the single fact
(animals duck horse cow)
```



since the relation animal-is or animals describes their relation and so provides some documentation  to the person reading the code.



The explicit relations, animal-is and animals, make more sense to a person than the implicit  meaning of (duck), (horse), and (cow). While this example is simple enough that anyone can  figure out the implicit relations, it is an easy trap to fall into to write facts in which the  relationship is not so obvious (In fact, it’s much easier to make something more complicated than  easy, since people are more impressed by complexity than simplicity.)



## 1.8.   Getting Spaced Out


Since spaces are used to separate multiple fields, it follows that spaces cannot simply be included  in facts. For example,

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is walrus))
<Fact-1>
CLIPS> (assert ( animal-is walrus ))
<Fact-1>
CLIPS> (assert ( animal-is walrus ))
<Fact-1>
CLIPS> (facts)
f-1 (animal-is walrus)
For a total of 1 fact.
CLIPS>
```



Only one fact, (animal-is walrus), is asserted since CLIPS ignores white space and considers all  these facts equivalent. Thus, CLIPS responds with <Fact-1> when you try to enter the last two  duplicate facts. CLIPS normally does not allow duplicate facts to be entered unless you change  the set-fact-duplication setting.


If you want to include spaces in a fact, you must use double quotes. For example,

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is "duck"))
<Fact-1>
CLIPS> (assert (animal-is "duck "))
<Fact-2>
CLIPS> (assert (animal-is " duck"))
<Fact-3>
CLIPS> (assert (animal-is " duck "))
<Fact-4>
CLIPS> (facts)
f-1 (animal-is "duck")
f-2 (animal-is "duck ")
f-3 (animal-is " duck")
f-4 (animal-is " duck ")
For a total of 4 facts.
CLIPS>
```


Note that the spaces make each of these facts different to CLIPS although the meaning is the  same to a person.


What if you want to include the double quotes in a field? The correct way to put double  quotes in a fact is with the backslash, “\”, as the following example shows.

```racket
CLIPS> (clear)
CLIPS> (assert (single-quote "duck"))
<Fact-1>
CLIPS> (assert (double-quote "\"duck\""))
<Fact-2>
CLIPS> (facts)
f-1 (single-quote "duck")
f-2 (double-quote ""duck"")
For a total of 2 facts.
CLIPS>
```


## 1.9.   Retract that Fact



Now that you know how to put facts into the fact-list, it’s time to learn how to remove them.  Removing facts from the fact-list is called retraction and is done with the retract command. To  retract a fact, you must specify the fact index of the fact as the argument of retract. For example,  set up your fact-list as follows.


```racket
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (assert (animal-sound quack))
<Fact-2>
CLIPS> (assert (The duck says "Quack."))
<Fact-3>
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (animal-sound quack)
f-3 (The duck says "Quack.")
For a total of 3 facts.
CLIPS>
```


To remove the last fact with index f-3, enter the retract command and then check your facts as  follows.


```racket
CLIPS> (retract 3)
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (animal-sound quack)
For a total of 2 facts.
CLIPS>
```



What happens if you try to retract a fact that’s already retracted, or a non-existent fact? Let’s try  it and see.


```racket
CLIPS> (retract 3)
[PRNTUTIL1] Unable to find fact f-3.
CLIPS>
```



Notice that CLIPS issues an error message if you try to retract a non-existent fact. The moral of  this is that you can’t take back what you haven’t given.
Now let’s retract the other facts as follows.


```racket
CLIPS> (retract 2)
CLIPS> (facts)
f-1 (animal-is duck)
For a total of 1 fact.
CLIPS> (retract 1)
CLIPS> (facts)
CLIPS>
```


You can also retract multiple facts at once, as shown by the following.

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (assert (animal-sound quack))
<Fact-2>
CLIPS> (assert (The duck says "Quack."))
<Fact-3>
CLIPS> (retract 1 3)
CLIPS> (facts)
f-2 (animal-sound quack)
For a total of 1 fact.
CLIPS>
```


To retract multiple facts, just list the fact-id numbers in the (retract) command.  You can just use (retract *) to retract all the facts, where the “*” indicates all .

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (assert (animal-sound quack))
<Fact-2>
CLIPS> (assert (The duck says "Quack."))
<Fact-3>
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (animal-sound quack)
f-3 (The duck says "Quack.")
For a total of 3 facts.
CLIPS> (retract *)
CLIPS> (facts)
CLIPS>
```


## 1.10.   Watch that Fact


CLIPS provides several commands to help you debug programs. One command allows you to  continuously watch facts being asserted and retracted. This is more convenient than having to  type in a (facts) command over and over again and trying to figure out what’s changed in the fact list.




<p class="code-label">To start watching facts, enter the command (watch facts) as shown in the following example.</p>
```racket
CLIPS> (clear)
CLIPS> (watch facts)
CLIPS> (assert (animal-is duck))
==> f-1 (animal-is duck)
<Fact-1>
CLIPS>
```


The right double arrow symbol, `==>`, means that a fact is entering memory while the left  double arrow indicates a fact is leaving memory, as shown following.


```racket
CLIPS> (reset)
<== f-1 (animal-is duck)
CLIPS> (assert (animal-is duck))
==> f-1 (animal-is duck)
<Fact-1>
CLIPS> (retract 1)
<== f-1 (animal-is duck)
CLIPS> (facts)
CLIPS>
```



The (watch facts) command provides a record that shows the dynamic; or changing state of the  fact-list. In contrast, the (facts) command show the static state of the fact-list since it displays the  current contents of the fact-list. To turn off watching facts, enter (unwatch facts).



There are a number of things you can watch. These include the following, which are  described in more detail in the CLIPS Reference Manual. The comment in CLIPS begins with a  semicolon. Everything after the semicolon is ignored by CLIPS.



<p class="code-label">The (watch facts) command provides a record that shows the dynamic; or changing state of the  fact-list</p>
```racket
(watch facts)
; instances used with objects
(watch instances)
; slots used with objects
(watch slots)
(watch rules)
(watch activations)
; messages used with objects
(watch messages)
; message-handlers used with objects
(watch message-handlers)
(watch generic-functions)
(watch methods)
(watch deffunctions)
; compilations are watched by default
(watch compilations)
(watch statistics)
(watch globals)
(watch focus)
; all watches everything
(watch all)
```


As you use more of the capabilities of CLIPS, you’ll find these (watch) commands very helpful in  debugging. To turn off a (watch) command, enter an unwatch command. For example, to turn  off watching compilations, enter (unwatch compilations).







