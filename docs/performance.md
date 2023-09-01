# Performance
When initially learning, and in general when problem solving, performance might not be much of a concern. Modern computers are quite fast enough that typical usage. If importing, cleaning and performing some computation on data takes less than one or a few seconds then, depending on the size of the data and the frequency of analysis, most users are happy to spend the minimal amount of time getting the answers in a reproducible way and then not being concerned with the *how* any longer.

However, if you are expecting to do run your program often, or do bulk processing of large data repeatedly, or deploy your application on hosted servers which charge for CPU compute time explicitly, or just generally want to reduce your computational and carbon footprint, then performance will be important to you.

From using set spellings (idioms) and specific computational techniques to pre-compiling parts of your code and utilising special hardware, Dyalog can help you reduce bottlenecks in your code to deliver performance which can even beat hand-coded C!

## Set Spellings
In natural language, there are sometimes [fixed expressions](https://en.wikipedia.org/wiki/Phraseme) which are known to convey some meaning. In programming languages, *idiomatic expression* means to write something in a way which is particularly natural or optimal in that particular language.

In Dyalog, there is a collection of set spellings which are recognised by the interpreter and executed using special code which uses fewer computations and less memory than would be required if the the expression were executed step-by-step as written. These are known as [idioms](https://docs.dyalog.com/latest/CheatSheet%20-%20Idioms.pdf) in the Dyalog documentation, but they are a special case of other phrases which are also referred to as idioms which are found historically in idiom lists and these days in the [APLCart searchable idiom library](https://aplcart.info).

Some operators also have special cases of operands which, while not formally documented (because they may change in future releases), are mentioned in some blog posts:

- [Towards Improvements to Stencil](https://www.dyalog.com/blog/2020/06/towards-improvements-to-stencil/)
- 

## Workshops
Workshops have been given on performance in Dyalog APL:

- SA2: Performance Tuning at [Dyalog '18](https://www.dyalog.com/user-meetings/dyalog18.htm)
- SA3: Performance Tuning at [Dyalog '17](https://www.dyalog.com/user-meetings/dyalog17.htm)
- TP4: Writing Efficient Code in Dyalog at [Dyalog '15](https://www.dyalog.com/user-meetings/dyalog15.htm)