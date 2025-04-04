date: 2025-04-02  
time: 08:37  

- Functions should either do something or answer something, but not both.
    
- Either your function should change the state of an object, or it should return some information about that object.
    
- Doing both often leads to confusion.
    
- Consider, for example, the following function:
    
    ```java
    public boolean set(String attribute, String value);
    ```
    
- This function sets the value of a named attribute and returns `true` if it is successful and `false` if no such attribute exists.
    
- This leads to odd statements like this:
    
    ```java
    if (set("username", "unclebob"))...
    ```
  
- The Better way will be
	
```java
if (attributeExists("username")) {
	setAttribute("username", "unclebob");
	...
}
```

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*