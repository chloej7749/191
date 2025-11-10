## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/EQb8u1nMqMFOkupWQ7r-FSABK7yK1mtN4Y0HwyHJzcngqQ?e=qWFA3m

## Question:
The most difficult part of this lab was just understanding the spinner syntax and getting used to GUI. There was a lot of code involved in this (slightly overwhelming), and the lecture was a great
resource that I used for assistance in this lab.

## Video:
https://1drv.ms/v/c/04e020fac6629467/EYla2rOhVItDjbwEx6bn6RUBLv2HLb7GYONHgf1yWRqWIA?e=mFJwe1

## Code:
``` java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JSpinner;
import javax.swing.JTextField;
import javax.swing.SpinnerModel;
import javax.swing.SpinnerNumberModel;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;

public class DistanceToKm extends JFrame implements ChangeListener {
    private JSpinner milesSpinner;
    private JTextField kmDistField;
    private JLabel miLabel;
    private JLabel kmLabel;
    
    // constructor
    DistanceToKm() {
        // variable initializers
        int initDist;
        int minDist;
        int maxDist;
        int stepVal;
        Object spinnerModel;
        
        initDist = 0;
        minDist = 0;
        maxDist = 100;
        stepVal = 10;
        
        GridBagConstraints layoutConst = null;
        
        setTitle("Distance (mi to km) Converter");
        
        miLabel = new JLabel("Select distance in miles (max 100): ");
        kmLabel = new JLabel("Distance (km): ");
        
        // spinner model to select distances in miles (increment by 10 from 0-100)
        spinnerModel = new SpinnerNumberModel(initDist, minDist, maxDist, stepVal);
        milesSpinner = new JSpinner((SpinnerModel) spinnerModel);
        milesSpinner.addChangeListener(this);
        
        // field that shows kilometers (calculated)
        kmDistField = new JTextField(15);
        kmDistField.setEditable(false);
        kmDistField.setText("0");
        
        setLayout(new GridBagLayout());
        
        // text label for miles
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,10,10,10);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(miLabel, layoutConst);
        
        // text label for kilometers
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,10,10,10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(kmLabel, layoutConst);
        
        // spinner box for selecting miles
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,10,10,10);
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        add(milesSpinner, layoutConst);
        
        
        // field for displaying kilometer distance
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,10,10,10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(kmDistField, layoutConst);
    }
    
    @Override
    // using ChangeEvent to change between different mile values
    public void stateChanged(ChangeEvent e) {
        Integer distMiles;
        // get integer value from spinner and set it equal to distMiles
        distMiles = (Integer) milesSpinner.getValue();
        
        // switch-case to show different kilometers based on different miles inputs (increemnt by 10)
        switch(distMiles) {
            case 0:
                kmDistField.setText("0");
                break;
            case 10:
                kmDistField.setText("16.0934");
                break;
            case 20:
                kmDistField.setText("32.1869");
                break;
            case 30:
                kmDistField.setText("48.2803");
                break;
            case 40:
                kmDistField.setText("64.3738");
                break;
            case 50:
                kmDistField.setText("80.4672");
                break;
            case 60:
                kmDistField.setText("96.5606");
                break;
            case 70:
                kmDistField.setText("112.654");
                break;
            case 80:
                kmDistField.setText("128.748");
                break;
            case 90:
                kmDistField.setText("144.841");
                break;
            case 100:
                kmDistField.setText("160.934");
                break;
            default:
                // calculation for kilometers, converting double to string
                double input = distMiles * 1.609;
                String str = Double.toString(input);
                kmDistField.setText(str);
        }
    }
    
    public static void main(String[] args) {
        // instantiate to create frame
        DistanceToKm myFrame = new DistanceToKm();
        
        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
    
}

```
