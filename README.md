# 2025_code-in-place
This is Liu's Final Project Submission in Stanford Code in Place
## Blackjack Versus
```python
import random

def draw_card():
    return random.randint(1, 11)

def blackjack_game():
    print("Welcome to the Blackjack Game (Player vs System: Turn-Based Mode)")

    player_total = 0
    system_total = 0
    player_done = False
    system_done = False

    while not (player_done and system_done):
        # Player's turn
        if not player_done:
            print(f"\nYour current total: {player_total}")
            choice = input("Draw a card? (y/n): ").lower()
            if choice == 'y':
                card = draw_card()
                player_total += card
                print(f"You drew a {card}. Current total: {player_total}")
                if player_total >= 21:
                    player_done = True
            else:
                player_done = True
                print(f"You chose to stop. Final total: {player_total}")
        else:
            print("\nYou have already stopped.")

        # System's turn (Auto strategy: draw if <17, 50% chance to draw if 17–20)
        if not system_done:
            print(f"\nSystem's current total: {system_total}")
            if system_total < 17:
                draw = True
            elif system_total < 21:
                draw = random.choice([True, False])
            else:
                draw = False

            if draw:
                card = draw_card()
                system_total += card
                print(f"System drew a {card}. Current total: {system_total}")
                if system_total >= 21:
                    system_done = True
            else:
                system_done = True
                print(f"System stops. Final total: {system_total}")
        else:
            print("System has already stopped.")

    # Game result
    print("\n=== Final Result ===")
    print(f"Your total: {player_total}")
    print(f"System's total: {system_total}")

    if player_total > 21 and system_total > 21:
        print("Both busted. It's a tie.")
    elif player_total > 21:
        print("You busted. System wins.")
    elif system_total > 21:
        print("System busted. You win!")
    elif player_total > system_total:
        print("You win!")
    elif player_total < system_total:
        print("You lose.")
    else:
        print("It's a tie!")

# Run the game
blackjack_game()
```
