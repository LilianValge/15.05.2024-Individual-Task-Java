```java
/*
Create a simple tic-tac-toe game. Depending on your skills and knowledge.

Game grid should be 3x3. It should be possible for the user to put values in the grid by typing row number and column number.

Easy: Ask user for row and column and write in the two dimensional array a value "1" in the correct place.
Check whether or not the row chosen by user contains all 1.
If all elements in row contain 1, then let player know they won.

*/
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        // Creating a 3x3 grid
        int[][] grid = new int[3][3];
        Scanner scanner = new Scanner(System.in);
        boolean won = false;

        while (!won) {
            printGrid(grid);
            // It should be possible for the user to put values in the grid by typing row number and column number.
            System.out.print("Enter row (0, 1, or 2): ");
            int row = scanner.nextInt();
            System.out.print("Enter column (0, 1, or 2): ");
            int col = scanner.nextInt();

            // Checking whether or not the row chosen by user contains all 1
            if (grid[row][col] != 0) {
                System.out.println("This cell is unfortunately already taken. Please choose a different cell.");
                continue;
            }

            grid[row][col] = 1;
            if (checkWinner(grid)) {
                printGrid(grid);
                System.out.println("Congratulations! You did it, you've just won the game!");
                won = true;
            }
        }
        
        // Closing the scanner
        scanner.close();
    }

    // Printing the current grid
    public static void printGrid(int[][] grid) {
        for (int[] row : grid) {
            for (int cell : row) {
                System.out.print(cell + " ");
            }
            System.out.println();
        }
        System.out.println();
    }

    // Checking if there is a winner
    public static boolean checkWinner(int[][] grid) {
        // Checking rows for winner
        for (int[] row : grid) {
            if (allCellsAreOne(row)) {
                return true;
            }
        }

        // Checking columns for winner
        for (int col = 0; col < 3; col++) {
            boolean win = true;
            for (int row = 0; row < 3; row++) {
                if (grid[row][col] != 1) {
                    win = false;
                    break;
                }
            }
            if (win) {
                return true;
            }
        }

        return false;
    }

    // Helper function to check if all cells in an array are 1
    public static boolean allCellsAreOne(int[] array) {
        for (int cell : array) {
            if (cell != 1) {
                return false;
            }
        }
        return true;
    }
}
```
