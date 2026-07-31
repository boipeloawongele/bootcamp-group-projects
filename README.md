# Blackjack Actions Project

## Overview

This project implements the player action logic for a game of Blackjack (21). The program can parse a game state, determine which actions are legal, and apply the selected action according to the rules of Blackjack.

The project focuses only on the player's turn. It does not simulate the dealer's turn, betting, or determine the winner of the game.

---

## Features

- Parse a Blackjack decision point
- Calculate the value of a hand
- Generate all legal player actions
- Apply player actions
- Handle special Blackjack rules including:
  - Hit
  - Stand
  - Double Down
  - Split
  - Surrender
  - Insurance

---

## Project Structure

```
blackjack.py
test_blackjack.py
README.md
```

---

## Data Model

The game state is represented as a dictionary.

Example:

```python
{
    "hand": ["10", "6"],
    "dealer": "9",
    "first": True
}
```

Where:

- **hand** – The player's cards.
- **dealer** – The dealer's visible card.
- **first** – Indicates whether this is the player's first decision.

---

## Functions

### hand_value(cards)

Calculates the total value of the player's hand while correctly handling Aces as either 1 or 11.

Example:

```python
hand_value(["A", "9"])
```

Returns:

```
20
```

---

### parse_state(text)

Converts a decision-point string into a dictionary.

Input:

```
10,6 | 9 | first
```

Output:

```python
{
    "hand": ["10", "6"],
    "dealer": "9",
    "first": True
}
```

---

### generate_actions(state)

Returns every legal action for the current game state.

Possible actions include:

- Hit
- Stand
- Double Down
- Split
- Surrender
- Insurance

The function automatically checks whether each action is currently legal.

---

### apply_action(state, action, next_card=None)

Applies a chosen action.

Examples:

Hit:

```python
apply_action(state, "Hit", "5")
```

Split:

```python
apply_action(state, "Split")
```

Double Down:

```python
apply_action(state, "Double Down", "K")
```

---

## Running the Tests

Run the following command from the project folder:

```bash
python -m unittest test_blackjack.py
```

If all tests pass, you should see output similar to:

```
..........
----------------------------------------------------------------------
Ran 10 tests

OK
```

---

## Teamwork Approach

Our team first agreed on a shared data model before dividing the work. Once everyone understood how the game state would be represented, each member worked on different Blackjack actions using the same data structure. We regularly reviewed each other's work and tested the project together to ensure consistency and correctness.

---

## Possible Improvements

Future improvements could include:

- Dealer gameplay
- Determining the winner
- Betting and bankroll management
- Multiple-player support
- Re-splitting hands
- Double Down after Split
- Command-line interface
- Graphical user interface (GUI)

---

## Author

Blackjack Actions Project

Created using Python as part of a software development bootcamp project.
