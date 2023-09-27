---
toc: False
comments: True
layout: post
title: Tic Tac Toe with the cool
description: funny tic tac toe
courses: {'csp': {'week': 3}}
categories: ['C3.7']
type: hacks
---

```python
import random
import ipywidgets as widgets
from IPython.display import display, clear_output

# Initialize the board
board = [' ' for _ in range(9)]

# Define winning combinations
winning_combinations = [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                        (0, 3, 6), (1, 4, 7), (2, 5, 8),
                        (0, 4, 8), (2, 4, 6)]

# Create buttons for the board
buttons = [widgets.Button(description=' ', layout=widgets.Layout(width='50px', height='50px')) for _ in range(9)]

# Create an output widget for displaying messages
output = widgets.Output()

# Function to display the Tic Tac Toe board
def display_board(board):
    for i in range(0, 9, 3):
        row_buttons = buttons[i:i + 3]
        display(widgets.HBox(row_buttons))
        if i < 6:
            print("-" * 9)

# Function to make a move
def make_move(player, position):
    if board[position] == ' ':
        board[position] = player
        buttons[position].description = player
        return True
    return False

# Function to check for a win
def check_win(player):
    for combo in winning_combinations:
        if all(board[i] == player for i in combo):
            return True
    return False

# Function to check for a draw
def check_draw():
    return ' ' not in board

# Event handler for button clicks
def button_click(b):
    position = buttons.index(b)
    if make_move(current_player, position):
        with output:
            clear_output(wait=True)
            display_board(board)
            if check_win(current_player):
                print(f"Player {current_player} wins!")
            elif check_draw():
                print("It's a draw!")
            else:
                current_player = 'O' if current_player == 'X' else 'X'

# Assign the event handler to the buttons
for button in buttons:
    button.on_click(button_click)

# Display the initial board
display_board(board)

# Initialize the game
current_player = 'X'
with output:
    print(f"Player {current_player}'s turn")

# Display the output widget
display(output)

```
