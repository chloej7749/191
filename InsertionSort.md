## Flowchart
https://1drv.ms/i/c/04e020fac6629467/IQAhG3YkKGOoQ7yLqf_6mL1rAXlWDNC9Bg0A6K1l--U88Rc?e=LP78sV

## Question:
The most challenging part of this lab was grasping the concept of having an i and j variable and how looping through the for loop and nested while loops could lead to the desired result.

## Video:
https://1drv.ms/v/c/04e020fac6629467/IQDyJHUqP_88TrxP5M_odv44AckoxMVfipS2jx9rcj0AwFU?e=N9f05I

## Code
``` java
import java.util.Scanner;

public class InsertionSort {
    // method to sort given array
    public static void insertionSort(int[] numbers) {
        int temp; // temporary storage variable
        int swap = 0; // initialize at 0
        int comparison = 0;
        // outside for loop, loops through i values
        for (int i = 1; i < numbers.length; i++) {
            int j = i;
            // inside while loop, loops through j values
            // the j values approach 0, rechecking to see if values need to be swapped (as shown in flowchart)
            while (j > 0) {
                // comparison happens regardless of if the if statement is satisfied
                comparison ++;
                // if the current number is less than the number in the previous position, swap them
                if (numbers[j] < numbers[j-1]) {
                    temp = numbers[j];
                    numbers[j] = numbers[j-1];
                    numbers[j-1] = temp;
                    // decrement j by 1 to recheck
                    j--;
                    // increase swap
                    swap ++;
                    // print the array after swapping
                    for (int k = 0; k < numbers.length; k ++) {
                        System.out.print(numbers[k] + " ");
                    }
                    System.out.println();
                }
                else {
                    break;
                }
            }
            // while loop only executes when j > 0, if not then it goes to the next i value
        }
        System.out.println("Comparisons: " + comparison);
        System.out.println("Swaps: " + swap);
    }

    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);
        System.out.print("Enter array size, followed by array: ");
        // tracks size
        int size = scnr.nextInt();
        int[] numArray = new int[size]; // initialize array
        // prints array
        for (int i = 0; i < size; i++) {
            numArray[i] = scnr.nextInt();
            System.out.print(numArray[i] + " ");
        }
        System.out.println();
        System.out.println();
        // calls method on numArray
        insertionSort(numArray);
        
        
    }
}
```
