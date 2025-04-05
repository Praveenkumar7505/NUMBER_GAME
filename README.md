# NUMBER_GAME
//THIS GAME IS GUESS LIKE  54 TOO LESS , 90 TOO HIGH TOTAL 5 ATTEMPTS


import java.util.Random;
import java.util.Scanner;

public class NumberGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        boolean playAgain = true;
        int totalScore = 0;
        
        System.out.println("Welcome to the Number Guessing Game!");
        
        while (playAgain) {
            int numberToGuess = random.nextInt(100) + 1; // Random number between 1 and 100
            int attempts = 5; // Limit the number of attempts
            boolean guessedCorrectly = false;
            
            System.out.println("\nI have selected a number between 1 and 100. You have " + attempts + " attempts to guess it.");

            while (attempts > 0) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts--;

                if (userGuess == numberToGuess) {
                    System.out.println("Congratulations! You guessed the number correctly.");
                    totalScore += attempts + 1; // More points for fewer attempts
                    guessedCorrectly = true;
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
                
                System.out.println("Attempts left: " + attempts);
            }
            
            if (!guessedCorrectly) {
                System.out.println("Sorry, you ran out of attempts. The correct number was: " + numberToGuess);
            }

            System.out.println("Your current score: " + totalScore);
            System.out.print("Do you want to play again? (yes/no): ");
            String response = scanner.next().toLowerCase();
            playAgain = response.equals("yes");
        }

        System.out.println("Thank you for playing! Your final score is: " + totalScore);
        scanner.close();
    }
}
