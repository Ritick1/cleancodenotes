date: 2025-03-04
time: 08:54

- We should not need the member prefixes anymore because classes are small enough thats why they do not need them
- And in today era the IDE'S become advanced that they highlight the variables and methods.
- People quickly learn to ignore the member prefixes to see the meaning of the names.
- For e.g 
```java
public class Part {
	private String m_dsc; // The textual description
	void setName(String name) {
	m_dsc = name;
	}
}
_________________________________________________

public class Part {
	String description;
	void setDescription(String description) {
	this.description = description;
	}
} 
```

Day 1 : done *2025-03-04*
Day 3: done *2025-03-07*
Day 7: done *2025-03-11*
Day 21: done *2025-03-25*