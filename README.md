# Portfolio Generator using Design Principles and Patterns

The portfolio generator application uses Java object oriented concepts and design principles and patterns to enable users to create visually appealing portfolios with modern UI design. The application allows users to input their personal information and project details through an intuitive web-based form. Upon submission, the application generates a dynamic HTML portfolio page based on the user's input, incorporating modern design and a contemporary layout. Users have the option to choose from multiple pre-designed templates to customise the appearance of their portfolios.


## Features

- **User Input**: Collects user information such as name, email, phone number, project title, project description, and project link.
- **HTML Generation**: Utilizes the **Factory Method** pattern to generate HTML content based on selected style options (Basic or Fancy).
- **Color Customization**: Implements the **Strategy** pattern to allow users to choose from different color options (Default, Red, or Blue) for the portfolio.
- **HTML File Export**: Writes the generated HTML content to a file named "portfolio.html" in the current directory.


## Design Patterns

### Observer Pattern
- **Description**: Establishes a one-to-many dependency between objects, notifying and updating dependents automatically when the state of one object changes.
- **Application**: `HTMLGenerationListener` interface as observer, `Main` class as subject. Other classes can register as listeners to be notified of HTML generation.

### Singleton Pattern
- **Description**: Ensures a class has only one instance and provides a global point of access to that instance.
- **Application**: `HTMLFileWriter` implements the singleton pattern, accessed through `getInstance`.

### Factory Method Pattern
- **Description**: Defines an interface for creating objects, allowing subclasses to alter the type of objects created.
- **Application**: 
  - `HTMLFactory` as an abstract class with `generateHTML()` method.
  - `createFactory()` as the factory method for creating instances of subclasses (`BasicHTMLFactory`, `FancyHTMLFactory`).

### Strategy Pattern
- **Description**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable, allowing the algorithm to vary independently from the client using it.
- **Application**:
  - `ColorStrategy` interface with `applyColor(String html)`.
  - `RedColorStrategy` and `BlueColorStrategy` implement `ColorStrategy`.
  - `Main` class as context, using `JComboBox<String>` for selecting color options and applying selected strategy on HTML content.

## Design Principles

### Open/Closed Principle (OCP)
- **Description**: Classes should be open for extension but closed for modification.
- **Application**: `HTMLFactory` and its subclasses (`BasicHTMLFactory`, `FancyHTMLFactory`) allow extension without altering existing code.

### Liskov Substitution Principle (LSP)
- **Description**: Objects of a superclass should be replaceable with objects of a subclass without affecting the program's correctness.
- **Application**: `BasicHTMLFactory` and `FancyHTMLFactory` can substitute `HTMLFactory` without altering program behavior, ensuring consistent behavior with overridden methods.

### Single Responsibility Principle (SRP)
- **Description**: A class should have only one reason to change, focusing on a single responsibility.
- **Application**: Each class (e.g., `User`, `Form`, `HTMLGenerator`) has a clearly defined responsibility, maintaining focus and clarity.

### Information Expert
- **Description**: A class should manage information it possesses the most knowledge about.
- **Application**: `User` class manages user details, encapsulating name, email, phone number, and address, adhering to the Information Expert principle.

## Installation

To run the Portfolio Generator, ensure you have the following installed:

- Java Runtime Environment (JRE)
- Default Java Development Kit (JDK)
- Java Extension for Visual Studio Code

## Usage

1. Compile the Java code: `javac Main.java`
2. Execute the compiled code: `java Main`
3. Fill in the required details in the GUI.
4. Select HTML style and color options.
5. Click on "Generate Portfolio" to create the HTML file.




## License

This project is licensed under the [MIT License](LICENSE).
