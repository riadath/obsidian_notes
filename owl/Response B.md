Creating a simple blackjack game using Pygame requires a basic understanding of Python programming and familiarity with the Pygame library. Below is a step-by-step guide to help you build a simplified version of a blackjack game. This example won't cover every rule or scenario but will provide you with a fundamental structure upon which you can build and improve.

Before starting, make sure you have Python and Pygame installed. You can download and install them from their official websites:

- Python: https://www.python.org/
- Pygame: https://www.pygame.org/

Once you have them installed, you can start coding your simple blackjack game.

1. **Set Up Your Game Environment:**
```python
import pygame
import random

# Initialize Pygame
pygame.init()

# Game window settings
width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Simple Blackjack")

# Define colors
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)
BLACK = (0, 0, 0)

# Card values
card_values = {
    '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9, '10': 10,
    'J': 10, 'Q': 10, 'K': 10, 'A': 11  # Aces can be 1 or 11, but we'll start with 11
}

# Load card images or use simple rectangles if you don't have images
# card_image = pygame.image.load('path/to/your/card_image.png')

# Game loop flag
running = True
```

2. **Define Helper Functions:**
```python
def draw_text(text, font, color, surface, x, y):
    textobj = font.render(text, 1, color)
    textrect = textobj.get_rect()
    textrect.topleft = (x, y)
    surface.blit(textobj, textrect)

def calculate_hand_value(hand):
    value = sum(card_values[card] for card in hand)
    # Adjust the value of Aces as needed
    for card in hand:
        if card == 'A' and value > 21:
            value -= 10
    return value
```

3. **Create Game Elements:**
```python
# Create a deck of cards
deck = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A'] * 4

# Shuffle the deck
random.shuffle(deck)

# Initial hands
player_hand = [deck.pop(), deck.pop()]
dealer_hand = [deck.pop(), deck.pop()]
```

4. **Game Loop:**
```python
# Game font
font = pygame.font.Font(None, 36)

while running:
    # Check for events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        # Add more controls here (hit, stand)

    # Game logic
    player_value = calculate_hand_value(player_hand)
    dealer_value = calculate_hand_value(dealer_hand)

    # Update display
    screen.fill(GREEN)

    # Display player's hand
    draw_text(f'Player Hand: {player_hand} Value: {player_value}', font, BLACK, screen, 50, 500)

    # Display dealer's hand
    draw_text(f'Dealer Hand: {dealer_hand} Value: {dealer_value}', font, BLACK, screen, 50, 100)

    # Update the display
    pygame.display.flip()

# Quit the game
pygame.quit()
```

5. **Implement Player Actions and Game Rules:**

To have a fully playable game, you'll need to add more features such as:

- Allowing the player to "hit" or "stand."
- Implementing what happens when the player stands (the dealer's turn and deciding the outcome).
- Handling cases like busts, blackjack, and push.
- Adding buttons or key events for player actions.
- Enhancing the user interface with images and more interactive elements.

This script provides a basic structure, but there's much more you can add to create a complete game experience. You can enhance it by adding more sophisticated rules, splitting hands, doubling down, or even adding betting mechanics. Happy coding, and enjoy building your blackjack game!