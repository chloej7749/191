# Library Builder

## 1. Flowchart 
https://drive.google.com/file/d/1NaLj-tZ010sLkCf41pl5h29f5XHMYY9A/view?usp=sharing

## 2. Question
I think the hardest part of the lab was implementing the new information into the code. It is always used without us really knowing about it, but now we are more aware of stacks, heaps, and the GC.
The most difficult part was understanding how these parts worked together, but was definitely made easier by visualizing it through documentation and comments. Since the files gave us, in a sense, a
"template" or "model" to use, the process was made easier and I also understood the principles better.



## 3. Video
correction: garbage collector "reclaims" is more appropriate \
https://1drv.ms/v/c/04e020fac6629467/ETer7v2yEOBBl-BfZOuIDP8BSXkWGigVWD5nl3NHyTTK6w?e=9HhGdP

## 4. Code
I wrote the requirements listed in "expected outputs" in the comments:
```java

package com.mycompany.librarybuilder;

/**
 *
 * @author chloe
 */
class Book {
    String title;
    String author;
    int pages;
    
    // constructor for creating objects of Book type
    public Book(String title, String author, int pages){
        this.title = title;
        this.author = author;
        this.pages = pages;
    }
    
    // method, when called, prints book information
    public void showBook(){
        System.out.println("Title: " + title + " by " + author + "(Pages: " + pages + ")");
    }
}
public class LibraryBuilder {
    // private method: addBook is only used in this LibraryBuilder class
    // initializes newBook using constructor
    private static Book addBook(String title, String author, int pages){
        Book newBook = new Book(title, author, pages);
        return newBook;
    }

    public static void main(String[] args) {
        String title1 = "Harry Potter and the Half Blood Prince";
        String author1 = "J. K. Rowling";
        int pages1 = 607;
        // book1 object exists, but has no value
        Book book1 = null;
        book1 = addBook(title1, author1, pages1);
        // stack: book1 
        // heap: book1 (HP & HBP)
        // heap has: [Book object] - book1: {title = "Harry....", author = "J. K...", pages: 607}
        
        String title2 = "The Hunchback of Notre-Dame";
        String author2 = "Victor Hugo";
        int pages2 = 528;
        Book book2 = null;
        book2 = addBook(title2, author2, pages2);
        // stack: book1 & book2
        // heap: book1 (HP & HBP), book2 (Hunchback)
        
        String title3 = "The Color Purple";
        String author3 = "Alice Walker";
        int pages3 = 304;
        Book book3 = null;
        book3 = addBook(title3, author3, pages3);
        // stack: book1, book2, book3
        // heap: book1 (HP & HBP), book2 (Hunchback), book3 (Color Purple)
         
        book3 = book2; // book3 now references hunchback instead of color purple
        // stack: book1, book2, book3
        // heap: book1 (HP & HBP), book2 & book3 (Hunchback), book3 (Color Purple) - unreachable, eligible for garbage collector which reclaims memory (since it is unreachable)
        
        book1.showBook(); // hp
        book2.showBook(); // hunchback
        book3.showBook(); // hunchback
    }
}
```
