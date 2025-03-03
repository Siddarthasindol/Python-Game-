# Python-Game-
This repo consists of game that I have submitted for python 
import random

# Function to roll the dice
def roll_dice():
    return random.randint(1, 6)

# Function to give hints
def give_hint(current_sum, target_number):
    if current_sum < target_number:
        return "Try rolling higher."
    elif current_sum > target_number:
        return "Try rolling lower."
    else:
        return "You are on target!"

# Function for Player 2 to try and match the number given by Player 1
def play_game():
    # Player 1 sets the target number
    print("Player 1, give a number between 1 and 100:")
    target_number = int(input())
    
    # Check if the target number is within the valid range
    if target_number < 1 or target_number > 100:
        print("Please enter a number between 1 and 100.")
        return
    
    # Player 2 tries to roll the dice
    total_sum = 0
    print("Player 2, you have 5 rolls to match the target number.")
    
    for roll_count in range(1, 6):
        print(f"Roll {roll_count}:")
        roll = roll_dice()
        print(f"You rolled a {roll}")
        total_sum += roll
        
        # Print the running total sum of the rolls
        print(f"Total sum so far: {total_sum}")
        
        # Give a hint based on the current sum
        hint = give_hint(total_sum, target_number)
        print(hint)
        
        # Check if Player 2 has matched the target
        if total_sum == target_number:
            print("Congratulations, Player 2! You won!")
            return
    
    # If Player 2 doesn't match the target after 5 rolls, they lose
    print(f"Sorry, Player 2! The total sum is {total_sum}. You lost!")

# Start the game
play_game()

