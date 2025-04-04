date: 2025-04-02  
time: 08:50  

- `try/catch` blocks are **ugly** in their own right.
    
- They **confuse** the structure of the code and **mix error processing with normal processing**.
    
- So it is better to **extract** the bodies of the `try` and `catch` blocks into functions of their own.
    

### **Example: Refactoring Try/Catch Blocks**

```java
public void delete(Page page) {
    try {
        deletePageAndAllReferences(page);
    } catch (Exception e) {
        logError(e);
    }
}

private void deletePageAndAllReferences(Page page) throws Exception {
    deletePage(page);
    registry.deleteReference(page.name);
    configKeys.deleteKey(page.name.makeKey());
}

private void logError(Exception e) {
    logger.log(e.getMessage());
}
```

### **Why is this better?**

- The `delete` function is **all about error processing**.
    
- The `deletePageAndAllReferences` function is **only about deleting a page**, without worrying about error handling.
    
- The `logError` function **isolates logging**, making it cleaner.
    

### **Benefits of this approach:**

✅ **Separation of concerns** → Normal logic and error handling are separate.  
✅ **Easier to read and modify** → The code is structured and understandable.  
✅ **More maintainable** → You can modify error handling without affecting the main process.
  

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*