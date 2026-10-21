# 🎯 Multiplayer Number Guessing Game

A browser-based number guessing game for one or more players, built as a single `index.html` file. No server or build step is needed, so it runs on GitHub Pages or by opening the file locally.

## How to Play

1. Open the page and log in.
2. Choose **Single Player** or **Multiplayer**.
3. In multiplayer, set the number of players (1–6), enter their names, pick avatars, and click **Confirm Players**.
4. Pick a difficulty in the sidebar and click **New Game**. A secret number with no repeated digits is generated.
5. Take turns guessing. After each guess you get a hint in the form `xN yP`:
   - **N**: how many digits of your guess appear anywhere in the secret number.
   - **P**: how many of those digits are also in the correct position.
6. The first player to get all digits in the correct position (P equals the number of digits) wins.

### Difficulty Levels

| Level  | Digits |
|--------|--------|
| Easy   | 3      |
| Medium | 4      |
| Hard   | 5      |

The difficulty you pick applies from the next **New Game**.

## Features

- **Login gate**: the game screen is not loaded until you log in.
- **Single and multiplayer modes**, with names and emoji avatars for each player.
- **Round-robin starts**: Player 1 starts game 1, Player 2 starts game 2, and so on, wrapping back to Player 1.
- **Guess history** showing every guess and its N/P hint, newest first.
- **Number colouring panel**: mark digits 0–9 as Red, Green or Yellow to track your deductions.
- **New Game reset**: clears the typing box, guess history and colour panel.
- **Reveal Secret Number** button.
- **Top 5 leaderboard**, ranked by fewest attempts.
- **Balloon celebration** when someone wins.

## Login

| Field    | Value                  |
|----------|------------------------|
| Email    | `wastefellows@game.com` |
| Password | `WasteFellows@123`      |

## Data Storage

GitHub Pages can't write files, so scores and game logs are saved in the browser's `localStorage`:

- Each browser and device keeps its own leaderboard.
- Clearing your browser's site data removes the saved scores.
- The sidebar has buttons to **download** the leaderboard (`Leaderboard.csv`) and game logs (`Game_Logs.csv`), and to **clear** saved data.

Leaderboard and log fields: date and time, player, attempts, difficulty, secret number, and all guesses.

## Running Locally

Open `index.html` in any modern browser.

## Deploying to GitHub Pages

1. Push `index.html` and `README.md` to a GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Source**, select your branch (e.g. `main`) and the `/ (root)` folder, then save.
4. Your game will be available at `https://<username>.github.io/<repository>/`.

## Project Structure

```
├── index.html   # The whole game (HTML, CSS, JavaScript)
└── README.md    # This file
```
