Clojure comes from an old family of languages called LISPs.  
LISP stands for 'List Processing'.  
Programming in LISP is very different from other languages but it allows you to do things that are not possible in other languages.  

Programming in Java requires that you:  
1. Write program  
2. Compile program  
3. Run program  

In Clojure we can use that style of programming, but we also can use a REPL.  
REPL stands for 'Read Eval Print Loop', this allows us to run code instantly and change a program that's currently running.  

Let's start with how to print 'Hello World' to the screen.  
In Java we'd write:  
 `System.out.println("Hello World");`  
In Clojure we write something similar:  
`(println "Hello World")`  

Notice, in Clojure we don't have to add any semicolons.  
We can also run the code instantly in an editor.  

What about more complex operations?  
One of the most important things we need to be able to do is add and subtract numbers.  
In Java we'd write the following:  
`int x = 1 + 2`;  

In Clojure we write:  
`(+ 1 2)`  

Notice, Clojure is a 'prefix' language, this is different than how we write math in English.  
We have to put the action in front of the variables.  
Notice, we didn't have to say 'int', Clojure automatically determines the type of variables you are using.  

Let's look at a more complex expression:  
In Java:  
`int x = 1 + 2 + 4 + 3;`

In Clojure:  
`(+ 3 (+ 4 (+ 1 2)))`

This starts at the inside, and then will work its way out adding the items together.  
Sometimes we need storage like arrays to put items together.  
In Java:  
```
String[] strings = new String[2];
strings[0] = "Hello";  
strings[1] = "World";
```

In Clojure:  
`'("Hello" "World")`  
or  
`["Hello" "World"]`  

We can add things to a list by using `conj`.  

`(conj [1 2 3] 4)`  -> [1 2 3 4]  
`(conj [5 6 7] "🚀")`  -> [5 6 7 "🚀"]

We can also do the following with lists:  
`(first [1 2 3])` -> returns the first item in the item list.  
`(last [1 2 3])` -> returns the last item in the item list.  
`(rest [1 2 3])` -> returns everything except the first item in the list.  
`(empty? [])` -> returns true if there is nothing in the given list.  

In Clojure we also use more advanced structures like Maps:  
In Java:
```
Map<String, String> fruits = new HashMap<>();
animals.put("apple", "🍎");  
animals.put("grape", "🍇");
animals.put("orange", "🍊");
```

In Clojure:  
```
{:apple "🍎" :grape "🍇" :orange "🍊"}

(:orange
  {:apple "🍎" :grape "🍇" :orange "🍊"})
```

In Clojure we have the ability to work with containers in ways that other languages can't.  
There are 3 big functions we can use which are not present in most other languages.  
1. Filter
2. Map
3. Reduce

Filter is the easiest to understand, it lets to keep or remove multiple items from a list.  
Let's say we want to have a list of only even numbers:  
`(even? 3)` -> false  
`(even? 2)` -> true  

`(filter even? [1 2 3 4 5 6])` -> [2 4 6]  

Map let's you do an action to each item in a list.  
Let's say we want to add a party popper emoji at the end of some strings.  
In Java:  
```
String[] strings = new String[2];
strings[0] = "Happy";
strings[1] = "Birthday!";

for(String s : strings){
  s += " 🎉";
}
```

In Clojure:  
`(map #(str % " 🎉") ["Happy" "Birthday!"])`

When we break this apart it looks like this:  
```
(str "Happy" " 🎉")
(str "Birthday" " 🎉")
```

And then it automatically, takes those two items and puts them back in a list.  
Reduce allows you to combine items in a list.  
Let's say we want to add up a bunch of numbers in a list:  
In Java:
```
int[] numbers = new int[3];
numbers[0] = 5;
numbers[1] = 10;
numbers[2] = 15;

int total = 0;
for(int i : numbers){
  total += i;
}
```

In Clojure:  
`(reduce + [5 10 15])`

Clojure turns this into:
```
(+ 15
  (+ 10)
    (+ 5))
```


So far, we haven't used any variables, but sometimes you need to store values.  
In Java:
```
int x = 3;
int y = x + 2;
```

In Clojure:  
```
(let [x 3
      y (+ x 2)])
```

When we're writing code, we need to create functions that return values.  
In Java:
```
private int addNumbers(int x, int y){
  int total = x + y;
  return total;
}

int example = addNumbers(2 3);
```

In Clojure:
```
(defn add-numbers[x y]
  (+ x y))

(add-numbers 2 3)
(add-numbers 2 3.14159)
```

Notice, we didn't specify the types, so we can use any numbers.  
We didn't specify return, the last item is always the one returned.  

Sometimes writing nested functions gets complicated.    
In Clojure we have helper functions called 'threading operators' to clean this type of operation up.  

The 'thread first' version takes each operation, performs it and then passes it as the first argument to the next step.  

Example:  
`(+ (+ 1 2) 3 )`

Becomes:  
`(-> 1
  (+ 2)
  (+ 3))`

The 'thread second' version takes each operation, performs it and then passes it as the second argument to the next step.  

Example:  
`(+ 3 (+ 2 1))`

Becomes:  
`(->> 1
  (+ 2)
  (+ 3))`

;;Do if statements here

In LISPs we don't have the ability to use a 'for loop' when iterating.  
We have to use recursive function calls instead.  
If we want to loop from 1 to 10 and print out each value, we do the following:  
```
(defn printer[numbers]
(if (empty? numbers)
  nil
  (do
    (println (first numbers))
    (printer (rest numbers))
    )))

(printer [1 2 3])
```
