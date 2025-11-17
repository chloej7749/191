## Flowchart
https://1drv.ms/i/c/04e020fac6629467/IQCjB-WjlWdqRbFIZAkBwT8rAUOPhfpq4V0pyGya0fRtOZY?e=I2kbFg

## Question
In my opinoin, merge sorting is more confusing than insertion sorting. Merge sorting was definitely slightly harder to grasp with all the different variables, which I found the most difficult part of this lab.

## Video


## Code
``` java
import java.util.Scanner;

public class MergeSort {
    // counts number of comparisons
    static int comparisons = 0;
    public static void merge(int[] numbers, int i, int j, int k) {
        int mergedSize = k - i + 1; // total number of elements (inclusive)
        int mergedNums[] = new int[mergedSize]; // create temp array
        int mergePos = 0;
        int leftPos = i; // left section: i to j
        int rightPos = j+1; // right section: j+1 to k
        
        // while its within each group range
        while(leftPos <= j && rightPos <= k) {
            comparisons ++;
            // looking back into original array
            if (numbers[leftPos] < numbers[rightPos]) {
                // take the lesser of the two
                // if left < right
                mergedNums[mergePos] = numbers[leftPos];
                leftPos ++;
            }
            else {
                // if right < left
                mergedNums[mergePos] = numbers[rightPos];
                rightPos ++ ;
            }
            // increment mergePos 0 -> 1
            mergePos ++;
        }
        // leftovers from left side
        while (leftPos <= j) {
            mergedNums[mergePos] = numbers[leftPos];
            // increment to continue (if more leftovers)
            leftPos++;
            mergePos++;
        }
        while (rightPos <= k) {
            mergedNums[mergePos] = numbers[rightPos];
            rightPos++;
            mergePos++;
        }
        // shift back to original starting point
        for (mergePos = 0; mergePos < mergedSize; mergePos++){
            numbers[i + mergePos] = mergedNums[mergePos];
        }
    }
    // utilizes recursion to sort
    public static void mergeSort(int[] numbers, int i, int k) {
        int j;
        // if not one singular element yet
        if (i < k) {
            j = (i+k) / 2; // finds mp to split in half
            // sort each half
            mergeSort(numbers, i, j);
            mergeSort(numbers, j+1, k);
            // merge all
            merge(numbers, i, j, k);
        }
    }
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);
        System.out.print("Enter array size followed by array: ");
        int size = scnr.nextInt();
        int[] numbers = new int[size];
        // print array
        for (int i = 0; i < size; i++) {
            numbers[i] = scnr.nextInt();
        }
        System.out.print("Unsorted: ");
        // for n in numbers
        for (int n : numbers) {
            System.out.print(n + " ");
        }
        System.out.println();
        mergeSort(numbers, 0, numbers.length-1);
        
        System.out.print("Sorted: ");
        for (int n : numbers) {
            System.out.print(n + " ");
        }
        System.out.println();
        System.out.println("Comparisons: " + comparisons);
    }
}

```
