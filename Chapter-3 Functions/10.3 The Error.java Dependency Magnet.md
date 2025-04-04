date: 2025-04-02  
time: 08:54  

- **Returning error codes** usually implies that there is some **class or enum** in which all error codes are defined.
    

### **Example:**

```java
public enum Error {
    OK,
    INVALID,
    NO_SUCH,
    LOCKED,
    OUT_OF_RESOURCES,
    WAITING_FOR_EVENT;
}
```

- Classes like this become a **dependency magnet** → Many other classes must **import and use them**.
    
- **Problem:** When the `Error` enum **changes**, all dependent classes need to be **recompiled and redeployed**.
    

### **Negative Effects:**

- Programmers hesitate to **add new errors** because it requires **rebuilding and redeploying everything**.
    
- Instead of adding new error codes, they **reuse old ones**, leading to **poor error handling**.
    

### **Better Approach: Using Exceptions**

- When you use **exceptions** instead of error codes,
    
    - New exceptions are **derivatives** of the `Exception` class.
        
    - They can be **added without forcing recompilation or redeployment**.
  

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*