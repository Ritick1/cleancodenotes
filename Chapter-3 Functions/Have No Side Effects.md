date: 2025-04-02  
time: 08:28  

- Side effects are lies. Your function promises to do one thing, but it also does other _hidden_
  things.  
```java
public class UserValidator {
    private Cryptographer cryptographer;

    public boolean checkPassword(String userName, String password) {
        User user = UserGateway.findByName(userName);
        
        if (user != User.NULL) {
            String codedPhrase = user.getPhraseEncodedByPassword();
            String phrase = cryptographer.decrypt(codedPhrase, password);

            if ("Valid Password".equals(phrase)) {
                Session.initialize();
                return true;
            }
        }
        return false;
    }
}
```

-  The side effect is the call to `Session.initialize()`, of course.
- The `checkPassword` function, by its name, says that it **checks** the password.
- The name does not imply that it **initializes** the session.
-  In this case we might rename the function checkPasswordAndInitializeSession, though that certainly violates “Do one thing.”

Day 1 : done *2025-04-02*  
Day 3 : pending *2025-04-05*  
Day 7 : pending *2025-04-09*  
Day 21: pending *2025-04-23*