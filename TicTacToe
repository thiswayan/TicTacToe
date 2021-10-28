import java.util.*;

public class TicTacToe {

    private static final String COMPUTER = "Computer", PLAYER = "Player";
    private static List<List> winningPositions;
    private static List<Integer> playerPositions;
    private static List<Integer> computerPositions;
    private static Random random;
    private static char[][] gameBoard;

    public static void main(String[] args) {
        setUpGameBoard();
        init();
        playGame();
    }

    private static void setUpGameBoard() {
        gameBoard = new char[][]{{' ', '|', ' ', '|', ' '},
                {'-', '+', '-', '+', '-'},
                {' ', '|', ' ', '|', ' '},
                {'-', '+', '-', '+', '-'},
                {' ', '|', ' ', '|', ' '}
        };
    }

    private static void init() {

        winningPositions = new ArrayList<>();
        playerPositions = new ArrayList<>();
        computerPositions = new ArrayList<>();
        random = new Random();

        List topRow = Arrays.asList(1, 2, 3);
        List middleRow = Arrays.asList(4, 5, 6);
        List bottomRow = Arrays.asList(7, 8, 9);
        List leftColumn = Arrays.asList(1, 4, 7);
        List middleColumn = Arrays.asList(2, 5, 8);
        List rightColumn = Arrays.asList(3, 6, 9);
        List leftDiagonal = Arrays.asList(1, 5, 9);
        List rightDiagonal = Arrays.asList(3, 5, 7);

        winningPositions.add(topRow);
        winningPositions.add(middleRow);
        winningPositions.add(bottomRow);
        winningPositions.add(leftColumn);
        winningPositions.add(middleColumn);
        winningPositions.add(rightColumn);
        winningPositions.add(leftDiagonal);
        winningPositions.add(rightDiagonal);
    }

    private static void playGame() {

        int playersTurn = random.nextInt(2) + 1;
        char firstMove;
        if (playersTurn == 1) {
            firstMove = 'P';
            playersTurn();
        } else {
            firstMove = 'C';
            computersTurn();
        }
        
        while (true) {
            if (firstMove == 'P') {
                computersTurn();
                playersTurn();
            } else {
                playersTurn();
                computersTurn();
            }
        }
    }

    private static void playersTurn() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter your position : (1-9)");

        int playerPosition = scanner.nextInt();
        while (playerPositions.contains(playerPosition) || computerPositions.contains(playerPosition) ||
                !(playerPosition >= 1 && playerPosition <= 9)) {
            System.out.println("Position enter a valid position: ");
            playerPosition = scanner.nextInt();
        }
        placePiece(playerPosition, PLAYER, gameBoard);
        printGameBoard(gameBoard, PLAYER);

        int result = isGameFinished();
        if (result != -1) {
            printResult(result);
        }
    }

    private static void computersTurn() {
        int computerPosition = random.nextInt(9) + 1;
        while (playerPositions.contains(computerPosition) || computerPositions.contains(computerPosition)) {
            computerPosition = random.nextInt(9) + 1;
        }
        placePiece(computerPosition, COMPUTER, gameBoard);
        printGameBoard(gameBoard, COMPUTER);

        int result = isGameFinished();
        if (result != -1) {
            printResult(result);
        }
    }

    private static void printGameBoard(char[][] gameBoard, String user) {
        if (user.equalsIgnoreCase("player")) {
            System.out.println("Player's Move : ");
        } else {
            System.out.println("Computer's Move : ");
        }

        System.out.println();

        for (char[] row : gameBoard) {
            for (char c : row) {
                System.out.print(c);
            }
            System.out.println();
        }

        System.out.println();
        System.out.println("-+-+-+-+-+-+-");
        System.out.println();
    }

    private static void placePiece(int position, String user, char[][] gameBoard) {
        char symbol;

        if (user.equalsIgnoreCase("player")) {
            symbol = 'X';
            playerPositions.add(position);
        } else {
            symbol = 'O';
            computerPositions.add(position);
        }

        switch (position) {
            case 1:
                gameBoard[0][0] = symbol;
                break;
            case 2:
                gameBoard[0][2] = symbol;
                break;
            case 3:
                gameBoard[0][4] = symbol;
                break;
            case 4:
                gameBoard[2][0] = symbol;
                break;
            case 5:
                gameBoard[2][2] = symbol;
                break;
            case 6:
                gameBoard[2][4] = symbol;
                break;
            case 7:
                gameBoard[4][0] = symbol;
                break;
            case 8:
                gameBoard[4][2] = symbol;
                break;
            case 9:
                gameBoard[4][4] = symbol;
                break;
            default:
                System.out.println("Please Enter a valid position");
                break;
        }
    }

    private static int isGameFinished() {
        for (List position : winningPositions) {
            if (playerPositions.containsAll(position)) {
                return 1;
            } else if (computerPositions.containsAll(position)) {
                return 2;
            }
        }
        if (playerPositions.size() + computerPositions.size() == 9)
            return 0;
        return -1;
    }

    private static void printResult(int result) {
        switch (result) {
            case 1:
                System.out.println("Yay, you win !!");
                break;
            case 2:
                System.out.println("Shoot, hard luck !!");
                break;
            case 0:
                System.out.println("It's a tie !!");
                break;
            default:
                break;
        }
        System.out.println("Do you want to play again ? Y / N");
        Scanner scanner = new Scanner(System.in);
        String input = scanner.next();
        if (input.equalsIgnoreCase("Y")) {
            resetGameBoard();
        } else {
            System.exit(0);
        }
    }

    private static void resetGameBoard() {
        setUpGameBoard();
        playerPositions.clear();
        computerPositions.clear();
    }
}
