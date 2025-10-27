## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/EfnAZmUTyM1OirFK8dCuSvUBwkWSnFNpexFMEpFjfKY18w?e=facvQB

## Question:
I think the most challenging part was actually reading the input correctly using scanner and using the delimiter. At first, I was testing my code and added a testing print statement, but the wor dwould never print, so I had to adjust that with the (add space when done) part. 
I also ended up having to use the Objects class because I entered "abcdefg" and it showed as "yes." I realized it was because it had been reading whether the value types were equal and not the values themselves.
The logic on this lab, however, was fairly simple.

## Video:
https://1drv.ms/v/c/04e020fac6629467/EZhQINalSWdAt1OFJwqkldEBSa6dkmAVMtzsj5ufgOSyeQ?e=m8YRbO

## Code:
``` java
import java.util.LinkedList;
import java.util.Deque;
import java.util.Objects;
import java.util.Scanner;

public class Palindrome {
    public static void main(String[] args) {
        // initiate new Deque of characters called word, using a LinkedList
        Deque<Character> word = new LinkedList<>();
        Scanner scnr = new Scanner(System.in);
        // the custom delimiter using the empty string allows the console to read character by character, rather than by word
        scnr.useDelimiter("");
        // storing the oriignal word to print later
        String originalWord = "";
        
        System.out.print("Enter word (press space to finish): ");
        
        // executes if there's another token in the scanner
        while (scnr.hasNext()){
            // sets inputChar equal to the character its reading
            String inputChar = scnr.next();
            // stores that character as a char, c (instead of string)
            char c = inputChar.charAt(0);
            
            // if character is space (what you should enter after the word), stop the loop -> doesn't execute in the statements below
            if (c == ' ') {
                break;
            }
            // add the character to word (at the end of it)
            word.addLast(c);
            // add the character to the originalWord tracker
            originalWord += c;
            // loop executes again to go to next character
        }
       
        // palindrome is true unless proven false
        boolean checker = true;
        
        // while loop needs to check if the size of the LinkedList is greater than 1, since pollLast() will fail otherwise
        // also if we do all the poll's and get to one character, the loop shouldn't execute anymore
        while (word.size() > 1) {
            // uses Objects class to ensure comparison of values, not value types
            if (!Objects.equals(word.pollFirst(), word.pollLast())){
                // if the first and last characters are not equal, then it is immediately not a palindrome
                checker = false;
            }
        }
        // validates palindrome status
        if (checker == true) {
            System.out.println("Yes, \"" + originalWord + "\" is a palindrome.");
        }
        else {
            System.out.println("No, \"" + originalWord + "\" is not a palindrome.");
        }
        
    scnr.close();   
    }
}
```
