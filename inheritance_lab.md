## Flowchart:


## Question:
This lab wasn't very challenging, especially given the partial code. I think the most challenging thing would have been just understanding the concept of inheritance and learning how to apply it in this 
situation, which shortens the code.

## Video:


## Code:
**StudentDerivationFromPerson.java**
``` java
public class StudentDerivationFromPerson {
   public static void main(String[] args) {
      // Student inherited methods of Person
      Student courseStudent = new Student();

      /* Your solution goes here  */
      // uses setID method from Student.java
      courseStudent.setID(9999);
      // uses setName and setAge method from Student.java inherited from Person.java
      courseStudent.setName("Smith");
      courseStudent.setAge(20);
      
      // uses printAll method (inherited) to print name + age
      courseStudent.printAll();
      System.out.println(", ID: " + courseStudent.getID());
      
   }
}
```
**Person.java** (given)
``` java
public class Person {
   private int ageYears;
   private String lastName;

   // void method setName that sets lastName equal to user input userName
   public void setName(String userName) {
      lastName  = userName;
   }
   
   // void method setAge that sets ageYears equal to user input numYears
   public void setAge(int numYears) {
      ageYears = numYears;
   }

   // prints name and age of user based on user input
   public void printAll() {
      System.out.print("Name: " + lastName);
      System.out.print(", Age: "  + ageYears);
   }
}
```
**Student.java** (given)
``` java
// inherits all methods of the Person class
public class Student extends Person {
   private int idNum;

   // void method that sets idNum equal to user input studentId
   public void setID(int studentId) {
      idNum = studentId;
   }

   // method that gives the user idNum when called (later used to print the ID number)
   public int getID() {
      return idNum;
   }
}
```
