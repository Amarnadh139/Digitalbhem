import java.util.Random;
import java.util.Scanner;

public class GuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        System.out.println("Welcome to the Guessing Game!");
        System.out.println("Try to guess the number between 1 and 100.");

        int randomNumber = random.nextInt(100) + 1;
        int userScore = 0;
        int maxAttempts = 10;

        for (int attempt = 1; attempt <= maxAttempts; attempt++) {
            System.out.print("Attempt " + attempt + ": Enter your guess: ");
            int userGuess = scanner.nextInt();

            if (userGuess < 1 || userGuess > 100) {
                System.out.println("Please enter a number between 1 and 100.");
                attempt--; // Don't count this invalid attempt
                continue;
            }

            if (userGuess == randomNumber) {
                System.out.println("Congratulations! You guessed the correct number.");
                userScore += 10; // You can adjust the scoring system as needed
                break;
            } else if (userGuess < randomNumber) {
                System.out.println("Too low. Try again.");
            } else {
                System.out.println("Too high. Try again.");
            }
        }

        System.out.println("Game over. The correct number was: " + randomNumber);
        System.out.println("Your score: " + userScore);
        
        scanner.close();
    }
}
