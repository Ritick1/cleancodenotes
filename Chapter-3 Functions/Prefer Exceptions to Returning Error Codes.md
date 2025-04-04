date: 2025-04-02  
time: 08:41  

  - Returning error codes from command functions is a subtle violation of **command-query separation**.
    
- It promotes commands being used as expressions in the predicates of `if` statements.
    
- Example:
    
    ```java
    if (deletePage(page) == E_OK)
    ```
    
- This does not suffer from **verb/adjective confusion**, but it leads to **deeply nested structures**.
    
- When you return an error code, the caller must handle the error **immediately**.
    

### **Example of Deeply Nested Error Handling:**

```java
if (deletePage(page) == E_OK) {
    if (registry.deleteReference(page.name) == E_OK) {
        if (configKeys.deleteKey(page.name.makeKey()) == E_OK) {
            logger.log("page deleted");
        } else {
            logger.log("configKey not deleted");
        }
    } else {
        logger.log("deleteReference from registry failed");
    }
} else {
    logger.log("delete failed");
    return E_ERROR;
}
```

- This structure makes the code **harder to read and maintain**.
    

### **Better Approach: Using Exceptions**

- If you use **exceptions** instead of returning error codes,
    
    - The **error-handling code** can be separated from the **happy path** code.
        
    - This simplifies the logic.
        

```java
try {
    deletePage(page);
    registry.deleteReference(page.name);
    configKeys.deleteKey(page.name.makeKey());
} catch (Exception e) {
    logger.log(e.getMessage());
}
```

- Now, the **main operations** are clearly separated from the **error-handling** logic.
    
- This makes the code **cleaner and easier to read**.

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*