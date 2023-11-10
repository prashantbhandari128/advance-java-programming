## Write a GUI application to find sum and difference of two integer numbers. Use two text fields for input and third text field for output. Your program should display sum if the users presses the mouse and difference if the users releases the mouse

```Java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class SimpleSwingCalculator {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Simple Swing Calculator");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 200);
        frame.setLayout(new GridLayout(4, 2));
        JTextField numField1 = new JTextField();
        JTextField numField2 = new JTextField();
        JTextField resultField = new JTextField();
        resultField.setEditable(false);
        frame.add(new JLabel("Number 1:"));
        frame.add(numField1);
        frame.add(new JLabel("Number 2:"));
        frame.add(numField2);
        frame.add(new JLabel("Result:"));
        frame.add(resultField);
        frame.setVisible(true);
        frame.addMouseListener(new MouseAdapter() {
            @Override
            public void mousePressed(MouseEvent e) {
                try {
                    int num1 = Integer.parseInt(numField1.getText());
                    int num2 = Integer.parseInt(numField2.getText());
                    int sum = num1 + num2;
                    resultField.setText("Sum: " + sum);
                } catch (NumberFormatException ex) {
                    resultField.setText("Invalid input");
                }
            }

            @Override
            public void mouseReleased(MouseEvent e) {
                try {
                    int num1 = Integer.parseInt(numField1.getText());
                    int num2 = Integer.parseInt(numField2.getText());
                    int diff = num1 - num2;
                    resultField.setText("Difference: " + diff);
                } catch (NumberFormatException ex) {
                    resultField.setText("Invalid input");
                }
            }
        });
    }
}
```