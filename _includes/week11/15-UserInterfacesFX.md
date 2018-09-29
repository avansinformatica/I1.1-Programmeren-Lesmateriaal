## 15. Graphical User Unterfaces

Let's look at creating Graphical User Interfaces (GUI). Graphical user interfaces differ from the previously used text user interfaces in several ways. When creating graphical user interfaces, we primarily use libraries that provide ready-to-use grapical components such as text boxes and buttons.

User inputs handling also differs from text user input. In which textual interfaces the functionality is coupled to a particular form of input, in graphical user interfaces that functionality needs to be added to handle the user interface input. For example, a programmer adds a method to a button related to pressing a button in the user interface.

We are using the Java [JavaFX](https://en.wikipedia.org/wiki/JavaFX) User Interface [Library](https://docs.oracle.com/javase/8/javafx/get-started-tutorial/jfx-overview.htm) to create graphical user interfaces.

### Graphical user interfaces and required libraries
>The JavaFx library is used to create graphical user interfaces. With Linux machines - depending on Java installation - install the openjfx library as well. To install this in Ubuntu (command line) command:
>
>```output
>  sudo apt-get install openjfx
>```
>
>You can find some test code on [JavaFx](https://github.com/TestFX/TestFX/wiki) to verify if your installation is working correctly.
{: .tip}

A simple window can be created with JavaFX using the following program.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        stage.setTitle("Hello world!");
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

When the program starts, the application looks like this.

![First GUI](images/15_first_gui.png)

>#### Create your own JavaFX applications
>To create your own JavaFx projects in IntelliJ, choose File -> New Project. select JavaFx from the project list and then JavaFx Application. Next, you have a view of creating projects location.
{: .tip}

What's wrong with the program? Our class `JavaFxExample` inherits a Class [Application](https://docs.oracle.com/javase/8/javafx/api/javafx/application/Application.html) that provides a framework for creating graphical user interfaces. The application is launched by the application class method [launch](https://docs.oracle.com/javase/8/javafx/api/javafx/application/Application.html#launch-java.lang.Class-java.lang.String...--), which will be given a class name *ClassName.class*  to be launched as a parameter.

When the method `launch` is called, the method in the `Application` class creates a new object of the class given in the parameter   and invokes the method `init`. The method `init` is inherited from `Application` class, and is used to initialize objects that are  used inside the program. We left it out of this, because our program is quite simple. After invoking the method, the program calls the method `start`, which gets a [Stage](https://docs.oracle.com/javase/8/javafx/api/javafx/stage/Stage.html) object describing the window as a parameter. In the implementation above of the methode `start`, the stage object is given as a parameter and sets the title by the method `setTitle`, after the method `show` called the window we be displayed. Eventually, the program will listen to user interface events such as window closure, which will lead to the application shutdown.

{% include week11/exercise/15_1.md %}
{: .exercises }

### 15.1. Structure of the user interface

The graphical user interfaces consist of essentially three parts. Stage is a program window. A Stage Object is set to a [Scene](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/Scene.html) object that reflects the view in the window. The Scene Object, however, includes an object corresponding to the layout of related components (e.g., FlowPane), which again contains specific user interface components.

The program below creates a user interface with a single button.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.FlowPane;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        Button button = new Button("First button!");

        FlowPane componentGroup = new FlowPane();
        componentGroup.getChildren().add(button);

        Scene scene = new Scene(componentGroup);

        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

The application looks like this:

![First Button App](images/15_1_firstButtonApp.png)

The user interface components are added to the "corresponding child" of the object corresponding to their layout - above the FlowPane. This is related to the decision made in JavaFx design, where any object used to set the user interface components may contain other objects used for the layout of the user interface components and, of course, also user interface components. This enables graphical user interfaces, the way the user interface components are placed depends on their location in the user interface. For example, the options in the top menu in the UI are usually placed side by side, while the items are listed below.

The structure of the user interface is therefore briefly as follows. The window contains a `Scene` object. The `Scene` Object contains an object corresponding to the layout of the user interface components. The object corresponding to the layout of the user interface components can include both user interface components and objects corresponding to the layout of the user interface components.

### 15.2. User interface Components

When creating graphical user interfaces, programmers typically utilize the components provided by ready-made UI libraries to develop applications. For example, the programmer should not create a user interface button from scratch (for example, create a class that draws a button and enables processing of related functionality), since the corresponding component is usually available from the user interface libraries. Let's look at the next few user interface components.

Text is displayed using the [Label](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/control/Label.html) component. `Label` provides a user interface component that can be set to text and the text can be edited using methods. The displayed text is set either in the constructor or in a separate methode `setText`.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.layout.FlowPane;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        Label label = new Label("First label!");

        FlowPane componentGroup = new FlowPane();
        componentGroup.getChildren().add(label);

        Scene scene = new Scene(componentGroup);

        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

![First Label](images/15_2_firstLabel.png)

You can use the Button component to add buttons on the user interface. Adding a button to a user interface is just like adding a text element.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.FlowPane;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        Button button = new Button("First button!");

        FlowPane componentGroup = new FlowPane();
        componentGroup.getChildren().add(button);

        Scene scene = new Scene(componentGroup);

        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

![First Button App](images/15_1_firstButtonApp.png)

Multiple user interface elements can also be added to the application at the same time. Below a button and a text element are added inside the same application.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.FlowPane;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        Label label = new Label("First label!");
        Button button = new Button("First button!");

        FlowPane componentGroup = new FlowPane();
        componentGroup.getChildren().add(label);
        componentGroup.getChildren().add(button);

        Scene scene = new Scene(componentGroup);

        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

The application looks like this:

![Button and label](images/15_2_buttonlabel.png)

At [https://docs.oracle.com/javase/8/javafx/user-interface-tutorial/](https://docs.oracle.com/javase/8/javafx/user-interface-tutorial/), a number of ready-to-use interface components are listed. The page also provides examples of how to use user interface components.

There are a considerable number of user interface components. You should use online ready-to-use tutorials, such as [https://docs.oracle.com/javase/8/javafx/user-interface-tutorial/](https://docs.oracle.com/javase/8/javafx/user-interface-tutorial/). It is worth first trying out user interface components to experiment with adding just one component and reviewing its functionality.

As individual components become familiar, their use is more straightforward. Almost all components are added in the same way to the application. As you know how to add a single component to your UI, you can virtually add all components to the UI.

The only significant difference between adding user interface components is to the point where the component user wants to display the component on the interface. Let's look at the layout of the interface components.

{% include week11/exercise/15_2.md %}
{% include week11/exercise/15_3.md %}
{: .exercises }

### 15.3. Layout of user interface components

Each user interface component has a location in the UI. The component's location is determined by the class used to set up the user interface components.

In the above examples, we used the class [FlowPane](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/layout/FlowPane.html) for the layout of the user interface components. With `FlowPanel`, the components that are added to the user interface will be placed side by side. If the size of the window decreases so that all the components do not fit next to each other, the components are automatically wrapped. In the figure below, the application generated by the previous example is narrowed, so that the elements are automatically routed.

![Narrowed](images/15_3_narrowed.png)

#### 15.3.1. BorderPlane

The [BorderPane](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/layout/BorderPane.html) component allows the user interface components to be set to five main locations: top, right, bottom, left and middle. Traditional apps, such as your web browser, use this layout style. At the top, there is a menu with an address bar, and the middle is the page content.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.BorderPane;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        BorderPane borderPane = new BorderPane();
        borderPane.setTop(new Label("top label"));
        borderPane.setRight(new Label("right label"));
        borderPane.setBottom(new Label("bottom label"));
        borderPane.setLeft(new Label("left label"));
        borderPane.setCenter(new Label("center label"));

        Scene scene = new Scene(borderPane);

        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

![BorderPlane](images/15_3_1_borderPlane.png)

{% include week11/exercise/15_4.md %}
{: .exercises }

#### 15.3.2. HBox

The [HBox](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/layout/HBox.html) component allows the user interface components to be horizontal aligned.

```java
    @Override
    public void start(Stage stage) {
        HBox hBox = new HBox();
        hBox.getChildren().add(new Label("One"));
        hBox.getChildren().add(new Label("Two"));
        hBox.getChildren().add(new Label("Three"));

        Scene scene = new Scene(hBox);

        stage.setScene(scene);
        stage.show();
    }
```

![HBox](images/15_3_2_hbox.png)

As noted in the previous example, HBox sets the interface components by default directly towards each other. With the method `setSpacing`, the amound of spacing between the components can be set.

```java
@Override
    public void start(Stage stage) {
        HBox hBox = new HBox();
        hBox.setSpacing(10);
        hBox.getChildren().add(new Label("One"));
        hBox.getChildren().add(new Label("Two"));
        hBox.getChildren().add(new Label("Three"));

        Scene scene = new Scene(hBox);

        stage.setScene(scene);
        stage.show();
    }
```

![Hbox with spacing](images/15_3_2_hbox_spacing.png)

The class [VBox](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/layout/VBox.html) works accordingly, but puts the user interface components vertically.

![VBox](images/15_3_2_vbox.png)

#### 15.3.3. GridPane

[GridPane](https://docs.oracle.com/javafx/2/api/javafx/scene/layout/GridPane.html) allows the user interface components to be placed in a grid. In the example below, a 3x3-square grid is created, each box contains a button.

```java
    @Override
    public void start(Stage stage) {
        GridPane  gridPane = new GridPane();
        
        for (int x = 1; x <= 3; x++) {
            for (int y = 1; y <= 3; y++) {
                gridPane.add(new Button("" + x + ", " + y), x, y);
            }
        }
        
        Scene scene = new Scene(gridPane);

        stage.setScene(scene);
        stage.show();
    }
```

![GridPane](images/15_3_3_gridpane.png)

#### 15.3.4. Multiple layers in the same interface

Layouts used in user interface components can also be combined. A typical solution is to use the `BorderPane` Layout on the base where other layouts are placed. In the example below, the top of the `BorderPanes` has a `HBox` used for the same line layout and the `VBox` used to fit the left-hand side. A text field is placed in the middle.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.HBox;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class JavaFxExample extends Application {

    @Override
    public void start(Stage stage) {
        BorderPane borderPane = new BorderPane();

        HBox hBox = new HBox();
        hBox.setSpacing(10);
        hBox.getChildren().add(new Button("One"));
        hBox.getChildren().add(new Button("Two"));
        hBox.getChildren().add(new Button("Three"));

        VBox vBox = new VBox();
        vBox.setSpacing(10);
        vBox.getChildren().add(new Label("One"));
        vBox.getChildren().add(new Label("Two"));
        vBox.getChildren().add(new Label("Three"));

        borderPane.setTop(hBox);
        borderPane.setLeft(vBox);
        borderPane.setCenter(new TextArea());
        
        Scene scene = new Scene(borderPane);

        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(JavaFxExample.class);
    }
}
```

![Multiple layouts](images/15_3_4_multipleLayouts.png)

{% include week11/exercise/15_5.md %}
{: .exercises }

## 15.4. Event Handling

The above interfaces do not react to events in the UI. This is not due to user interface components, but because we have not implemented the functionality required to handle events from the user interface components.

Pressing the buttons will be handled with in the class when you implement the interface [EventHandler](https://docs.oracle.com/javase/8/javafx/api/javafx/event/EventHandler.html). The event type is [ActionEvent](https://docs.oracle.com/javase/8/javafx/api/javafx/event/ActionEvent.html). The implementation of the interface defines *what needs to done* when the user presses the button.

```java
        Button button1 = new Button("One");
        button1.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                System.out.println("Hello World!");
            }
        });
```

The explicit implementation of the interface can be replaced by a Lambda expression.

```java
        Button button1 = new Button("One");
        button1.setOnAction((event) -> {
                System.out.println("Hello World!");
            });
```

When the button above is pressed, the word *"Hello World!"* Is printed in the console.

Event handlers associated with user interface components like the `EventHandler` we used above, are always linked to specific user interface component. Each time a method is applied to the user interface component, for example, pressing a button on a button, each event handler associated with that specific user interface component is called and the associated program code is executed.

Typically, we want the event handler to modify the status of an object. To get access to the object, the event handler has a reference to the object being handled. Consider the following UI with two text fields and a button.

```java
@Override
    public void start(Stage stage) {
        TextField textFieldLeft = new TextField();
        TextField textFieldRight = new TextField();
        Button button = new Button("Copy");

        HBox hBox = new HBox();
        hBox.setSpacing(20);
        hBox.getChildren().addAll(textFieldLeft, button, textFieldRight);

        Scene scene = new Scene(hBox);

        stage.setScene(scene);
        stage.show();
    }
```

There is a text field on the left and right of the user interface. In addition to the text fields, there is a button labeled "Copy" in the center of the user interface.

![Copy text](images/15_4_copyText.png)

We would like to create a program where the contents of the left text field will be copied into the content of the right field when the user presses the button. This is achieved through the interface `EventHandler`. The method to implement must be able to use the above defined objects, if the values ​​of the objects are not redefined with the same name (ie the references do not change).

```java
 @Override
    public void start(Stage stage) {
        TextField textFieldLeft = new TextField();
        TextField textFieldRight = new TextField();
        Button button = new Button("Copy");

        button.setOnAction(event -> {
            textFieldRight.setText(textFieldLeft.getText());
        });
        HBox hBox = new HBox();
        hBox.setSpacing(20);
        hBox.getChildren().addAll(textFieldLeft, button, textFieldRight);

        Scene scene = new Scene(hBox);

        stage.setScene(scene);
        stage.show();
    }
```

![Text Copy](images/15_4_copyText_2.png)

{% include week11/exercise/15_6.md %}
{% include week11/exercise/15_7.md %}
{: .exercises }
