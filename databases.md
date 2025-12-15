## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/IQAaDcJl_-_HTI_SQzaTfXazAThlG7g1pKL4oT1QyWya-LI?e=fvKP8W

## Question:
I think the most challenging part of this lab was understanding how SQL worked because I found it a slightly confusing topic. I also had to get my computer to cooperate which took a long time.

## Video:
https://1drv.ms/v/c/04e020fac6629467/IQDzLeqAHVGUTZ0Wh_d8Mwr8AXwqauEF9e4nlBdKE6RNz5c?e=jScvsI

## Code:
``` sql
USE Miramar;
CREATE TABLE Student (
    ssn VARCHAR(9) PRIMARY KEY,
    firstName VARCHAR(50),
    middleName VARCHAR(50),
    lastName VARCHAR(50),
    dob DATE,
    street VARCHAR(100),
    phone VARCHAR(20),
    zipcode VARCHAR(10),
    deptID INT
);
```

``` java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.miramarstudent;

/**
 *
 * @author chloe
 */
import java.sql.*;

public class MiramarStudent {
    public static void main(String[] args) throws SQLException, ClassNotFoundException {
        // loads the MySQL JDBC driver
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver loaded.");
        
        // establish connection with database (user: testuser, password: Pa$$word)
        Connection connection = DriverManager.getConnection(
                "jdbc:mysql://localhost/Miramar",
                "testuser",
                "Pa$$word"
        );
        System.out.println("Database connected");
        
        // create statement to execute SQL statements
        Statement statement = connection.createStatement();
        // insert a new student with info
        String insertSQL = 
                "INSERT INTO Student " +
                "(ssn, firstName, middleName, lastName, dob, street, phone, zipcode, deptID) " +
                "VALUES ('111222333', 'Philip', 'David Charles', 'Collins', " +
                "'1951-01-30', 'NA', 'NA', 'NA', 1234)";
        statement.executeUpdate(insertSQL);
        System.out.println("Student record inserted.");
        
        // updating zipcode
        String updateSQL = 
                "UPDATE Student SET zipCode = '92126' WHERE ssn = '111222333'";
        statement.executeUpdate(updateSQL);
        System.out.println("Zipcode updated.");
        
        // execute statement; allows manipulation of table data
        ResultSet resultSet = statement.executeQuery(
                "SELECT * FROM Student WHERE ssn = '111222333'"
        );
        
        // printing information
        while(resultSet.next()) {
            System.out.println(
                resultSet.getString("ssn") + "\t" +
                resultSet.getString("firstName") + "\t" +
                resultSet.getString("middleName") + "\t" +
                resultSet.getString("lastName") + "\t" +
                resultSet.getString("dob") + "\t" +
                resultSet.getString("street") + "\t" +
                resultSet.getString("phone") + "\t" +
                resultSet.getString("zipcode") + "\t" +
                resultSet.getString("deptID")
            );
        }
        
        // close connection
        connection.close();
        System.out.println("Database connection closed.");
    }
}
```
