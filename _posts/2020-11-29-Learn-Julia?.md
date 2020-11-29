---
title: scientific computing with Julia
layout: post
categories: <programming> <julia> <computing>
---

Once again, a shiny new object in the programming/engineering/data science world has caught my eye. This time it's Julia language. A co-worker introduced it to me as a counter to their woes with the dynamic type system of python. At first I thought, nah, python great! Who needs anything else other than the good old snek lang. But of course, the fates floated Julia lang in front of me again and again until I caved and began the often exciting, sometimes frustrating, and always entertaining process of learning a new programming language and paradigm. Julia has loads of interesting features like multiple dispatch (meaning not just overloaded function calls, but identical function signatures with differing types where Julia is smart enough to pick the right one, wicked cool!) but strong typing, speed, gpu integration, and a thriving community of contributors, libraries, and scientific computing libraries. There is a whole lot of promise in this, so I'm playing catch up to learn, and hopefully contribute back! Starting with the MIT Computational Thinking series available for free on YouTube, check the Julia Lang channel.

## Learnings and Notes

### Basics
- 1 Indexed!
- println to print
- typeof to check type
- Julia will infer and set types
- You can use emojis! \: + <tab> --> auto complete from there
- easy variable reassignment ala python
- literally can use emojis as numeric variables, and then do arithmetic with emojis lol
- comments with #, and #= =#
- ? is help operator, works in the REPL and in notebook

### Strings
- strings are " " or """ """ when you want to have quotes in the string
- ' ' is a char unlike python
- $ for inserting variables into a string
- string concat via string(s1,...,sn) or the * operator, which is interesting
- julia has a repeat operator, repeat(A, counts)

### Data Structures
- Tuples, Dictionaries, Arrays covered here
- Tuples and Arrays are ordered sequences of elements. Dictionaries and Arrays are mutable, tuples not!
#### Tuples
- Tuple creation via (item1, item2, ...)
- Tuples are not mutable!
- NamedTuples allow for dot notation for named elements, (bird="penguin"...)
#### Dictionaries
- Dict(key => value, key => value)
- mydict["key"] for indexing
- mydict["key"] = newvalue for assignment after init
- pop!(mydict, key) for deletion
- Dictionaries not ordered
- Dicts can have same or mixed types, if dict is mono type, then you can't add new types as the values after init
#### Arrays
- arrays are mutable, and ordered
- [v, v,...]
- can be mixed types within array
- push! pop! functions add/remove elements from end of array
- arrays can be n-dimenstional
- Array{Type, ndims)
- be cautious copying arrays, unless you explicitly call copy it's just another view of the original array!

### Loops
- for loops and while loops
- it's length(iter) not len() in Julia
- When iterating over multi dimensional loops, it's best to iterate in a column major way, that is, have for j in ... in the outer loop
- there is a fill function, ala np.zeros
- array comprehensions are a thing

### Conditionals
- if elseif else end
- && for and
- ternary operators ie: a ? b : c is like if a, then b, else c
- Julia does short circuit evaluation on && || checks!
- this means you can do things like have error as second part of && ||. ie (x > 0) && error("x cannot be greater than 0")

### Functions
- declare with function f(x) or inline like f(x) = println(x)
- there are even anonymous functions, like
    func1 = x -> x^2

####  Duck Typing
- this allows Julia functions to work on any input that makes sense, so you can have a function like f(x) => x^2 and it will work on ints, floats, and even matrices. But f(x) of a vector will not work because vec^2 is not defined

#### Mutating and Non-Mutating Functions
- By convention, functions followed by ! alter contents and functions without ! do not

#### Higher Order Functions
- map takes a functions and applies it to every element of a data structure, map(f, [1, 2, 3])
- can pass anonymous functions into map, map(x -> x^3, [1, 2, 3])
- broadcast is a generalization of map, and can use the func.(data) syntactic sugar

### Pkg
- actually has calls to Python and R via libraires
- using Pkg
  Pkg.add("Example")
- using is the equivalent of import
- Julia has excellent colors support via Colors pkg! 

### Plotting
#### Plots.jl
- can change backends seamlessly
  - backend include gr, unicodeplots, plotlyjs
- use plot(x, y, label)
- use scatter(...)
- remember you can use mutating functions! 
  so scatter!(x, y) updates the plot as data updates!
- xflip flips x an y values
- stack plot calls to create multiplot layout
 - p1 = plot(..)
 - p2 = plot(..)
 - plot(p1, p2, layout = (1, 2))

### Speed of Julia
- use @time macro to time basic stuff
- use BenchmarkTools.jl for more accurate results

### Multiple Dispatch
- remember above, we can let Julia infer and make the call on if a function works on a data type, additionally we can specify the input types with :: notation., This restricts the function to only be called on that data type matching the signature. However, this can also be advantageous because now we can be very explict, have functions with same number of arguments, but different types. and Julia picks the correct function to actually call
- A generic function called foo can have multiple methods. The generic functions is the abstract concept of a particular operation and a method is a specific implementation of that generic function for a particular argument type.
- we can call the Julia function methods to see how many methods there are for a generic function
- use the @which macro to see which method is being dispatched in a given call

### Basic Linear Algebra in Julia
- rand can define matrices like rand(possible values, dim1, dim2)
- most operations work how you would expect them to out of box in Julia
- Matrix A can get transpose via transpose(A)
- Conjugate transpose via A' (adjoint)
- Transpose multiplication via A'A
- There is the LinearAlgebra standard pkg as well
- 
### Factorizations
- LinearAlgebra package used
#### Factorizations, Eigen
- LU factorization vi lu
  - returns a composite type for storage that can be accessed via dot notation
  - can operate on the composite type just as you would the actual matrix
- Same with QR factorization
- Eigendecompositions
  - use eigen function
  - returns eigenvectors and eigenvalues
  - also a composite
#### Matrix Structures
- Julia has issymmetric functions to check matrix properties
- there are special functions to declare explicit structure in a matrix to avoid floating point errors - Diagonal, Triangular, Symmetric, Hermitian, Tridiagonal and SymTridiagonal.
#### Rational numbers
- Julia has rational numbers built in, use // to construct

----
 More to come!
