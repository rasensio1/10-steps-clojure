# 10-steps-clojure

A Clojure library designed to... teach beginners how to get started with Clojure! 

## No Fat

I want to get you up and running in a fun environment as quickly as possible.

I find that the biggest hurdle in learning something new is getting stuck before you can have any fun!

#Get Excited!

Why learn Clojure?

  * It's a LISP! Be the diamond in the rough of programmers who understand how these work.
  * Smart people respect LISPs! [like this guy](http://www.paulgraham.com/avg.html) [and this one](http://blog.bigml.com/2013/06/21/clojure-based-machine-learning/)
  * Learn about functional programming concepts like `lazy-sequences`, `comp`, and `partial` (this is super cool if you're coming from ObjOriented like I did)
  * Learn about threading and asynchronous functions.
  * You can get a job in Clojure!
  * The ecosystem is filled with **really great tools**, and **very helpful people**. I am seriously amazed.


#####Let's get started!

#Web Resources

If you don't care about running clojure locally (yet), there is a REPL (place to type in code and see what happens) [here.](http://www.tryclj.com/)

An awesome list of exercises is found at [4Clojure.](http://www.4clojure.com/problems). You just type in what you think should go in the blank, and see if you're right. Test your intuition.

Skip down to [Tips](#tips) if you don't care about a local environment.

#Setting up your local Environment

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

`cmd + alt + L` splits the Atom window, and gives you a REPL on one half
`cmd + alt + B` while the cursor is inside of a clojure expression evaluates that function inside the REPL! 

#####VIM

For VIM users, grab TPope's [fireplace](https://github.com/tpope/vim-fireplace). You need to be inside of your leiningen directory with a REPL running in the command line for this to work.

`cpp` while the cursor is inside of a clojure expression evaluates that function inside a REPL! You'll see the output at the very botto of the window.

#Tips

So now we have a pretty good way of editing Clojure. How else can I help you? Maybe a few code samples and explanations.


####Example 1: Math
Take the following code sample:

    (+ 1 (* 2 (- 10 1)))

We read this from the inside out. So step by step, this expression looks like...

    (+ 1 (* 2 (- 10 1)))
    (+ 1 (* 2 9))
    (+ 1 18)
    19

Woohoo!

####Example 2: Strings

    (reverse (str "hello" "ok"))

`str` takes any number of arguments and combines them to become a string
You can guess what `reverse` does.

    (reverse (str "hello" "ok"))
    (reverse "hellook")
    "koolleh"

####Example 3: Variables

In clojure, we call an Array a **Vector**. And we don't need to use commas.
This is a vector of numbers `[1 2 3 4]`
If we want to reference this vector without retyping it, we can store it as a variable.
We use `def` to do this.

    (def my-vector [1 2 3 4])

Then, if we test this by typing: `my-vector`
    `> [1 2 3 4]` 

What if we only want the **first element** of the vector?
    `(first my-vector)`
    `> 1` 
    
What if we want to **sum** the elements?  
    `(reduce + my-vector)`
    `> 10` 

What if we want to see which elemets are **even?**
    `(map even? my-vector)`
    `> [false true false true]` 

`map` applies a function to each element in a collection, and returns the results of the functions.

What if we want to add one to each element?
    `(map (partial + 1) my-vector)`
    `> [2 3 4 5]` 

Woah. Cool. A `partial` creates a function that has some of the arguments already applied, and is waiting for the remaining arguments.

It's basically saying "We are going to add one and ..." And then it applies each element in the vector to the function.

    "We are going to add 1 and **1**" >> 2
    "We are going to add 1 and **2**" >> 3
    "We are going to add 1 and **3**" >> 4
    "We are going to add 1 and **4**" >> 5
    
  
####Example 4: Make your own functions

## License
MIT

