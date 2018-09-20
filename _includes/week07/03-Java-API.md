## 3. Java API

The Java programming language we use in our course is made of three things. The first is the program syntax and semantics: the way we define variables, the control flow, the variable and class structure, and their functionality. The second is JVM, i.e. Java Virtual Machine, used for running our programs. Our Java programs are translated into a bytecode, which can be run on whatever computer has JVM. We haven't dealt with program translation because the program environment does it on our behalf. Sometimes, if the program environtment does not work as expected we may have to choose clean & build, which deletes the old source code and translates our program again. The third is API (Application Programming Interface), that is to say the program interface or standard library.

API is a set of built-in classes specific of the programming language, which is provided to users for their own projects. For instance the casses `ArrayList`, `Arrays`, `Collections`, and `String` are all part of Java's build-in API. A description of the API of Java 8 can be found at the address [http://docs.oracle.com/javase/8/docs/api/](http://docs.oracle.com/javase/8/docs/api/). On the left side of the page we find a description of Java's built-in classes. If you look for the `ArrayList` class, you find a link to [http://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html](http://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html), which shows the stucture, constructors, and methods of the class.


{% include week07/exercise/004.md %}
{: .exercises }
