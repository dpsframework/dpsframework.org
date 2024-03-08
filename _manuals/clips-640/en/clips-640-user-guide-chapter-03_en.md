---
layout: manual
ref:  c640ug03
lang:  en
idiom:  us-EN
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug

toc:  true

title:  "CLIPS 6.4 User`s Guide"
subtitle:  "In the first two chapters, you learned the fundamentals of CLIPS. Now you will see how to build on that foundation to create more powerful programs."
headtitle:  'Adding Details'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Giarratano, Joseph C. Ph.D.'
department:  
authors:

departments:

chapter:  3
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'
date_published:  '2021-04-09'
date_modified:  '2022-08-14'

---




  
#  **Chapter 3**
  

  

#  3. Adding Details



   
>It’s not the big picture that is the problem — it’s the details




In the first two chapters, you learned the fundamentals of CLIPS. Now you will see how to build  on that foundation to create more powerful programs.




##  3.1. Stop And Go




Until now, you’ve only seen the simplest type of program consisting of just one rule. However,  expert systems consisting of only one rule are not very useful. Practical expert systems may  consist of hundreds or thousands of rules. Let’s now take a look at an application requiring  multiple rules.




Suppose you wanted to write an expert system to determine how a mobile robot should  respond to a traffic light. It is best to write this type of problem using multiple rules.




<p class="code-label">For example,  the rules for the red and green light situations can be written as follows.</p>
```scheme
  (defrule red-light
(light red)
=>
(printout t "Stop" crlf))

(defrule green-light
(light green)
=>
(printout t "Go" crlf))

``` 

After the rules have been entered into CLIPS, assert a fact (light red) and run. You’ll see “Stop”  printed. Now assert a (light green) fact and run. You should see “Go” printed.




##  3.2. Take a Walk




If you think about it, other possibilities beside the simple red, green, and yellow cases exist. Some  traffic lights also have a green arrow for protected left turns. Some have a hand that lights up to indicate whether a person can walk or not. Some have signs that say walk or don’t walk. So  depending on whether our robot is walking or driving, it may have to pay attention to different  signs.




The information about walking or driving must be asserted in addition to information about  the status of the light. Rules can be made to cover these conditions, but they must have more  than one pattern.




<p class="code-label">For example, suppose we want a rule to fire if the robot is walking and if the  walk-sign says walk. A rule could be written as follows:</p>
```scheme
(defrule take-a-walk
(status walking)
(walk-sign walk)
=>
(printout t "Go" crlf))

```


The above rule has two patterns. Both patterns must be satisfied by facts in the fact-list for the  rule to fire. To see how this works, enter the rule and then assert the facts (status walking) and  (walk-sign walk). When you (run), the program will print out “Go” since both patterns are  satisfied and the rule is fired.




You can have any number of patterns or actions in a rule. The important point to realize is  that the rule is placed on the agenda only if all the patterns are satisfied by facts. This type of  restriction is called a **logical AND conditional element (CE)** in reference to the AND  relation of Boolean logic. An AND relation is said to be true only if all its conditions are true.




   Because the patterns are of the logical AND type, the rule will not fire if only one of the  patterns is satisfied. All facts must be present before the LHS of a rule is satisfied and the rule is  placed on the agenda.




##  3.3. A Question of Strategy




The word **strategy** was originally a military term for the planning and operations of warfare.  Today, the term strategy is commonly used in business (because business is war) to refer to the  high-level plans of an organization in achieving its goals, e.g., “Make a lot of money by selling  more greasy hamburgers than anyone else in the world!”




In expert systems, one use of the term strategy is in conflict resolution of activations. Now you  might say, “Well, I’ll just design my expert system so that only one rule can possibly be activated  at one time. Then there is no need for conflict resolution.” The good news is that if you succeed,  conflict resolution is indeed unnecessary. The bad news is that this success proves that your application can be well represented by a sequential program. So you should have coded it in C,  Java, or Ada in the first place and not bothered writing it as an expert system.




CLIPS offers seven different modes of conflict resolution: depth, breadth, LEX, MEA,  complexity, simplicity, and random. It’s difficult to say that one is clearly better than another  without considering the specific application. Even then, it may be difficult to judge which is  “best.” For more information on the details of these strategies, see the _CLIPS Reference Manual_.




The **depth strategy** is the standard **default strategy** of CLIPS. The default setting is  automatically set when CLIPS is first started. Afterwards, you can change the default setting. In  the depth strategy, new activations are placed on the agenda after activations with higher  salience, but before activations with equal or lower salience. All this simply means is that the  agenda is ordered from highest to lowest salience.




>   &clubs;   _In this book, all discussions and examples will assume depth strategy._




Now that all these different optional settings are available, be sure that before you run an expert  system developed by someone else, that your settings are the same as theirs. Otherwise, you may  find the operation is inefficient or even incorrect. In fact, it’s a good idea to explicitly encode all  the settings in any system that you develop so that it will be configured properly.




##  3.4. Gimme Deffacts




As you work with CLIPS, you may become tired of typing in the same assertions from the top level. If you are going to use the same assertions every time a program is run, you can first load  assertions from a disk using a batch file. An alternative way to enter facts is by using the define  facts keyword, **deffacts**.




<p class="code-label">For example,</p>
```scheme
CLIPS> (unwatch facts)
CLIPS> (unwatch activations)
CLIPS> (clear)
CLIPS>
(deffacts walk "Some facts about walking"
   ; status fact to be asserted
    (status walking)
    ; walk-sign fact to be asserted
    (walk-sign walk))
CLIPS> (reset)
; reset causes facts from
; deffacts to be asserted
CLIPS> (facts)
f-1 (status walking)
f-2 (walk-sign walk)
For a total of 2 facts.
CLIPS>
```



The required name of this deffacts statement, walk, follows the deffacts keyword. Following the  name is an optional comment in double quotes. Like the optional comment of a rule, the  (deffacts) comment will be retained with the (deffacts) after it’s been loaded by CLIPS. After the  name or comment are the facts that will be asserted in the fact-list. The facts in a deffacts  statement are asserted using the CLIPS (reset) command.




The (reset) has an advantage compared to a (clear) command in that (reset) doesn’t get rid of  all the rules. The (reset) leaves your rules intact. Like (clear), it removes all activated rules from  the agenda and also removes all old facts from the fact-list. Giving a (reset) command is a  recommended way to start off program execution, especially if the program has been run before  and the fact-list is cluttered with old facts.




In summary, the (reset) does two things for facts.


  

1. It removes existing facts from the fact-list, which may remove activated rules from the  agenda.


2. It asserts facts from existing (deffacts) statements.




Actually, the (reset) also does corresponding operations on objects. It deletes instances and  asserts instances from **definstances**.




##  3.5. Selective Elimination




The **undeffacts** command excises a (deffacts) from asserting facts by eliminating the deffacts  from memory.



<p class="code-label">For example,</p>
```scheme
CLIPS> (undeffacts walk)
CLIPS> (reset)
CLIPS> (facts)
CLIPS>

``` 


This example demonstrates how the (deffacts) walk has been excised. To restore a deffacts  statement after an (undeffacts) command, you must enter the deffacts statement again. In  addition to facts, CLIPS also allows you to eliminate rules selectively by using the **undefrule**.




##  3.6. Watch It!




You can **watch rules** firing and **watch activations** on the agenda. The **watch statistics** prints information about the number of rules fired, run time, rules per second, mean number of  facts, maximum number of facts, mean number of activations, and maximum number of  activations. The statistics information may be useful in **tuning up** an expert system to optimize  its speed. Another command, called **watch compilations**, shows information when rules are  being loaded. The watch all command will watch everything.




Printing of watch information to the screen or to disk with the **dribble** command will slow  down your program somewhat because CLIPS uses more time to print or to save to disk. The  **dribble-on** command will store all input and output entered at the command prompt to a disk  file until the **dribble-off** command is entered. This is convenient in providing a permanent  record of everything that happens.




These commands are as follows.



```scheme
(dribble-on <filename>)
(dribble-off <filename>)
```


Another useful debugging command is (run) which takes an optional argument of the number of  rule firings. For example, a (run 21) command would tell CLIPS to run the program and then  stop after 21 rule firings. A (run 1) command allows you to step through a program firing one rule  at a time.




Just like many other programming languages, CLIPS also gives you the capability of setting  breakpoints. A breakpoint is simply an indicator to CLIPS to stop execution just prior to  executing a specified rule. A breakpoint is set by the set-break command. The remove-break command will remove a breakpoint that has been set. The show-breaks will list all the rules  which have breakpoints set.




The syntax of these commands for the argument `<rulename>` is  shown following.



```scheme
(set-break <rulename>)
(remove-break <rulename>)
(show-breaks)
```



##  3.7. A Good Match




You may encounter a situation in which you are certain a rule should be activated but isn’t. While  it is possible that this is due to a bug in CLIPS, it’s not very likely because of the great skill of the  people who programmed CLIPS (NOTE: PAID COMMERCIAL ANNOUNCEMENT FOR  THE DEVELOPERS).




In most cases, the problem occurs because of the way that you wrote the rule. As an aid to  debugging, CLIPS has a command called matches that can tell you which patterns in a rule  match facts. Patterns which do not match prevent the rule from becoming activated. One  common reason that a pattern won’t match a fact results from misspelling an element in the  pattern or in the assertion of the fact.




<p class="code-label">The argument of (matches) is the name of the rule to be checked for matches. To see how  (matches) works, first (clear), then enter the following rule.</p>
```scheme
(defrule take-a-vacation
; Conditional element 1
(work done)
; Conditional element 2
(money plenty)
; Conditional element 3
(reservations made)
=>
(printout t "Let's go!!!" crlf))

```


The following shows how (matches) is used. Enter the commands as shown. Notice that (watch  facts) is turned on.




<p class="code-label">This is a good idea when you are asserting facts manually since it gives you an  opportunity to check the spelling of facts.</p>
```scheme
CLIPS> (watch facts)
CLIPS> (assert (work done))
 ==> f-1 (work done)
<Fact-1>
CLIPS> (matches take-a-vacation)
Matches for Pattern 1
f-1
Matches for Pattern 2
None
Matches for Pattern 3
None
; CE is conditional element
Partial matches for CEs 1 - 2
None
Partial matches for CEs 1 - 3
None
Activations
None
; The return value indicates
; the total patterns
; matched, the total partial
; matches, and the
; total activations
(1 0 0)
CLIPS>
``` 


The fact with fact-identifier f-1 matches the first pattern or conditional element in the rule and is  reported by (matches). Given that a rule has N patterns, the term partial matches refers to any  set of matches of the first N-1 patterns with facts. That is, the partial matches begin with the first  pattern in a rule and end with any pattern up to but not including the last (Nth) pattern. As soon as one partial match cannot be made, CLIPS does not check any further. For example, a rule  with four patterns would have partial matches of the first and second patterns and also of the  first, second, and third patterns. If all N patterns match, the rule will be activated.




##  3.8. Other Features




Some additional commands are useful with deffacts. For example, the command **list-deffacts** will list the names of currently loaded deffacts in CLIPS. Another useful command is  **ppdeffacts** which prints the facts stored in a deffacts.




Other functions allow you to manipulate strings easily:


-  **assert-string**: Performs a string assertion by taking a string as argument and asserted as a  non-string fact.


-  **str-cat**: Constructs a single-quoted string from individual items by string concatenation.  str-index: Returns a string index of the first occurrence of a substring.


-  **sub-string**: Returns a substring from a string.


-  **str-compare**: Performs a string compare.


-  **str-length**: Returns the string length which is the length of a string.


-  **sym-cat**: Returns a concatenated symbol.




If you want to printout a multifield variable without parentheses, the simplest way is by using the  string implode function, **implode$**.
