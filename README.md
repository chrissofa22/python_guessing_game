# Python Web Development Techdegree
# Project 1 - Number Guessing Game

# Used https://inventwithpython.com/chapter4.html as a reference.

import random
number_picked = 0
number = False

def hidden():
    return random.randint(1, 10)
answer = hidden()

def guessing(player_guess):
    if player_guess < answer:
        print("\nSorry, your number is too low!")  
    if player_guess > answer:
        print("\nSorry, your number is too high!")

def end_game():
    global number
    number = True
def start_game():
    global number
    global answer
    global number_picked
    number = False

    print("\n------------------------------------\nWelcome to the Number Guessing Game!\n------------------------------------\n\nPlease pick a number between 1-10.")

    highscore = number_picked

    if highscore == 0:
        highscore = number_picked
    elif number_picked < highscore:
        highscore = number_picked

    while not number:
        guess = -1
        try:
            prompt_player = input("\nPlease choose a number: ")
            guess = int(prompt_player)
            if guess != answer:
                guessing(guess)
                number_picked = number_picked + 1

            else:
                print("\nAwesome!\nIt took you {} trys!".format(number_picked + 1))
                play_again = input("\nWould you like to play again? Y/N: ")
                if play_again.lower().startswith("y"):
                    answer = hidden()
                    number_picked = 0
                    print("\nHigh score: {}".format(highscore))
                    highscore = 0
                    continue
                elif play_again.lower().startswith("n"):
                    print("\nThanks for playing! Have a great day.\n")
                    end_game()
                else:
                    print("\nSorry, please enter a valid option.")
                    return play_again

        except ValueError:
            print("\nSorry, please enter a valid option.")
            continue

start_game()
