import java.util.*; // Import the java.util package for Scanner and Random classes

public class WordleGame {
    // Constants for the maximum number of attempts and the length of the word to guess
    private static final int MAX_ATTEMPTS = 6;
    private static final int WORD_LENGTH = 5;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in); // Initialize a Scanner object for user input
        String secretWord = generateSecretWord(); // Generate a random secret word

        // Print welcome message and instructions
        System.out.println("Welcome to Wordle!");
        System.out.println(" ");
        System.out.println("Uppercase letters (e.g., 'A') for correct letters in the correct position (Green).");
        System.out.println("Lowercase letters (e.g., 'a') for correct letters in the wrong position (Yellow).");
        System.out.println("Dashes ('-') for incorrect letters (Grey).");
        System.out.println(" ");
        System.out.println("Guess the secret word within " + MAX_ATTEMPTS + " attempts!");


        boolean hasWon = false; // Flag to check if the player has won
        for (int attempt = 1; attempt <= MAX_ATTEMPTS; attempt++) { // Loop through each attempt
            // Prompt the player to enter a guess
            System.out.print("Attempt " + attempt + ": Enter your guess (5-letter word): ");
            String guess = scanner.nextLine().toLowerCase(); // Read and convert the guess to lowercase

            // Check if the guess has the correct length
            if (guess.length() != WORD_LENGTH) {
                System.out.println("Invalid guess! Please enter a " + WORD_LENGTH + "-letter word.");
                attempt--; // Decrement the attempt counter to allow re-guessing
                continue; // Continue to the next iteration
            }

            // Check if the guess matches the secret word
            if (guess.equals(secretWord)) {
                hasWon = true; // Set the hasWon flag to true if the guess is correct
                break; // Exit the loop
            }

            // Generate and display a hint based on the guess
            String hint = generateHint(secretWord, guess);
            System.out.println("Hint: " + hint);
        }

        // Print the final result based on whether the player won or lost
        if (hasWon) {
            System.out.println("Congratulations! You guessed the secret word: " + secretWord);
        } else {
            System.out.println("Sorry, you couldn't guess the secret word: " + secretWord);
        }

        scanner.close(); // Close the scanner
    }

    // Method to generate a random secret word from a predefined list
    private static String generateSecretWord() {
        String[] wordList = {"apple", "beach", "dance", "fudge", "grape", "hello", "adieu", "pasta", "jelly",
                "karma", "lemon", "magic", "olive", "nanny", "quiet", "round", "unity", "witty", "vital"};
        Random random = new Random(); // Initialize a Random object
        int randomIndex = random.nextInt(wordList.length); // Get a random index
        return wordList[randomIndex]; // Return the word at the random index
    }

    // Method to generate a hint based on the secret word and the player's guess
    private static String generateHint(String secretWord, String guess) {
        StringBuilder hint = new StringBuilder(); // Initialize a StringBuilder for the hint
        boolean[] secretUsed = new boolean[WORD_LENGTH]; // Track which letters in the secret word are used
        boolean[] guessUsed = new boolean[WORD_LENGTH]; // Track which letters in the guess are used

        // First pass: mark correct letters (correct position)
        for (int i = 0; i < WORD_LENGTH; i++) {
            if (guess.charAt(i) == secretWord.charAt(i)) {
                hint.append(Character.toUpperCase(guess.charAt(i))); // Correct letter in the correct position (Green)
                secretUsed[i] = true;
                guessUsed[i] = true;
            } else {
                hint.append('-'); // Placeholder for incorrect letters (Grey)
            }
        }

        // Second pass: mark correct letters (wrong position)
        for (int i = 0; i < WORD_LENGTH; i++) {
            if (!guessUsed[i]) { // Only check unused letters
                for (int j = 0; j < WORD_LENGTH; j++) {
                    if (!secretUsed[j] && guess.charAt(i) == secretWord.charAt(j)) {
                        hint.setCharAt(i, Character.toLowerCase(guess.charAt(i))); // Correct letter in the wrong position (Yellow)
                        secretUsed[j] = true;
                        break;
                    }
                }
            }
        }

        return hint.toString(); // Return the generated hint
    }
}
