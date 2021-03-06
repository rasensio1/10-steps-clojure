# 10-steps-clojure

A Clojure library designed to... teach beginners how to get started with Clojure! 

## No Fat

I want to get you up and running in a fun environment as quickly as possible.

I find that the biggest hurdle in learning something new is getting stuck before you can have any fun!

# Get Excited!

Why learn Clojure?

  * It's a LISP! Be the diamond in the rough of programmers who understand how these work.
  * Smart people respect LISPs! [like this guy](http://www.paulgraham.com/avg.html) [and this one](http://blog.bigml.com/2013/06/21/clojure-based-machine-learning/)
  * Learn about functional programming concepts like `lazy-sequences`, `comp`, and `partial` (this is super cool if you're coming from ObjOriented)
  * Learn about threading and asynchronous functions.
  * You can get a job in Clojure!
  * The ecosystem is filled with **really great tools**, and **very helpful people**. I am seriously amazed.


##### Let's get started!

# Web Resources

If you don't care about running clojure locally (yet), there is a REPL (place to type in code and see what happens) [here.](http://www.tryclj.com/)

An awesome list of exercises is found at [4Clojure.](http://www.4clojure.com/problems). You just type in what you think should go in the blank, and see if you're right. Test your intuition.

Skip down to [Tips](#tips) if you don't care about a local environment.

# Setting up your local Environment

You need a few things to started writing Clojure on your computer.

  1. Java
  2. Leiningen
  3. An editor with a built-in REPL (not necessary, but makes developing way better)

### Java

Clojure compiles into Java and runs on the JVM. So we need Java.

Run `java -version` in your terminal. If you have version `1.6` or later, your'e fine! If not, go [here](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and get the newest version.

### Leiningen

Leiningen gives us many important things including...

  * A way to manage dependencies in Clojure
  * A REPL we can use to try out some code!

Now, install [Leiningen](http://leiningen.org/). If you're a Mac user with homebrew, `brew install leiningen` should do the trick.

If you type `lein new SomeRandomName`, it will generate a new leiningen project for you. `cd` into that directory and run `lein repl`.

After it boots up the JVM, this will give us a Clojure REPL. Cooooool. Try it out! `(+ 1 1)`

### Editor

Technically, we already have everything we need to start writing Clojure. But if we are going to define multi-line functions and run them, doing all of this in a REPL can be a pain.

##### Atom

For the [Atom](https://atom.io/) editor, here is a [ cool plugin ](https://atom.io/packages/proto-repl). You need to be inside of your leiningen directory for this plugin to work.

`cmd + alt + L` splits the Atom window, and gives you a REPL on one half
`cmd + alt + B` while the cursor is inside of a clojure expression evaluates that function inside the REPL! 

##### VIM

For VIM users, grab TPope's [fireplace](https://github.com/tpope/vim-fireplace). You need to be inside of your leiningen directory with a REPL running in a command line window for this to work.

`cpp` while the cursor is inside of a clojure expression evaluates that function inside a REPL! You'll see the output at the very bottom of the window.

# Tips

So now we have a pretty good way of editing Clojure. How else can I help you? Maybe a few code samples and explanations.


#### Example 1: Math
Take the following code sample:

    (+ 1 (* 2 (- 10 1)))

We read this from the inside out. So step by step, this expression looks like...

    (+ 1 (* 2 (- 10 1)))
    (+ 1 (* 2 9))
    (+ 1 18)
    19

Woohoo!

#### Example 2: Strings

    (reverse (str "hello" "ok"))

`str` takes any number of arguments and combines them to become a string
You can guess what `reverse` does.

    (reverse (str "hello" "ok"))
    (reverse "hellook")
    "koolleh"

#### Example 3: Variables

In clojure, we call an Array a **Vector**. And we don't need to use commas.
This is a vector of numbers `[1 2 3 4]`
If we want to reference this vector without retyping it, we can store it as a variable.
We use `def` to do this.

    (def my-vector [1 2 3 4])

Then, if we test this by typing: `my-vector`

    > [1 2 3 4]

What if we only want the **first element** of the vector?

    (first my-vector)
    > 1 
    
What if we want to **sum** the elements?  

    (reduce + my-vector)
    > 10 

What if we want to see which elemets are **even?**

    (map even? my-vector)
    > [false true false true]

`map` applies a function to each element in a collection, and returns the results of the functions.

What if we want to add one to each element?

    (map (partial + 1) my-vector)
    > [2 3 4 5]

Woah. Cool. A `partial` creates a function that has some of the arguments already applied, and is waiting for the remaining arguments.

It's basically saying "We are going to add one and ..." And then it applies each element in the vector to the function.

    "We are going to add 1 and ... **1**" >> 2
    "We are going to add 1 and ... **2**" >> 3
    "We are going to add 1 and ... **3**" >> 4
    "We are going to add 1 and ... **4**" >> 5
    
  
#### Example 4: Make your own functions

What if we want to map over our collection and do something really cool? Like add two and then multiply by two.

We can define our own function! We use `defn` to do this.

Our function would look like this:
    (defn my-special-function [element] (* 2 (+ 2 element)))

We put the arguments that the function takes in brackets " [] ". This function takes one argument, an 'element'. If we wanted it to take two arguments, we could write 

    (defn some-func [elem1 elem2])

We can apply our function this way:
    
    (map my-special-function my-vector)
    > [8 10 12 14]

# More advanced examples

Lets take a look at something a bit more advanced. From [ Project Euler ](https://projecteuler.net/problem=6)...

    Sum of the squares of the first ten natural numbers is,

    12 + 22 + ... + 102 = 385
    The square of the sum of the first ten natural numbers is,

    (1 + 2 + ... + 10)2 = 552 = 3025
    Hence the difference between the sum of the squares of the first ten
    natural numbers and the square of the sum is 3025 − 385 = 2640.

    Find the difference between the sum of the squares of the first one 
    hundred natural numbers and the square of the sum.

...


Ok. How do we approach this? By breaking the problem down into smaller pieces!

  * Finding the sum of squares of a collection
  * Finding the square of sums of a collection

**And even smaller**

  * Finding the square of one number
  * Applying that to every element in a collection
  * Summing up a collection of those numbers

  * Summing up a collection of numbers
  * Finding the square of that number


#### Square of one number

    (defn square [num] (* num num))


#### Applying 'square' to a collection
Where 'coll' is collection of numbers like [1 2 3 4]
  
    (map square coll)

#### Summing up the squares

    (defn sum-squares [coll] (reduce + (map square coll)))

So now, we can find the sum of squares!

#### Summing up a collection of numbers
We've already done this a few times.

    (reduce + coll)

#### Finding the square of that one number
We've already done this too!

    (square (reduce + coll))

Let's put that in a function.

    (defn square-sums [coll] (square (reduce + coll)))

#### Wrapping it up...

Now, our **sum of squares** applied to ten numbers looks like:

    (sum-squares [1 2 3 4 5 6 7 8 9 10])

Or even simpler

    (sum-squares (range 1 11))

Our **square of sums** applied to ten numbers looks like:

    (square-sums (range 1 11))

The difference could be put in a function like so:
  
    (defn difference [coll] (- (square-sums coll) (sum-squares coll)))

Then, to call it...

    (difference (range 1 11))

Boom. You did it!


# Additional Resources

Having mostly been teaching myself, the two best resources have been

  * [ Living Clojure ](http://shop.oreilly.com/product/0636920034292.do)
  * Stack Overflow

Living Clojure, I prefer over Clojure for the Brave and True because I feel it is more succinct.

# Another fun path

Did you know there is a version of Clojure that compiles into Javascript? It's called [Clojurescript](https://github.com/clojure/clojurescript).

This means that you can make web apps in Clojure! There are even libraries that let you use ReactJS style components.

I built [ Snake ](https://github.com/rasensio1/gametime) using Clojurescript and [explained the process here.](http://rasensio.svbtle.com/beginners-guide-to-an-app-in-clojure)

# Final Thoughts

I'm excited for the future of Clojure. It seems like it is being used more and more in the professional world, something that the LISP community was previously lacking.

Happy coding!

# License
MIT

