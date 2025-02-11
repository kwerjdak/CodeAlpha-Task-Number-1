# CodeAlpha-Task-Number-1
#include <iostream>
#include <cstdlib>  // For rand() and srand()
#include <ctime>    // For time()
#include <vector>   // For storing user guesses

using namespace std;

int main() {
    srand(time(0));  
    int randomNumber = rand() % 100 + 1;  // Generates a number between 1 and 100

    vector<int> guesses;  // Stores all user guesses
    int userGuess, attempts = 0;
    time_t startTime, endTime;

    cout << "Welcome to the Number Guessing Game!\n";
    cout << "I have chosen a number between 1 and 100. Try to guess it!\n";

    time(&startTime); // Start timing

    do {
        cout << "Enter your guess: ";
        cin >> userGuess;
        guesses.push_back(userGuess); // Store the guess
        attempts++;

        if (userGuess > randomNumber) {
            cout << "Too high! Try again.\n";
        } else if (userGuess < randomNumber) {
            cout << "Too low! Try again.\n";
        } else {
            cout << "Congratulations! You guessed the number in " << attempts << " attempts.\n";
        }
    } while (userGuess != randomNumber);

    time(&endTime); // Stop timing
    double timeTaken = difftime(endTime, startTime); // Calculate time taken

    // Display game summary
    cout << "\n========== GAME SUMMARY ==========\n";
    cout << "Number guessed: " << randomNumber << "\n";
    cout << "Total attempts: " << attempts << "\n";
    cout << "Time taken: " << timeTaken << " seconds\n";
    cout << "Your guesses: ";
    
    // Use a traditional for loop to ensure compatibility with older C++ versions
    for (size_t i = 0; i < guesses.size(); i++) {
        cout << guesses[i] << " ";
    }

    cout << "\n==================================\n";

    return 0;
}
