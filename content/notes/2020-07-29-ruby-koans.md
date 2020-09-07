---
title: Ruby Koans
author: Desmond Tuiyot
date: '2020-07-29'
slug: ruby-koans
categories: []
tags:
  - ruby
  - koans
  - ruby koans
---

## 1. About Asserts

* `assert` - if the expression returns `true`, it passes and continues. If not, it fails.
* `assert "add some message"` - it's probably a good idea to add a message next to the insert
* `assert some_val == some_other_val` - makes sense to compare reality against what is expected. 
  * use `assert_equal some_val, some_other_val` instead.
  * you can also have more than 2 values here. `assert_equal some_val, other_val, again_val...` is valid
* `assert_match(/  /, "...")`

## 2. About nil

* In ruby, `nil` has a type **Object**, unlike other languages. Syntax for checking if a value is of a particular type
  ```{ruby}
  nil.is_a?(Object)
  ```
* What happens when you call a method that doesn't exist? (on nil or in general?)
  * You get a ***NoMethodError*** and a message with "undefined method 'method_name' for nil:NilClass"
  * *begin/rescue/end* clause is the equivalent to *try/catch/finally*
    ```{ruby}
    begin
      # some code that might fail
    rescue Exception => ex
      # code executed when an error occurs
    end
    ```
* Nil evaluates to false.
* Methods defined on nil. 
  ```{ruby}
  nil.to_s    # returns empty string
  nil.inspect # returns the string "nil"
  nil.nil?    # returns true
  nil.to_i/to_f/to_c/ # returns some variation of 0
  nil.to_a    # returns [], to_h returns {}
  ```
  * `obj.nil?` vs `obj == nil` - here both perform the same function. All objects aside from `nil` will return false on `obj.nil?`
  
## 3. About Objects

* Almost everything in Ruby is an object, including `nil`.
* Inspecting objects will return the string representation of the object?
  ```{ruby}
  123.inspect     # "123"
  "ruby".inspect  # "ruby"
  false.inspect   # "false"
  nil.inspect     # "nil"
  ```
* Every object has an id - it is of type `Integer` - each of them have different ids
* Small integers have fixed object id - the pattern is `2x + 1`, where x is the integer
* Clones create new objects
  * method to clone an object - `obj.clone`
    
    
    
    
# References