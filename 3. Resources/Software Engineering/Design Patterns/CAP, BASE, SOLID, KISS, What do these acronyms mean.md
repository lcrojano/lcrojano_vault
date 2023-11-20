---
url: https://blog.bytebytego.com/subscribe
tags:
  - design
  - architech
  - design-pattern
  - "#diagram"
---
## CAP, BASE, SOLID, KISS, What do these acronyms mean?

The diagram below explains the common acronyms in system designs.


![diagram](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_lossy/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F691f370f-db47-4f18-a9ad-db3b8dacfe8e_1536x1536.gif "diagram")



## CAP  
CAP theorem states that any distributed data store can only provide two of the following three guarantees:  
**1. <mark style="background: #ADCCFFA6;">Consistency</mark>** - Every read receives the most recent write or an error.  
**2. <mark style="background: #ADCCFFA6;">Availability</mark>** - Every request receives a response.  
**3. <mark style="background: #ADCCFFA6;">Partition tolerance</mark>** - The system continues to operate in network faults.  
      
However, <mark style="background: #ADCCFFA6;">this theorem was criticized for being too narrow for distributed systems</mark>, and we shouldn’t use it to categorize the databases. Network faults are guaranteed to happen in distributed systems, and we must deal with this in any distributed systems.  
  
You can read more on this in “Please stop calling databases CP or AP” by Martin Kleppmann.

## BASE  
The ACID (<mark style="background: #ADCCFFA6;">Atomicity-Consistency-Isolation-Durability</mark>) model used in relational databases is too strict for NoSQL databases. The BASE principle offers more flexibility, choosing availability over consistency. It states that the states will eventually be consistent.
    
## - SOLID  
SOLID principle is quite famous in OOP. There are 5 components to it.  
  
1. **SRP (Single Responsibility Principle)**  Each unit of code should have one responsibility.  
2. **OCP (Open Close Principle)**  Units of code should be open for extension but closed for modification.  
3. **LSP (Liskov Substitution Principle)**  A subclass should be able to be substituted by its base class.  
4. **ISP (Interface Segregation Principle)**  Expose multiple interfaces with specific responsibilities.  
5. **DIP (Dependency Inversion Principle**)  Use abstractions to decouple dependencies in the system.
## - KISS  
"Keep it simple, stupid!" is a design principle first noted by the U.S. Navy in 1960. It states that most systems work best if they are kept simple.

