---
layout:     post
title:      "Redis in Action: A Review"
date:       2020-09-22 21:48:00 -0500
categories: Redis caching review performance deep-learning learning-path
---

I took a little break from MySQL in my [deep learning] paths in favor of 
looking a bit more broadly.  In particular, I realized that I barely knew
what Redis what capable of.  I knew it was effective as a key value store
and had some data structures like lists but I had never really touched anything
outside of really basic caching.  I picked up [Redis in Action] by Josiah L. Carlson
(there's also a  [free ebook version]) because it looked like it would 
give me a good introduction to the possibilities.

While I'm by no means an expert on Redis at this point.  I definitely feel a lot
more comfortable with the options that Redis makes available.  Carlson does
an excellent job of giving a basic introduction to Redis and it's capabilities.
The book gives an introduction to the basic Redis philosophy, Redis datastructures,
and general Redis management.

In addition to being an introduction, some parts of the book end up serving
as a cookbook of sorts.  Carlson works through building out different applications
using Redis as the database of choice.  Sometimes, these applications can get a bit
in the weeds for my taste.  There's a lot of discussion about various python features 
(I'm a python dev so that may weigh into it).  This also doesn't seem like the right
format.  For some of those sections, it'd be really cool to do an interactive lesson
on building it out.  Reading it from a book didn't seem to help make it stick.

That being said, the book is a fairly quick and easy read.  While I'm not an expert
on Redis now, I definitely know some of the options.  This means that when something
comes up I know that Redis may be an effective option even if I don't know
off the top of my head how to implement it.

[Redis in Action]: https://www.amazon.com/Redis-Action-Josiah-L-Carlson/dp/1617290858
[free ebook version]: https://redislabs.com/ebook/part-2-core-concepts/
[deep learning]: {% post_url 2020-08-22-mysql-internals-review %}