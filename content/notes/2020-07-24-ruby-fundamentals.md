---
title: Ruby Fundamentals
author: Desmond Tuiyot
date: '2020-07-24'
slug: ruby-fundamentals
categories: []
tags:
  - ruby
  - language fundamentals
bibliography: ref.bib
---


# 1. Introduction to Ruby

* Some characteristics of Ruby:
  * High level
  * Interpreted - does not need a compiler to run
  * Object-oriented
  * Easy to use
* **Data Types: Numbers, Strings, Booleans** -  Things to note
  * Ruby is case sensitive
  * Booleans are `true`, `false` (note capitalized)
  * No line ending semi colons (or any other symbol for that matter)
* **Variables**
  * Naming convention - snake_case, not camelCase like javascript. 
* **Operations** -  the usual
  * including `+=` and `-=` notation
  * Ruby doesn't have `++` or `--`
* **`puts` and `print`**
  * no parenthesis needed
  * `print` simply prints out whatever value you specify. Can take multiple arguments
  * `puts` (put string) does the same but adds a newline after what you've printed. Only takes one argument
    ```{ruby}
    print "Desmond", 1, true
    puts "Tuiyot"
    ```
* **All things are objects**
  * Becoming more and more a rule of the world
  * Because everything is an object, they have methods
    * These method calls don't have parenthesis at the end of them? Confusing as hell
    * Can chain method calls
  * The *interpreter* takes in the code you wrote, runs it, and shows the results (if any) on a console
* **String methods**
  * string`.length`
  * string`.reverse`
  * string`.upcase`, string`.downcase`
  * string.`.capitalize` - this capitalizes only the first letter and returns a new string
  * string`.capitalize!` - same as `.capitalize` but modifies the string in place. 
* **Comments**
  * *single-line* - `#` symbole
  * *multi-line* -  anything in between `=begin` and `=end`. Remember, no space between `=` and `begin/end`.
* **Naming conventions**
  * As I'd observed, use snake_case
  * You can start with capital letters, `$`'s and `@`'s, but these mean different things (I bet)
* **Getting User input**
  * `gets` - used to ask for user input.
  * `chomp` - Ruby automatically adds a new line after each bit of input. User `.chomp` to remove this newline
  * `gets.chomp`
* **String formatting**
  * To perform *string interpolation*, use the syntax `"... #{variable_name} ..."`
    ```{ruby}
    first_name = "Desmond"
    puts "Hi, my name is #{first_name}"
    ```
* **In place modification**
  * Attach `!` at the end of the method call in order to do this.
  * `.capitalize!`, `.upcase!`, `downcase!`

# 2. Control Flow in Ruby

* **Basic syntax**
  ```{ruby}
  if expr1
    # statement1
  elsif expr2
    # statement2
  else
    # statement3
  end
  ```
  * Ruby doesn't care about whitespaces, so indentations are not necessary. However, it's good practice to indent if/elsif/else code blocks anyways. Use 2 spaces for indentation.
* **String to integer conversion**
  * `Integer(some_var)`
* **Unless**  - *(this is interesting)*
  * This is used to check if a condition is *false* rather than if it's true
  ```{ruby}
  hungry = true
  unless hungry
    print "Gonna write some code"
  else
    print "Gotta eat fam!"
  ```
* **Comparators/Relational Operators**
  * `==` and `!=`
  * `</<=`, `>/>=`
* **Boolean/Logical operators**
  * `&&`, `||`, `!`
* **Check for substring in string**
  ```{ruby}
  if string_to_check.include? "substring"
  ```
  * As a general rule, ruby methods that end with `?` evaluate to `true` or `false`
* **Replacing some string with another**
  * use `gsub!` *(global substitution)*
    ```
    string_to_change.gsub!(/s/, "th")
    ```
  * Why have the string in between slashes instead of quotes?

# 3. Looping w/ Ruby

* **the `while` loop**
  ```{ruby}
  counter = 1
  while counter < 11
    puts counter
    counter = counter + 1
  end
  ```
* **the `until` loop**
  * This is the complement of the `while` loop. It does the reverse of what `while` does.
  ```{ruby}
  counter = 1
  until counter > 10
    puts counter
    counter += 1
  end
  ```
* **the `for` loop**
  * There are inclusive vs exclusive ranges. 
  * To exclude the last value in the range, use 3 dots `...`. Otherwise, use 2 dots `..`.
  ```
  for num in 1...10
    puts num
  end
  # prints out 1 to 9
  
  for num in 1..10
    puts num
  end
  # prints out 1 to 10
  ```
* **the `loop` iterator**
  * It's possible to repeat action using an *iterator* - Ruby method that repeatedly invokes a block of code.
  * `loop` is a basic iterator, the simplest, most basic one.
  ```{ruby}
  i = 0
  loop do
    i += 1
    print "#{i}"
    break if i > 5
  end
  ```
  * In ruby, curly braces are essentially equivalent to keywords `do` (=`{`), and `end` (=`}`)
* **the `next` keyword**
  * works like Python `continue`. 
  ```{ruby}
  for i in 1..5
    next if i % 2 == 0
    print i
  end
  ```
* **the `array` data structure**
  * basic declaration and initialization  - `my_array = [1,2,3,4,5]`
* **the `.each` iterator**
  * This can apply an expression to each element in an object, one by one
  * Basic syntax 
    ```{ruby}
    object.each { |item| 
      # Do something 
    }
    ```
  * Or, replacing the curly braces with keywords
    ```{ruby}
    object.each do |item| 
      # Do something 
    end
    ```
  * those object elements can be accessed using `item`
* **the `.times` operator**
  * It's like a compact `for` loop: it can perform a task on each item in an object a specified number of times.
    ```{ruby}
    10.times { print "Chunky bacon!" }
    ```
* **more string methods**
  * text`.split` or  text`.split(delimeter)` - returns an array of strings

  

# 4. Arrays & Hashes

* **Arrays**
  * `my_array = [...]`
  * access by index
  * pushing to an array `my_array.push(4)`
* **Hashes**
  * Hash *literal* initialization. (Called *literal* since I literally describe what I want inside the hash)
    ```{ruby}
    hash = {
    key1 => value1,
    key2 => value2,
    key3 => value3
    }
    ```
  * You can use ***ANY*** ruby object, including mutable ones like arrays
* **Access** involves
  ```{ruby}
  hash[key1]
  hash[key2]
  ...
  ```
* To create an empty hash
  ```{ruby}
  my_hash = Hash.new
  my_hash2 = Hash.new(0)
  ```
  * With this, you can add a *default value* to the hash. Attempted access to a non existent `key` will return that default value.
  * **Adding to empty hash**
    ```{ruby}
    pets = Hash.new
    pets["Beezus"] = "Dog"
    ```
* **Iterating over a hash**
  ```{ruby}
  hash = {
    key1 => value1,
    key2 => value2,
    key3 => value3
    }
  
  hash.each { |x| puts "#{x}\n" }
  hash.each { |x ,y| puts "#{x}: #{y}" }
  ```
* **Iterating over multi-dimensional arrays**
  * Loop within a loop
    ```{ruby}
    s = [["ham", "swiss"], ["turkey", "cheddar"], ["roast beef", "gruyere"]]

    s.each { |x| 
      x.each { |y|
      puts y
      }
    }
    ```
* **More methods**
  * **Sorting:** I assume this works on any iterable, since it works on hashes as well
  * This returns an array of arrays
    ```{ruby}
    colors = { 
      "blue" => 3,
      "green" => 1,
      "red" => 2
      }
    colors = colors.sort_by do |color, count|
    count
    end 
    ```
  * **Reversing an array or string**
    ```{ruby}
    colors.reverse!
    ```

# 5. Methods, Blocks, and Sorting

* There are no functions in Ruby
* **Methods Syntax**
  ```{ruby}
  def puts_1_to_10
    (1..10).each { |i| puts i }
  end

  puts_1_to_10
  ```
* **Parameters and Arguments**
  * *Argument* - what you put in the parenthesis when *calling* the method
  * *Parameter* - what you put in the parenthesis when *defining* the method
  ```{ruby}
  def square(n)
    puts n ** 2
  end
  ```
  * Parenthesis in Ruby are optional
* **Splat arguments**
  * These are preceded by `*`, and allows a function to take in a variable number of arguments. 
    ```{ruby}
    def what_up(greeting, *friends)
      friends.each { |friend| puts "#{greeting}, #{friend}!" }
    end

    what_up("What up", "Ian", "Zoe", "Zenas", "Eleanor")
    ```
* **return** keyword - as per usual
* **methods that return a boolean** - it's best practice to end them with a question mark
* **Blocks - nameless methods?**
  * they are defined by the `do...end` or `{ ... }` duo and are not named
    ```{ruby}
    1.times do
      puts "I'm a code block!"
    end
    ```
* **Using code blocks**
  * A method can take a block as a parameter - it's what `.each` has been doing
  * Passing a block to a method is a great way of abstracting certain tasks from a method and defining those tasks when we call the method
  ```{ruby}
  [1, 2, 3, 4, 5].each { |i| puts i }

  [1, 2, 3, 4, 5].each { |i| puts i*5 }
  ```
* **Sorting**
  * `my_array.sort!`
* **the *combined comparison operator***
  * a.k.a the *spaceship operator* is used to compare two values. `val1 <=> val2` returns -1, 0, or 1 if `val1` is less than, equal to, or greater than `val2`
  ```
  book_1 = "A Wrinkle in Time"
  book_2 = "A Brief History of Time"

  puts book_1 <=> book_2   # returns 1
  ```
* **specifying order**
  * A block that's passed to a `sort` method must return 1, 0, or -1 appropriately
  * `sort` takes an optional argument that tells it how to compare two items
    ```{ruby}
    arr = [1,2,3,4]
    arr.sort! { |first, second| second <=> first }  
    # prints out [4, 3, 2, 1]
    ```
* **misc**
  * the last evaluated value is returned implicitly
  

# 6. Hashes and Symbols

* **Nil: a formal introduction**
  * When you try to access a non-existent key in a hash, you get the value `nil`
  * I get the feeling that this is just Ruby's `undefined` and `null` combined.
  * Along with the boolean `false`, `nil` is one of two falsy values in Ruby - everything else is considered truthy 
  * Interesting - even integer `0` and the empty string are truthy
* **Setting a hash default**
  * Initializing a hash with `Hash.new` allows you to set a default value
    ```{ruby}
    no_nil_hash = Hash.new("this is the default")
    puts no_nil_hash["does not exist"] # returns "this is the default"
    ```
* **The Rubyist key is a Symbol object**
  * Symbols are a kind of name, but are different from strings. There syntax is as such - `:symbol_name`
  * Another difference is that while there can be multiple different strings all with the same value, there can only be one copy of a particular symbol at a time
    * The `.object_id' method returns the id of an object and is probably what Ruby uses to determine if 2 objects are the same object.
    ```{ruby}
    s1 = :symbol
    s2 = :symbol
    s3 = :symbol
    puts "#{s1.object_id}, #{s2.object_id}, #{s3.object_id}"  
    # 802268, 802268, 802268
    ```
* **Symbol syntax rules**
  * Always start with a colon, then either a letter or underscore, after which any combination of letters, underscores, and numbers is allowed.
* **What are symbols used for?**
  * Often used in Ruby: `(1)` as Hash keys or `(2)` to reference method names(??).
  * Symbols make good hash keys for these reasons:
    1. they are immutable once created
    2. they save memory since there can only be one copy of a symbol at a time
    3. symbols-as-keys are faster than strings-as-keys because of the above reasons
* **Converting between symbols and strings**
  * to string => `.to_s`, and to symbol => `.to_sym`
  * `.intern` also converts a string to a symbol. It internalizes(??) the string into a symbol.
* **the Hash rocket style**
  * This refers essentially the syntax `=>` we've been using in hashes between the keys and their values - looks like a tiny rocket
  * However, this changed in Ruby 1.9
    1. the colon is now placed at the end of a symbol
    2. there is no need for the rocket anymore
  ```{ruby}
  old_hash {
    :ahs => "some series",
    :itaewon => "some other series"
  }
  
  new_hash {
    ahs: "some series",
    itaewon: "some other series"
  }
  ```
  * This change in syntax only applies in a hash.
* **Comparing string-as-keys and symbols-as-keys**
  * *importing modules* - `require 'some_module'`
  * *alphabetical ranges* - `("a".."z")`, `(:a..:z)`
  * *converting ranges to arrays* - `(1..26).to_a`
  * *zip function* - `arr1.zip(arr2)`
  * *testing runtime*
    ```{ruby}
    require 'benchmark'
    t = Benchmark.realtime do 
      # code to be tested
    end
    ```
  * *number readability* - you can have underscores in a number to enhance readability. `num = 900_000_000` is a valid statement
* **Filtering your hash**
  * Use `.select`
  ```{ruby}
  grades = { alice: 100,
    bob: 92,
    chris: 95,
    dave: 97
  }

  grades.select { |name, grade| grade <  97 }
  # ==> { :bob => 92, :chris => 95 }

  grades.select { |k, v| k == :alice }
  # ==> { :alice => 100 }
  ```
* **Iterating over just keys or just values**
  * use `each.key` or `each_value` respectively 
  ```
  my_hash = { one: 1, two: 2, three: 3 }

  my_hash.each_key { |k| print k, " " }
  # ==> one two three

  my_hash.each_value { |v| print v, " " }
  # ==> 1 2 3
  ```
* **Case statement**
  * Basic syntax
  ```{ruby}
  case language
    when "JS"
      puts "Websites!"
    when "Python"
      puts "Science!"
    when "Ruby"
      puts "Web apps!"
    else
      puts "I don't know!"
  end
  ```
* **conversions, checking type**
  * `.nil?` checks if the value is nil
  * `.to_i` converts a string to integer
* **deleting a key-value pair**
  * `my_hash.delete(key_to_delete)`

# 7. Refactoring: the Zen of Ruby

* *Ruby prioritizes programmer productivity over program optimization*
  * It might be slower, but it's a delight
* **short-hand if/unless statement** - use this when the if statement is short
  ```{ruby}
  # expression if boolean
  puts "an expression" if true
  
  # expression if boolean
  puts "an expression" unless true
  ```
* **Ternary operator**
  ```{ruby}
  # boolean ? do this if true: do this if false
  def eloquent?
    return true
  end
  ruby_is = eloquent? ? "eloquent": "not eloquent"
  
  # prints out 'eloquent'
  ```
* **Ruby folded case**
  ```{ruby}
  case language
    when "JS" then puts "Websites!"
    when "Python" then puts "Science!"
    when "Ruby" then puts "Web apps!"
    else puts "I don't know!"
  end
  ```
* **Conditional assignments** - when we want to assign a value to a variable only when it hasn't been assigned
  ```{ruby}
  favorite_book ||= "Cat's Cradle"
  puts favorite_book    # Cat's Cradle

  favorite_book ||= "Why's (Poignant) Guide to Ruby"
  puts favorite_book    # Cat's Cradle
  ```
* **Implicit Return** - just like R in this sense. It returns the value of the last evaluated expression. I love it!
* **Short circuit evaluation** is also a thing in Ruby.
* **The right tool for the job** - instead of for loops use:
  * `5.times { # some task  }` any time you want to perform a task a certain number of times
  * `[a1, a2, a3].each { |v| # some task involving v  }` any time you want to perform a task for each element in an array 
* **upto and downto for ranges**
  ```{ruby}
  95.upto(100) { |x| print x, " " } # 95 96 97 98 99 100
  100.downto(98) { |x| print x, " "  } # 100 99 88
  "A".upto("D") { |c| print c, " " } # A B C D
  ```
  * these work on alphabets as well (even the ... notation)
* **Call and response** - this answers how symbols can be used to reference methods
  * *getting the next integer (or letter, I assume)* - `1.next => 2`, `"A".next => "B`
  * `.respond_to?` is a method that is called on an object/value and takes a symbol (the name of a method) then returns true if that symbol can be called on that object and false otherwise
  ```{ruby}
  puts 1.respond_to?(:next) # true
  puts [1,2,3].respond_to?(:push) # true
  puts [1,2,3].respond_to(:to_sym) # false
  ```
* **pushing with a shovel** - the *concatenation operator*, `<<` can be used as a substitute for `push` in arrays and `+` in strings
  ```{ruby}
  puts [1,2,3] << 4 # [1,2,3,4]
  puts "I am a " << "god"
  ```
* **String interpolation** - I been doing this
  ```{ruby}
  drink = "alcohol"
  age = 21
  puts "I'm #{age} now, and I love #{drink}!"
  ```
  * The longer route is pretty damn long
    ```
    "I love " + drink
    "I am " + age.to_s + " years old" 
    ```
* **Refactoring**
  1. Using single line `if's`, `unless's` and `ternary operators`.
    * `.is_a object_type` checks to see if attached object is of a specified object type
  2. Eliminating return statements 
  
# 8. Blocks, Procs, and Lambdas

* **Blocks**
  * A *block* is a bit of code that can be executed. It's usually nested within `do ... end` or `{ ... }` and can be combined w/ methods like `.each` or `.times` to execute the code repeatedly.
* **the `collect` method, also the `map` method**
  * This method takes a block and applies the expression inside it to every element of the object it's called on, then returns it.
    ```{ruby}
    arr = [1,2,3,4]
    arr.collect { |x| x**2 } 
    # returns [1,4,9,16], but original doesn't change
    arr.collect! { |x| x**2 } # original changes
    ```
  * *Aside:* `!` at the end of a method in ruby  means that the method could do something potentially dangerous or unexpected. In many cases, the method modifies the object it's called on in place. 
* **Learning to `yield`**
  * How are some methods able to accept blocks and others don't? Because those that do use `yield` to transfer control from the calling method to the block and back again. What does the following return?
    ```{ruby}
    def block_test
      puts "First line in code"
      puts "still in block test"
      yield
      puts "back in block test"
    end
    
    block_test { puts "in the damn block fam!" }
    ```
  * You can pass parameters to `yield` - what does the code below return?
    ```{ruby}
    def yield_name(name)
      yield("Kim")
      yield(name)
    end
    
    yield_name("Eric") { |n| puts "My name is #{n}." }
    ```
* **Procs**
  * Not everything in Ruby is an object - blocks are not objects and therefore cannot be saved to a variable and re-used
  * For that, we need *Procs*. We declare a proc as below and pass it in to a method that would otherwise take a block. 
    ```{ruby}
    multiples_of_3 = Proc.new do |n|
      n % 3 == 0
    end
    
    (1..100).to_a.select(&multiples_of_3)
    # prints out multiples of 3 between 1 and 100
    ```
  * The `&` converts the proc to a block, and we use that anytime we pass in a proc to a method that expects a block.
  * `collect!` and `map!` do the exact same thing.
  * The `.floor` function does what it says
  * *Why Procs?* 
    1. They are objects, and therefore come with all the capabilities of one (which I don't know about)
    2. They can be called repeatedly without having to rewrite them. **DRY**
* **calling procs**
  * You can call procs directly using `.call` method
    ```{ruby}
    hi = Proc.new { puts "Hey hey hello there!" }
    hi.call
    # prints out "Hey hey hello there!"
    ```
* **Symbols and procs**
  * One of the uses of symbols was to reference method names/pass methods around
  * You can also convert symbols to procs; i.e. convert methods to procs.
    ```{ruby}
    numbers_array = [1, 2, 3, 4, 5, 6]
    strings_array = numbers_array.collect(&:to_s)
    
    puts strings_array
    # ["1", "2", "3", "4", "5", "6"]
    ```
* **the Ruby `Lambda`**
  * Lambdas are objects, just like Procs. 
  * With the exception of some syntax and behavioral quirks, lambdas are quite identical to procs.
  * Passing a lambda to a method works the same as procs too.
  * *Lambda syntax*
    ```{ruby}
    # lambda { |param| block }
    
    lambda { |s| s.to_sym }
    lambda { puts "Hello!" }
    ```
* **Lambdas vs Procs**
  1. A lambda checks the number of arguments passed to it, while a proc does not.
    * Thus, lambdas will return an error when the wrong number of arguments are passed, while procs will ignore unexpected warnings and assigns the missing arguments to `nil`
  2. When a lambda returns, it passes control over to the calling method, but when a proc returns it does so immediately without going into the calling method. What's the output of the code below?
    ```{ruby}
    def batman_ironman_proc
      victor = Proc.new { return "Batman will win!" }
      victor.call
      "Iron Man will win!"
    end
    
    puts batman_ironman_proc
    
    def batman_ironman_lambda
      victor = lambda { return "Batman will win!" }
      victor.call
      "Iron Man will win!"
    end
    
    puts batman_ironman_lambda
    ```

# 9. Object Oriented Programming I

* **Classes**
  * Objects have *methods* and *attributes*
  * A *class* is a way of organizing and producing objects with similar attributes and methods
* **Class syntax**
  * The class name is CamelCased and the `__init__` function equivalent is called `initialize`
  * We specify *instance variables* by prefixing the variable name with `@` => `@name, @make`
  * A basic declaration looks like:
    ```{ruby}
    class Person
     def initialize(name)
       @name = name
     end
    end
    ```
  * To instantiate a `Person` object
    ```{ruby}
    matz = Person.new("Yukihiro")
    ```
* **Scope**
  * Inside a class, we can have:
    1. *global variables* accessible from anywhere
    2. *local variables* only available within a method
    3. *class variables* which belong to a specific class
    4. *instance variables* which belong to a specific instance of a class
  * Instance and class variables are `nil` until assigned
  * The same goes for methods as well - *global*, *class*, and *instance*
  * We use `$`, `@`, `@@` to indicate global, instance, and class variables respectively
  * Global variables can also just be declared outside of any method or class as normal (without the `$`) - the sign is only used when defining a global variable from within a class or method.
  * That said, global variables are generally not a good idea
    ```{ruby}
    class MyClass
      $my_variable = "Hello!"
    end
    
    puts $my_variable
    ```
* **Inheritance**
  * The process by which one class takes on the attributes and methods of another. 
  * It describes an `is-a` relationship: *Fox `is-a`n Animal, Man `is-a` Human*
    ```{ruby}
    class DerivedClass < BaseClass
      # class magicks
    end
    ```
* **Overriding methods** - this is of course possible. Just define a method with the same name as one found in its parent
* **super** - you can use the `super` keyword inside a method to access it's base/parent's class
  ```{ruby}
  class DerivedClass < Base
    def some_method
      super(optional args)
        # Some stuff
      end
    end
  end
  ```
  * This code looks in the *superclass* of the current class for a method with the same name as the one in which *super* was called.
* **Multiple Inheritance?**
  * Ruby disallows this, unfortunately. It is possible, however, to incorporate data and behavior from different classes in one, through *mixins* (to be covered later)
  * *Aside:* you can use a semi colon `;` to end a statement w/out moving to a new line.
  * What happens when you make one class inherit from multiple classes? You get a `superclass mismatch error`
    ```{ruby}
    class Creature ... ; end
    
    class Person ... ; end
    
    class Dragon < Creature; end
    class Dragon < Person; end
    ```
* **Miscellaneous**
  * *Getting the current time*  -`time = Time.now`
  * *Declaring a class method* -prefix it with the `ClassName` itself.
    ```{ruby}
    class Machine
      def Machine.hello
        puts "Hello from the machine!"
      end
    end 
    ```
 
# 10. Object Oriented Programming II

* **public vs private**
  * Ruby allows you to specify if methods(what about attributes) are public or private.
  * Just write either `public` or `private` on a single line and define all the appropriate methods below it. 
  * `private` methods can only be called from inside the object in which it's defined.
  * Specifically, these methods cannot be called with an *explicit receiver* (these are objects on which a method is called)
  * If we wanna access private information, we can create public methods that return them.
  * *private implementation* vs *public interface*
    ```{ruby}
    class ClassName
      # Some class stuff
    
      public
      # Public methods go here
      def public_method; end
    
      private
      # Private methods go here
      def private_method; end
    end
    ```
* **getting and setting properties**
  * Previously, in order to get or set instance attributes, we'd need to define a public method that does so
    ```{ruby}
    def name
      @name
    end
    
    def name=(name)
      @name = name
    end
    ```
    * The `name=` notation is Ruby convention for specifying that the method is a setter. Just like we attach `?` at the end of a boolean returning method.
  * We don't have to create these methods anymore, but can use the notation `attr_reader` and `attr_writer` to perform the same functions. We pass in the instance variables as symbols to these two.
  * In case we want to make one variable readable and writable, we can use `attr_accessor`
    ```{ruby}
    attr_reader :name
    attr_writer :name
    
    # or
    attr_accessor :name
    ```
* **Modules**
  * What are they? A kind of toolbox that stores set methods and constants. They are like classes, but can't create instances nor have classes
  * *module syntax*
    ```{ruby}
    module SomeModule
      # stuff
    end
    ```
  * Modules usually hold either methods or constants (makes no sense to have variables). Constants are ALL_CAPS and separated by underscores in case there's more than one word.
  * Ruby allows you to change the value of a constant once initialized, but it warns you when you do so.
* **Namespacing and scope resolution**
  * One of the main purposes of modules is ***namespacing***, which means to separate methods and constants into different *name spaces*.
  * We can use double colon notation `::` to tell Ruby where to look for certain methods or constants; this is called the ***scope resolution operator***
    ```{ruby}
    module MyLib
      PI = 1.1111
    end
    puts MyLib::PI # = 1.1111
    puts Math::PI  # = 3.141592653589793 
    ```
* **Importing/Requiring modules**
  ```{ruby}
  require 'date'
  ```
* **Including modules** 
  * Any class that includes a certain module can use that module's methods and constants
  * A nice consequence of this is that it's no longer necessary to prepend method and constant names with `Module::` in order to access it
    ```
    class Angle
      include Math
      attr_accessor :radians
      
      def initialize(radians)
        @radians = radians
      end
      
      def cosine
        cos(@radians)
      end
    end
    
    acute = Angle.new(1)
    acute.cosine
    ```
* **Marrying Modules and Classes**
  * When a module is used to mix in additional behavior and info into a class, it's known as a `Mixin`
  * *Mixins* allow us to customize a class without having to rewrite code
* **Extending classes**
  * *Mixins* have allowed instances of a class to use a module's methods, `extends` allows classes themselves to use these modules' methods. 



  
  
# References