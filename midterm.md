Pharmacy.java (main)
``` java
import java.util.Scanner;
import java.util.ArrayList;

public class Pharmacy {
    // protected strings; accessible to subclasses
    protected String itemName;
    protected String companyName;
    
    // Method updates item and company name, given user input, and validates user input
    public void updateItem(Scanner scnr){
        // guarantees correct itemName input
        while(true) {
            try {
                System.out.println("Item name: ");
                itemName = scnr.nextLine();
                // Will create new IllegalArgumentException object if .isEmpty succeeds
                if (itemName.trim().isEmpty()) {
                    throw new IllegalArgumentException("Error: Item name cannot be empty.");
                }
                break;
            } catch (IllegalArgumentException e) {
                System.out.println(e.getMessage());
            }
        }
        // guarantees correct companyName input
        while(true) {
            try {
                System.out.println("Company name: ");
                companyName = scnr.nextLine();
                // Will create new IllegalArgumentException object if .isEmpty succeeds
                if (companyName.trim().isEmpty()) {
                    throw new IllegalArgumentException("Error: Company name cannot be empty.");
                }
                break;
            } catch (IllegalArgumentException e) {
                System.out.println(e.getMessage());
            }
        }
    }
    
    // Method overloading: Methods display individual characteristic information for Painkillers, Bandages, and Equipment
    // Indiivdual pk, bd, ep objects are created in respective classes to call corresponding methods
    public void displayItem(Painkillers pk) {
        System.out.println("Painkiller \t Item name: " + pk.getItemName() + ", Company name: " + pk.getCompanyName() +
                ", Expiry date: " + pk.getExpiryDate() + ", Age group: " + pk.getAgeGroup());
    }
    public void displayItem(Bandages bd) {
        System.out.println("Bandage \t Item name: " + bd.getItemName() + ", Company name: " + bd.getCompanyName() + 
                ", Expiry date: " + bd.getExpiryDate() + ", Age group: " + bd.getAgeGroup() + 
                ", Waterproof: " + (bd.getWaterProof() ? "Y" : "N"));
    }
    public void displayItem(Equipment ep) {
        System.out.println("Equipment \t Item name: " + ep.getItemName() + ", Company name: " + ep.getCompanyName() +
                ", Item weight: " + ep.getItemWeight() + " lbs");
    }
    
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);
        // creating 3 ArrayLists to keep track of all information
        ArrayList<Painkillers> allPainkillers = new ArrayList<>();
        ArrayList<Bandages> allBandages = new ArrayList<>();
        ArrayList<Equipment> allEquipment = new ArrayList<>();
        
        int userChoice;
        
        // do while loop executes if the user does not want to terminate the program
        do {
            System.out.println("Pharmacy Inventory");
            System.out.println("1. Add Painkiller Information");
            System.out.println("2. Add Bandage Information");
            System.out.println("3. Add Equipment Information");
            System.out.println("4. Display All Information");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            userChoice = scnr.nextInt();
            scnr.nextLine();
            
            // switch-case is more efficient than if-elseif-else in this scenario
            // the rule switch (->) formatting allows us to eliminate the break statements (nice feature!)
            switch(userChoice) {
                // if the user choice is 1, then a new painkiller will be added
                case 1 -> {
                    // initialized values using the Painkillers constructor
                    Painkillers pk = new Painkillers(null, null, null, null);
                    pk.updateItem(scnr);
                    allPainkillers.add(pk);
                }
                case 2 -> {
                    Bandages bd = new Bandages(null, null, null, null, false);
                    bd.updateItem(scnr);
                    allBandages.add(bd);
                }
                case 3 -> {
                    Equipment ep = new Equipment(null, null, 0.0);
                    ep.updateItem(scnr);
                    allEquipment.add(ep);
                }
                // displays all inventory information
                case 4 -> {
                    Pharmacy inventory = new Pharmacy();
                    // Displays every item p in the ArrayList allPainkillers
                    for (Painkillers p : allPainkillers) {
                        inventory.displayItem(p);
                    }
                    // Displays every item b in the ArrayList allBandages
                    for (Bandages b : allBandages) {
                        inventory.displayItem(b);
                    } 
                    // Displays every item e in the ArrayList allEquipment
                    for (Equipment e : allEquipment) {
                        inventory.displayItem(e);
                    }
                }
                // break statement - exit
                case 5 -> {
                }
                // if the user input is NOT 1,2,3,4,5
                default -> System.out.println("Invalid choice.");
        }
    } while (userChoice != 5);
        
    scnr.close();
    }
}
```
Painkillers.java
``` java
import java.util.Scanner;

// subclass of Pharmacy
public class Painkillers extends Pharmacy {
    // get methods to retrieve respective variables
    public String getItemName() {
        return itemName;
    }
    
    public String getCompanyName() {
        return companyName;
    }
    
    private String expiryDate;
    public String getExpiryDate() {
        return expiryDate;
    }
    
    private String ageGroup;
    public String getAgeGroup() {
        return ageGroup;
    }
    
    // Painkillers constructor with the following parameters
    public Painkillers(String itemName, String companyName, String expiryDate, String ageGroup) {
        this.itemName = itemName;
        this.companyName = companyName;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
    }
    
    // Overrides superclass updateItem, now specific to Painkillers - has expiry date and age group
    @Override
    public void updateItem(Scanner scnr) {
        // updating superclass parameters - itemName & companyName - same for rest of the overrides
        super.updateItem(scnr);
        System.out.println("Expiry date: ");
        expiryDate = scnr.nextLine();
        System.out.println("Age group: ");
        ageGroup = scnr.nextLine();
    }
    
}
```
Bandages.java
``` java
import java.util.Scanner;

// subclass of Pharmacy
public class Bandages extends Pharmacy {
    // get methods to retrieve variables
    public String getItemName() {
        return itemName;
    }
    public String getCompanyName() {
        return companyName;
    }
    private String expiryDate;
    public String getExpiryDate(){
        return expiryDate;
    }
    private String ageGroup;
    public String getAgeGroup(){
        return ageGroup;
    }
    private boolean waterProof;
    public boolean getWaterProof() {
        return waterProof;
    }
    // Bandages constructor with the following parameters
    public Bandages(String itemName, String companyName, String expiryDate, String ageGroup, boolean waterProof) {
        this.itemName = itemName;
        this.companyName = companyName;
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
        this.waterProof = waterProof;
    }
    // Overrides superclass updateItem - with expiry date, age group, and waterproof
    @Override
    public void updateItem(Scanner scnr) {
        super.updateItem(scnr);
        System.out.println("Expiry date: ");
        expiryDate = scnr.nextLine();
        System.out.println("Age group: ");
        ageGroup = scnr.nextLine();
        // validates user input - checks if it is not y/Y or n/N, if true  then prints error message using InputException class
        while(true){
            try {
                System.out.println("Waterproof? (Y/N): ");
                String userInput = scnr.nextLine().toUpperCase();

                if (!userInput.equals("Y") && !userInput.equals("N")) {
                    throw new InputException("Please enter 'Y' or 'N' only.");
                }
                // if userInput is yes, then waterProof is true
                waterProof = userInput.equals("Y");
                break;
            } catch (InputException e) {
                System.out.println(e.getMessage());
            }
        }
    }
    
}
```
Equipment.java
``` java
import java.util.Scanner;
import java.util.InputMismatchException;

// subclass of Pharmacy
public class Equipment extends Pharmacy {
    public String getItemName() {
        return itemName;
    }
    public String getCompanyName() {
        return companyName;
    }
    private double itemWeight;
    public double getItemWeight(){
        return itemWeight;
    }
    
    public Equipment(String itemName, String companyName, double itemWeight) {
        this.itemName = itemName;
        this.companyName = companyName;
        this.itemWeight = itemWeight;
    }
    
    // Overrides superclass updateItem - has item weight
    @Override
    public void updateItem(Scanner scnr) { 
        super.updateItem(scnr);
        while(true) {
            // if the user's input is negative or not a number, it continues asking for item weight 
            // it also throws the error message for input mismatch (string vs double) and illegal argument (negative value, in this case)
            try {
                System.out.println("Item weight (lbs): ");
                itemWeight = scnr.nextDouble();

                if (itemWeight < 0) {
                    throw new IllegalArgumentException("Error: Weight must be positive.");
                }
                break;
            } catch (InputMismatchException e) {
                System.out.println("Error: Weight must be a number.");
                scnr.nextLine();
            } catch (IllegalArgumentException e) {
                System.out.println(e.getMessage());
                scnr.nextLine();
            }
        }
        
    }
    
}
```
InputException.java (for ver 3)
``` java
public class InputException extends Exception {
    // Constructor for exception
    public InputException(String message) {
        // e.getMessage() will now print the user-dictated message given when the constructor was called
        super(message);
    }
}
```
