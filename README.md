# hangman-game-in-python
import random


def hangman():
    words = ["apple", "grape", "mango", "peach", "berry"]
    word = random.choice(words)
    guessed = ["_"] * len(word)
    attempts = 6
    guessed_letters = []

    print("Welcome to Hangman!")
    print("Guess the word one letter at a time.")
    print(" ".join(guessed))

    while attempts > 0 and "_" in guessed:
        guess = input("Enter a letter: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("Please enter a single valid letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word:
            for i in range(len(word)):
                if word[i] == guess:
                    guessed[i] = guess
            print("Correct!")
        else:
            attempts -= 1
            print(f"Wrong! You have {attempts} tries left.")

        print("Word: " + " ".join(guessed))
        print("Guessed letters:", ", ".join(guessed_letters))

    if "_" not in guessed:
        print("You won! The word was:", word)
    else:
        print("You lost! The word was:", word)


hangman()
