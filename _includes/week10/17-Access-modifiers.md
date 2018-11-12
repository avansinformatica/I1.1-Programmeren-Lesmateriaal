## 18. Access Modifiers

When extending a class, it is possible to use the public methods and attributes of the superclass. It is however, not possible to access the private methods and attributes. Sometimes it is needed to access those methods from a subclass, but not from other classes. We can use the `protected` keyword to access these methods and attributes

| Modifier    | Class | Package | Subclass | World |
|-------------|-------|---------|----------|-------|
| `public`    | Y     | Y       | Y        | Y     |
| `protected` | Y     | Y       | Y        | N     |
| no modifier | Y     | Y       | N        | N     |
| `private`   | Y     | N       | N        | N     |

As we can see, protected members are also accessable by other classes in the same package. 
