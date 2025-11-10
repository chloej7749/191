## Flowchart:
https://1drv.ms/i/c/04e020fac6629467/EYVNvO3TkXlHkc2rPH0olL8BRE6DZbYIqhPrV2Sqj7jtwA?e=fQ7g6c

## Question:
The most difficult part of this code was definitely also grasping what each part ment and how it came together to function as an interactive interface.
I think that although there is a lot of code, most of it is repetitive, especially since this lab converts from mi -> km, m, and feet. Overall, though, the material was easy with the guidance from the lecture

## Video:
https://1drv.ms/v/c/04e020fac6629467/ERTkLOMLCyVOlGkT47MIcdYBdL18zkErRIGc0cIWCQ5n3w?e=a0627w

## Code:
``` java:
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.NumberFormat;
import javax.swing.JButton;
import javax.swing.JFormattedTextField;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTextField;

public class DistanceConverter extends JFrame implements ActionListener {
    private JButton calcButton;
    private JLabel distLabel;
    private JLabel kmDistLabel;
    private JLabel mDistLabel;
    private JLabel ftDistLabel;
    private JTextField kmDistField;
    private JTextField mDistField;
    private JTextField ftDistField;
    private JFormattedTextField distField;
    
    // constructor
    DistanceConverter() {
        GridBagConstraints layoutConst = null;
        
        setTitle("Distance Convertor");
        
        distLabel = new JLabel("Distance (mi): ");
        kmDistLabel = new JLabel("Distance (km): ");
        mDistLabel = new JLabel("Distance (m): ");
        ftDistLabel = new JLabel("Distance (ft): ");
        
        // button (action) that calculates value when pushed
        calcButton = new JButton("Calculate");
        calcButton.addActionListener(this);
        
        // kilometer field
        kmDistField = new JTextField(15);
        kmDistField.setEditable(false);
        
        // meter field
        mDistField = new JTextField(15);
        mDistField.setEditable(false);
       
        // feet field
        ftDistField = new JTextField(15);
        ftDistField.setEditable(false);
        
        // regular distance field; formattedtextfield has restrictions
        distField = new JFormattedTextField(NumberFormat.getNumberInstance());
        distField.setEditable(true);
        distField.setText("0");
        distField.setColumns(15);
        
        setLayout(new GridBagLayout());
        
        // distance label
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,10,10,1);
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(distLabel, layoutConst);
        
        // distance field/box
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,1,10,10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(distField, layoutConst);
        
        // calculator button
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,5,10,10);
        layoutConst.gridx = 2;
        layoutConst.gridy = 0;
        add(calcButton, layoutConst);
        
        // km label
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,0,1,10);
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        add(kmDistLabel, layoutConst);
        
        // km field/box
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1,0,10,10);
        layoutConst.gridx = 0;
        layoutConst.gridy = 2;
        add(kmDistField, layoutConst);
        
        // m label
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,0,1,10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(mDistLabel, layoutConst);
        
        // m field/box
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1,0,10,10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 2;
        add(mDistField, layoutConst);
        
        // ft label
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10,0,1,10);
        layoutConst.gridx = 2;
        layoutConst.gridy = 1;
        add(ftDistLabel, layoutConst);
        
        // ft field/box
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1,0,10,10);
        layoutConst.gridx = 2;
        layoutConst.gridy = 2;
        add(ftDistField, layoutConst);
    }
    
    // overriding original actionPerformed - button clicking
    @Override
    public void actionPerformed(ActionEvent event) {
        double distMiles;
        double distKM;
        double distM;
        double distFT;
        
        distMiles = ((Number) distField.getValue()).doubleValue();
        
        // if the input (in the original editable box) is positive
        if (distMiles >= 0.0) {
            distKM = distMiles * 1.609;
            distM = distMiles * 1609.34;
            distFT = distMiles * 5280;
            
            // convert double to string to display
            kmDistField.setText(Double.toString(distKM));
            mDistField.setText(Double.toString(distM));
            ftDistField.setText(Double.toString(distFT));
        }
        // if negative, print popup error message
        else {
            JOptionPane.showMessageDialog(this, "Enter a positive distance.");
        }
    }
    
    public static void main(String[] args) {
        DistanceConverter myFrame = new DistanceConverter();
        
        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```
