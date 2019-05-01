Swift Syntax Review
--------------------------

1. Comments

        Two types of comments i.e one line(//)
        // Say something
        
        and multiline comment(/* blah blah */)
        /* Say something
        about anything
        */

2. Declaration and Initialization

        In Swift, declaration must occur first before initialiation, you can't initialize a variable/constant that was not declared.
```   
        let answer: Int //DECLARE!
        answer = 100    //THEN INITIALIZE! (called Full Syntax)
```

        Or do it in one line, by using type inference (called Short-hand Syntax)
```
        let answer = 100 //INFERED TYPE IS INT
```                
3. Data Types 

        Swift is Strongly-Typed!...which means Swift's compiler works with types, knowing the type is the objects it is working with is very crucial, you need to give the types always.
        
        Swift's toNote with regards to Data Types: 
        NB: Swift defaults to using Double when given floating-point number. Why?
            I assume it is because a Double is 8 bytes(64 bits) wide while a float is 4 bytes(32 bits) wide. The Double has more precision hence has less rounding errors.
```
            let myFloat: Float = 3.14159
            let myDouble = 3.14159 // myDouble's type is inferred to be Double
```
      NB: Colections types must be explicit about the type of their contents. Can a collection have a type? No, only the collection's contents can have a type...collections contain objects, they are containers! A collection is an object that holds references to other objects. Swift as a strongly-typed language is more concerned about the contents in the collection. 
        So...is a collection a type...can it be in itself a String, not looking at the contents. No, it is only a container, look at type thoery for further investigation.
        
        NB: Dictionaries and Arrays can be written using the shorthand syntax, meaning we can rely on the compiler to infer the type, by writhing short code. 
            BUT!
        NB: Sets MUST! be declared using full syntax. No fancy compiler type inference thinger magicer is tolerable with sets.  
```      
            let mySet: Set<Bool> = [true, false]
            // or...
            let setOfInts = Set<Int>()
```
