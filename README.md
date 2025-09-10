# Custom-pizza-order
This program will make a custom pizza order based on the user's input of size, additional toppings, and crust type. It will then calculate the total cost of the pizza and display it to the user.

/* Name: Zihan
  Date: 22/07/2024
  Description: This program will make a custom pizza order based on the user's input of size, additional toppings, and crust type. It will then calculate the total cost of the pizza and display it to the user.
*/

import java.util.Scanner;

public class Main {
  public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    boolean confirmOrder = true;
    double sizePrice = 0.0;

    do {
      menuDisplay();
      sizePrice = size(sizePrice);
      // System.out.println(sizePrice);
      crust(input);

    } while (confirmOrder == true);
    System.out.println("Thank you for using the pizza ordering system.");

    input.close();
  }

  // menuDisplay
  public static void menuDisplay() {
    System.out.println("\n *********");
    System.out.println("Welcome to Cindy's Pizza \n");
    System.out.println("Make your custom pizza today!");
    System.out.println("");
    System.out.println(" ☆    Medium Pizza -------- $9.99");
    System.out.println(" ☆    Large Pizza --------- $12.99");
    System.out.println(" ☆    X-Large Pizza ------- $15.99");
    System.out.println("");
    System.out.println("  Additional Toppings: $1.25 ea.");
    System.out.println("  Crust options: Regular, Thin, Pan");
  }

  // size
  public static double size(double sizePrice) {
    Scanner input = new Scanner(System.in);

    final double M_PRICE = 9.99;
    final double L_PRICE = 12.99;
    final double XL_PRICE = 15.99;
    String sizeChoice;

    System.out.println("\n*** SIZE ***");
    System.out.println("What size of pizza would you like?");
    System.out.println("Please enter 'M' for medium, 'L' for large, or 'XL' for X-Large.");
    System.out.print("Your choice: ");
    sizeChoice = input.nextLine();

    boolean validInput = false;
    boolean isConfirmSize = false;

    while (!isConfirmSize) {
      while (!validInput) {
        if (sizeChoice.equalsIgnoreCase("m")) {
          System.out.println("You have selected a medium pizza.");
          sizePrice = M_PRICE;
          validInput = true;
        } 
        else if (sizeChoice.equalsIgnoreCase("l")) {
          System.out.println("You have selected a large pizza.");
          sizePrice = L_PRICE;
          validInput = true;
        } 
        else if (sizeChoice.equalsIgnoreCase("xl")) {
          System.out.println("You have selected an X-Large pizza.");
          sizePrice = XL_PRICE;
          validInput = true;
        } 
        else {
          System.out.println("Sorry " + sizeChoice + " is not a valid option. Please try again.");
          System.out.print("Your choice: ");
          sizeChoice = input.nextLine();
        }

        System.out.println("Please confirm your size choice. Enter 'Y' for yes or 'N' for no.");
        System.out.print("Your choice: ");
        String confirmSize = input.nextLine();

        if (confirmSize.equalsIgnoreCase("y")) {
          isConfirmSize = true;
          System.out.println("Size Confirmed...");
        } 
        else if (confirmSize.equalsIgnoreCase("n")) {
          isConfirmSize = false;
          validInput = false;
          System.out.println("\n*** SIZE ***");
          System.out.println("What size of pizza would you like?");
          System.out.println("Please enter 'M' for medium, 'L' for large, or 'XL' for X-Large.");
          System.out.print("Your choice: ");
          sizeChoice = input.nextLine();
        } 
        else {
          System.out.println("Sorry " + confirmSize + " is not a valid option. Please try again.");
          System.out.print("Your choice: ");
          confirmSize = input.nextLine();
        }
      }
    }
    return sizePrice;
  }

  // additional toppings
  public static void toppings() {
    Scanner input = new Scanner(System.in);

    final String toppingsChoice[] = { "Cheese", "Pepperoni", "Bacon", "Mushroom" };

    final double toppingsPrice = 1.25;
    int numberOfToppings = 0;

    System.out.println("TOPPINGS");
    System.out.println("All pizzas come with cheese.");
    System.out.println("Additional toppings are $1.25 each. Choose from: ");
    System.out.println("Cheese, Pepperoni, Bacon, Mushroom");
    System.out.println("");

    System.out.println("Would you like cheese? Y/N");
    String addToppings = input.nextLine();
  }

  // crust
  public static void crust(Scanner input) {

    boolean validInput = false;
    boolean isConfirmCrust = false;

    int crustChoice = 0;

    while (!isConfirmCrust) {
      do {
        try {
          System.out.println("\n*** CRUST TYPE ***");
          System.out.println("Choose from (type 1-3): ");
          System.out.println("1. Regular     2. Thin     3. Pan");
          System.out.println("");
          System.out.print("Your choice: ");
          crustChoice = input.nextInt();
          validInput = true;
        } catch (java.util.InputMismatchException e) {
          System.out.println("Sorry, that is not a valid input. Please try again.");
          input.nextLine();
        }
      } while (!validInput);

    }

    System.out.println("Please confirm your crust choice. Enter 'Y' for yes or 'N' for no.");
    System.out.print("Your choice: ");
    String confirmCrust = input.nextLine();
    if (confirmCrust.equalsIgnoreCase("y")) {
      isConfirmCrust = true;
    } 
    else if (confirmCrust.equalsIgnoreCase("n")) {
      isConfirmCrust = false; 
      validInput = false; 
    } 
    else {
      System.out.println("Sorry " + confirmCrust + " is not a valid option. Please try again.");
      System.out.print("Your choice: ");
      confirmCrust = input.nextLine();
    }
  }

  // cost
  // confirmOrder

}
