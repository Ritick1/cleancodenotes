date: 2025-04-02  
time: 08:59  

- Looking back at **Listing 3-1**, there is an algorithm that gets **repeated four times**:
    
    - **SetUp**
        
    - **SuiteSetUp**
        
    - **TearDown**
        
    - **SuiteTearDown**
        
- This duplication is **not easy to spot** because:
    
    - The four instances are **intermixed with other code**.
        
    - They aren’t **uniformly duplicated**.
        

### **Problems with Duplication:**

- **Bloats the code** → Makes it harder to read and maintain.
    
- **Requires four-fold modification** if the algorithm needs to change.
    
- **Increases the chance of errors** (e.g., missing one instance when making updates).
    

### **Solution: Using the `include` Method**

- This duplication was **remedied** in **Listing 3-7** using the `include` method.
    
- **Result:**
    
    - The **readability** of the whole module is **enhanced**.
        
    - The **duplication is eliminated**, making the code **cleaner and more maintainable**.
        

### **Duplication: The Root of All Evil?**

- Many principles and practices in software development exist **to control or eliminate duplication**:
    
    - **Codd’s database normal forms** → Eliminate duplication in **data**.
        
    - **Object-Oriented Programming (OOP)** → Concentrates reusable code into **base classes**.
        
    - **Structured Programming** → Organizes code to reduce redundancy.
        
    - **Aspect-Oriented Programming (AOP)** → Helps remove cross-cutting concerns.
        
    - **Component-Oriented Programming (COP)** → Encourages code reuse and modularity.
        
- Since the **invention of the subroutine**, software development has been an **ongoing attempt to eliminate duplication** in source code.
  

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*