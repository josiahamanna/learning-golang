## Introduction:

1. Conceived - sep 2007, Announced - nov 2009
2. The goals of the language and its accompanying tools were to be expressive, efficient in both compilation and execution, and effective in writing reliable and robust programs.
3. Go bears similarity to C (C for the 21st century)
4. It has automatic memory management or garbage collection
5. Go is especially well suited for building infrastructure like networked servers, and tools and systems for programmers, but it is truly a general-purpose language and ﬁnds use in domains as diverse as graphics, mobile applications, and machine learning.

## The Go Project:
1. Suffering from explosion of complexity: "Complexity is multiplicative" - fixing a problem by making one part of the system more complex slowly but surely adds complexity to other parts
2. It has garbage collection, a package system, ﬁr class functions, lexical scope, a system call interface, and immutable strings in which text is generally encoded in UTF-8. 
3. It has no implicit numeric conversions, no constructors or destructors, no operator overloading, no default parameter values, no inheritance, no generics, no exceptions, no macros, no function annotations, and no thread-local storage.
4. Go has concurrency features  based on CSP (communicating sequential process). [The variab size stacks of Go’s lightweight threads or goroutines are initially small enough that creating one goroutine is cheap and creating a million is practical]

## Tutorial
**Guide to write go code**

### 1.1 Hello, World
1. Go is a compiled language.
	* To execute a short experimental Go code run $ go run filename.go
	* If the program is more than a one-shot experiment, compile the code once and save the compiled result for later use. $ go build filename.go
1. Go code is organized into packages, which are similar to libraries or modules in other languages. A package consists of one or more .go source files in a single directory that define what the package does.
1. Package main is the standalone executable program, not a library. Function main will be within package main. It's where the execution begins, whatever this function does is what the program does.
1. After package declaration import declaration is written. This tells the compiler what packages are needed by the source file. You must import exactly the packages you need. (or else program wont compile. same goes if there are missing imports)
1. Go takes a strong stance on code formating. (The gofmt tool rewrites code into the standard format)

### Command-Line Arguments
1. Command-Line arguments are available to a program in a variable named Args that is part of the os package. This is a *slice* of strings.

1. Refer echo1.go
	* Comments begins with //
	* If a variable is not explicitely initialised, it is implicitely initialised to the *zero* value for its type.
	* Addition operator (+) for strings concatenates the values.
	* The **:=** symbol is part of a *short variable declaration*, a statement that declares one or more variables and gives them appropriate types based on the initializer values.
	* While writing for loop these parts may be omitted
		* A traditional while loop
		```
		for condition {
		   // ...
		}
		```
		* A traditional infinite loop
		```
		for {
		   // ...
		}
		```

1. Refer echo2.go
	* range produces a pair of values: the index and the value of the element at that index.
	* If we don't need to use the index we can use *blank identifier* i.e., underscore (\_)
	* Go does not allow unused variables, it would result in compilation error.

1. Two ways of declaring variable (strings)
	* s := "" // Only used within a function, not for package level variables
	* var s string // Default initilization to the zero value for strings, that is ""


### 1.3 Finding Duplicate lines
1. Programs for ﬁle copying, printing, searching, sorting, counting, and the like all have a similar structure: a loop over the input, some computation on each element, and generation of output on the ﬂy or at the end.

1. Refer dup1.go
	* Map holds a set of key/value pairs
	* Built in function creates a new empty map (in this example)
	* The first time a new line is seen, the expression counts[line] on the right-hand side evaluvates to the zero value for its type, which is 0 for int.
	* The order of map iteration in practice is random, varying from one run to another
	* bufio.NewScanner reads input and breaks it into lines or words. (naturally it comes in lines)
	* Each call to input.Scan() reads the next line and removes the newline character from the end; the result can be retrieved by calling input.Text()
	* The scan function returns true if there is a line and false when there is no more input.
