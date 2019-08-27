
# Methods

## About Methods

* There is a differentiation between methods and functions, but it is slight, and many don't make the distinction
* Methods in Scala belong to context like a `class`, `object`, `trait`, a script, or another method.
* In Scala, a method starts with `def`
* Parameters are in reverse of what is expected in Java, value or variable before the type, e.g `age:Int`

## A Basic Non-Concise Method

* The `:Int` is the return type
* If you expect something in return you need, an equal sign (=)
* If you do not then leave it out


```scala
def add(x: Int, y: Int):Int = {
      return x + y
}
```




    add: (x: Int, y: Int)Int
    



## Cleaning up our Method

* A method can make use of type inference
* The braces are optional
* `return` is optional, in fact, it is rarely used

Therefore…​


```scala
def add(x: Int, y: Int) = x + y
```




    add: (x: Int, y: Int)Int
    



Discuss: Why there no longer is :Int at the end?

## When type inference is not good enough

There are times when you need the type:

* To make things clear
* Because the type inferencer could be wrong
* Your method might be overloaded and it would be needed disambiguate from other methods
* You’re doing recursion
* You’re doing method overloading

## Figuring out the type

Given the following, what return type is inferred? See if you can figure it out before running the cell.


```scala
def numberStatus(a:Int) =
   if (a < 10) "Less than 10"
   else if (a > 10) "Greater than 10"
   else "It is 10!"
```




    numberStatus: (a: Int)String
    



## Methods Conclusion

* Methods are defined using def and are always defined using def
* Methods are not to be confused with functions.
* The return keyword is unnecessary…​because the last evaluated statement will be returned
* Most of the time you can omit the return type in method unless:
  * You need it for clarity
  * To override the type inferencer
  * You will be performing recursion
  * You will be performing method overloading

## Methods Different Return Types

### Type Inferencing

* Scala’s type "inferencer"
  * Will always make the best choice possible given the information that it has.
  * If it cannot find a match it will search for the parent of the two classes
  * This will apply to how a `List` (which we will see soon) is created and return types from an `if` 
  

### Scala's class hierarchy

![scalahierarchy.png](attachment:scalahierarchy.png)

* `Any` is the super most type, above all!
* `AnyVal` is the super type of all JVM primitives
* `AnyRef` is the super type of all objects, analagous to `java.lang.Object`

### Lab: Colliding types
* When there is a chance that two or more types are being returned, the type inferencer will choose the parent of the types being returned.

**Step 1:** Try to guess what the return type for the following below will be before running it. Use the diagram above use your intuition as to where `String` will be in the diagram and run the cell.

**Step 2:** Discuss reasons


```scala
def add(x: Int, y: Int) = {
  if (x > 10) (x + y).toString
  else x + y
}
```




    add: (x: Int, y: Int)Any
    



**Step 3:** Try other combinations and ask questions

## *Lab:* isPrime

**Step 1:** Create a method that is called `isPrime` that takes a `Int` and returns whether the number provided is a prime number.
A prime is a positive integer $p$ where $p > 1$ that has no positive integer divisors other than $1$ and $p$ itself. 
More concisely, a prime number $p$ is a positive integer having exactly one positive divisor other than $1$, meaning it is a
number that cannot be factored.

__Hint:__ `1` is not prime, `2` is prime, and use something like a for loop to iterate from `2` to `n` and determine if any number is divisible

__More Hint:__ Here is a solution in Python:

```
def test_prime(n):
   if (n==1):
      return False
   elif (n==2):
      return True;
   else:
      for x in range(2,n):
         if(n % x==0):
            return False
      return True
```

NOTE: `test_prime` is not our style, use `isPrime` to name the method for Scala-style

## Methods Conclusion

* Methods are defined using def and are always defined using def
* Methods are not to be confused with functions.
* The return keyword is unnecessary…​because the last evaluated statement will be returned
* Most of the time you can omit the return type in method unless:
  * You need it for clarity
  * To override the type inferencer
  * You will be performing recursion
  * You will be performing method overloading
* Types inside of a method (this will also be applied to functions) will be inferred.
* Type inferencer will make its judgment based on what is available
* If types are different it will find a common ancestor and use that type
