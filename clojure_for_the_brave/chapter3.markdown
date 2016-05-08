# Chapter 3: Clojure crash course

* 2 kinds of structures
** literal representation of data structures
** operations
* operation: `(operator operand1 operand2.. operandn)`
* `if` is for single form branches
* use `do` to have multiple forms

```clojure
(if true
  (do (println "Success!")
      "Something else!")
  (do (println "Not true!")
      "Something here!"))
```

* `when` allows multiple forms, but with no `else` part
* `nil?` function checks if a value is "no value"
* `=` is a comparison operator
* `and` and `or` are boolean operators
** they return values; `or` returns first thruthy value or last false value
** `and` returns first falsey value or last thruthy value
* `def` is used to bind a name to a value

## Data structures
* all data structures are immutable
* no string interpolation - only `str` function that concatenates strings
* maps - `{}`
** values can be of any type
** `{:first-name "John" :last-name "Test"}`
** can also use `hash-map` function: `(hash-map :a 1 :b 2)`
** use `get` function to look up a value: `(get {:a 0 :b 1} :a)`
** `get-in` look up values in nested maps: `(get-in {:a 0 :b {:c "here"}} [:b
:c])`
** keyword lookup: `({:a 123 :b 456} :b)` -> `456`
* keywords - :keyword
** primarily used as keys in maps
** can be used as a function to look up values in a map: `(:a {:a 1 :b 2 :c
3})`
* vectors - `[]`
** 0-indexed collection
** use `get` to get by index: `(get [3 2 1] 0])` -> `3`
** add elements to the end of the vector: `(conj [1 2 3] 4)`
* lists - `'()'`
** similar to vectors
** can't retrieve by index; use `nth` function
** search complexity of a list is O(n), while vector is few hops (most likely
a tree under the hood)
** can create lists with a `list` function
** `conj` adds elements to the beginning of a list
* sets - `#{}`
** collections of unique values
** there are 2 kinds: hash sets and sorted sets
** `#{"test" 2 :something}`
** `#{}` notation will throw exception on duplicates; `hash-set` function will
remove duplicates
** `set` function creates a set from a vector or a list

## Functions
* function expression - an expression that returns a function: `(or + -)`
* higher order functions - functions that can take other functions as
  parameters or return a function
* Clojure evaluates all function parameters recursively before passing them to
  the function
* other kinds of expression: macro calls and special forms
* special forms - unlike functions they don't always evaluate all operands
** also, they can't be used as arguments to functions
* `defn` defining functions

```clojure
(defn function-name
  "Docstring goes here"
  [param1 param2]
  (println "This is function body"))
```

* view docs for a function: `(doc function-name)`
* arity-overloading - defining a function that does different things based on
  the number of arguments passed to it
** one way to implement default values
* `&` is used to capture all extra parameters (something like `*args` in
  Python)

```clojure
(defn test [& other_params]
  (map inc other_params))
```

* destructuring - bind names to values within a collection

```clojure
(defn return-first
  [[first-thing]]
  first-thing)
```

* destructuring a map:
```clojure
(defn some-function
  [{:keys [first second]}]
  (println (str first second)))
```
* this will extract keys first and second from a passed in map, and bind them
  to names `first` and `second`
* anonymouse functions - `fn` or compact way: `#()`
** eg. `(#(* % 3) 8)` - `%` is a placeholder for an argument
* functions returned from other functions are closures - they have access to
  the scope where they were defined
* `let`
** binds names to values and introduces a new (local) scope
** can reference global scope: `(let [x (inc x)] x)`
** `let` allows us to name things, and allows to evaluate expression only once
and reuse the result (important on expensive API calls or side-effects)
* `loop` a handy way to do recursion
```clojure
(loop [iteration 0]
  (println (str "Iteration " iteration))
  (if (> iteration 3)
    (println "Goodbye!")
    (recur (inc iteration))))
```
* parameters to `loop` are bindings (4 parameters in `[]` means 2 bindings)
* regular expressions: `#"regex"`

## Sample program
