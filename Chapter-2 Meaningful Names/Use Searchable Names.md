date: 2025-03-02
time: 16:28


**1. We should give the names of the variables which are easy to search.**
**2. We should avoid the numeric constant and given a suitable names to it.**

---

**3. Names should depend on the scope where we are using them.**

This means that the names of variables, functions, or classes should be meaningful within their respective scopes.

**Example:**

```java
class OrderProcessor {
    void process() {
        List<Order> orders = getPendingOrders();
        for (Order order : orders) {
            order.process();
        }
    }
}
```

🔹 Here, order is used inside the loop, which is a small scope, so a short but meaningful name is fine.

🔹 orders is used for the entire method, so it has a slightly broader and meaningful name.

🔹 getPendingOrders() is a function, and its name clearly describes what it does.

If order had a larger scope, a more descriptive name like pendingOrder would be better.

---

**4. The length of the name corresponds to the size of its scope.**

This means that **shorter names** can be used for small scopes (like loop variables), but **longer and more descriptive names** should be used for larger scopes to improve readability.

**Example:**

```java
class OrderProcessor {
    List<Order> pendingOrders; // Class-level variable (wider scope) has a long name
    
    void processOrders() {
        for (Order order : pendingOrders) { // Loop variable (small scope) has a short name
            order.process();
        }
    }
}
```

🔹 pendingOrders is a class-level variable, so it has a **longer and more descriptive** name.

🔹 order is a loop variable with a **smaller scope**, so a shorter name works well.

If we named pendingOrders as just o, it would be hard to understand. But using order in a small loop is fine because it’s easy to grasp in that limited scope.

---

**Key Takeaways:**

✔ Use **short** names for variables with **small scope** (like loop variables).

✔ Use **longer, descriptive** names for variables with **larger scope** (like class-level or method-level variables).

✔ A name should always be **searchable and meaningful** to make the code easy to understand.


Day 1 : done *2025-03-02*
Day 3: done *2025-03-05*
Day 7: done *2025-03-09*
Day 21: done *2025-03-23*