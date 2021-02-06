Naked Objects–Really Naked?

![naked-objects-icon](assets\naked-objects-icon.jpg)

Naked Objects is an eye catching name. No wonder that it has been demonstrated at the OOPSLA 2001 conference under the banner of Intriguing Technologies.

Copyright (c) 2002 nakedobjects.org

## The Naked Objects Pattern

- Design behaviourally complete domain objects i.e.- Encapsulate all the behaviour/functionality within the domain objects.
- Single point definition: All the representations of a domain object such as user-interface, database-mapping, should be derived automatically from the domain object class itself.
- Object-oriented user-interface (OOUI): By exposing behaviourally-complete objects, users can view and interact with underlying domain

---



[![NakedPOJOScreen](https://fastandsteady.files.wordpress.com/2012/05/nakedpojoscreen.png?w=240&h=161)](https://fastandsteady.files.wordpress.com/2012/05/nakedpojoscreen.png)



### Benefits

The benefits that this approach offers look very appealing as mentioned by Richard Pawson in his thesis:

- A homogeneous business object model has to be developed in-house and not bought piecemeal from different suppliers.
- The developer should focus only on writing Model objects and the business logic instead of scattering it Model, View and Controller objects.
- The system requirements should be captured by identifying objects and their responsibilities directly rather than from a set of use-cases and then using these to identify the shared objects and their responsibilities.
- The metaphor if envisaging the role of business systems as a deterministic process, transforming input information into output information through a sequence of value-added steps needs to be questioned.
- Instead of focusing on optimization of processes (a finite set of scripted tasks), focus on user interaction that gives user more control in the order of execution thereby maximizing the overall effectiveness.
- Design systems that allow users to become more expert as they learn, rather than constraining everyone to the lowest common denominator.

### Real-life experience

So when faced with the task of designing an Admin interface for a banking application, the Naked Objects pattern looked to be an obvious choice. The screenshots in the documentation (one is pasted above) also looked very similar to the application we intended to design. We included a business analyst in the team for creating and modifying the business objects on the fly as they were being proto-typed. The analyst put down his requirements as a set of user stories supplemented by wire frames and sketches. We also decided to use an annotation based persistence and user interface model using the custom in-house frameworks. Our findings based on this experience were:

- This pattern is very well suited for sovereign applications like the one we were working on i.e. used by power users who are comfortable with the functionality and need to control the way operations are invoked.
- The pattern is obviously very well suited for DDD (Domain Driven design) and MDA (Model driven analysis). It also supports BDD (Behaviour driven design) very well since the business analyst can directly define and view objects. An SOA model can be derived by exposing operations as RESTful services
- The Model objects tend to become bloated as one keeps on adding business logic, scaffolding code, persistence and UI annotations. Hence the Model needs to be defined at the proper level of granularity to start with. Objects need to be properly decomposed using containment, aggregation patterns to avoid creating huge monolith blocks of code. The Model starts looking like a well of big fat Naked objects, not a very pretty sight!
- The OOUI model of one UI page per object works well for an application like ours. However it may not work well when the user has to interact with various Model objects to complete the transaction. Many web applications fall in the second category.
  Moreover, a UI page per object becomes unmanageable when the no. of objects keeps on increasing.
- Selecting an action first and then the object later looks a more natural way of transacting. For example, for doing a Funds Transfer one would select the Transfer and then select the From/To accounts later. It may be more easy for power users to make this switch in the way they interact with the application.
- The business analyst need not be on his toes all the time since the Model objects can be changed at any stage.
- The pattern in it’s pure form, may need to be tweaked. This includes modelling Controllers as objects (although Controllers are abhorred), flows as objects (Transactions for example), side-stepping the one UI page per object as required… This should b e OK as long as the original intent of the pattern is preserved.
  Even Pawson indicates that it is OK to tweak the model as mentioned by the following. example

> The solution is to implement Transfer as a class of object in its own right. Its attributes are the two accounts, the amount to transfer, and the date/time. The methods on the two account objects then become, effectively, ‘Create New Transfer’, which creates a new instance of Transfer, ready populated with the ‘from’ account. Alternatively, the user could shortcut this by dragging one account onto the other, which returns a new Transfer object with both the ‘from’ and ‘to’ fields populated. After specifying the amount to transfer, the user then invokes the ‘Execute’ or ‘Make it so’ method on the Transfer object.
> Critics will say that all we have done is created a Transfer process, or even a Transfer dialog box, and called it an object; but they are missing an important point. Because each transfer is now modelled as an instantiated object, it can be directly referred to in future, for purposes of audit, or even reversal. In fact, for our banking application, Withdrawals and Deposits should similarly be treated as noun-objects not as verbs. (It would be legitimate to refer to all of these examples as ‘form’ objects, where the form provides a permanent record of that instance of a process). If you treat each of those concepts as merely a verb or process then you cannot refer directly to, say, a particular withdrawal, but must reconstruct it, in effect, from the audit trail.

So we can have a country with naked objects as first class citizens and the remaining tweaked constructs as the rest.

- The pattern can also be a useful tool when rapid prototyping is required i.e. business model is not clear. The penalty may be the efforts required in retrofitting a custom UI model to an existing Naked Objects model.
  As Pawson says, a conventional scripted user interface that invokes the capabilities of the same objects (on the server) for specific class of users, or to cope with the limitations of a browser interface can always be developed after refining the initial model.
- From a modelling perspective, it is possible that use-cases become top layer software constructs resulting in a weakly designed domain layer. This approach focuses on creating a strong Domain layer – a substantial advantage since it is much more costly to change the Domain model later.
- Managers may love this pattern since the ROI is tied to business features and the efforts spent on supplementary activities are less. The developers can also focus on developing the actual business features rather than spending time in beautifying UI. Any developer who has spent time in using frameworks like Struts can testify to this.

## Interesting stuff to look at:

- [Thesis on Naked Objects](http://downloads.nakedobjects.net/resources/Pawson thesis.pdf)by Richard Pawson: This is where it started.
- [The Emperor Has No Clothes: Naked Objects Meet the Interface](http://www.foruse.com/articles/nakedobjects.pdf): A beautiful article by Larry Constantine. May be a better place to start if one feels being confused by the verbiage in the thesis.
- [Apache ISIS](http://incubator.apache.org/isis/index.html): Java based Naked object model framework with options to deploy with a custom UI or persistence framework.
- [Naked Objects](http://nakedobjects.codeplex.com/): .Net based Naked object model framework
- JMatter: Naked Objects model framework using Swing, Hibernate, and deployed with Java WebStart.
- [Emperor’s New Clothes](https://www.se.auckland.ac.nz/p4projects/posters-2004/pictures/proj_091.pdf): Deals with generation of Naked Objects adapters for Java system integration.
- [Domain-Driven Design Using Naked Objects by Dan Haywood](http://www.amazon.com/Domain-Driven-Design-Objects-Pragmatic-Programmers/dp/1934356441): A good book to understand the pattern in detail. Although Naked Objects is covered as a n implementation framework, [it](http://www.webmd.com/fitness-exercise/guide/20061101/never-too-late-exercise) is good to understand the concepts. Particularly interesting is how this pattern ties into the [Hexagonal architecture](http://alistair.cockburn.us/Hexagonal+architecture) put forward by Alistair Cockburn.

## The Takeaway

To make a long story short, you can use the Naked Objects pattern for rapid prototyping for the core domain even though it may not be your final model.

Tags: design
