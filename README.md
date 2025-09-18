import random

secret_number = random.randint(1, 100)
difficulty = str(input("Enter difficulty (EASY, MEDIUM, HARD): ")).strip().upper()
score = 0
attempts = 0

if difficulty == "EASY":
    attempts = 20
elif difficulty == "MEDIUM":
    attempts = 10
elif difficulty == "HARD":
    attempts = 5
else:
    print("INVALID INPUT! Please enter EASY, MEDIUM, or HARD.")
    attempts = 0

if attempts > 0:
    print(f"\033[96mYou have {attempts} attempts to guess the number\033[0m")

while attempts > 0:
    guess = int(input(f"Make a guess: You have {attempts} attempts left: "))

    if guess < secret_number:
        print("Raise your guess! Too Low.")
    elif guess > secret_number:
        print("Lower your guess! Too High.")
    else:
        print(f"\033[97mCongratulations! You guessed the number in {score + 1} moves.\033[0m")
        break

    attempts -= 1
    score += 1

if attempts == 0:
    print(f"\033[91mGame Over! The secret number was {secret_number}. Better luck next time.\033[0m")
