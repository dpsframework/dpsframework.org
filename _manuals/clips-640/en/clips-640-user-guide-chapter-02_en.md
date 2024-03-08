---
layout: manual
ref:  c640ug02
lang:  en
idiom:  us-EN
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug
toc:  true
title:  "CLIPS 6.4 User's Guide"
headtitle:  'Following the Rules'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Giarratano, Joseph C. Ph.D.'
department:  
authors:



departments:



chapter:  2
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'




date_published:  '2021-04-09'
date_modified:  '2022-08-09'

---




  
#  **Chapter 2**
  

>  

#  2. Following the Rules



   
>If you want to get anywhere in life, don’t break the rules — make the rules!




##  2.1. Making Good Rules




To accomplish useful work, an expert system must have rules as well as facts. Since you’ve seen  how facts are asserted and retracted, it’s time to see how rules work. A rule is similar to an IF  THEN statement in a procedural language like Java, C, or Ada.




<p class="code-label">An IF THEN rule can be  expressed in a mixture of natural language and computer language as follows:</p>
```scheme
IF certain conditions are true
THEN execute the following actions

``` 


Another term for the above statement is **pseudocode**, which literally means false code. While  pseudocode cannot be directly executed by the computer, it serves as a very useful guide to  writing executable code. Pseudocode is also helpful in documenting rules. A translation of rules  from natural language to CLIPS is not very difficult if you keep this IF THEN analogy in mind.  As your experience with CLIPS grows, you’ll find that writing rules in CLIPS becomes easy. You  can either type rules directly into CLIPS or load rules in from a file of rules created by a text  editor.



  
<p class="code-label">The pseudocode for a rule about duck sounds might be</p>
```scheme
IF the animal is a duck
THEN the sound made is quack
``` 



The following is a fact, and a rule named duck which is the pseudocode above expressed in CLIPS  syntax. The name of the rule follows immediately after the keyword defrule.




<p class="code-label">Although you can  enter a rule on a single line, it’s customary to put different parts on separate lines to aid  readability and editing.</p>
```scheme
CLIPS> (unwatch facts)
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS>
(defrule duck
    (animal-is duck)
=>
    (assert (sound-is quack)))
CLIPS>

``` 


If you type in the rule correctly as shown, you should see the CLIPS prompt reappear.  Otherwise, you’ll see an error message. If you get an error message, it is likely that you misspelled  a keyword or left out a parenthesis. Remember, the number of left and right parentheses always  must match in a statement.





The same rule is shown following with comments added to match the parts of the rule. Also  shown is the optional **rule-header** comment in quotes, "Here comes the quack". There can be  only one rule-header comment and it must be placed after the rule name and before the first  **pattern**. Although we’re only discussing pattern matching against facts now, more generally a  pattern can be matched against a **pattern entity**. A pattern entity is either a fact or an instance of  a user-defined class. Pattern matching on objects will be discussed later.




CLIPS tries to match the pattern of the rule against a pattern entity. Of course, white space  consisting of spaces, tabs, and carriage returns may be used to separate the elements of a rule to  improve readability. Other comments begin with a semicolon and continue until the carriage  return key is pressed to terminate a line.




<p class="code-label">Comments are ignored by CLIPS:</p>
```scheme
; Rule header
(defrule duck
    ; Comment
    "Here comes the quack"
     ; Pattern
        (animal-is duck)
=> ; THEN arrow
     ; Action  
     (assert (sound-is quack)))

``` 



>    &clubs; _Only one rule name can exist at one time in CLIPS._





Entering the same rule name, in this case `duck`, will replace any existing rule with that name.  That is, while there can be many rules in CLIPS, there can be only one rule which is named  `duck`. This is analogous to other programming languages in which only one procedure name  can be used to uniquely identify a procedure.





<p class="code-label">The general syntax of a rule is shown following.</p>
```scheme
(defrule rule_name "optional_comment"
(pattern_1) ; Left-Hand Side (LHS)
(pattern_2) ; of the rule consisting
.           ; of elements before
.           ; the "=>"
.
(pattern_N)
=>
(action_1)  ; Right-Hand Side (RHS)
(action_2)  ; of the rule consisting
.           ; of elements after
.           ; the "=>". The last ")"
.           ; balances the opening
(action_M)) ; "(" to the left of
; "defrule". Be sure all
; your parentheses
; balance or you will
; get error messages

``` 


The entire rule must be surrounded by parentheses. Each of the rule patterns and **actions** must  be surrounded by parentheses. An action is actually a function which typically has no **return  value**, but performs some useful action, such as an (assert) or (retract). For example, an action  might be (assert (duck)). Here the function name is `assert` and its argument is `duck`. Notice  that we don’t want any return value such as a number. Instead, we want the fact (duck) to be  asserted. A **function** in CLIPS is a piece of executable code identified by a specific name, which  returns a useful value or performs a useful side-effect, such as (printout).




   A rule often has multiple patterns and actions. The number of patterns and actions do not  have to be equal, which is why different indices, N and M, were chosen for the rule patterns and  actions.




Zero or more patterns may be written after the rule header. Each pattern consists of one or  more fields. In the duck rule, the pattern is (animal-is duck), where the fields are `animal-is` and  `duck`. CLIPS attempts to match the patterns of rules against facts in the fact-list. If all the  patterns of a rule match facts, the rule is **activated** and put on the **agenda**. The agenda is a  collection of **activations** which are those rules which match pattern entities. Zero or more  activations may be on the agenda.




The symbol `=>` that follows the patterns in a rule is called an arrow. The arrow  represents the beginning of the THEN part of an IF-THEN rule (and may be read as `implies`).




The last part of a rule is the list of zero or more actions that will be executed when the rule  fires. In our example, the one action is to assert the fact (sound-is quack). The term fires means  that CLIPS has selected a certain rule for execution from the agenda.




>    &clubs; _A program will cease execution when no activations are on the agenda._




When multiple activations are on the agenda, CLIPS automatically determines which activation  is appropriate to fire. CLIPS orders the activations on the agenda in terms of increasing priority  or salience.





The part of the rule before the arrow is called the left-hand side **(LHS)** and the part of the  rule after the arrow is called the right-hand side **(RHS)**. If no patterns are specified, CLIPS  automatically activates the rule when a **(reset)** command is entered.




##  2.2. Let’s Get Quacking




CLIPS always executes the actions on the RHS of the highest priority rule on the agenda. This  rule is then removed from the agenda and the actions of the new highest salience rule is  executed. This process continues until there are no more activations or a command to stop is  encountered.




<p class="code-label">You can check what’s on the agenda with the **agenda** command. For example:</p>
```scheme
CLIPS> (agenda)
0 duck: f-1
For a total of 1 activation.
CLIPS>

``` 


The first number `0` is the salience of the `duck` activation, and `f-1` is the fact-identifier of  the fact, (animal-is duck), which matches the activation. If the salience of a rule is not declared  explicitly, CLIPS assigns it the default value of zero, where the possible salience values range  from -10,000 to 10,000. In this book, we’ll use the definition of the term **default** as meaning the  standard way.





<p class="code-label">If there is only one rule on the agenda, that rule will fire. Since the LHS pattern of the duck sound rule is</p>
```scheme
(animal-is duck)

``` 

this pattern will be satisfied by the fact (animal-is duck) and so the duck-sound rule should fire.




Each field of the pattern is said to be a **literal constraint**. The term **literal** means having  a constant value, as opposed to a variable whose value is expected to change. In this case, the  literals are `animal-is` and `duck`.




To make a program **run**, just enter the run command. Type (run) and press the carriage  return key.


<p class="code-label">Then do a (facts) to check that the fact was asserted by the rule.</p>
```scheme
CLIPS> (run)
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (sound-is quack)
For a total of 2 facts.
CLIPS>

``` 


Before going on, let’s save the duck rule with the **save** command so that you don’t have to type it  in again (if you haven’t already saved it in an editor).



<p class="code-label">Just enter a command such as:</p>
```scheme
(save "duck.clp")

``` 



to save the rule from CLIPS memory to disk and name the file `duck.clp` where the `.clp` is  simply a convenient extension to remind us this is a CLIPS source code file. Note that saving the  code from CLIPS memory like this will only preserve the optional rule-header comment in  quotes and not any semicolon comments.




##  2.3. Kick your Duck




An interesting question may occur to you at this time. What if you (run) again? There is a rule  and a fact which satisfies the rule, so the rule should fire. However, if you try this and (run) again,  you’ll see that the rule won’t fire. This may be somewhat frustrating. However, before you do  something drastic to ease your frustration — like kicking your pet duck — you need to know a  little more about some basic principles of expert systems.



A rule is activated if its patterns are matched by a:

1. a brand new pattern entity that did not exist before or,
2. a pattern entity that did exist before but was retracted and reasserted, i.e., a `clone` of  the old pattern entity, and thus now a new pattern entity.




The rule, and indices of the matching patterns, is the activation. If either the rule or the pattern  entity, or both change, the activation is removed. An activation may also be removed by a  command or an action of another rule that fired before and removed the conditions necessary for  activation.




The Inference Engine sorts the activations according to their salience. This sorting process is  called conflict resolution because it eliminates the conflict of deciding which rule should fire  next. CLIPS executes the RHS of the rule with the highest salience on the agenda, and removes  the activation. This execution is called firing the rule in analogy with the firing of a neuron. A  neuron emits a voltage pulse when an appropriate stimulus is applied. After a neuron fires, it  undergoes refraction and cannot fire again for a certain period of time. Without refraction,  neurons would just keep firing over and over again on exactly the same stimulus.




Without refraction, expert systems always would be caught in trivial loops. That is, as soon as  a rule fired, it would keep firing on that same fact over and over again. In the real world, the  stimulus that caused the firing eventually would disappear. For example, a real duck might swim  away or get a job in the movies. However, in the computer world, once data is stored, it stays  there until explicitly removed or the power is turned off.




The following example shows activations and firing of a rule. Notice that the (watch)  commands are used to more carefully show every fact and activation. The arrow going to the  right means an entering fact or activation while an arrow to the left would mean an exiting fact  or activation.



<p class="code-label">Comments in blue/italics have been added for explanation. You will not see these in the actual output:</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule duck
   (animal-is duck)   
=>
    (assert (sound-is quack)))
CLIPS> (watch facts)
CLIPS> (watch activations)
CLIPS> (assert (animal-is duck))
==> f-1 (animal-is duck)
; Activation salience is 0 by default,
; then rule name:pattern entity index
==> Activation 0 duck: f-1
<Fact-1>
; Notice that duplicate fact
; cannot be entered
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (agenda)
0 duck: f-1
For a total of 1 activation.
CLIPS> (run)
==> f-2 (sound-is quack)
; Nothing on agenda after rule fires
; Even though fact matches rule,
; refraction will not allow this
; activation because the rule already
; fired on this fact
CLIPS> (agenda)
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (sound-is quack)
For a total of 2 facts.
CLIPS> (run)
CLIPS>

``` 





You can make the rule fire again if you retract the fact and then assert it as a new fact.


##  2.4. Show Me the Rules

Sometimes you may want to see a rule while you’re in CLIPS. There’s a command called  **ppdefrule** – the pretty print rule – that prints a rule.




<p class="code-label">To see a rule, specify the rule name as an  argument to ppdefrule. For example;</p>
```scheme
CLIPS> (ppdefrule duck)
(defrule MAIN::duck
(animal-is duck)
=>
(assert (sound-is quack)))
CLIPS>

``` 



CLIPS puts different parts of the rule on different lines for the sake of readability. The patterns  before the arrow are still considered the LHS and the actions after the arrow are still considered  the RHS of the rule. The term MAIN refers to the MAIN module that this rule is in by default.  You can define modules to put rules in analogous to the statements that may be put in different  packages, modules, procedures, or functions of other programming languages. The use of  modules make it easier to write expert systems having many rules since these may be grouped  together with their own agendas for each module. For more information, see the CLIPS Reference  Manual.




What if you want to print a rule but can’t remember the name of the rule? No problem. Just  use the rules command in response to a CLIPS prompt and CLIPS will print out the names of  all the rules.



<p class="code-label">For example, enter:</p>
```scheme
CLIPS> (rules)
duck
For a total of 1 defrule.
CLIPS>

``` 


##  2.5. Write to Me




Besides asserting facts in the RHS of rules, you also can print out information using the  printout function. CLIPS also has a carriage return/linefeed keyword called crlf which is very  useful in improving the appearance of output by formatting it on different lines.



<p class="code-label">For a change, the  crlf is not included in parentheses. As an example:</p>
```scheme
CLIPS>
  (defrule duck
    (animal-is duck)
=>
     ;; Be sure to type in the "t"
     (printout t "quack" crlf))
==> Activation 0 duck: f-1
CLIPS> (run)
quack
CLIPS>

``` 



The output is the text within the double quotes. Be sure to type the letter "**t**" following the  printout command. This tells CLIPS to send the output to the **standard output device** of  your computer. Generally, the standard output device is your terminal (hence the letter `t` after printout). However, this may be redefined so that the standard output device is some other device,  such as a modem or disk.




##  2.6. Other Features




The declare salience command provides explicit control over which rules will be put on the  agenda. You must be careful in using this feature too freely lest your program become too  controlled. One way to make a rule fire again is to force the rule to be re-activated by the  refresh rule command.




The load command loads in the rule that you had previously saved to disk in the file  `duck.clp` or whatever name and directory that you had saved it under. You can load a file of  rules made on a text editor into CLIPS using the load command.




A faster way to load files is to first save them in a machine readable binary format with the  save binary command called bsave. The load binary command, bload, can then be used to  read these binary rules into CLIPS memory much faster since the files do not have to be re interpreted by CLIPS.




Two other useful commands allow you to save and load facts using a file. These are save facts and load-facts. The (save-facts) will save all the facts in the fact-list to a file while (load-facts)  will load in the facts from a file into the fact-list.




The batch command allows you to execute commands from a file as if they were typed in at  the top-level. Another useful command provides an interface to your operating system. The  system command allows the execution of operating system commands or executables within  CLIPS. For more information on all these topics, see the CLIPS Reference Manual.


