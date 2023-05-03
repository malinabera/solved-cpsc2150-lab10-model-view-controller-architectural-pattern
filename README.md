Download Link: https://assignmentchef.com/product/solved-cpsc2150-lab10-model-view-controller-architectural-pattern
<br>
In this lab, you will be working with the Model-View-Controller architectural pattern. While the Model-View-Controller pattern will be beneficial for working with Graphical User Interfaces (GUI), we will not be working with a GUI for this assignment yet. We will be building off the code from a previous lab, specifically the Mortgage and Customer interfaces and classes.




<h1>Instructions</h1>

You will need to create a new project with a package called cpsc2150.banking. Add your Mortgage and Customer classes and interfaces from lab 6 to that package. (<strong>Note:</strong> You will need to create the models folder for these files to match their package structure.) You will then need three more classes:




<h2>MortgageApp.java</h2>

MortgageApp will be a very simple class. It will contain our main method that will be the entry point of the program. All it will do is declare an instance of IMortgageView and an instance of IMortgageController, and then call MortageController.submitApplication(). The code should look like this:




package cpsc2150.banking;




public class MortgageApp {

public static void main(String [] args) {         IMortgageView view = new MortgageView();

IMortgageController controller = new MortgageController(view);         view.setController(controller);         controller.submitApplication();     }

}




This type of setup is common when using MVC architectural pattern in Java. We just need the entry point to set up our <strong>Controller</strong> and <strong>View</strong>, then turn over control of the program to the <strong>Controller</strong>.




<h2>MortgageView.java</h2>

MortgageView will serve as the <strong>View</strong> layer of our MVC architecture. That means that MortgageView is the only class that can get input from the user or print to the screen. The <strong>Controller</strong> layer will use MortgageView to perform these tasks. MortgageView also does not know about our <strong>Model</strong> layer, so it cannot perform any input validation on whether or not the given values meet our Mortgage or Customer classes’ preconditions. MortgageView can still validate whether a “Y” or “N” was entered for yes or no prompts since that is a requirement of the <strong>View</strong> itself, not the <strong>Model</strong>.

The only class-level variables that MortgageView should have are a Scanner object and its IMortgageController object. Remember, we can have issues if we have multiple Scanner objects looking at the same input source, so we don’t want to declare one in each function. We actually won’t need to use the IMortgageController object, but the initialization ensures clause says we must include it

MortgageView should implement the IMortgageView interface using a command-line prompt for the user interface. The “get” methods all ask the user for the specified value. They do not perform any data validation (except for validating the Y/N response) as the view does not have access to the <strong>Model</strong> layer. We can assume the user will input the correct data type (i.e., a number when a number is expected).




<strong>Note 1:</strong> You may not need to use all the functionality that IMortgageView provides to complete this assignment. That is completely fine; the interface was written to be used for multiple programs, so it may include extra functionality that we don’t need right now.




<strong>Note 2:</strong> The IMortgageView and MortgageView files should be placed inside a new views folder to match the package cpsc2150.banking.views.




<h2>MortgageController.java</h2>

The MortgageController class implements IMortgageController and serves as the

<strong>Controller</strong> layer in our MVC architecture. It controls the flow of control in our program. This class can use both the <strong>View</strong> and the <strong>Model</strong> layers to accomplish this task. This class will check to make sure the data that the user provides (through the <strong>View</strong> layer) meets the preconditions that exist in our <strong>Model</strong> layer. If the input is not valid, the <strong>Controller</strong> will (through the <strong>View</strong>) alert the user to the error and reprompt the user for correct input. The MortgageController class will also use the <strong>Model</strong> layer (Mortgage and Customer interfaces and classes) to actually apply for the mortgage. After a mortgage has been applied for, the <strong>Controller</strong> will (through the <strong>View</strong> layer) display the Customer and Mortgage information to the user (<strong>Note:</strong> use the toString methods to do this).

The controller will allow for a customer to apply for multiple loans (without having to re-enter the customer information) and allow for the user to enter information about multiple customers. Remember, the <strong>Controller</strong> layer cannot directly interact with the user, it must go through the <strong>View</strong> layer.

The MortgageController class will have one private field, an IMortgageView object, which is set by an argument passed into the constructor. The MortgageController class will have one public method, called submitApplication() which runs the program.

All the logic concerning validating the <strong>Model’s</strong> preconditions, and the order of events, is handled by the <strong>Controller</strong> layer. The logic concerning the Mortgage application or the Customer itself are handled by the <strong>Model</strong> layer.




<strong>Note:</strong> The IMortgageController and MortgageController files should be placed inside a new controllers folder to match the package cpsc2150.banking.controllers.




<h1>TIPS and additional Requirements</h1>

<ul>

 <li>You must provide a makefile with make, make run and make clean

  <ul>

   <li>This will be a large deduction if you do not</li>

  </ul></li>

 <li>You do not need to provide any automated testing, although you should test your program.</li>

 <li>You do not need to provide any contracts for MortgageView, MortgageController, or MortgageApp. Mortgage and Customer should have contracts from a previous assignment.</li>

 <li>You <strong><u>DO</u></strong> need to comment your code</li>

 <li>You need to follow the Model-View-Controller architectural pattern for this assignment.

  <ul>

   <li>All interaction with the user goes through the <strong>View</strong> <strong>View</strong> does not have access to the <strong>Model</strong> layer.</li>

   <li><strong>Controller</strong> layer handles input validation, and the order of events of the program. The <strong>Controller</strong> layer has access to the <strong>View</strong> and the <strong>Model</strong>, so it is the go between for those two layers</li>

   <li>The <strong>Model</strong> layer handles our entity objects and the “lower level” logic. It does not have any access to the other two layers.</li>

  </ul></li>

 <li>Follow our best practices: No magic numbers, information hiding, separation of concerns, etc.</li>

 <li>java has a toString method that will be useful.</li>

 <li>Make sure your package structure is correct. If IntelliJ / Java gives you an error, check to see if your constructors and functions have the correct visibility!</li>

</ul>


