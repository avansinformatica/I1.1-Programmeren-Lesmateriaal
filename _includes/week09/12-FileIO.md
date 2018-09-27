## 12. FileIO

### 12.1 Reading a File
A relevant part of programming is related to stored files, in one way or in another. Let's take the first steps in Java file handling. Java's API provides the class [File](http://docs.oracle.com/javase/8/docs/api/java/io/File.html), whose contents can be read using the already known [Scanner](http://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) class.

If we read the desciption of the `File` [API](http://docs.oracle.com/javase/8/docs/api/java/io/File.html) we notice the `File` class has the constructor `File(String pathname)`, which *creates a new File instance by converting the given pathname string into an abstract pathname*. This means the `File` class constructor can be given the pathname of the file we want to open.

*In the NetBeans programming environment, files have got their own tab called Files, which contains all our project files. If we add a file to a project root -- that is to say outside all folders -- we can refer to it by writing only the its name. We create a file object by fiving the file pathname to it as parameter:*

```java
    File file = new File("file-name.txt");
```

`System.in` input stream is not the only reading source we can give to the constructor of a `Scanner` class. For instance, the reading source can be a file, in addition to the user keyboard. `Scanner` provides the same methods to read a keyboard input and a file. In the following example, we open a file and we print all the text contained in the file using the `System.out.println` statement. At the end, we close the file using the statement `close`.

```java
        // The file we read
        File file = new File("filename.txt");

        Scanner reader = new Scanner(file);
        while (reader.hasNextLine()) {
            String line = reader.nextLine();
            System.out.println(line);
        }

        reader.close();
```

The `Scanner` class constructor [public Scanner(File source)](http://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html#Scanner(java.io.File)) (*Constructs a new Scanner that produces values scanned from the specified file.*) throws a [FileNotFoundException](http://docs.oracle.com/javase/8/docs/api/java/io/FileNotFoundException.html) when the specified file is not found. The `FileNotFoundException` is different than `RuntimeException,` and we have either to handle it or throw it forward. At this point, you only have to know that the programming environment tells you whether you have to handle the exception or not. Let's first create a try-catch block where we handle our file as soon as we open it.

```java
    public void readFile(File f) {
        // the file we read
        Scanner reader = null;

        try {
            reader = new Scanner(f);
        } catch (Exception e) {
            System.out.println("We couldn't read the file. Error: " + e.getMessage());
            return; // we exit the method
        }

        while (reader.hasNextLine()) {
            String line = reader.nextLine();
            System.out.println(line);
        }

        reader.close();
    }
```

Another option is to delegate the exception handling responsibility to the method caller. We delegate the exception handling responsibility by adding the definition `throws ExceptionType` to the method. For instance, we can add `throws Exception` because the type of all exceptions is `Exception`. When a method has the attribute `throws Exception`, whatever chunk of code which calls that method knows that it may throw an exception, and it should be prepared for it.

```java
    public void readFile(File f) throws Exception {
        // the file we read
        Scanner reader = new Scanner(f);

        while (reader.hasNextLine()) {
            String line = reader.nextLine();
            System.out.println(line);
        }

        reader.close();
    }
```

In the example, the method `readFile` receives a file as parameter, and prints all the file lines. At the end, the reader is closed, and the file is closed with it, too. The attribute `throws Exception` tells us that the method may throw an exception. Same kind of attributes can be added to all the methods that handle files.

Note that the `Scanner` object's method `nextLine` returns a string, but it does not return a new line at the end of it. If you want to read a file and still maintain the new lines, you can add a new line at the end of each line:

```java
    public String readFileString(File f) throws Exception {
        // the file we read
        Scanner reader = new Scanner(f);

        String string = "";

        while (reader.hasNextLine()) {
            String line = reader.nextLine();
            string += line;
            string += "\n";
        }

        reader.close();
        return string;
    }
```

Because we use the `Scanner` class to read files, we have all `Scanner` methods available for use. For instance the method `hasNext()` returns the boolean value true if the file contains something more to read, and the method `next()` reads the following word and returns a `String` object.

The following program creates a `Scanner` object which opens the file *file.txt*. Then, it prints every fifth word of the file.

```java
        File f = new File("file.txt");
        Scanner reader = new Scanner(f);

        int whichNumber = 0;
        while (reader.hasNext()) {
            whichNumber++;
            String word = reader.next();

            if (whichNumber % 5 == 0) {
                System.out.println(word);
            }
        }
```

Below, you find the text contained in the file, followed by the program output.

```output
Exception handling is the process of responding to the occurrence, during computation, of exceptions – anomalous or exceptional events 
 requiring special processing – often changing the normal flow of program execution. ...
```

```output
process
occurrence,
–
requiring
changing
program
```

#### 12.1.1 Character Set Issues

When we read a text file (or when we save something into a file), Java has to find out the character set used by the operating system. Knowledge of the character set is required both to save text on the computer harddisk in binary format, and to translate binary data into text.

There have been developed standard character sets, and "UTF-8" is the most common nowadays. UTF-8 character set contains both the alphabet letters of everyday use and more particular characters such as the Japanese kanji characters or the information need to read and save the chess pawns. From a simplified programming angle, we could think a character set both as a character-number hashmap and a number-character hashmap. The character-number hashmap shows what binary number is used to save each character into a file. The number-character hashmap shows how we can translate into characters the values we obtain reading a file.

Almost each operating system producer has also got their own standards. Some support and want to contribute to the use of open source standards, some do not. If you have got problems with the use of Scandinavian characters such as ä and ö (expecially Mac and Windows users), you can tell which character set you want to use when you create a `Scanner` object. In this course, we always use the the "UTF-8" character set.

You can create a Scanner object which to read a file which uses the UTF-8 character set in the following way:

```java
    File f = new File("examplefile.txt");
    Scanner reader = new Scanner(f, "UTF-8");
```

Anther thing you can do to set up a character set is using an environment variable. Macintosh and Windows users can set up an the value of the environment variable `JAVA_TOOL_OPTIONS` to the string `-Dfile.encoding=UTF8`. In such case, Java always uses UTF-8 characters as a default.

{% include week09/exercise/017.md %}
{% include week09/exercise/018.md %}
{% include week09/exercise/019.md %}
{: .exercises }


### 12.2 Writing a File

In section 12.1, we learnt that reading from a file happened with the help of the classes `Scanner` and `File`. The class [FileWriter](http://docs.oracle.com/javase/6/docs/api/java/io/FileWriter.html) provides the functionality to write to a file. The `FileWriter` constructor is given as parameter a `String` illustrating the file location.

```java
FileWriter writer = new FileWriter("file.txt");
writer.write("Hi file!\n"); // the line break has to be written, too!
writer.write("Adding text\n");
writer.write("And more");
writer.close(); // the call closes the file and makes sure the written text goes to the file
```

In the example we write the string "Hi file!" to the file "file.txt"; that is followed by a line break, and by more text. Note that when you use the `write` method, it does not produce line breaks, but they have to be added later manually.

Both the `FileWriter` constructor and the `write` method may throw an exception, which has to be either handled or the responsibility has to be delegated to the calling method. The method which is given as parameter the file name and the text to write into it can look like the following.

```java
public class FileHandler {

    public void writeToFile(String fileName, String text) throws Exception {
        FileWriter writer = new FileWriter(fileName);
        writer.write(text);
        writer.close();
    }
}
```

In the above `writeToFile` method, we first create a `FileWriter` object, which writes into the `fileName` file stored at the location specified as parameter. After this, we write into the file using the `write` method. The exception the constructor and write method can possibly throw has to be handled either with the help of a `try-catch` block or delegating the responsibility. In the method `writeToFile` the responsibility was delegated.

Let's create a `main` method where we call the `writeToFile` method of a `FileHandler` object. The exception does not have to be handled in the `main` method either, but the method can declare to throw possibly an exception throw the definition `throws Exception`.

```java    public static void main(String[] args) throws Exception {
        FileHandler handler = new FileHandler();
        handler.writeToFile("diary.txt", "Dear Diary, today was a nice day.");
    }
```

When we call the method above, we create the file "diary.txt", where we write the text "Dear Diary, today was a nice day.". If the file exists already, the old content is erased and the new one is written. `FileWriter` allows us to add text at the end of the already existing file by providing additional parameter `boolean append`, without erasing the existing text. Let's add the method `appendToFile()` to the class `FileHandler`; the method appends the text received as parameter to the end of the file.

```java
public class FileHandler {
    public void writeToFile(String fileName, String text) throws Exception {
        FileWriter writer = new FileWriter(fileName);
        writer.write(text);
        writer.close();
    }

    public void appendToFile(String fileName, String text) throws Exception {
        FileWriter writer = new FileWriter(fileName, true);
        writer.write(text);
        writer.close();
    }
}
```

In most of the cases, instead of writing text at the end of a file with the method `append`, it is easier to write all the file again.

### Exercise 34: File Manager

Together with the exercise body, you find the class `FileManager`, which contains the method bodies to read a write a file.

#### Exercise 34.1: File Reading

Implement the method `public ArrayList<String> read(String file)` to return the lines of the parameter file in `ArrayList` form, each file line being a `String` contained by the `ArrayList`.

There are two text files to help testing the project: *src/testinput1.txt* and *src/testinput2.txt*. The methods are supposed to be used in the following way:

```java
    public static void main(String[] args) throws FileNotFoundException, IOException {
        FileManager f = new FileManager();

        for (String line : f.read("src/testinput1.txt")) {
            System.out.println(line);
        }
    }
```

The print output should look like the following

```output
first
second
```

#### Exercise 34.2: Writing a Line

Modify the method `public void save(String file, String text)` so that it would write the string of the second argument into the file of the first argument. If the file already exists, the string is written over the old version.

#### Exercise 34.3: Writing a List

Modify the method `public void save(String file, ArrayList<String> texts)` so that it would write the strings of the second argument into the file of the first argument; each string of the array list has to go to its own line. If the file already exists, the strings are written over the old version.

### Exercise 35: Two-Direction Dictionary

With this exercise, we develop the dictionary we implemented earlier, so that words can be both read and written into the file. Also, the dictionary has to translate in both directions, from Finnish into English and from English into Finnish (in this exercise, we suppose unofficially that Finnish and English do not have words which are spellt the same). Your task is creating the dictionary in the class `MindfulDictionary`. The class has to be implemented in the package `dictionary`.

#### Exercise 35.1: Forgetful Basic Functionality

Create a parameterless constructor, as well as the methods:

* `public void add(String word, String translation)` adds a word to the dictionary. Each word has only one translation; if the same word is added twice, nothing happens.
* `public String translate(String word)` returns the word translation; if the word isn't recognised, it returns null

At this point, the dictionary has to work in the following way:

```java
MindfulDictionary dict = new MindfulDictionary();
dict.add("apina", "monkey");
dict.add("banaani", "banana");
dict.add("apina", "apfe");

System.out.println( dict.translate("apina") );
System.out.println( dict.translate("monkey") );
System.out.println( dict.translate("programming") );
System.out.println( dict.translate("banana") );
```

Prints:

```output
monkey
apina
null
banaani
```

As you notice from the example, after adding a pair the dictionary can translate in both directions.

#### Exercise 35.2: Removing Words

Add the method `public void remove(String word)`, which removes the given word and its translation from your dictionary.

At this point, the dictionary has to work in the following way:

```java
MindfulDictionary dict = new MindfulDictionary();
dict.add("apina", "monkey");
dict.add("banaani", "banana");
dict.add("ohjelmointi", "programming");
dict.remove("apina");
dict.remove("banana");

System.out.println( dict.translate("apina") );
System.out.println( dict.translate("monkey") );
System.out.println( dict.translate("banana") );
System.out.println( dict.translate("banaani") );
System.out.println( dict.translate("ohjelmointi") );
```

Prints:

```output
null
null
null
null
programming
``` 

As you see, the delection happens in both ways: whether you remove a word or its translation, the dictionary loses the both the pieces of information.

#### Exercise 35.3: Loading a File

Create the constructor `public MindfulDictionary(String file)` and the method `public boolean load()`, which loads a file whose name is given as parameter in the dictionary constructor. If opening or reading the file does not work, the method returns false and otherwise true.

Each line of the dictionary file contains a word and its translation, divided by the character ":". Together with the exercise body, you find a dictionary file meant to help the tests. It looks like the following:

```output
apina:monkey
alla oleva:below
olut:beer
```

Read the dictionary file line by line with the reader method `nextLine`. You can split the lines with the `String` method `split`, in the following way:

```java
Scanner fileReader = new ...
while ( fileReader.hasNextLine() ){
    String line = fileReader.nextLine();
    String[] parts = line.split(":");   // the line is split at :

    System.out.println( parts[0] );     // the part of the line before :
    System.out.println( parts[1] );     // the part of the line after :
}
```

The dictionary is used in the following way:

```java
MindfulDictionary dict = new MindfulDictionary("src/words.txt");
dict.load();

System.out.println( dict.translate("apina") );
System.out.println( dict.translate("ohjelmointi") );
System.out.println( dict.translate("alla oleva") );
```

Printing:

```output
monkey
null
below
```

#### Exercise 35.4: Saving Data

Create the method `public boolean save()`; when the method is called, the dictionary contents are written into the file whose name was given as parameter to the constructor. The method returns false if the file can't be saved; otherwise it returns true. Dictionary files have to be saved in the form described above, meaning that the program has to be able to read its own files.

**Attention:** even though the dictionary can translate in both directions, only one direction has to be stored into the dictionary file. For instance, if the dictionary knows that *tietokone = computer*, you have to write either the line:

```output
tietokone:computer
```

or the line

```output
computer:tietokone
```

but not both!

It may be useful to write the new translation list over the old file; in fact, the `append` command which came out in the material should not be used.
The final version of your dictionary should be used in the following way:

```java
MindfulDictionary dict = new MindfulDictionary("src/words.txt");
dict.load();

// using the dictionary

dict.save();
```

At the beginning we load the dictionary from our file, and we save it back in the end, so that the changes made to the dictionary will be available next time, too.