
**Terms and Keywords to read**

- Free Lunch (Law of diminishing returns)

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

**Writing good code**

1. Reduce cyclomatic complexity
2. Reduce Size
3. Reduce Coupling

| Coupling | Method Call | Instantiation | Comments |
| --- |:---:|:---:| --- |
| interface | &#9745; | &#9746; | |
| lambda | &#9745; | &#9746; | |
| duck | &#9745; | &#9746; | |
| --- | --- | --- | |
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
