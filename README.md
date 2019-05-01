Swift Syntax Review
--------------------------

1. Comments

        Swift has two types of comments, namely, One line
        
            // Say something
        
        and multiline comment(/* blah blah */)
            /* Say something
            about anything
            */

2. Declaration and Initialization

        In Swift, declaration must occur first before initialiation, you can't initialize a variable/constant that was not declared.
 
            let answer: Int //DECLARE!
            answer = 100    //THEN INITIALIZE! (called Full Syntax)


        Or do it in one line, by using type inference (called Short-hand Syntax)

            let answer = 100 //INFERED TYPE IS INT
               
3. Data Types 

        Swift is Strongly-Typed!...which means Swift's compiler works with types, knowing the type is the objects it is working with is very crucial, you need to give the types always.
        
        Swift's toNote with regards to Data Types: 
        NB: Swift defaults to using Double when given floating-point number. Why?
            I assume it is because a Double is 8 bytes(64 bits) wide while a float is 4 bytes(32 bits) wide. The Double has more precision hence has less rounding errors.

            let myFloat: Float = 3.14159
            let myDouble = 3.14159 // myDouble's type is inferred to be Double

        NB: Colections types must be explicit about the type of their contents. Can a collection have a type? No, only the collection's contents can have a type...collections contain objects, they are containers! A collection is an object that holds references to other objects. Swift as a strongly-typed language is more concerned about the contents in the collection. 
        So...is a collection a type...can it be in itself a String, not looking at the contents. No, it is only a container, look at type thoery for further investigation.
        
        NB: Dictionaries and Arrays can be written using the shorthand syntax, meaning we can rely on the compiler to infer the type, by writhing short code. 
            BUT!
        NB: Sets MUST! be declared using full syntax. No fancy compiler type inference thinger magicer is tolerable with sets.  
            
            let mySet = Set<Bool>()
            // or...
            let mySet: Set<Bool> = [true, false]
            
            NB: All Data Types must NOT be NIL(empty- no even zero), this is how Optionals come in. Swift's Strongly-typed and Statically-typed nature can't deal with a nil value, what type is nil? Nil poses a serious problem to the Swift Compiler. Nil values and Swift's Compiler are enermies!
            
               Objective-C's objects are dynamically-typed and provides runtime libraries to Swift, but this does't make Swift in anyway a dynamically typed language. 
            
4. Optionals 

        NB: The optional property is created by adding the ? to a Swift Type. Swift Type plus ? equals Optional Property.
        
        NB: Optionals must be unwrapped before they can be used.
        
        
        Unwrapping optionals can be done in a couple of ways, and they differ a lot, some are not safe.
        
        NB: Optional binding is the safest way. It is safer than force unwrapping and implicit unwrapping. How is it used?
            For if-let/if-var, the else clause if NOT a MUST!
            Use optional binding to find out whether an optional contains a value, and if so, make that value available as a temporal constant ot variable. 
            
            if let myConstantName = someOptional {
                //statements using 'myConstantName' 
            } else {
                // the value of someOptional is not set (or nil).
            }
            
            Lets unpack this, let myConstantName = someOptional. We are assigning someOptional value to myConstantName. Wait a minute, what type is myConstantName?
            myConstantName;s type is unknown yet, it will be infered once we know that someOptional has the value. someOptional is allowed to either have or not have a value, so in this one line we crack open the optional box called someOptional to see what value is inside.
            
            Writting if-let/if-var is a direct order to the compiler that we need open the box and take what is inside, use it only if it exists.  
            
            Swift's convention is to reuse the property name
            
            if let myOptional = myOptional {
                print(myOptional)
            }
            
            Error message would be (fatal error): unexpectedly found nil while unwrapping an Optional value 
            
            if for some reason you want to change the myConstantName's value inside the closure. then use if var for unwrapping the optional.
            
        NB: Forced uwrapping is to be used only when we know for sure the value will never ever be nil.
            Xcode likes to suggests to add !
            
            let myOptionalIntAsDouble = Double(myOptionalInt!)

            Make the compiler understand what you mean, you can not tell the compiler to cast the nil value(nothing value) to a double(something value), the compiler is no magician. 

        NB: Implicit unwrapping can be used only if we are sure a value will exist runtime. 
        
            var definetelyExists: String! = "Bulana"
            definetelyExists = nil
            let shoutyString = definetelyExists.uppercased()
            
        NB: Guard statement checks for some condition and if it evaluates to be false, then the else statement executes which normally will exit a method.
            Guard is not optional binding. Guard MUST always have an else clause!!!
            
            guard let/var myResult = data["results"] else { return }
            
            The else case of the guard MUST Exit/End Current Scope!!, this means it MUST call return or abort the program. early exit means faster execution.  
            
            Guard when used well, can out perform if-let/if-var with regards to execution speed.
                
            "In general, if the if-let block was going to be the rest of the function, or its else clause would have a return or abort in it, then you should be using guard instead. This often means (at least in my experience), when in doubt, guard is usually the better answer. But there are plenty of situations where if let still is appropriate" by Rob Napier


        all in all, gaurd and if key-words stand on the same ground. They are both used for validating data, but guard is more specifc and strict. Guard must have the else clause, should to almost a must return(exit out of the code block using control transfer statement return-break-continue-thrown) thus you get early exit and fewer brackets.
        
        Choose Gaurd for password validation and related stuff, for example
        
            func validatePassword(password:String) ->   Bool    {
                
                guard password.characters.count > 6 else {
                    print(“Password should contain atleast 3 characters”)
                    return false
                }
                
                guard password.characters.count > 13 else {
                    print(“Password should contain more than 13 characters”)
                    return false
                }
                    
                guard checkPasswordCharacterSet(password) else {
                    print(“Password should contain one capital letter , one small letter, one special character”)
                    return false
                }
                    return true
                }
