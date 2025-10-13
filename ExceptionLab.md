## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/Ea7hIqgTIgREr9faS-ZoXdsBWx1mCzM0B-lKt4PQDGI1zg?e=1krVhc

## Question:
I think the most challenging part of this lab was implementing the while loop so that it could continuously display the enter message if the user input was invalid. One time, I had written the while loop
but it had threw an infinite number of Exception messages. Fixing this was challenging, but I managed to get it to succeed.
## Video:
https://1drv.ms/v/c/04e020fac6629467/EfpGncS56dxOrfMam19t9NUBQhhW7b1Dqjefyzet0f40Qw?e=YumMNY

## Code:
``` java
import java.util.Scanner;

/**
 *
 * @author chloe
 */
public class StepsToMiles {
    public static double stepsToMiles(int steps) throws Exception{
        if (steps < 0) {
            // creates new exception object that displays the following message
            throw new Exception("Exception: Negative step count entered.");
        }
        // calculates number of miles (double)
        return steps/2000.0;
    }
    public static void main(String[] args) {
        boolean validInput = false;
        double miles = 0.0;
        Scanner scnr = new Scanner(System.in);
        
        // while the input is not valid
        while (!validInput){
            System.out.print("Enter Number of Steps: ");
            // reads user input and stores it in number of steps
            int steps = scnr.nextInt();
            
            try {
                // returns miles value and prints
                miles = stepsToMiles(steps);
                // input is true; does not execute again
                validInput = true;
            // if steps < 0, the exception message is printed
            // Exception object e
            } catch(Exception e){
                System.out.println(e.getMessage());
            }
        }
        System.out.printf("%.2f", miles);
    }
}
```
