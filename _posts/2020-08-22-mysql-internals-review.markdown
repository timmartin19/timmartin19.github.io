---
layout:     post
title:      "MySQL Internals: A Review"
date:       2020-08-22 16:00:00 -0500
categories: MySQL performance review deep-learning learning-path
---

Lately, I've felt like I don't understand the underlying tools I use on a day-to-day
basis to the degree that I would like.  MySQL is an excellent example.  
I'm comfortable with the SQL and I can generally get the performance I
want out of a query.  I can diagnose query problems and determine when to index
and when to restructure a query.

That being said, there's still something I'm missing.  I keep feeling like
there's more and more about MySQL that I just don't know (hopefully, because I'm
finally breaking past the [Advanced Beginner] stage). I've decided to take things
into my own hands and try to find out what I don't know.  In particular, I want 
to track down what I don't know that I don't know.  The unknown unknowns.

As a starting point, I ordered three books on MySQL: [MySQL Internals], [High Performance MySQL],
and [MySQL High Availability]. My hope is that these three books will at least
give me a starting point to dive deeper into MySQL.  To help me figure out what
I should look more closely at.

In particular, I was excited for [MySQL Internals] by Sasha Pachev because I figured 
that if you want to have a truly deep understanding of tool you have to be able to
understand the underlying code itself. I didn't expect this book to give me a total
understanding of the MySQL codebase.  Rather, I was hoping that it gave me a place to
jump into the codebase.  A high-level understanding of how things are structured.

Unfortunately, I think that this book kind of misses the mark.  I knew going into it
that the book was going to be out of date (it was written in 2007).  But like I said,
I was hoping for a starting point so that might not necessarily be a huge issue.  The
way the book is structured it is a big issue.  There's some discussion of the architecture
but it felt like the majority of the book was focused on the actual internal APIs
and interfaces.  Literally spelling out the interfaces.  Not only does this not
age well, but quite frankly, the comments in the MySQL codebase tended to give a better
explanation anyhow.

The book is broken up into sections on the various "modules" of MySQL.  There's relatively
little discussion of how these modules work together and generally it seems like Pachev
dives into a random part of the code in depth without explaining why it's important.  Probably
the most helpful part is that he at least points to the primary files where certain modules
are handled. This does make it easier to find out where to look if you want to learn more about
something specific.  But if you're interested in the architecture this isn't even the best source
for that ([High Performance MySQL] definitely gives a more succinct and yet more in-depth discussion
of the architecture).

Finally, Pachev waxes a bit poetic about Monti and the MySQL development in general.  Sometimes,
it feels more like the book is an ode to how smart the MySQL developers were.  He makes
it sound like MySQL is the perfect code base and could never possibly have been improved.
It's honestly really off-putting at times.

Overall, I would not recommend taking the time to read this book. The density of valuable information
is low.  That being said, all is not lost.  I did find the [MySQL Internals Manual] which has been
much more helpful thus far.  It's the official internal documentation from MySQL.  Plus it has the
advantage of being up to date and free!  If you prefer a hard-bound version, [High Performance MySQL]
does provide a decent understanding of the architecture of MySQL, even if that isn't the intention
of the book.

[Advanced Beginner]: https://daedtech.com/how-developers-stop-learning-rise-of-the-expert-beginner/
[MySQL Internals]: https://www.amazon.com/Understanding-MySQL-Internals-Discovering-Improving/dp/0596009577/ref=sr_1_3?dchild=1&keywords=mysql+internals&qid=1598125461&sr=8-3
[High Performance MySQL]: https://www.amazon.com/High-Performance-MySQL-Optimization-Replication/dp/1449314287/ref=sr_1_3?dchild=1&keywords=mysql+internals&qid=1598125485&sr=8-3
[MySQL High Availability]: https://www.amazon.com/MySQL-High-Availability-Building-Centers/dp/1449339581/ref=pd_bxgy_img_3/130-5516818-3318163?_encoding=UTF8&pd_rd_i=1449339581&pd_rd_r=9af16a0f-7906-4ad5-912e-bd6f3773e098&pd_rd_w=BfRED&pd_rd_wg=gefUY&pf_rd_p=ce6c479b-ef53-49a6-845b-bbbf35c28dd3&pf_rd_r=FVT1JC5K4JMYH0YFKYFM&psc=1&refRID=FVT1JC5K4JMYH0YFKYFM
[MySQL Internals Manual]: https://dev.mysql.com/doc/internals/en/