# Code Smells

- **Bloaters:** Long Method, Large Class, Primitive Obsession, Long Parameter List, Data Clumps
  - **Data Clumps:** Different parts of the code contain identical groups of variables (e.g., parameters for connecting to a database). These clumps should be turned into their own class.
- **Object-Orientation Abusers:** Switch Statements, Temporary Field, Refused Bequest, Alternative Classes with Different Interfaces
  - **Temporary Field:** Objects that have fields that are only used in certain situations.
  - **Refused Bequest:** A subclass that doesn't use all of the properties and methods inherited from its parent class.
  - **Alternative Classes with Different Interfaces:** Two classes perform similar functions but have different method names.
- **Change Preventers:** Divergent Change, Shotgun Surgery, Parallel Inheritance Hierarchies
  - **Divergent Change:** When you have to change many unrelated methods when you make changes to a class.
  - **Shotgun Surgery:** When a single change is made to multiple classes simultaneously.
  - **Parallel Inheritance Hierarchies:** Every time you make a subclass of one class, you also have to make a subclass of another.
- **Dispensables:** Comments, Duplicate Code, Lazy Class, Data Class, Dead Code, Speculative Generality
- **Couplers:** Feature Envy, Inappropriate Intimacy, Message Chains, Middle Man
  - **Feature Envy:** A method seems more interested in a class other than the one it actually is in.
  - **Inappropriate Intimacy:** One class knows too much about the internals of another class.
  - **Message Chains:** A pattern like **`a.getB().getC().doSomething()`**, where a client is coupled to the structure of the navigation.
  - **Middle Man:** A class that seems to just delegate its work to other classes.
