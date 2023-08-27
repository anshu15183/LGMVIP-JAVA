import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class TicTacToe extends JFrame {
    private JButton[][] buttons;
    private char currentPlayer;
    private Color originalButtonColor;


    public TicTacToe() {
        setupUI();
        initializeGame();
    }

    private void setupUI() {
        setTitle("Tic Tac Toe");
        setSize(300, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        createButtons();
    }

    private void initializeGame() {
        currentPlayer = 'X';
    }

    private void createButtons() {
        buttons = new JButton[3][3];
        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(3, 3));

        for (int row = 0; row < 3; row++) {
            for (int col = 0; col < 3; col++) {
                buttons[row][col] = createButton();
                panel.add(buttons[row][col]);
            }
        }

        add(panel);
    }

    private JButton createButton() {
        JButton button = new JButton("");
        button.setFont(new Font("Arial", Font.PLAIN, 40));
        originalButtonColor = button.getBackground();
        
        button.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                button.setBackground(Color.YELLOW); // Change the color on click
            }
        });

        button.addMouseListener(new java.awt.event.MouseAdapter() {
            @Override
            public void mouseReleased(java.awt.event.MouseEvent e) {
                button.setBackground(originalButtonColor); // Revert to original color on release
            }
        });


        button.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                handleButtonClick(button);
            }
        });

        return button;
    }

    private void handleButtonClick(JButton button) {
        if (button.getText().equals("")) {
            button.setText(String.valueOf(currentPlayer));
            if (checkWin()) {
                showWinMessage(currentPlayer + " wins!");
                restartGame();
            } else if (checkDraw()) {
                showWinMessage("It's a draw!");
                restartGame();
            } else {
                switchPlayer();
            }
        }
    }

    private boolean checkWin() {
        String symbol = String.valueOf(currentPlayer);
    
        // Check rows, columns, and diagonals for a win
        for (int i = 0; i < 3; i++) {
            if (buttons[i][0].getText().equals(symbol) &&
                buttons[i][1].getText().equals(symbol) &&
                buttons[i][2].getText().equals(symbol)) {
                return true; // Row win
            }
            
            if (buttons[0][i].getText().equals(symbol) &&
                buttons[1][i].getText().equals(symbol) &&
                buttons[2][i].getText().equals(symbol)) {
                return true; // Column win
            }
        }
        
        if (buttons[0][0].getText().equals(symbol) &&
            buttons[1][1].getText().equals(symbol) &&
            buttons[2][2].getText().equals(symbol)) {
            return true; // Diagonal win (top-left to bottom-right)
        }
        
        if (buttons[0][2].getText().equals(symbol) &&
            buttons[1][1].getText().equals(symbol) &&
            buttons[2][0].getText().equals(symbol)) {
            return true; // Diagonal win (top-right to bottom-left)
        }
        
        return false;
    }
    
    private boolean checkDraw() {
        for (int row = 0; row < 3; row++) {
            for (int col = 0; col < 3; col++) {
                if (buttons[row][col].getText().equals("")) {
                    return false; // If any cell is empty, the game isn't a draw
                }
            }
        }
        return true; // All cells are filled, indicating a draw
    }

    private void showWinMessage(String message) {
        JOptionPane.showMessageDialog(this, message, "Game Over", JOptionPane.INFORMATION_MESSAGE);
    }

    private void restartGame() {
        clearButtons();
        currentPlayer = 'X';
    }

    private void clearButtons() {
        for (int row = 0; row < 3; row++) {
            for (int col = 0; col < 3; col++) {
                buttons[row][col].setText("");
            }
        }
    }

    private void switchPlayer() {
        currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new TicTacToe().setVisible(true);
            }
        });
    }
}
