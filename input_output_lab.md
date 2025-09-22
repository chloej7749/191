## 1. Flowchart:
https://drive.google.com/file/d/1Y9M2p0KgdSavoAHxsEWsJyQh5gwIslrx/view?usp=sharing

## 2. Question:
##### What were your challenges in performing the lab (from design to the implementation phases)?
A challenge in this lab was definitely trying to debug the code. At first, I could not get a successful execution because I didn't place my .txt file in the right place, so I realized
I had to copy the file path in order to make it work. It wasn't a complicated fix, but it did take up some time trying to make the code work.

## 3. Video:
https://1drv.ms/v/c/04e020fac6629467/EYxNxNXSwgpLpW_Q-4-hhRABI6whdK3x6HG46dfkarPQ-w?e=4uzMA8

## 4. Code:
``` java

package com.mycompany.photoorganization;
import java.util.Scanner;
import java.io.IOException;
// reads raw bytes from file
import java.io.FileInputStream;

/**
 *
 * @author chloe
 */
public class PhotoOrganization {
    // IOExection catches errors - may throw exception
    public static void main(String[] args) throws IOException{
        // create input stream that reads from a file -- not System.in (keyboard input)
        // set as null; defined later
        FileInputStream fileByteStream = null;
        
        // Scanner object that reads keyboard input from console for the fileName (photos.txt)
        Scanner scnr = new Scanner(System.in);
        // sets the file name variable equal to the file name the user enters
        String fileName = scnr.nextLine();
        
        
        System.out.println("opening file " + fileName);
        // opens the file photos.txt -> provides byte stream to be read by scanner
        fileByteStream = new FileInputStream(fileName);
        // Scanner allows us to read photos.txt line by line
        Scanner fileScanner = new Scanner(fileByteStream);
        
        // loop executes if there is another line in the file photos.txt
        while (fileScanner.hasNextLine()){
            // sets the name of the photo equal to the line value (e.g. Acadia2003_photo.jpg)
            String photoName = fileScanner.nextLine();
            // if the line is not empty ->
            if (!photoName.isEmpty()){
                // replace _photo.jpg with _info.txt but keep original (e.g. Acadia2003)
                String textName = photoName.replace("photo.jpg", "info.txt");
                // print the replaced value textName
                System.out.println(textName);
            }
        }
        
        System.out.println("Closing file " + fileName);
        // closes stream and releases resources
        fileByteStream.close();
    }
}
```
