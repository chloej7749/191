## FINAL CODE
java:
``` java
import javax.swing.*;
import java.sql.*;

public class Auto {
    // listed database information
    static final String url = "jdbc:mysql://localhost:3306/Auto";
    static final String user = "root";
    static final String password = "mypassword";
    
    public static void main(String[] args) {
        // loads JDBC driver so that MySQL can connect to Java
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            System.out.println("Driver not found.");
            return;
        }
        
        // JFrame popup window
        JFrame frame = new JFrame("Auto Program");
        
        // search button created
        JTextField searchField = new JTextField(10);
        JButton searchButton = new JButton("Search");
        //sliders 
        JSlider mpgSlider = new JSlider(10,50,20);
        JSlider hpSlider = new JSlider(50,250,150);
        
        // creates borders for the sliders
        mpgSlider.setBorder(BorderFactory.createTitledBorder("MPG"));
        hpSlider.setBorder(BorderFactory.createTitledBorder("H-PWR"));
        
        // textbox (not editable)
        JTextArea output = new JTextArea(20,50);
        output.setEditable(false);
        
        // search panel
        JPanel top = new JPanel();
        top.add(new JLabel("User input: "));
        top.add(searchField);
        top.add(searchButton);
        // sliders
        JPanel sliders = new JPanel();
        sliders.add(mpgSlider);
        sliders.add(hpSlider);
        // panels are added: North, Center, South
        frame.add(top, "North");
        frame.add(sliders, "Center");
        frame.add(new JScrollPane(output), "South");
        
        // this allows a button click to activate search
        searchButton.addActionListener(e -> {
            String text = searchField.getText().trim();
            int minMPG = mpgSlider.getValue();
            int maxHP = hpSlider.getValue();
            output.setText("");
            
        // connects to MySQL    
        String line;
        try(Connection connection = DriverManager.getConnection(url, user, password)) {
            // build string for SQL
            line = "SELECT * FROM cars " +
                "WHERE car_name LIKE '%" + text + "%' " + "AND mpg IS NOT NULL AND horsepower IS NOT NULL " + "AND mpg >= " + minMPG + " AND horsepower <= " + maxHP;

            // prints execution to the console
            System.out.println("Info: " + text + ", minMPG = " + minMPG + ", maxH-PWR = " + maxHP);

            // create statement that allows for query executions
            Statement statement = connection.createStatement();
            // gets results from sql
            ResultSet resultset = statement.executeQuery(line);
            
            // prints information to the output box while there is info to be read (next)
            boolean hasResults = false;
            while(resultset.next()) {
                hasResults = true;
                output.append(
                    resultset.getString("car_name") +
                    " MPG: " + resultset.getDouble("mpg") +
                    " H-PWR: " + resultset.getDouble("horsepower") + "\n"
                );
            }
            // prints no results found if nothing can be returned
            if(!hasResults) {
                output.setText("No results found!");
            }
        } catch (Exception exception) {
            output.setText("Error: " + exception.getMessage());
            }
        });

        frame.pack();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }            
}
```

## VIDEO
had to re-record now because i realized the pop up window didn't show up; sorry for late submission
https://1drv.ms/v/c/04e020fac6629467/IQDkolWZ5CbCTJX9kyOalljqAaKFdHVJgnv2RzjcMXetd_E?e=YmPdye
