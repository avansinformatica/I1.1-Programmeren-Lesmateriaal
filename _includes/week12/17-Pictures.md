## 17. Pictures

There are several ways to display an image inside a Java application. One straightforward approach used JavaFx's the class [Image](https://docs.oracle.com/javafx/2/api/javafx/scene/image/Image.html) and the class [ImageView](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/image/ImageView.html).

The parameter given to Image class is the name of the image file to be opened. The name should start with the prefix *file:* that tells the image is a file. In the example below, the file humming.jpg is given as parameter towards the ImageView. Then the ImageView object is placed in the `Layout`. The layout is placed into the Scene Object and placed inside the view.

```java
import javafx.application.Application;
import static javafx.application.Application.launch;
import javafx.scene.Scene;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.Pane;
import javafx.stage.Stage;

public class ImageApplication extends Application {

    @Override
    public void start(Stage stage) {

        Image image = new Image("file:humming.jpg");
        ImageView imageView = new ImageView(image);

        Pane pane = new Pane();
        pane.getChildren().add(imageView);

        stage.setScene(new Scene(pane));
        stage.show();

    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

Executing a program creates the following window. It is assumed that the file *humming.jpg* exists and is found at the root of the project (from the same folder as the file pom.xml).

![ImageView](images/17_ImageView.png)

The example uses the picutre [Linda Tanner](https://www.flickr.com/photos/15323831@N05) available at [http://www.freestockphotos.biz/stockphoto/17874](http://www.freestockphotos.biz/stockphoto/17874). Image is licensed under the Creative Commons CC BY 2.0 license.

The class `ImageView` provides a set of methods for image (simple processing). In other words, the image can be rotated, its size can be changed and it can be moved on the screen. In the example below, the picture is rotated around, its size is halved and moved slightly to the right.

```java
@Override
public void start(Stage stage) {

    Image image = new Image("file:humming.jpg");
    ImageView imageView = new ImageView(image);
  
    imageView.setRotate(180);
    imageView.setScaleX(0.5);
    imageView.setScaleY(0.5);
  
    imageView.setTranslateX(50);

    Pane pane = new Pane();
    pane.getChildren().add(imageView);

    stage.setScene(new Scene(ruutu));
    stage.show();
}
```

![ImageView2](images/17_ImageView2.png)

The ImageView component provides access to the image, but it can not access individual pixels. [PixelReader](https://docs.oracle.com/javafx/2/api/javafx/scene/image/PixelReader.html) is interface to the individual pixels of an image. `PixelReader` allows you to go through a full image through a pixel, while writing goes via the class [WritableImage](https://docs.oracle.com/javafx/2/api/javafx/scene/image/WritableImage.html).

In the example below, the image is copied from the object `PixelReader` to a separate object `WritableImage`, that is displayed in the application.

```java
@Override
public void start(Stage stage) {

    Image image = new Image("file:humming.jpg");

    PixelReader lukija = image.getPixelReader();

    int width = (int) image.getWidth();
    int height = (int) image.getHeight();

    WritableImage writableImage = new WritableImage(width, height);
    PixelWriter pixelWriter = writableImage.getPixelWriter();

    for (int y = 0; y < height; y++) {
        for (int x = 0; x < width; x++) {

            Color color = lukija.getColor(x, y);
            double red = color.getRed();
            double green = color.getGreen();
            double blue = color.getBlue();
            double opacity = color.getOpacity();

            Color newColor = new Color(red, green, blue, opacity);

            pixelWriter.setColor(x, y, newColor);
        }
    }

    ImageView imageView = new ImageView(writableImage);

    Pane pane = new Pane();
    pane.getChildren().add(imageView);

    stage.setScene(new Scene(pane));
    stage.show();
}
```

The appearance of the picture has not changed at all.

![ImageView3](images/17_ImageView3.png)

TODO create exercise!
