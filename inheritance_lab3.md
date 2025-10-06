## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/Ee3hLpUT2VxFi1v5GDbu3DMB2iyBzZeRGyVVXrdbAAplGQ?e=25IMJe

## Question:
Similar to the other lab, the most challenging part of this was implementing Scanner. Luckily with experience on lab 2, this wasn't _too_ hard. Another challenging part was understanding how @Override and
polymorphism were incorporated into the code. It was fascinating to see two methods of the same name be eexecuted diffrently based on the object they were acting on.

## Video:
https://1drv.ms/v/c/04e020fac6629467/ETkb_Di6DxtAoHt9gimoM4cBWCWYmiDg2TLb4urE0N2JSw?e=eSgfdc

## Code:
**BookInformation.java**
``` java
import java.util.Scanner; 


public class BookInformation {

    public static void main(String[] args) {
        // declare new object newBook for regular book: type Book
        Book newBook = new Book();
        // declare new object newEnc for encyclopedia: type Encyclopedia
        Encyclopedia newEnc = new Encyclopedia();
        Scanner scnr = new Scanner(System.in);
        
        // store information for regular book using scanner
        newBook.storeBookTitle(scnr.nextLine());
        newBook.storeBookAuthor(scnr.nextLine());
        newBook.storeBookPublisher(scnr.nextLine());
        newBook.storeBookPubDate(scnr.nextLine());
        
        // store information for encyclopedia using scanner (contains edition and numPages)
        newEnc.storeBookTitle(scnr.nextLine());
        newEnc.storeBookAuthor(scnr.nextLine());
        newEnc.storeBookPublisher(scnr.nextLine());
        newEnc.storeBookPubDate(scnr.nextLine());
        newEnc.storeBookEdition(scnr.nextLine());
        newEnc.storeBookNumPages(scnr.nextInt());

        // print information for new book
        newBook.printInfo();
        /* print information for encyclopedia: same method name as previous line, but overrided for encyclopedia
        more information in Encyclopedia.java
        */
        newEnc.printInfo();

        scnr.close();
    }
}
```
**Book.java**
``` java
public class Book {
    private String bookTitle;
    private String bookAuthor;
    private String bookPublisher;
    private String bookPubDate;
    
    public void storeBookTitle(String title){
        bookTitle = title;
    }
    
    public void storeBookAuthor(String author){
        bookAuthor = author;
    }
    
    public void storeBookPublisher(String publisher){
        bookPublisher = publisher;
    }
    
    public void storeBookPubDate(String pubDate){
        bookPubDate = pubDate;
    }
    
    public String getBookTitle(){
        return bookTitle;
    }
    
    public String getBookAuthor(){
        return bookAuthor;
    }
    
    public String getBookPublisher(){
        return bookPublisher;
    }
    
    public String getBookPubDate(){
        return bookPubDate;
    }
    
    public void printInfo(){
        System.out.println("Book Information: ");
        System.out.println("\t Book Title: " + bookTitle);
        System.out.println("\t Author: " + bookAuthor);
        System.out.println("\t Publisher: " + bookPublisher);
        System.out.println("\t Publication Date: " + bookPubDate);
    }
}
```
**Encyclopedia.java**
```java
// subclass of Book class
public class Encyclopedia extends Book {
    private String edition;
    private int numPages;
    
    // method that stores inputted edition
    public void storeBookEdition(String editionNum){
        edition = editionNum;
    }
    
    // method that stores inputted number of pages
    public void storeBookNumPages(int pages){
        numPages = pages;
    }
    
    // method that returns the stored edition
    public String getEdition(){
        return edition;
    }
    
    // method that returns the stored numPages
    public int getPages(){
        return numPages;
    }
  
    // checks during compilation - tells computer that override is about to happen
    @Override
    // same name: printInfo() as superclass, but overrides the other as part of Encyclopedia class
    public void printInfo(){
        System.out.println("Book Information: ");
        System.out.println("\t Book Title: " + getBookTitle());
        System.out.println("\t Author: " + getBookAuthor());
        System.out.println("\t Publisher: " + getBookPublisher());
        System.out.println("\t Publication Date: " + getBookPubDate());
        System.out.println("\t Edition: " + edition);
        System.out.println("\t Number of Pages: " + numPages);
    }
}
```
