[[ReadItLater]] [[Article]]

# [Why you should never use an UUID as the primary key in SQL Databases](https://dev.to/frederik_vl/why-you-should-never-use-an-uuid-as-the-primary-key-in-sql-databases-147b?ref=dailydev)

Using a UUID (Universally Unique Identifier) as a primary key in SQL databases has both advantages and disadvantages. While UUIDs offer benefits in certain scenarios, there are reasons why they might not be the best choice for a primary key:

**Indexing and Performance:**  
<mark style="background: #ADCCFFA6;">UUIDs are 128 bits long, compared to 32 bits for a typical integer</mark>. This larger size can <mark style="background: #ADCCFFA6;">result in increased storage requirements and decreased performance,</mark> especially when dealing with large datasets.

Indexes built on UUID columns may not perform as efficiently as those on smaller data types. <mark style="background: #ADCCFFA6;">This is because larger keys can lead to more page reads, impacting query performance.</mark>

**Readability and Debugging:**  
Unlike integers, <mark style="background: #ADCCFFA6;">UUIDs are not human-readable</mark>, which can make debugging and manual inspection of the database more challenging. Integers or other smaller data types may be more convenient for developers and database administrators.

**Clustering:**  
UUIDs are designed to be globally unique, but <mark style="background: #ADCCFFA6;">they are not guaranteed to be sequential</mark>. This lack of sequential ordering<mark style="background: #ADCCFFA6;"> can result in suboptimal disk I/O patterns, </mark>affecting the performance of certain types of queries, especially those involving range-based searches.

**Fragmentation**  
UUIDs are often generated using a combination of timestamp and random values. This randomness <mark style="background: #ADCCFFA6;">can lead to higher levels of index fragmentation, impacting database performance over time.</mark>

**Storage Overhead:**  
Storing UUIDs can lead to<mark style="background: #ADCCFFA6;"> increased storage requirements, both in terms of disk space and memory.</mark> This can be a concern in environments where storage costs are a critical factor.

**Application Complexity:**  
Managing UUIDs, especially their generation and uniqueness across distributed systems, can add complexity to the application logic. This complexity may not be necessary if simpler primary key types suffice for the application's requirements.