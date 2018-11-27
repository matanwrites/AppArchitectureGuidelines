Original article was published on medium: https://medium.com/@mathieutan/how-to-keep-calm-and-stay-sane-in-modern-app-development-4bab43dcd4b0

---


# 10 Rules to avoid the Software Bolognese Club
  
> If code is a recipe as Richard Stallman says, we must all have been grand italian chefs.
  
  
### 1. On POs and PMs
* Requirements should be controlled, contained and tamed, not spread over all the app like a disease, if a requirement changes 5 times, only one class should change for this feature and be contained into ChatFeatureMyPOChangedHisMind.java/swift.
* In the end, a requirement is just a bunch of conditions, no matter if it is related to UI, Navigation, Networking etc.. These conditions form an algorithm that can live on their own world, segregated of your app. One way to think about it is "business logic as micro-service", given a query what is the expected output?
* Change is your enemy, distinguish Infrastructure/Skeleton of your system from the Business Logic. The infrastructure is the solid core and business logic are the moving parts that will after the few first months, keep changing again and again.



### 2. Empathy
* Do yourself a favor and write the code for your future self in 3 months or your teammate or your future teammate.
* [Programs must be written for people to read, and only incidentally for machines to execute.](https://www.goodreads.com/quotes/9168-programs-must-be-written-for-people-to-read-and-only)



### 3. APIs over Code
* Create APIs not code, encapsulate, modularize, even better lock write permissions on your class (it's a figure of speech but actually in VisualStudio this something you can actually do).
* If someone changes the class you made, what is the reason? (See Single Responsibility Principle).
* If someone changes your class, modifications should be localized to your class or in the worst case to its neighbors, changes should not happen throughout the system. Otherwise why bother doing OOP in the first place?




### 4. On Swift/ObjC/Java/Kotlin/YouNameIt
* A code review is language agnostic, it is good to use a language to its fullest when it makes implementation easier. But complexity should come from the design not from the implementation. An app is already complexed as it is.
* If you have made a class so cool that it inherits from a super class and made it implements several interface/protocols you probably went wrong somewhere. Because no one will be able to understand your class without digging through 5 different files and keeping a mental model both vertical (inheritance) and horizontal (behaviors through protocol/interfaces).



### 5. On Architecture
* Architecture is a not so grand word which is not about the newest letters in the MV… trends ([or snake trends](https://medium.com/@ankoma22/the-good-the-bad-and-the-ugly-of-viper-architecture-for-ios-apps-7272001b5347))
* It's about the control of the Data Flow, where does the Data Flow comes from and where does it end, does it flow into all direction? [Is it one way, two way, three way?](https://medium.com/@AdamRNeary/unidirectional-data-flow-yes-flux-i-am-not-so-sure-b4acf988196c)
* Looking at your architecture, can we see clearly see where the data flows through? Where are the sources? Where are the consumers? More importantly where is the truth?
* We have so long relied on our fancy compilers for memory management that we forgot the [side effects introduced by sharing our objects all around the code base](http://softwaremaniacs.org/blog/2016/02/11/ownership-borrowing-hard/en/)
* Algorithms is not only about sorting and LeetCode, how complex is the DataFlow algorithm you made? Where is the core and where are the moving parts?



### 6. On Frameworks
* Adding a library/framework should be carefully considered, what are the trade-offs?
* What is the support like? How easy is it to customize it? How easy is it to debug it? Is it just syntactic sugar?
* Will my teammates be able to catch-up, understand, work with it optimally?
* Is this framework a pattern or a helper? Ex: JWT is a helper since it provides a feature, while Rx is a pattern and once used will influence every callbacks and data mutation and flow in your app.



### 7. Being Fashion
* It's good to keep-up with the latests trends but consider how much value does it add over the drawbacks.



### 8. On Legacy Code
* As long as you work on this project, there is no difference between legacy and new code. You own this code it is all yours; Past, Present and Future.
* One way to think about it is: imagine a new teammate comes to your project what is the difference for him between "legacy before you" and "legacy after you"?




### 9. On Tests
* What is computable is testable, something that given an input, produces an output, is by definition testable. Different strategies need to be used depending on the situation though. (UITest, Integration, black box testing, white box testing etc..) .
Testing legacy code does not need a Grand-Sky-Refactor project.

* A strategy for "legacy code" can look like this:
1. Take your beloved Monster-Manager class, start by the hands and the feet, wrap them into a clean API -> you get your testable input and output.
2. Little by little change the arms, the legs, then the core.
3. At each step add a test to see that you did not break step 1.

* Testing is not a so long term investment, as you might think, just consider how many times a PM changes the requirement in a single sprint? Tests also serve as feature documentation.

http://www.growing-object-oriented-software.com provides good strategies on the testing/refactoring process



### 10. On Branching
* Does this fit into this branch? Should I create a separate PR called refactorX?
* If you are creating a new way to serialize or do networking or something big: YES (please talk to your teammates first about the trade-offs and where can this fit in the release).
* If not, you can refactor it, the grand refactor in the sky will never happen so better start somewhere, if you can get a win out of it.



### The End?
In the end we can have rules, guidelines, hell, a new set of letters to name your architecture. Without automation and linters it is like having a government and laws without anyone to enforce the policies.
Developers have bad day and good day review quality will always vary.
Let automation do its job everywhere it can and let human review data flow, api design and modularity instead of language specifics.


### Food for Thought
* OOP, Rust and Ownerships Graphs (https://dpc.pw/the-faster-you-unlearn-oop-the-better-for-you-and-your-software)
* Rust ownership model (http://softwaremaniacs.org/blog/2016/02/11/ownership-borrowing-hard/en/)
* Andy Matuschak on data flow and the "Truth" (https://developer.apple.com/videos/play/wwdc2014/229/)
* API Design (https://mattgemmell.com/api-design/)
* Unidirectional data flow (https://medium.com/@AdamRNeary/unidirectional-data-flow-yes-flux-i-am-not-so-sure-b4acf988196c)
