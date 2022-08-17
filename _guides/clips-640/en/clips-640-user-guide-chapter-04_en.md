---
layout: guide
ref:  c640ug04
lang:  en
idiom:  us-EN
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug

toc:  true

title:  "CLIPS 6.4 User`s Guide"
subtitle:  "The type of rules that you’ve seen so far illustrates simple matching of patterns to facts. In this  chapter, you’ll learn very powerful ways to match and manipulate facts."
headtitle:  'Variable Interests'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Giarratano, Joseph C. Ph.D.'
department:  
authors:

departments:

chapter:  4
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'
date_published:  '2021-04-09'
date_modified:  '2022-08-17'

---




  
#  **Chapter 4**
  

  

#  4. Variable Interests



   
>  Nothing changes more than change




The type of rules that you’ve seen so far illustrates simple matching of patterns to facts. In this  chapter, you’ll learn very powerful ways to match and manipulate facts.




##  4.1. Let’s Get Variable




Just as with other programming languages, CLIPS has **variables** to store values. Unlike a fact,  which is **static** or unchanging, the contents of a variable are **dynamic** as the values assigned to  it change. In contrast, once a fact is asserted, it’s fields can only be modified by retracting and  asserting a new fact with the changed fields, Even the modify action (described later in the chapter  on deftemplate) acts by retracting and asserting a modified fact, as you can see by checking the  fact-index.




The name of a variable, or **variable identifier**, is always written by a question mark  followed by a symbol that is the name of the variable.




<p class="code-label">The general format is</p>
```scheme
  ?<variable-name>
``` 



Global variables, to be described in more detail later, have a slightly different syntax.




<p class="code-label">Just as in other programming languages, variable names should be meaningful for good style.  Some examples of valid variable names follow.</p>
```scheme
?x
?noun
?color
?sensor
?valve
?ducks-eaten
``` 







<p class="code-label">Before a variable can be used, it should be assigned a value. As an example of a case where a  value is not assigned, try to enter the following and CLIPS will respond with the error message  shown.</p>
```scheme
CLIPS> (unwatch all)
CLIPS> (clear)
CLIPS>
(defrule test
=>
(printout t ?x crlf))

[PRCCODE3] Undefined variable x
referenced in RHS of defrule.

ERROR:
(defrule MAIN::test
=>
(printout t ?x crlf))
CLIPS>
``` 



**CLIPS** gives an error message when it cannot find a value **bound** to ?x. The term bound means  the assignment of a value to a variable. Only global variables are bound in all rules. All other  variables are only bound within a rule. Before and after a rule fires, non-global variables are not  bound and so CLIPS will give an error message if you try to query a non-bound variable.




##  4.2. Be Assertive




One common use of variables is to match a value on the LHS and then assert this bound  variable on the RHS. For example, enter


<p class="code-label"></p>
```scheme
(defrule make-quack
(duck-sound ?sound)
=>
(assert (sound-is ?sound)))
``` 


Now assert (duck-sound quack), then (run) the program. Check the facts and you’ll see that the  rule has produced (sound-is quack) because the variable ?sound was bound to quack.

<p class="code-label">Of course, you also can use a variable more than once. For example, enter the following. Be  sure to do a (reset) and assert (duck-sound quack) again.</p>
```scheme
(defrule make-quack
(duck-sound ?sound)
=>
(assert (sound-is ?sound ?sound)))
```

When the rule fires, it will produce (sound-is quack quack) since the variable ?sound is used twice.

##  4.3. What the Duck Said

<p class="code-label">Variables also are used commonly in printing output, as in</p>
```scheme
(defrule make-quack
(duck-sound ?sound)
=>
(printout t "The duck said "
?sound crlf))
```


Do a (reset), enter this rule, and assert the fact and then (run) to find out what the duck said. How  would you modify the rule to put double quotes around quack in the output?



<p class="code-label">More than one variable may be used in a pattern, as the following example shows.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule whodunit
(duckshoot ?hunter ?who)
=>
(printout t ?hunter " shot "
?who crlf))
CLIPS> (assert (duckshoot Brian duck))
<Fact-1>
; Duck dinner tonight!
CLIPS> (run)
Brian shot duck
CLIPS> (assert (duckshoot duck Brian))
<Fact-2>
; Brian dinner tonight!
CLIPS> (run)
duck shot Brian
; Missing third field
CLIPS> (assert (duckshoot duck))
<Fact-3>
; Rule doesn't fire,
; no output
CLIPS> (run)
CLIPS>
``` 



Notice what a big difference the order of fields makes in determining who shot who. You can also  see that the rule did not fire when the fact (duckshoot duck) was asserted. The rule was not  activated because no field of the fact matched the second pattern constraint, ?who.




##  4.4. The Happy Bachelor




Retraction is very useful in expert systems and usually done on the RHS rather than at the top level. Before a fact can be retracted, it must be specified to CLIPS. To retract a fact from a rule,  the **fact-address** first must be bound to a variable on the LHS.




There is a big difference between binding a variable to the contents of a fact and binding a  variable to the fact-address. In the examples that you’ve seen such as (duck-sound ?sound), a  variable was bound to the value of a field. That is, ?sound was bound to quack. However, if you  want to remove the fact whose contents are (duck-sound quack), you must first tell CLIPS the  address of the fact to be retracted.


The fact-address is specified using the **left arrow**, “<-”. To create this, just type a “<”  symbol followed by a “-”. As an example of fact retraction from a rule,ç

<p class="code-label">As an example of fact retraction from a rule,</p>
```scheme
CLIPS> (clear)
CLIPS> (assert (bachelor Dopey))
<Fact-1>
CLIPS> (facts)
f-1 (bachelor Dopey)
For a total of 1 fact.
CLIPS>
(defrule get-married
?duck <- (bachelor Dopey)
=>
(printout t "Dopey is now happily married "
?duck crlf)
(retract ?duck))
CLIPS> (run)
Dopey is now happily married <Fact-1>
CLIPS> (facts)
CLIPS>
``` 



Notice that the (printout) prints the fact-index of ?duck, <Fact-1>, since the left arrow bound the  address of the fact to ?duck. Also, there is no fact (bachelor Dopey) because it has been retracted.




<p class="code-label">Variables can be used to pick up a fact value at the same time as an address, as shown in the  following example. For convenience, a (deffacts) has also been defined.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule marriage
?duck <- (bachelor ?name)
=>
(printout t ?name
 is now happily married
crlf)
(retract ?duck))
CLIPS>
(deffacts good-prospects
(bachelor Dopey)
(bachelor Dorky)
(bachelor Dicky))
CLIPS> (reset)
CLIPS> (run)
Dicky is now happily married
Dorky is now happily married
Dopey is now happily married
CLIPS>
``` 



Notice how the rule fired on all facts that matched the pattern (bachelor ?name). CLIPS also has  a function called **fact-index** which can be used to return the fact index of a fact address.




##  4.5. It’s Not Important




Instead of binding a field value to a variable, the presence of a nonempty field can be detected  alone using a **wildcard**. For example, suppose you’re running a dating service for ducks, and a  duckette asserts that she only dates ducks whose first name is Dopey. Actually, two criteria are in this specification since there is an implication that the duck must have more than one name. So a  plain (bachelor Dopey) isn’t adequate because there is only one name in the fact.




This type of situation, in which only part of the fact is specified, is very common and very  important. To solve this problem, a wildcard can be used to match the Dopeys.




The simplest form of wildcard is called a **single-field wildcard** and is shown by a question  mark, “?”. The “?” is also called a **single-field constraint**.




<p class="code-label">A single-field wildcard stands for  exactly one field, as shown following.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule dating-ducks
(bachelor Dopey ?)
=>
(printout t "Date Dopey"
crlf))
CLIPS>
(deffacts duck
(bachelor Dicky)
(bachelor Dopey)
(bachelor Dopey Mallard)
(bachelor Dinky Dopey)
(bachelor Dopey Dinky Mallard))
CLIPS> (reset)
CLIPS> (run)
Date Dopey
CLIPS>
``` 



The pattern includes a wildcard to indicate that Dopey’s last name is not important. So long as  the first name is Dopey and there is any last name (but no middle names), the rule will be satisfied  and fire. Because the pattern has three fields of which one is a single-field wildcard, only facts of  exactly three fields can satisfy it. In other words, only Dopeys with exactly two names can satisfy  this duckette.




<p class="code-label">Suppose you want to specify Dopeys with exactly three names? All that you’d have to do is  write a pattern like</p>
```scheme
(bachelor Dopey ? ?)
or, if only persons with three names whose middle name was Dopey,
(bachelor ? Dopey ?)
or, if only the last name was Dopey, as in the following:
(bachelor ? ? Dopey)
``` 



Another interesting possibility occurs if Dopey must be the first name, but only those Dopeys with  two or three names are acceptable. One way of solving this problem is to write two rules.



<p class="code-label">For  example</p>
```scheme
(defrule eligible
(bachelor Dopey ?)
=>
(printout t "Date Dopey" crlf))
(defrule eligible-three-names
(bachelor Dopey ? ?)
=>
(printout t "Date Dopey" crlf))
``` 



Enter and run this and you’ll see that Dopeys with both two and three names are printed. Of  course, if you don’t want anonymous dates, you need to bind the Dopey names with a variable  and print them out.




##  4.6. Going Wild




Rather than writing separate rules to handle each field, it’s much easier to use the **multifield wildcard**. This is a dollar sign followed by a question mark, **“$?”**, and represents zero or more  fields. Notice how this contrasts with the single-field wildcard which must match exactly one field.




<p class="code-label">The two rules for dates can now be written in a single rule as follows.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule dating-ducks
(bachelor Dopey $?)
=>
(printout t "Date Dopey" crlf))
CLIPS>
(deffacts duck
(bachelor Dicky)
(bachelor Dopey)
(bachelor Dopey Mallard)
(bachelor Dinky Dopey)
(bachelor Dopey Dinky Mallard))
CLIPS> (reset)
CLIPS> (run)
Date Dopey
Date Dopey
Date Dopey
CLIPS>
``` 



Wildcards have another important use because they can be attached to a symbolic field to create  a variable such as ?x, $?x, ?name, or $?name. The variable can be a **single-field variable** or a  **multifield variable** depending on whether a “?” or “$?” is used on the LHS. Note that on the  RHS only a ?x is used, where the “x” can be any variable name. You can think of the “$” as a  function whose argument is a single-field wildcard or a single-field variable and returns a  multifield wildcard or a multifield variable, respectively.





<p class="code-label">As an example of a multifield variable, the following version of the rule also prints out the  name field(s) of the matching fact because a variable is equated to the name field(s) that match:</p>
```scheme
CLIPS>
(defrule dating-ducks
(bachelor Dopey $?name)
=>
(printout t "Date Dopey " ?name crlf))
CLIPS> (reset)
CLIPS> (run)
Date Dopey (Dinky Mallard)
Date Dopey (Mallard)
Date Dopey ()
CLIPS>
``` 



As you can see, on the LHS, the multifield pattern is $?name but is ?name when used as a variable  on the RHS. When you enter and run, you’ll see the names of all eligible Dopeys. The multifield  wildcard takes care of any number of fields. Also, notice that multifield values are returned  enclosed in parentheses.




Suppose you wanted a match of all ducks who had a Dopey somewhere in their name, not  necessarily as their first name.




<p class="code-label">The following version of the rule would match all facts with a  Dopey in them and then print out the names:</p>
```scheme
CLIPS>
(defrule dating-ducks
(bachelor $?first Dopey $?last)
=>
(printout t "Date "
?first
 Dopey 
?last crlf))
CLIPS> (reset)
CLIPS> (run)
Date () Dopey (Dinky Mallard)
Date (Dinky) Dopey ()
Date () Dopey (Mallard)
Date () Dopey ()
CLIPS>
``` 



The pattern matches any names that have a Dopey anywhere in them.




Single- and multifield wildcards can be combined.




<p class="code-label">For example, the pattern</p>
```scheme
(bachelor ? $? Dopey ?)
``` 



means that the first and last names can be anything and that the name just prior to the last must  be Dopey. This pattern also requires that the matching fact will have at least four fields, since the  “$?” matches zero or more fields and all the others must match exactly four.




Although multifield variables can be essential for pattern matching in many cases, their  overuse can cause much inefficiency because of increased memory requirements and slower  execution.





>    &clubs; _As a general rule of style, you should use $? only when you don’t know the length of fields. Do not use $?  simply as a typing convenience._




##  4.7. The Ideal Bachelor




Variables used in patterns have an important and useful property, which can be stated as follows.





>    &clubs; _The first time a variable is bound it retains that value only within the rule, both on the LHS and also on the  RHS, unless changed on the RHS._




<p class="code-label">For example, in the rule below</p>
```scheme
(defrule bound
(number-1 ?num)
(number-2 ?num)
=>)
If there are some facts
f-1 (number-1 0)
f-2 (number-2 0)
f-3 (number-1 1)
f-4 (number-2 1)
``` 



then the rule can only be activated by the pair f-1, f-2, and the other pair f-3, f-4. That is, fact f-1  cannot match with f-4 because when ?num is bound to 0 in the first pattern, the value of ?num in  the second pattern also must be 0. Likewise, when ?num is bound to 1 in the first pattern, the  value of ?num in the second pattern must be 1. Notice that the rule will be activated twice by these  four facts: one activation for the pair f-1, f-2, and the other activation for the pair f-3, f-4.




As a more practical example, enter the following rule. Notice that the same variable, ?name,  is used in both patterns.




<p class="code-label">Before doing a (reset) and (run), also enter a (watch all) command so that  you can see what happens during execution.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule ideal-duck-bachelor
(bill big ?name)
(feet wide ?name)
=>
(printout t "The ideal duck is "
?name crlf))
CLIPS>
(deffacts duck-assets
(bill big Dopey)
(bill big Dorky)
(bill little Dicky)
(feet wide Dopey)
(feet narrow Dorky)
(feet narrow Dicky))
CLIPS> (watch facts)
CLIPS> (watch activations)
CLIPS> (reset)
==> f-1 (bill big Dopey)
==> f-2 (bill big Dorky)
==> f-3 (bill little Dicky)
==> f-4 (feet wide Dopey)
==> Activation 0 ideal-duck-bachelor: f-1,f-4  '==> f-5 (feet narrow Dorky)
==> f-6 (feet narrow Dicky)
CLIPS> (run)
The ideal duck is Dopey
CLIPS>
``` 



When the program is run, the first pattern matches Dopey and Dorky since they both have big  bills. The variable ?name is bound to each name. When CLIPS tries to match the second pattern  of the rule, only the variable ?name which is bound to Dopey also satisfies the second pattern of  (feet wide).




##  4.8. The Lucky Duck




Many situations occur in life where it’s wise to do things in a systematic manner. That way, if  your expectations don’t work out you can try again systematically (such as the common algorithm  for finding the Perfect Spouse by getting married over and over again).




One way of being organized is to keep a list. (Note: if you really want to impress people, show  them a list of your lists.) In our case, we’ll keep a list of duck bachelors, with the most likely  prospect for matrimony at the front. Once an ideal duck bachelor has been identified, we’ll shoot  him up to the front of the list as the lucky duck.




<p class="code-label">The following program shows how this can be done by adding a couple of rules to the ideal duck-bachelor rule.</p>
```scheme
(defrule ideal-duck-bachelor
(bill big ?name)
(feet wide ?name)
=>
(printout t "The ideal duck is "
?name crlf)
(assert (move-to-front ?name)))
(defrule move-to-front
?move-to-front <- (move-to-front ?who)
?old-list <-
(list $?front ?who $?rear)
=>
(retract ?move-to-front ?old-list)
(assert (list ?who ?front ?rear))
(assert (change-list yes)))
(defrule print-list
?change-list <- (change-list yes)
(list $?list)
=>
(retract ?change-list)
(printout t "List is : " ?list crlf))
(deffacts duck-bachelor-list
(list Dorky Dinky Dicky))
(deffacts duck-assets
(bill big Dicky)
(bill big Dorky)
(bill little Dinky)
(feet wide Dicky)
(feet narrow Dorky)
(feet narrow Dinky))
``` 



<p class="code-label">The original list is given in the duck-bachelor-list deffacts. When the program is run, it will  provide a new list of likely candidates.</p>
```scheme
CLIPS> (unwatch all)
CLIPS> (reset)
CLIPS> (run)
The ideal duck is Dicky
List is : (Dicky Dorky Dinky)
CLIPS>
``` 



Notice the assertion (change-list yes) in the move-to-front rule. Without this assertion, the print list rule would always fire on the original list. This assertion is an example of a **control fact** made to control the firing of another rule. Control facts are very important in controlling the  activation of certain rules, and you should study this example carefully to understand why it’s  used. Another method of control is modules, as discussed in the CLIPS Reference Manual.




The move-to-front rule removes the old list and asserts the new list. If the old list was not  retracted, two activations would be on the agenda for the print-list rule but only one would fire.  Only one will fire because the print-list rule removes the control fact required for the other activation of the same rule. You would not know in advance which one would fire, so the old list  might be printed instead of the new list.


