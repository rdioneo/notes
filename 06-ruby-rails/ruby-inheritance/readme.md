# Inheritance in Ruby

## Objectives

* Implement inheritance
* Describe what has been inherited from one class to another
* Compare and contrast inheritance in Ruby with Prototypical inheritance in Javascript
* Utilize inheritance to reduce repetition
* Utilize inheritance to model the world
* Install `pry` using `gem`. Pry is an improved REPL for Ruby that allows for better debugging and lets you work interactively with pre-written scripts through the use of `binding.pry`

####Quick Review
1. What is a method? What is a class?
2. What is an instance method?
3. Why do we use a class?

##Inheritance

Inheritance is used to indicate that one class will get most or all of its features from a parent class. Inheritance is useful for a couple reasons.

* DRY - Don't Repeat Yourself & reuse code functionality
* Faster implementation time

###Example

```rb
class Rectangle

  def initialize(l, w)
    @length = l
    @width = w
  end

  def get_area
    @length * @width
  end

  def print_shape
    puts "This is a rectangle"
  end

end

class Square < Rectangle
  def initialize(s)
    super(s, s)
  end

  def print_shape
    puts "This is a rectangle and a square"
  end
end
```

Note from the example above...

* In order to inherit from a class, we use the `<` keyword and specify the class we want to inherit from
* In order to correctly inherit from `Square`, we need to call the parent class's `initialize` method. We can do so by using the `super` method.
  * If we forget to do this, class and instance variables in the parent will not be initialized
  * When you invoke the `super` method with arguments, Ruby sends a message to the parent of the current object, asking it to invoke a method of the same name as the method invoking super.
* Once we inherit from another class, we can access methods and properties from the parent. In the case of this `Square` class, we also overrode the functionality of the `print_shape` method.

### A Guide through Animals

```rb
class Animal

  def initialize(kind)
    @kind = kind
    @state = "awake"
  end

  def eat(food)
    if @state == "awake"
      puts "NOM-nom!!"
      puts "(#{kind} has eaten #{food})"
    else
      puts "SLEEPING"
    end
    self
  end

  def sleep
    @state = "sleeping"
    self
  end

  def wake
    @state = "awake"
    self
  end
end

class Person < Animal
  def initialize(age, gender, name)
    super("Human")
    @age = age
    @gender = gender
    @name = name
  end
end
```

####Single Inheritance vs Multiple Inheritance
* In Ruby, a class can only inherit from a single other class. It **cannot** inherit from multiple classes.
  * Think about it. What are some benefits and disadvantages to single & multiple inheritance?

####Exercise
Create a Mammal class, Cat class, and Dog class. Have Cat and Dog inherit from Mammal. Include some attributes for each class and a method for mammal.
