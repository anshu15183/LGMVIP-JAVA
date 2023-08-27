package JAVA.MyCurrencyConverter;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class CurrencyConverter extends JFrame implements ActionListener {
    private JComboBox<String> fromCountry, toCountry;
    private JButton convert, reset, exit;
    private JTextField fromText, myResult;

    private String[] currencyUnits = {
            "units" ,"Pakistani Rupee", "US Dollar", "Canadian Dollar", "Hungarian Forint",
            "Euro", "Japanese Yen", "British Pound", "Swiss Franc", "Australian Dollar",
            "Indian Rupee", "Chinese Yuan", "South Korean Won", "Russian Ruble", "Brazilian Real"
    };

    private double[] currencyRates = {
            1.0, 364.04, 1.31, 1.71, 434.18, 1.16, 183.36, 0.85, 0.92, 1.37, 74.47, 6.48, 1729.63, 73.61, 5.44
    };

    public CurrencyConverter() {
        setTitle("Currency Converter");
        setBounds(300, 60, 700, 600);
        getContentPane().setBackground(Color.GRAY);
        setResizable(false);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JLabel title = new JLabel("Currency Converter");
        title.setBounds(150, 30, 400, 60);
        title.setFont(new Font("SansSerif", Font.BOLD, 28));
        title.setForeground(Color.BLACK);
        add(title);

        JLabel from = new JLabel("From");
        from.setBounds(100, 150, 100, 30);
        from.setFont(new Font("Arial", Font.BOLD, 18));
        add(from);

        fromCountry = new JComboBox<>(currencyUnits);
        fromCountry.setBounds(190, 150, 200, 30);
        add(fromCountry);

        fromText = new JTextField();
        fromText.setBounds(410, 150, 120, 30);
        add(fromText);

        JLabel to = new JLabel("To");
        to.setBounds(100, 210, 100, 30);
        to.setFont(new Font("Arial", Font.BOLD, 18));
        add(to);

        toCountry = new JComboBox<>(currencyUnits);
        toCountry.setBounds(190, 210, 200, 30);
        add(toCountry);

        myResult = new JTextField();
        myResult.setBounds(410, 210, 120, 30);
        myResult.setEditable(false);
        add(myResult);

        convert = new JButton("Convert");
        convert.setBounds(180, 280, 100, 30);
        convert.setFont(new Font("Arial", Font.BOLD, 14));
        convert.addActionListener(this);
        add(convert);

        reset = new JButton("Reset");
        reset.setBounds(310, 280, 100, 30);
        reset.setFont(new Font("Arial", Font.BOLD, 14));
        reset.addActionListener(this);
        add(reset);

        exit = new JButton("Exit");
        exit.setBounds(440, 280, 100, 30);
        exit.setFont(new Font("Arial", Font.BOLD, 14));
        exit.addActionListener(this);
        add(exit);

        setLayout(null);
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == convert) {
            try {
                double inputValue = Double.parseDouble(fromText.getText());
                double result = convertCurrency(inputValue, fromCountry.getSelectedIndex(), toCountry.getSelectedIndex());
                myResult.setText(String.format("%.2f", result));
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Please enter a valid numeric amount.");
            }
        } else if (e.getSource() == reset) {
            fromCountry.setSelectedIndex(0);
            toCountry.setSelectedIndex(0);
            fromText.setText("");
            myResult.setText("");
        } else if (e.getSource() == exit) {
            System.exit(0);
        }
    }

    private double convertCurrency(double amount, int fromIndex, int toIndex) {
        double fromRate = currencyRates[fromIndex];
        double toRate = currencyRates[toIndex];
        return (amount / fromRate) * toRate;
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> new CurrencyConverter());
    }
}
