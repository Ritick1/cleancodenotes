date: 2025-04-02  
time: 08:26  

- Choosing good names for a function can go a long way toward explaining the intent of the function and the order and intent of the arguments.
    
- In the case of a monad, the function and argument should form a very nice verb/noun pair.
    
- For example, `write(name)` is very evocative. Whatever this “name” thing is, it is being “written.”
    
- An even better name might be `writeField(name)`, which tells us that the “name” thing is a “field.”
    
- This last is an example of the **keyword form** of a function name.
    
- Using this form, we encode the names of the arguments into the function name.
    
- For example, `assertEquals` might be better written as `assertExpectedEqualsActual(expected, actual)`.
    
- This strongly mitigates the problem of having to remember the ordering of the arguments.

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*