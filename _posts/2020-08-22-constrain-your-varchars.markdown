---
layout:     post
title:      "Constrain Your VARCHARs"
date:       2020-08-22 16:31:00 -0500
categories: MySQL performance deep-learning learning-path high-performance-mysql
---

As part of my commitment to [deep learning], I've been working through the book
[High Performance MySQL].  While they were discussing data types and the specifics,
they had an aside, on why you should limit the size of `VARCHAR` even though the size
on disk is the same regardless.

> Storing the value 'hello' requires the same amount of space in a VARCHAR(5) and a VARCHAR(200).
> Is there any advantage to using the shorter column?
>
> As it turns out, there is a big advantage.  The larger column can use much more memory
> because MySQL often allocates fixed-size chunks of memory to hold the values internally.
> This is especially bad for sorting or operations that use in-memory temporary tables.
> The same thing happens with filesorts that use on-disk temporary tables.
>
> The best strategy is to allocate only as much space as you really need.

This seems to be a classic trap of having a basic understanding of MySQL because
I know that at one point I believed that you should pretty much always just use `VARCHAR(255)`.
Finally, I questioned my reasoning on this (why even give the option of setting the max length
if it didn't really matter) and decided to look more deeply into it.  Ever since then,
I've been trying to convince people to constrain it to a reasonable size and every time I'm 
met with, "but it's a VARCHAR so it's the same size on disk".  Obviously, you should have some
breathing room, just not too much.

The aside above from [High Performance MySQL], should be enough to convince you to set a reasonable
max length.  That being said, here are a few more reasons to constrain it.

Number 1: Increasing a `VARCHAR` size is cheaper than reducing it because it can be done [online and in place]

This makes a lot of sense when you stop and think about it.  If we increase the `VARCHAR` size, we usually
only need to change the metadata to let MySQL know that any new rows/updates can have a larger size.
Every row in the table already is fine.  However, if we're decreasing the row size, then at the very
minimum we would need to investigate every row to make sure it conforms.  In reality, MySQL treats it as
changing the column type.

Note there is one exception where increasing the VARCHAR size may not be online and that's when you're
increasing the column size past 255 bytes.  That's because MySQL uses two bytes for the length of the
`VARCHAR` when it's larger than 255 bytes but only one byte when it's less than that.    Therefore, it needs
to update all of the rows and add another byte for the length.  You'll want to look at your character set
to determine when this will impact you.

Number 2: You should know how big your data will be

It's generally not hard to have a grip on approximately how big a column will need to be. You don't
need to be exact, and it's fine to give yourself a bit of a buffer.  But don't go overboard.  Even if it's
something that is user supplied, there's generally a sane limit to the size.  I like to use a [Lorem Ipsum generator]
to figure out how big a certain number of characters is.  Alternatively, I'll use the tweet comparison.
When you see a `VARCHAR(255)` I like to ask whether that column really needs a full length tweet (280 characters,
though keep in mind that the [mode tweet length is 33 characters]).  Being stricter about VARCHAR lengths may even
prevent subtle data corruption in the long run.  If you normally have a 5 characters stored and all of a sudden you
get a 200 character word stored, I'm willing to bet that it's probably some programming mistake.  With a `VARCHAR(255)`
you have subtle data corruption.  But with `VARCHAR(10)` you have a much more noisy (and easy to debug) error.
Of course that's assuming that you have strict SQL mode enabled (which you totally should, but that's a story
for another day).

In the end, I'm not saying that every `VARCHAR(255)` is bad.  Rather, I'm advocating that you take a few minutes (it rarely takes more than that)
to think about how long it should be and try to be a little more thoughtful rather than just defaulting to some value.


[deep learning]: {% post_url 2020-08-22-mysql-internals-review %}
[High Performance MySQL]: https://www.amazon.com/High-Performance-MySQL-Optimization-Replication/dp/1449314287/ref=sr_1_3?dchild=1&keywords=mysql+internals&qid=1598125485&sr=8-3
[online and in place]: https://dev.mysql.com/doc/refman/5.7/en/innodb-online-ddl-operations.html#online-ddl-column-operations
[Lorem Ipsum generator]: https://loremipsum.io/generator/
[mode tweet length is 33 characters]: https://techcrunch.com/2018/10/30/twitters-doubling-of-character-count-from-140-to-280-had-little-impact-on-length-of-tweets/
