date: 2025-03-09
time: 22:02

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


Day 1 : done *2025-03-09*
Day 3: done *2025-03-12*
Day 7: done *2025-03-16*
Day 21: done *2025-03-21*