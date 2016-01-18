# 10-steps-clojure

A Clojure library designed to... teach beginners how to get started with Clojure! 

## No Fat

I want to get you up and running in a fun environment as quickly as possible.

I find that the biggest hurdle in learning something new is getting stuck before you can have any fun!

#Get Excited!

Why learn Clojure?

  * It's a LISP! Be the diamond in the rough of programmers who understand how these work.
  * Smart people respect LISPs! [ this guy! ](http://www.paulgraham.com/avg.html) [ and this one! ](http://blog.bigml.com/2013/06/21/clojure-based-machine-learning/)
  * Learn about functional programming concepts like `lazy-sequences` and `comp` (this is super cool if you're coming from ObjOriented like I did!)
  * Learn about threading and asynchronous functions.
  * There are jobs in Clojure!
  * The ecosystem is filled with **really great tools**, and **very helpful people**. I am seriously amazed.


#####Let's get started!

#Web Resources

If you don't care about running clojure locally (yet), there is a REPL (place to type in code and see what happens) [here.](http://www.tryclj.com/)

An awesome list of exercises is found at [4Clojure.](http://www.4clojure.com/problems)

I also found that doing [ Project Euler problems ](https://projecteuler.net/archives) was very beneficial to getting comfortable in Clojure.

Skip down to [Tips](#tips) if you don't care about a local environment.

#Setting up your local Environment.

You need a few things to started writing Clojure on your computer.

  1. Java
  2. Leiningen
  3. An editor with a built-in REPL (not necessary, but developing way better)

###Java

Clojure compiles into Java and runs on the JVM. So we need Java.

Run `java -version` in your terminal. If you have version `1.6` or later, youre fine! If not, go [here](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and get the newest version.

###Leiningen

Leiningen gives us many important things including...

  * A way to manage dependencies in Clojure
  * A REPL we can use to try out some code!

Now, install [Leiningen](http://leiningen.org/). If you're a Mac user with homebrew, `brew install leiningen` should do the trick.

If you type `lein new SomeRandomName`, it will generate a new leiningen project for you. `cd` into that directory and run `lein repl`.

After it boots up the JVM, this will give us a Clojure REPL. Cooooool. Try it out! `(+ 1 1)`

###Editor

Technically, we already have everything we need to start wrtiing Clojure. But if we are going to define multi-line functions and run them, doing all of this in a REPL can be a pain.

#####Atom
For the [Atom](https://atom.io/) editor, here is a [ cool plugin ](https://atom.io/packages/proto-repl). You need to be inside of your leiningen directory for this plugin to work.

#####VIM
For VIM users, grab TPope's [fireplace](https://github.com/tpope/vim-fireplace). You need to be inside of your leiningen directory with a REPL running in the command line for this to work.



#Tips




## License
MIT

