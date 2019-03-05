
**Terms and Keywords to read**

- Free Lunch (Law of diminishing returns)


**Tuning (post mortem) vs Engineering (pre thoughts)**
*Ethical Hacking (Pentesting) vs Threat Modelling
*Performance Tuning vs Performance Engineering


**Quality Roadmap**
```
	Quality					|				Tactic
1. Availability					|	Re-try, Watchdog
1. Scalability					|	Stateless, Threads, Manage Queue
	Volume (I/O, data, logic)		|	
1. Security					|
1. Performance					|	Chunky network calls, Compression/minify, Concurrency, Cache, Cache,
						|	Object Pooling, Lazy Loading
1. Testability					|	
1. Maintainability				|	Extensibility, Readability, Health monitoring, logging
1. Reliability	(Trust)				|	ACID, Audit
1. Robustness	(Rugged)			|	Input Validation, Handling bad flows first
1. Usability					|
1. Interoperability				|
```


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


**Creating cleaner code**

1. Remove flags --> Create interface for each flag
			|--> create as many implementations for each interface class as we have number of distict
				values for the flag


**Ways of calling a method**

1. obj

do(Object a){
    a.fun()
}

1. interface

do(Interface i){
    i.fun()
}

1. lambda

do(func fun){
    fun()
}

1. duck typing (javascript, python)

1. reflection

2/4 vs 3 are style choices (If we have functional interfaces only i.e. one function per interface)
2 vs 4 are lang choices


**Closure**

Functional way of implementing state (of a function) similar to data members for classes in OOPs


**Functional Programming**

1. Higher order functions
2. Closures
