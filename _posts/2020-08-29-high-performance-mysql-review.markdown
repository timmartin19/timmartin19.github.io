---
layout:     post
title:      "High Performance MySQL: A Review"
date:       2020-08-29 18:19:00 -0500
categories: MySQL performance deep-learning learning-path
---

As part of my attempt at [learning MySQL more deeply], I picked up the book
[High Performance MySQL] by Baron Schwartz, Peter Zaitsev, and Vadim Tkachenko.
In opposition to my review on [MySQL Internals], this book was quite excellent.
There's was lots of information presented in a readable, yet information dense way.
It's definitely a book worth studying more than read.  But trust me it's worth it.
I wish I had read this book earlier in my career.  It would have made me embrace
the database a bit more and try solving problems there first.

My only complaint with the book is that they tended to dive into asides on Percona Server
a bit too frequently for my taste.  Given that the writers all work for/founded Percona
this makes sense.  That being said, these side-bars were definitely brief and not
intended to serve as an advertisement for Percona Server.  In fact, they explicitly
suggest that you stick with Oracle's distribution of MySQL unless there is something
specific Percona Server does that you know will help.  This lack of favoritism was refreshing.

I think there are a few sections that application developers
should focus in on.  Some of the chapters are a bit less relevant to non-DBAs (or
people who are running heavily managed instances of MySQL via tools like Aurora).
I'm being broad with the term application developer to refer to anyone who has to write
performant queries against a database.

Chapter 1 will be helpful for everyone.  If you've been working with MySQL for a bit,
you probably already know most of it, but it's a quick and easy read and there may be something
critical that you're missing.

Chapters 2 and 3 are looking at server wide benchmarking and profiling.  This is probably not something, that
an application developer will need to be doing too frequently (ever?).  In my experience,
most of the time, I'm diving into specific queries that are taking too long.  There are some
good tidbits about how to think about performance and it's an interesting read but probably not critical.

Chapters 4, 5, and 6 are where the meat is for application developers.  These cover designing
your schema, indexing, and optimizing your queries for performance.  When I said that I wished
I had read this book earlier in my career, these were the chapters I was talking about.
If you can really understand these 3 chapters as an application developer, you will probably
be considered a "SQL expert" at your job and your DBAs might not hate you.

Chapter 7 on Advanced MySQL Features is definitely not critical for day to day usage.  That being said, if you want
to sound like you know what you're talking about you should probably know about these features.
And more importantly, the tradeoffs of using them

Chapter 8 on configuration is not necessary for application developers, but I'd highly recommend it.
I felt like this chapter was super helpful to get a deeper understanding of the MySQL internals.
There's a fairly strong discussion of the various configuration parameters and what they really do
from a literal and practical standpoint.

Chapter 9 discusses hardware and operating system optimization.  I currently use Aurora and have
pretty much always used some sort of cloud provider so I was expecting this to be the least valuable
chapter for me.  I was actually pretty wrong.  I think this gave me a real appreciation for the balance
between the hardware and software with databases in general.  I think I may have actually learned more
from this chapter than any other chapter.  That being said, a lot of it was not directly relevant
information but was helpful none the less.

Chapter 10 on replication is one of the chapters I would skip if I was short on time.  Unless of
course, you're trying to use replication to boost performance.  In which case, please read this
chapter so that you don't dig yourself in a whole.

Chapter 11 on scaling MySQL is worth reading as an application developer.  They effectively argue a cautious
approach.  They discuss the different strategies but with a heavy dose of reality (sharding is hard).
There are a couple jobs I've worked where if they had read this chapter, we wouldn't have been in 
such a whole.

Chapter 12, 15 and 16 are pretty DBA focused.  They can be interesting but may not be relevant.

Chapter 13 discusses "MySQL in the Cloud"  I found this was the only part of the book that didn't
age well.  It was a bit out of date and there wasn't a ton of great information.

Chapter 14 on application level optimization felt like they kind of dropped the ball.  A lot
of "database" problems are application problems and they hinted at this but I didn't feel like they
really addressed it well.

Finally the appendices were interesting but much more worthwhile as a reference guide than something
to read through.


[deep learning]: {% post_url 2020-08-22-mysql-internals-review %}
[High Performance MySQL]: https://www.amazon.com/High-Performance-MySQL-Optimization-Replication/dp/1449314287/ref=sr_1_3?dchild=1&keywords=mysql+internals&qid=1598125485&sr=8-3
[MySQL Internals]: {% post_url 2020-08-22-mysql-internals-review %}
