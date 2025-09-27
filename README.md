# JacGuess

This tutorial demonstrates how to progressively rewrite a simple number guessing game using the Jac programming language. It begins with a standard Python implementation and gradually introduces Jac-specific features across six steps. Each version maintains the same core functionality while introducing new concepts and syntax.


## Overview of Steps

### Step 0 – Python Version

The base implementation is written in Python. It uses object-oriented principles to build a simple command-line guessing game.

```python
import random

class Game:
    def __init__(self, attempts):
        self.attempts = attempts

    def play(self):
        raise NotImplementedError()

class GuessTheNumberGame(Game):
    def __init__(self, attempts=10):
        super().__init__(attempts)
        self.correct_number = random.randint(1, 10)

    def play(self):
        ...
### Step 1 – Direct Jac Translation
File: guess_game1.jac

This version mirrors the Python implementation closely. It uses class, def, and super.init in Jac syntax. The game runs inside a with entry block.



### Step 2 – Declaring Fields with has
File: guess_game2.jac

This version introduces the has keyword for declaring fields directly within the object body. Method signatures are simplified, and the object definition becomes more concise.



### Step 3 – Separating Implementation with impl
Files: guess_game3.jac, guess_game3.impl.jac

This version separates object interfaces from their method implementations. It uses .impl.jac files to define method bodies, improving code organization for maintainability.


### Step 4 – Walking the Graph
Files: guess_game4.jac, guess_game4.impl.jac

This version introduces Jac's object-spatial model using nodes and walkers. A walker navigates through connected turn nodes, simulating the game logic through graph traversal.


### Step 5 – Scale-Agnostic Design
Files: guess_game5.jac, guess_game5.impl.jac

This version prepares the game for cloud deployment. Walkers can now be triggered as API endpoints using jac serve. The same code runs locally and in distributed environments without modification.


### Step 6 – AI-Enhanced Gameplay with byLLM
Files: guess_game6.jac, guess_game6.impl.jac

This final version adds LLM (large language model) capabilities via the byLLM plugin. Instead of basic responses like "too high" or "too low", the game provides intelligent, AI-generated hints to the player.


### File Structure
.
├── guess_game.py              # Step 0
├── guess_game1.jac            # Step 1
├── guess_game2.jac            # Step 2
├── guess_game3.jac            # Step 3
├── guess_game3.impl.jac
├── guess_game4.jac            # Step 4
├── guess_game4.impl.jac
├── guess_game5.jac            # Step 5
├── guess_game5.impl.jac
├── guess_game6.jac            # Step 6
├── guess_game6.impl.jac
└── README.md


### How to Run
### To execute a Jac file:

jac guess_game1.jac
### To expose the walker as an API:


jac serve guess_game5.jac
### To use AI features in guess_game6.jac, ensure you have a valid API key and model setup (e.g., for Gemini or GPT).

### Notes
J### ac version 1.0 or above is required

### Python 3.11+ is recommended

### Install Jac using 
pip install jaclang

### Install byLLM using 
pip install byllm

### Ensure .env or API key configuration files are not committed to version control

echo ".env" >> .gitignore

### This project is intended for learning and demonstration purposes only.

## Author Johnson Alala - Software Engineer & Generative AI