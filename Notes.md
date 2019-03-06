
**Terms and Keywords to read**

- Free Lunch
- Law of diminishing returns
- V-Table (of functions)
- loopback (JS)
- Dispatch (single, dual, multi dispatch)

---

**Tuning (post mortem) vs Engineering (pre thoughts)**
- Ethical Hacking (Pentesting) vs Threat Modelling
- Performance Tuning vs Performance Engineering

---

**Quality Roadmap**

|No.|Quality|Tactic|
|:--- |:--- |:--- |
|1.| Availability | Re-try, Watchdog |
|2.| Scalability - Volume (I/O, data, logic)| Stateless, Threads, Manage Queue |
|3.| Security | |
|4.| Performance | Chunky network calls, Compression/minify, Concurrency, Cache, Cache, Object Pooling, Lazy Loading |
|5.| Testability | |	
|6.| Maintainability | Extensibility, Readability, Health monitoring, logging |
|7.| Reliability (Trust) | ACID, Audit |
|8.| Robustness	(Rugged) | Input Validation, Handling bad flows first |
|9.| Usability | |
|10.| Interoperability | |

---

**What is Architecture?**

Software architecture is a way of doing software engineering

```
___________				     ___________
| Quality |   collect	 O	choose	    | Tactics   |
| Req.    |  ————————> / | \ —————————-->   | 	        |
————------- 		 |		     —————-------
			/ \    		   forms Architecture
```
Architecture deals with system quality

Anti-architecture pattern
- Alice in wonderland —> nothing matters, no quality requirements, just trying to build whatever is best
- Google/Netflix arch. —> reference architectures, without knowing requirements copying other “good” architectures

---

**What is Design?**

```
_______________				             __________
| Requirements |  understands	  O	creates	    | skeleton |  (may use procedural, oops, functional)
| 	       |  —----———————> / | \ ————————--—>  | for code |
————------------		  |		     —————-----
		                 / \		    forms design
```

Design deals with code quality.
Easily adding functionality without modifying much of existing code.

---

**Creating cleaner code**

Removing flags/enums (technical flags and not domain flags) and hence conditions by replacing them with interfaces

- Technical flags are predominantly == and !=
- Domain flags can be <, >, >=, <=, !=, ==, etc.

1. Remove flags/enums
	- Create interface for each flag
		- Each interface has as many functions as the functions in which it is used
			- Each interface has as many implementations as the number of values possible for the flag

---

**Ways of calling a method**

1. obj

```
do(Object a){
    a.fun()
}
```

2. interface

```
do(Interface i){
    i.fun()
}
```

3. lambda

```
do(func fun){
    fun()
}
```

4. duck typing (javascript, python)

5. reflection

2/4 vs 3 are style choices (If we have functional interfaces only i.e. one function per interface)
2 vs 4 are lang choices

---

**Closure**

Functional way of implementing state (of a function) similar to data members for classes in OOPs

---

**Functional Programming**

1. Higher order functions
1. Closures

---

**Writing good code - Basics of design**

1. **Reduce cyclomatic complexity**
1. **Reduce Coupling**
1. Reduce Size

| Coupling | Method Call | Instantiation | Comments |
| --- |:---:|:---:| --- |
| interface | &#9745; | &#9746; | |
| lambda | &#9745; | &#9746; | |
| duck | &#9745; | &#9746; | |
| lookup | &#9745; | &#9746; | |
| Reflection (last weapon) | &#9745; | &#9746; | |
| Wrapper (last weapon) | &#9745; | &#9746; | |
| --- | --- | --- | |
| DI | &#9746; | &#9745; | (Preferred than Factory) |
| Factory | &#9746; | &#9745; | |

---

**Factory vs DI**

**Factory**

```
IXFactory factory = new IXFactory();
IX obj = factory.get();
obj.f1();
obj.f2();
```

**DI (with factory)**

DI could be used with or without factory.

```
IXFactory factory = new IXFactory();
IX obj = factory.get();
IY obj2 = new Y(obj);
obj2.g1();
obj2.g2();
```

Factory and DI are both used for instantiation.
1. Factory can return instances (based on parameters to factory or based on some config). Client can get the instance into an interface variable and use it without knowing the actual implementation of the interface.
1. DI is a way of creating an instance by injecting another instance into it (can be done in constructor if always required for a valid state or in setters for lazy loading).

---

**Polymorphism**

1. Static or compile time (Over-loading, dynamic languages like ruby, js, python, etc. don't have it) --> works with references
	- Overloading is not good for a family/hierarchy of types as it may need downcasting (anti-abstraction). But it can be used for different data types, which don't fall into hierarchy e.g. int, float, string
1. Dynamic or run-time (Over-riding)
	1. Single Dispatch
	```
			      _____ f1
			     /
		obj.fun() --|------ f2 
			     \_____ f3
	```
	2. Dual Dispatch
	```
			      	       _____ f1
			    	      /
		(obj1, obj2).fun() --|------ f2 
			     	      \_____ f3
	```
	3. Multi Dispatch
	
- Java, python and many other languages don't have dual, multi dispatches. In that case we can use lookups/Maps (but it should be the last weapon).

---

**Trivia**

- _We create classes when there is behavioural change else if there is only attribute change, we create instances._
- _While designing classes, do usage first design i.e. how would a class be used._
- _Static methods lead to high coupling since the class using the method should know about the implementing class. (Anti Abstraction)_
	- _high coupling lead to poor testability since it's harder (without using advanced methods or frameworks such as mockito or proxy classes) to mock methods which are highly coupled_

---

**Reduce Cyclomatic Complexity**
 - Remove Flags

| Tech (== or !=) | Domain |
| --- | --- |
| interface | Specification pattern |
| lambda | Rule Engine |
| duck | |
| delegated interface | |
| objects | |
| lookup | | 
