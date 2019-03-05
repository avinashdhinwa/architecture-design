```
Terms and Keywords to read

Free Lunch (Law of diminishing returns)
```

```
Tuning (post mortem) vs Engineering (pre thoughts)
Ethical Hacking (Pentesting) vs Threat Modelling
Performance Tuning vs Performance Engineering
```

```
Quality Roadmap

	Quality					|				Tactic
1. Availability					|	Re-try, Watchdog
2. Scalability					|	Stateless, Threads, Manage Queue
	Volume (I/O, data, logic)		|	
3. Security					|
4. Performance					|	Chunky network calls, Compression/minify, Concurrency, Cache, Cache, Object Pooling, Lazy Loading
5. Testability					|	
6. Maintainability				|	Extensibility, Readability, Health monitoring, logging
7. Reliability	(Trust)				|	ACID, Audit
8. Robustness	(Rugged)			|	Input Validation, Handling bad flows first
9. Usability					|
10. Interoperability				|
```

```
What is Architecture?
Software architecture is a way of doing software engineering

___________				     ___________
| Quality |   collect	 O	choose	    | Tactics   |
| Req.    |  ————————> / | \ —————————-->   | 	        |
————------- 		 |		     —————-------
			/ \    		   forms Architecture
Architecture deals with system quality

Anti-architecture pattern
- Alice in wonderland —> nothing matters, no quality requirements, just trying to build whatever is best
- Google/Netflix arch. —> reference architectures, without knowing requirements copying other “good” architectures
```

```
What is Design?

_______________				             __________
| Requirements |  understands	  O	creates	    | skeleton |  (may use procedural, oops, functional)
| 	       |  —----———————> / | \ ————————--—>  | for code |
————------------		  |		     —————-----
		                 / \		    forms design

Design deals with code quality.
Easily adding functionality without modifying much of existing code.
```
