## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/EYXXdceRqNpEqKjg9Ljw4BAB3CPNrkWlut05yDaCCiBXEg?e=X5nnx3

## Question:
I think the challenging part in this lab was combining Scanner with the other factors. I had to figure out how to get the code to line up with the expected input, so it could print the expected output. This meant I needed to have a Course object and OfferedCourse object because the expected object had both.

## Video:
https://1drv.ms/v/c/04e020fac6629467/ES85Hz4TrQ5Epg-uN0Pu4ZQBRYU-7pVEkBD9PkAqDdRPSw?e=pa24fu

## Code:
**CourseInformation.java**
``` java
import java.util.Scanner;

public class CourseInformation {

    public static void main(String[] args) {
        // create new object newCourse of type OfferedCourse - which extends the Course class
        Course newCourse = new Course();
        OfferedCourse newOfferedCourse = new OfferedCourse();
        Scanner scnr = new Scanner(System.in);
        
        // set input values for regular course
        newCourse.storeCourseNum(scnr.nextLine());
        newCourse.storeCourseTitle(scnr.nextLine());
        // set input values for offered course
        newOfferedCourse.storeCourseNum(scnr.nextLine());
        newOfferedCourse.storeCourseTitle(scnr.nextLine());
        newOfferedCourse.storeCourseInstructor(scnr.nextLine());
        newOfferedCourse.storeCourseLocation(scnr.nextLine());
        newOfferedCourse.storeCourseTime(scnr.nextLine());
        
        // call method that prints course number and title
        newCourse.printInfo();
        newOfferedCourse.printInfo();
        
        // print course instructor/location/time using defined get methods - for OfferedCourse
        System.out.println("\t Instructor Name: " + newOfferedCourse.getInstructor());
        System.out.println("\t Location: " + newOfferedCourse.getLocation());
        System.out.println("\t Class Time: " + newOfferedCourse.getTime());

        scnr.close();
    }
}

```
**Course.java**
``` java
public class Course {
    private String courseNum;
    private String courseTitle;
    
    // method storeCourseNum takes input num and stores it in variable courseNum
    public void storeCourseNum(String num) {
        courseNum = num;
    }
    
    // method storeCourseTitle takes input title and stores it in variable courseTitle
    public void storeCourseTitle(String title) {
        courseTitle = title;
    }
    
    // method printInfo prints the course number and title when called
    public void printInfo(){
        System.out.println("Course Information: ");
        System.out.println("\t Course number: " + courseNum);
        System.out.println("\t Course title: " + courseTitle);
    } 
}
```
**OfferedCourse.java**
``` java
// subclass OfferedCourse that inherits methods from Course
public class OfferedCourse extends Course {
    private String instructorName;
    private String classLocation;
    private String classTime;
    
    // method storeCourseInstructor that takes input instructor and stores it in variable instructorName
    public void storeCourseInstructor(String instructor){
        instructorName = instructor;
    }
    
    // method storeCourseLocation that takes input location and stores it in variable classLocation
    public void storeCourseLocation(String location) {
        classLocation = location;
    }
    
    // method storeCourseTime that takes input time and stores it in variable classTime
    public void storeCourseTime(String time) {
        classTime = time;
    }
    
    // getInstructor/Location/Time methods that return values dictated above; used for printing into console
    public String getInstructor(){
        return instructorName;
    }
    public String getLocation(){
        return classLocation;
    }
    public String getTime(){
        return classTime;
    }
}
```
