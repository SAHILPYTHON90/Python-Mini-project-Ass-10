# Python-Mini-project-Ass-10
import random

def number_guessing_game():
    print("🎉 Welcome to the Enhanced Number Guessing Game! 🎉")
    print("I'm thinking of a number, and it's your job to guess it. Let's see how good you are!")

    # Choose difficulty level
    print("\nChoose a difficulty level:")
    print("1. Easy (Unlimited attempts)")
    print("2. Medium (10 attempts)")
    print("3. Hard (5 attempts)")
    
    while True:
        try:
            difficulty = int(input("Enter your choice (1, 2, or 3): "))
            if difficulty == 1:
                max_attempts = None
                print("You've chosen Easy mode. Take your time!")
                break
            elif difficulty == 2:
                max_attempts = 10
                print("You've chosen Medium mode. Let's see if you can guess it in 10 tries!")
                break
            elif difficulty == 3:
                max_attempts = 5
                print("You've chosen Hard mode. No pressure, just 5 tries to prove your skills!")
                break
            else:
                print("Please choose a valid option (1, 2, or 3).")
        except ValueError:
            print("Invalid input. Please enter a number.")

    # Generate a random number
    secret_number = random.randint(1, 100)
    attempts = 0

    while True:
        # Check if attempts are exhausted
        if max_attempts is not None and attempts >= max_attempts:
            print(f"😞 Oh no! You've used up all your {max_attempts} attempts. The number was {secret_number}.")
            break

        try:
            guess = int(input("\nEnter your guess (between 1 and 100): "))
            attempts += 1

            if guess < secret_number:
                print("📉 Too low! Try a higher number.")
            elif guess > secret_number:
                print("📈 Too high! Aim lower.")
            else:
                print(f"🎉 Amazing! You guessed it right in {attempts} attempts.")
                break

            # Encouraging or funny comments
            if max_attempts:
                print(f"You have {max_attempts - attempts} attempts left. Keep going!")
            else:
                print("Keep guessing, you've got this!")

        except ValueError:
            print("⚠️ Please enter a valid number.")

    # Ask to play again
    play_again = input("\nDo you want to play again? (yes/no): ").strip().lower()
    if play_again == "yes":
        number_guessing_game()
    else:
        print("Thanks for playing! Goodbye! 👋")

# Start the game
number_guessing_game()
