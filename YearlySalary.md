## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/EchxpYzlzxxLuqITzH4IiWIBdlN0C6AW_Uhq9cHoHSg1xQ?e=Guwbh2

## Question:
This was the first GUI lab that I completed, so everyting was still very confusing to me, and I was especially surprised by the upsurge in the amount of code. It was difficult understanding
all the formatting and syntax that comes with creating these frames, but I was able to understand how everything worked.

## Video:
https://1drv.ms/v/c/04e020fac6629467/ETWTRZrnEShKpZi5dYXXHGABkiBs7drZieRnL2cZAVberA?e=fLreXS

## Code:
``` java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

// uses actionlistener (enter key)
public class YearlySalary extends JFrame implements ActionListener {
    private JLabel wageLabel;
    private JLabel hourLabel;
    private JLabel salLabel;
    private JTextField wageField;
    private JTextField hourField;
    private JTextField salField;
    
    YearlySalary() {
        GridBagConstraints layoutConst = null;
        
        // set title of frame
        setTitle("Yearly Salary");
        
        // set label titles
        wageLabel = new JLabel("Hourly wage: ");
        hourLabel = new JLabel("Hours per week: ");
        salLabel = new JLabel("Yearly salary: ");
        
        // want user to edit wage amount
        wageField = new JTextField(15);
        wageField.setEditable(true);
        wageField.setText("0");
        wageField.addActionListener(this);
        
        // want user to edit hours per week number
        hourField = new JTextField(15);
        hourField.setEditable(true);
        hourField.setText("0");
        hourField.addActionListener(this);
        
        // don't want user to edit calculated salary value
        salField = new JTextField(15);
        salField.setEditable(false);
        
        setLayout(new GridBagLayout());
        
        // displays wage title
        layoutConst = new GridBagConstraints();
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        layoutConst.insets = new Insets(10,10,10,10);
        add(wageLabel, layoutConst);
        
        // displays wage box
        layoutConst = new GridBagConstraints();
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        layoutConst.insets = new Insets(10,10,10,10);
        add(wageField, layoutConst);
        
        // displays hours per week title
        layoutConst = new GridBagConstraints();
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        layoutConst.insets = new Insets(10,10,10,10);
        add(hourLabel, layoutConst);
        
        // displays hours per week box
        layoutConst = new GridBagConstraints();
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        layoutConst.insets = new Insets(10,10,10,10);
        add(hourField, layoutConst);
        
        // displays salary title
        layoutConst = new GridBagConstraints();
        layoutConst.gridx = 0;
        layoutConst.gridy = 2;
        layoutConst.insets = new Insets(10,10,10,10);
        add(salLabel, layoutConst);
        
        // displays salary box
        layoutConst = new GridBagConstraints();
        layoutConst.gridx = 1;
        layoutConst.gridy = 2;
        layoutConst.insets = new Insets(10,10,10,10);
        add(salField, layoutConst);
    }
    
    // overrides actionPerformed (implemented, extends JFrame)
    @Override
    public void actionPerformed(ActionEvent event) {
        String userWage;
        String userHours;
        int hourlyWage;
        int hoursPerWeek;
        
        // convert to integer
        userWage = wageField.getText();
        hourlyWage = Integer.parseInt(userWage);
        userHours = hourField.getText();
        hoursPerWeek = Integer.parseInt(userHours);
        
        // calculate salary based on 52 weeks
        salField.setText(Integer.toString(hourlyWage * hoursPerWeek * 52));
    }
    
    public static void main(String[] args) {
        YearlySalary myFrame = new YearlySalary();
        
        // show frame on user end
        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```
