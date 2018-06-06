# General stuff

- Tests annoteren met @Test
- Klassen annoteren met @Points("2-10")
- @Points is een space-seperated lijst met te behalen punten voor deze opgaven... "week1 1" is dus punt "week1" en punt "1"
- @Rule wordt uitgevoerd voordat tests uitgevoerd worden


# Tests

## Running main method and catching std output

```java
import org.junit.Test;
import org.junit.Rule;

import static org.junit.Assert.*;
import fi.helsinki.cs.tmc.edutestutils.Points;
import fi.helsinki.cs.tmc.edutestutils.MockStdio;

@Points("1")
public class NameTest {
    @Rule
    public MockStdio io = new MockStdio();

    @Test
    public void test() {
        Name.main(new String[0]);
        String out = io.getSysOut();
        assertTrue("You did not print anything!",out.length()>0);
    }
}
```

## Running method with std input

```java
    ReflectionUtils.newInstanceOfClass(PositiveValue.class);
    io.setSysIn("100\n200\n");
    PositiveValue.main(new String[0]);

    String out = io.getSysOut();
```

## Assertions

```java
    assertTrue("Message", condition);
    assertFalse("Message", condition);
    assertEquals(object1, object2, condition);
    assertNotEquals(object1, object2, condition);
    //....
```

