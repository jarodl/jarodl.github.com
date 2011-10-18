---

title: Prettier CSS with Flair
layout: default

---

I'm not a big fan of writing CSS. I love writing Ruby and Python, thus, Flair was born. Check out the source and more information on [Github](https://github.com/jarodl/flair).

The very basic example of what the syntax looks like works, but the more complicated examples that will make the "language" special are currently being worked on. Right now Flair has the ability to compile the following:

    id Container:
        width = "680px"
        margin = "2em auto"

    class Column:
        float = "left"
        width = "60%"
        padding = "2em 0"

into this:

    #container {
      width: 680px;
      margin: 2em auto;
    }

    .column {
      float: left;
      width: 60%;
      padding: 2em 0;
    }

As you can see nothing special is happening right now but check out the [README](https://github.com/jarodl/flair/blob/master/README.md) on Github to see where I would like the project to go. While you are there go ahead and fork it!

If you would like to learn more about doing something similar, check out Marc-Andre Cournoyer's book [Create Your Own Freaking Awesome Programming Language](http://createyourproglang.com/). The book covers the implementation of a programming language similar to Python and Ruby.
