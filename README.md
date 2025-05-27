# NumberGuessingGame
    import java.util.*;

    public class NumberGuessingGame 
    {

    private static final int MAX_ATTEMPTS = 5;
    private static final int MIN_NUMBER = 1;
    private static final int MAX_NUMBER = 100;

    public static void main(String[] args) 
    {
        Scanner s = new Scanner(System.in);
        Random r = new Random();
        int roundsPlayed = 0;
        int roundsWon = 0;

        System.out.println("=== Welcome to the Number Guessing Game ===");

        boolean playAgain;

        do 
        {
            int targetNumber = r.nextInt(MAX_NUMBER - MIN_NUMBER + 1) + MIN_NUMBER;
            int attempts = 0;
            boolean hasWon = false;

            System.out.println("\nI have selected a number between " + MIN_NUMBER + " and " + MAX_NUMBER + ".");
            System.out.println("You have " + MAX_ATTEMPTS + " attempts to guess it!");

            while (attempts < MAX_ATTEMPTS) 
            {
                System.out.print("Enter your guess: ");
                int guess = s.nextInt();
                attempts++;

                if (guess == targetNumber) 
                {
                    System.out.println("Correct! You guessed the number in " + attempts + " attempts.");
                    hasWon = true;
                    roundsWon++;
                    break;
                } 
                else if (guess < targetNumber) 
                {
                    System.out.println("Too low!");
                } 
                else 
                {
                    System.out.println("Too high!");
                }

                System.out.println("Attempts left: " + (MAX_ATTEMPTS - attempts));
            }

            if (!hasWon) 
            {
                System.out.println("Sorry! You've used all attempts. The number was: " + targetNumber);
            }

            roundsPlayed++;

            System.out.print("Do you want to play another round? (yes/no): ");
            s.nextLine(); // consume newline
            String response = s.nextLine().trim().toLowerCase();
            playAgain = response.equals("yes");

       } while (playAgain);

        System.out.println("\nGame Over! You played " + roundsPlayed + " rounds and won " + roundsWon + " times.");
        s.close();
    }
    }
