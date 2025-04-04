
---
Naming is one of two hard things in programming other then cache-invalidation.

To give a good name in programming requires a understanding of the thing. If name is not coming naturally it might indicating that understanding of the thing is not complete yet.

### Things to take care of before giving names:

**Use Intention-Revealing Names**

```java

int d; // elapsed time in days
int elapsedTimeInDays; // use this one instead of above

```

---
**Avoid Disinformation:**

> For example, hp, aix, and soc would be poor variable names because they are the names of Unix platforms or variants. Even if you are coding a hypotenuse and hp looks like a good abbreviation, it could be dis-informative.

Apart from keywords of a programming language which we can't take as variable names, there are identifiers which has special meaning in context of the framework we are using.

Let's take an example of Jackson, if we are serializing a Java object with it and object contains `getName()` method event thought we don't have name variable in the object, still we will get a name key in json value.

```java
public class DataObj {
    private String greet;

    public String getName() {
        return greet;
    }

}

public class Test {
    public static void main(String[] args) {
        DataObj dataObj = new DataObj("Hello Manish");
        String jsonString = ObjectMapperUtils.toJsonString(dataObj);
        System.out.println(jsonString);
    }
}

// Output Was::
// {"greet":"Hello Manish","name":"Hello Manish"}

```

Hibernate meta-model-gen produces wrong `.class` file in case we use `set+Varialbe` and  variable doesn't exits in the `Entity` class. Below code will give issue because `set` has special meaning the context of meta-model-gen tool, it uses those `set` prefixed method to enhance code.

```java

@Entity
class Student {
	Long id;

	// model-gen will look for a member "name" in student entity
	// and there is no name member named "name" in student
	// entity so it gonna cause issue.
	void setName(String name) {
		// doing somthing here
	}
}

```

Do not refer to a grouping of accounts as an `accountList` unless it’s actually a List. Because `list` has special meaning in programming language like it can contains duplicate values, so adding `List` at the end of `account` can cause dis-information.

---
**Make meaningful distinction**

Beware of using names which vary in small ways. How long does it take to spot the subtle difference between a `XYZControllerForEfficientHandlingOfStrings` in one module and, somewhere a little more distant, `XYZControllerForEfficientStorageOfStrings`? The words have frightfully similar shapes.

Number-series naming (`a1`, `a2`, .. `aN`) is the opposite of intentional naming. Such
names are not dis-informative—they are non-informative; they provide no clue to the author’s intention. When calling a `Set<Student>` as `studentList` it is a dis-information, `studentList` gives reader a false perception that it is a list but calling `Set<Student>` as `a1` is non-informative because variable name is not revealing anything about the variable.

```java

// Non-Informative a1 & a2, Wrong way, Don't do it.
public static void copyChars(char a1[], char a2[]) {
	for (int i = 0; i < a1.length; i++) {
		a2[i] = a1[i];
	}
}

// infromative variables source & destination, Right Way.
public static void copyChars(char source[], char destination[]) {
	for (int i = 0; i < source.length; i++) {
		destination[i] = source[i];
	}
}

```

If you have another called `ProductInfo` or `ProductData`, you have made the names different without making them mean anything different. Info and Data is literally has same meaning, so how another programmer(or me in case code was written few weeks ago) will choose which class to use from `ProductInfo` and `ProductData` when he requires it.

Noise words are redundant. The word `variable` should never appear in a variable
name.

```java

// Example noise words.
public static void main(String[] args) {
	String variable = "Java"; // variable should not appear here
	String nameString = "Manish"; // String in varible name is noise.
	Student studentObject = new Student(); // Object is noise.
}

```


---

**Use Pronounceable Names**

Pronounceable name enhance communication, for effective exchange of idea in any discussion it requires good  Pronounceable names.

```java

// Wrong Way
class DtaRcrd102 {
	// gen-> generation y-> year, m-> month, d -> day, h -> hour
	// m -> minute, s -> second
	private Date genymdhms;

	// gen-> modification y-> year, m-> month, d -> day, h -> hour
	// m -> minute, s -> second
	private Date modymdhms;
	private final String pszqint = "102";
}

// Righ Way
class Customer {
	private Date generationTimestamp;
	private Date modificationTimestamp;;
	private final String recordId = "102";
}

```

---


**Use Searchable Names**

**Avoid Encoding**
Do not including unnecessary prefixes, suffixes, or Hungarian notation in names.
```java

// prefix-postix with type-encoding (Hungarian notation)
String stringName; // prefix of str is un-necesaary
List<Courses> coursesList; // postfix List is just adding noice

// ----
StudentEntity student; // It can be student only.

// Avoid Scope Encoding
String pr_name; // name is private
String pu_name; // name is public

// Avoid Abbreviations & Cryptic Encoding
String subCd; // it should be subjectCode
ClassTimeTable clsTmTbl; // it should be classTimeTable.

```

**Avoid metal mapping**

**Class Names**

> Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser. Avoid words like Manager, Processor, Data, or Info in the name of a class. A class name should not be a verb.


**Method Names**

> Methods should have verb or verb phrase names like postPayment, deletePage, or save. Accessors, mutators, and predicates should be named for their value and preﬁxed with get, set, and is according to the javabean standard.

Pick one word for one abstract concept and stick with it. For instance, it’s confusing to have fetch, retrieve, and get as equivalent methods of different classes.;

---


**Don't [[Pun]]

`Tune mere jaana kabhi nahi jaana, ishq mera dard mera` -song

Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

Example 1: Using "Add" for Two Different Purposes

```java
public classm ShoppingCart {
    private List<Item> items = new ArrayList<>();

    public void add(Item item) {
        items.add(item);
    }

    public void add(int quantity) {
        System.out.println("Adding " + quantity + " items to the inventory.");
    }

}
```

Here, the method `add` is overloaded to handle two unrelated tasks:

1. Adding an `Item` to the shopping cart.
2. Logging an inventory action.

#### Why It's Confusing:

- The method name `add` is overloaded, but the two methods have entirely different purposes.
- A developer reading the code might struggle to understand the intended meaning of `add` in a specific context.

Solution:
```java

public class ShoppingCart {
    private List<Item> items = new ArrayList<>();

    public void addItemToCart(Item item) {
        items.add(item);
    }

    public void logInventoryAddition(int quantity) {
        System.out.println("Adding " + quantity + " items to the inventory.");
    }
}

```

Example 2:

```java

// Wrong
public class AccountManager {
    public void withdraw(int amount) {
        // Deduct money from account
    }

    public void withdraw(String application) {
        // Withdraw an application for account creation
    }
}

// Right
public class AccountManager {
    public void withdrawFunds(int amount) {
        // Deduct money from account
    }

    public void cancelApplication(String application) {
        // Withdraw an application for account creation
    }
}

```


---

**Use Solution Domain Names**
use computer science terms, algorithm names or pattern names etc.
Like: `AccountVisitor` -> Visitor Pattern, `JobQueue` etc.

**Use Problem Domain Names**
Names that can verified/revealed by domain experts.

1. **E-commerce System**
    - ❌ `ItemContainer`
    - ✅ `ShoppingCart` (more meaningful in the e-commerce domain)
2. **Banking Application**
    - ❌ `TransactionLogger`
    - ✅ `AuditTrail` (common term in finance and security)
3. **Healthcare System**
    - ❌ `AppointmentManager`
    - ✅ `PatientScheduler` (more specific to the domain of patient care)
    - ❌ `DataProcessor`
    - ✅ `MedicalRecordParser` (clearly defines its purpose in handling medical records)

**Add Meaningful Context**
It is conflicting with "Don't Add Prefix Postfix"  but there are cases where it can be useful like below:

```java

Address companyAddress;
Address homeAddress;

```
