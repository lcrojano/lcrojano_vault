[[ReadItLater]] [[Article]]

# [How Instagram scaled to 14 million users with only 3 engineers](https://engineercodex.substack.com/p/how-instagram-scaled-to-14-million)

Instagram scaled from **0 to 14 million users in just over a year**, from October 2010 to December 2011. They did this with only **3 engineers.**

They did this by following 3 key principles and having a reliable tech stack.

-   Keep things very simple.
    
-   Don’t re-invent the wheel.
    
-   Use proven, solid technologies when possible.
    

Early Instagram’s infrastructure ran on AWS, using EC2 with Ubuntu Linux. For reference, EC2 is Amazon’s service that allows developers to rent virtual computers.

To make things easy, and since I like thinking about the user from an engineer’s perspective, **let’s go through the life of a user session.** (Marked with `Session:`*)*

`Session: A user opens the Instagram app.`

Instagram initially launched as an iOS app in 2010. Since Swift was released in 2014, we can assume that Instagram was written using **Objective-C and a combination of other things like UIKit.**

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb1f72ce0-1963-4176-a493-517a1788a277_374x395.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb1f72ce0-1963-4176-a493-517a1788a277_374x395.png)

`Session: After opening the app, a request to grab the main feed photos is sent to the backend, where it hits Instagram’s load balancer.`

Instagram used **Amazon’s Elastic Load Balancer.** They had 3 NGINX instances that were swapped in and out depending on if they were healthy.

Each request hit the load balancer first before being routed to the actual application server.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc2e2b88d-751d-4c2c-b87e-95cd90aef20e_642x395.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc2e2b88d-751d-4c2c-b87e-95cd90aef20e_642x395.png)

`Session: The load balancer sends the request to the application server, which holds the logic to process the request correctly.`

Instagram’s application server used **Django** and it was written in Python, with **Gunicorn** as their WSGI server. 

As a refresher, a WSGI (Web Server Gateway Interface) forwards requests from a web server to a web application.

Instagram use **Fabric** to run commands in parallel on many instances at once. This allows to deploy code in just seconds.

These lived on over 25 Amazon High-CPU Extra-Large machines. Since the server itself is stateless, when they needed to handle more requests, they could add more machines.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd644ba96-4f13-4fe2-8e9f-e01cdec85171_1005x395.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd644ba96-4f13-4fe2-8e9f-e01cdec85171_1005x395.png)

`Session: The application server sees that the request needs data for the main feed. For this, let’s say it needs:`

1.  `latest relevant photo IDs`
    
2.  `the actual photos that match those photo IDs`
    
3.  `user data for those photos.`
    

`Session: The application server grabs the latest relevant photo IDs from Postgres.`

The application server would pull data from **PostgreSQL**, which stored most of Instagram’s data, such as users and photo metadata.

The connections between Postgres and Django were pooled using [Pgbouncer](https://github.com/pgbouncer/pgbouncer).

**Instagram sharded their data** because of the volume they were receiving ([over 25 photos and 90 likes a second](https://instagram-engineering.com/sharding-ids-at-instagram-1cf5a71e5a5c)). They used code to map several thousand ‘logical’ shards to a few physical shards.

**An interesting challenge that Instagram faced and solved is generating IDs that could be sorted by time.** Their resulting sortable-by-time IDs looked like this:

-   41 bits for time in milliseconds (gives us 41 years of IDs with a custom epoch)
    
-   13 bits that represent the logical shard ID
    
-   10 bits that represent an auto-incrementing sequence, modulus 1024. This means we can generate 1024 IDs, per shard, per millisecond
    

(You can read more [here](https://instagram-engineering.com/sharding-ids-at-instagram-1cf5a71e5a5c).)

`Thanks to the sortable-by-time IDs in Postgres, the application server has successfully received the latest relevant photo IDs.`

`Session: The application server then gets the actual photos that match those photo IDs with fast CDN links so that they load fast for the user.`

Several terabytes of photos were stored in Amazon **S3**. These photos were served to users quickly using Amazon **CloudFront**.

`Session: To get the user data from Postgres, the application server (Django) matches photo IDs to user IDs using Redis.`

Instagram used **[Redis](https://instagram-engineering.com/storing-hundreds-of-millions-of-simple-key-value-pairs-in-redis-1091ae80f74c)** to store a mapping of about 300 million photos to the user ID that created them, in order to know which shard to query when getting photos for the main feed, activity feed, etc. All of Redis was stored in-memory to decrease latency and it was sharded across multiple machines.

**With some clever hashing, Instagram was able to store 300 million key mappings in less than 5 GB.**

This photoID to user ID key-value mapping was needed in order to know which Postgres shard to query.

`Session: Thanks to efficient caching using Memcached, getting user data from Postgres was fast since the response was recently cached.`

For general caching, Instagram used **Memcached**. They had 6 Memcached instances at the time. Memcached is relatively simple to layer over Django.

Interesting fact: 2 years later, in 2013, Facebook released a landmark paper on how they scaled Memcached to help them handle *[billions](https://research.facebook.com/publications/scaling-memcache-at-facebook/)* [](https://research.facebook.com/publications/scaling-memcache-at-facebook/)*[of requests per second.](https://research.facebook.com/publications/scaling-memcache-at-facebook/)*

`Session: The user now sees the home feed, populated with the latest pictures from people he is following.`

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F96c6476f-b900-4591-a672-295048bda0a4_1466x597.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F96c6476f-b900-4591-a672-295048bda0a4_1466x597.png)

Both Postgres and Redis ran in a **master-replica setup** and used Amazon EBS (Elastic Block Store) snapshotting to take frequent backups of the systems. 

`Session: Now, let’s say the user closes the app, but then gets a push notification that a friend posted a photo.`

**This push notification was sent using [pyapns](https://github.com/samuraisam/pyapns)**, along with the billion+ other push notifications Instagram had sent out already. Pyapns is an open-source, universal Apple Push Notification Service (APNS) provider.

`Session: The user really liked this photo! So he decided to share it on Twitter.`

On the backend, the task is pushed into **[Gearman](https://gearman.org/), a task queue** which farmed out work to better-suited machines. Instagram had ~200 Python workers consuming the Gearman task queue.

Gearman was used for multiple asynchronous tasks, like pushing out activities (like a new photo posted) to all of a user’s followers (this is called fanout). 

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb586cf1d-c74f-4166-abe3-c143c54c4151_682x678.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb586cf1d-c74f-4166-abe3-c143c54c4151_682x678.png)

`Session: Uh oh! The Instagram app crashed because something erred on the server and sent an erroneous response. The three Instagram engineers get alerted instantly.`

Instagram used **Sentry**, an open-source Django app, to monitor Python errors in real-time.

**Munin** was used to graph system-wide metrics and alert anomalies. Instagram had a bunch of custom Munin plugins to track application-level metrics, like photos posted per second.

**Pingdom** was used for external service monitoring and **PagerDuty** was used for handling incidents and notifications.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fa279781f-8c76-4e67-8a63-6b9930d1a48c_1984x937.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fa279781f-8c76-4e67-8a63-6b9930d1a48c_1984x937.png)

Sources:

-   [What Powers Instagram: Hundreds of Instances, Dozens of Technologies](https://instagram-engineering.com/what-powers-instagram-hundreds-of-instances-dozens-of-technologies-adf2e22da2ad)
    
-   [Storing hundreds of millions of simple key-value pairs in Redis](https://instagram-engineering.com/storing-hundreds-of-millions-of-simple-key-value-pairs-in-redis-1091ae80f74c)
    
-   [Sharding IDs at Instagram](https://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram)