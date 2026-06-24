# CodeAlpha_HangmanGame
import random
# List of 5 predefined words
words = ["python", "apple", "robot", "cloud", "music"]
# Select a random word
word = random.choice(words)
# Create hidden word display
guessed_word = ["_"] * len(word)
# Variables
guessed_letters = []
incorrect_guesses = 0
max_incorrect = 6
print("🎮 Welcome to Hangman!")
print("Guess the word one letter at a time.")
# Game loop
while incorrect_guesses < max_incorrect and "_" in guessed_word:
    print("\nWord:", " ".join(guessed_word))
    print("Incorrect guesses left:", max_incorrect - incorrect_guesses)
    guess = input("Enter a letter: ").lower()
    # Check if already guessed
    if guess in guessed_letters:
        print("You already guessed that letter!")
        continue
    guessed_letters.append(guess)
    # Check if letter is in the word
    if guess in word:
        print("✅ Correct Guess!")
        for i in range(len(word)):
            if word[i] == guess:
                guessed_word[i] = guess
    else:
        print("❌ Wrong Guess!")
        incorrect_guesses += 1
# Result
if "_" not in guessed_word:
    print("\n🎉 Congratulations! You guessed the word:", word)
else:
    print("\n😢 Game Over!")
    print("The correct word was:", word)
