# COSC 310 Team 5 Project

This is the public repository team 5 will be using to collaborate on the project throughout the term.

### Compile instructions:
 - After cloning the whole repo, navigate to the src directory using the command prompt for your system (terminal/cmd/mac terminal).
 - run the command `javac -cp ../lib/* -d ../bin/ *.java`
 - change directory to the bin folder and run `java -cp ../lib/*; InventorySystemMain`
 - note that the password for the credential check is `password` but can be changed via the UI and will be saved and encrypted in bin/InventorySystem.state

### Explanation of classes:
 - **InventorySystemMain:** this is the main class with the main logic, although the program is mainly event-based. It contains 7 methods that are called by event listener within the MainUI class: load, save, add, edit, order, transaction, and setTime. This class contains instances of MainUI (for methods related to the GUI), JFileChooser (for opening/saving files), LocalDate (for determining when Orders have arrived), Database (for tracking the loaded database), an arraylist of Orders (for tracking all current Orders), and a double revenue for tracking the total gain/loss of that session.
 - **MainUI:** this is the main UI window that contains the listener that calls back to methods in InventorySystemMain. This class also contains a method for updating the visual JTable element when the backend Database instance is changed, as well as a method for updating the revenue label and returning the currently selected row.
 - **PasswordUI:** this is a fairly barebones UI class that simply checks if the user entered the correct password before the window got disposed.
 - **ProductUI:** this is the UI window used for adding new products to the database as well as editing existing products. Its event listener method does error checking for input validation before allowing the data to be submitted to the parent dialogue.
 - **TransactionUI:** this is the UI window used for simulating customer transactions as well as ordering new stock for products. Its event listener compiles a dictionary structure for each product and the quantity selected before being disposed.
 - **SetTimeUI:** this is the UI window used for simulating the passage of time within the program, it is fairly simple and only consists of a listener that returns the 2 integer values (months and days to fast forward) upon activation.
 - **Order:** this is the class that tracks orders the administrator has made for new stock. It contains a Product instance (to identify what product is being ordered), an integer quantity (for tracking how many of the product was ordered), a LocalDate instance of the day the order was placed (to track when the order arrives), and a boolean value to determine if this order is still in shipment or has been received. This class also contains a boolean method to check given the current date whether the order has arrived yet as well as a void method to handle everything when the order is received.
 - **Product:** each instance of the product class represents a unique product (also 1 row from the database). The constructor will create each product instance from the csv file provided in the Database class. This class contains attributes for each column name and have the proper data types for each. Methods for getting and setting the attribute values, and formatting the list into a String is included as well.
 - **Database:** this class communicates with the UI and handles the backend functions of the inventory system. The class takes a csv file stored locally on the computer and accesses the data stored. The method available allows for adding products, removing products, editing products information, and searching for products via each attribute values.

- **Inventory Analysis:** This class provides the necessary methods for analysis of the inventory. Methods to check if the Stock available is below 10 so that it pops a message to the manager to re-stock and methods to change delivery time depending upon the delays. Currently the class contains methods such as add, edit, save, load, remove which are used in database class in order to have a functional system. The analysis methods will be updated in assignment 3.
