# Developing Application with Objective Caml

Available online for free [here](http://caml.inria.fr/pub/docs/oreilly-book/pdf/index.html)


# Chapter 2: Functional Programming

## BASICS
* there are 3 different types of declarations
  * value declaration : let
  * exception declaration : exception
  * type declaration : type

* toplevel prints 3 things:
  * val fact : int -> int = <fun>
  * <name> : <type> = <value>

* string concatenation operator is ^
  * `"ASDASD" ^ "dddd"`

* type `int * string` is the type of pairs whose first element is an integer (of type `int`) and whose second is a character string (of type `string`)

* tuples
  * `let t = (12, "test")`
  * values of different types, cartesian product

* lists = [1;2;3];;
  * values of the same type
  * concatenating lists operator is @
  * `[1] @ [2;3];;`


## VALUE DECLARATIONS
* Global declaration:
  * `let year = 2003;`

* Local declaration:
  * `let year = 2003 in ...`

* function declaration is the same as value declaration:
  * `let func_name param1 param2 = param1 + param2;;`

* type constraints:
  * let add (x:int) (y:int) = x + y;;


## PATTERN MATCHING
* syntax:
    ```
    match <expr> with
    | <p1> -> <expr1>
    | <p2> -> <expr2>
    ```

* `<expr>` is matched sequentially


## TYPE DECLARATIONS
* two major families of types:
  * product types (records and tuples)
  * sum types (unions)
* type declarations are recursive by default
* syntax:
    `type <name> = <typedef>;;`
* they can be parametrized by type variables which begin with '
    `type 'a <name> = <typedef>;;`


## RECORDS
* record always corresponds to the declaration of a new type
    ```
    type <name> = {
        <name1> : t1;
        <name2> : t2
    };;
    ```

* creating a record:
    `lec c = {re=2.; im=3.}`

* there are 2 ways to get a field in a record: dot notation and pattern matching


## SUM TYPES
* corresponds to a union of sets
* declaration:
    ```
    type <name> = 
        | Name1 ....
        | Name2 of type2 ...
        | Name3 of type3 * type4
    ```

* constant constructor - constructor which doesn't take an argument

* = is structural equality (compares values)
* == is physical equality (compares memory addresses)
