# Image resizer: MTS Teta backend selection task

A Java 8 command-line image processing exercise submitted for the MTS Teta summer school's backend selection. It uses Picocli for arguments and image-processing libraries for resize, crop, blur and format conversion.

The original task statement has been moved unchanged to [`docs/assignment.md`](docs/assignment.md) so that this README can focus on the implementation.

## Supported options

The command class in `ResizerApp.java` accepts two positional file paths: **input** followed by **output**.

| Option | Arguments | Purpose |
| --- | --- | --- |
| `--resize` | width height | Resize the image |
| `--crop` | width height x y | Crop to a rectangle |
| `--blur` | radius | Apply blur |
| `--quality` | value | Set output quality |
| `--format` | format | Select output format |

The CLI advertises JPEG and PNG support. Check the image processor for the behavior of each combination of options.

## Build and run

Prerequisites: Java 8 or later and Maven.

```sh
mvn test
mvn package
java -jar target/resizer-1.0-SNAPSHOT-jar-with-dependencies.jar --help
```

Example invocation pattern:

```sh
java -jar target/resizer-1.0-SNAPSHOT-jar-with-dependencies.jar input.jpg output.jpg --resize 640 480
```

The runnable JAR name comes from the Maven assembly configuration. Commands are documented from the repository; they have not been executed in this update.

## Code map

- [`ResizerApp.java`](src/main/java/mts/teta/resizer/ResizerApp.java): application entry point.
- [`ConsoleAttributes.java`](src/main/java/mts/teta/resizer/ConsoleAttributes.java): command-line options.
- [`ImageProcessor.java`](src/main/java/mts/teta/resizer/imageprocessor/ImageProcessor.java): image operations and validation.
- [`ResizerAppTest.java`](src/test/java/mts/teta/resizer/ResizerAppTest.java): tests.

This is a selection exercise, not a maintained image-processing service. Performance requirements in the assignment are task criteria, not benchmarks verified by this README.
