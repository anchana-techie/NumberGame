# 🎮 Game Hub

A single-file (`index.html`) browser game hub for playing with friends online. No server, build step or login needed – just open the file.

## Games

### 🎯 Number Game
Guess a secret number in turns.
- **N** = how many digits are correct (anywhere), **P** = how many are in the correct position.
- Faster win = more points (`11 − attempts`, minimum 3).
- Guess History is shown as a table (Name / Number / Position).
- Personal colouring panel and a scratchpad (pen, eraser, undo, clear) for your notes.
- Settings: rounds, difficulty (3/4/5 digits), time per guess, max guesses.

### 🕵️ Who Is the Spy?
3–15 players. Everyone gets a secret word on their own screen; the spy's word is different (or missing).
- Players give clues in order (person 1, 2, 3 …) and keep cycling.
- Anyone who suspects the spy presses **🗳️ Voting Needed** – all active players vote; most votes is out.
  - **Spy caught** → round over, civilians win.
  - **Civilian voted out** → eliminated (can't give clues or vote), play continues. The spy wins when civilians left ≤ spies left (2 players left with 1 spy).
  - **Tie / no votes** → nobody is out.
- Scoring: catch the spy = +2 per civilian, +1 extra for each civilian who voted for the spy; spy wins = +3 for the spy.
- Settings: rounds, clue time, voting time, number of spies, spy word mode, random/custom words.

### 👑 Raja Rani
3–20 players. Secret roles are dealt; the Police must find the Thief. A wrong guess hands the Police's points to the Thief.
- Settings: rounds, time for the Police to guess.

### 🎨 Scribblio (draw & guess)
2–12 players, room based. Each turn one player gets a secret word and draws it; everyone else guesses in the chat.
- **Layout:** players on the left (rank, points, and a ✏️ next to the emoji of whoever is drawing), the canvas in the middle, the chat on the right.
- **Blanks & letter count:** guessers see the word as `_ _ _ _ _` with the number of letters next to it (multi-word answers show one count per word).
- **Letter hints:** after ⅓ of the drawing time one letter appears in its position (`_ _ a _ _`), after ⅔ a second one (`_ _ a _ b`). Short words never get fully revealed.
- **Guessing:** type guesses in the chat. A correct guess is announced without showing the word and turns that player green; players who already guessed can chat privately with the drawer. A near-miss gets a private "very close!" nudge.
- **Scoring:** a guesser earns 100–500 points depending on how much time was left; the drawer earns the average of what the guessers earned. The turn ends early when everybody has guessed. Everyone draws once per round.
- **Drawer tools:** 12 colours, 4 brush sizes, eraser, undo, clear.
- **Settings:** rounds, drawing time (30 sec – 3 min), one random word or pick from 3, letter hints on/off, built-in words or your own comma-separated list.
- If the drawer leaves or stays offline for 8 seconds the turn is skipped. A player who refreshes mid-turn gets the drawing back.

### 🎄 ChristMom ChristChild / 🪔 Diwali Daddy Diwali Kid
Secret-Santa style draws. Names and emails are entered, a random matching (nobody gets themselves) is made, and each person is emailed their match. Pairs are never shown on screen.

## How to play online
1. Open `index.html` (host it on any static host, e.g. GitHub Pages, Netlify, or open locally).
2. Pick a game, enter your name and avatar, and **Create room**.
3. Share the **room code** or **Invite link** with friends. They open the page and **Join room**.
4. In the lobby the host changes the room settings and presses **Start game**.

### Host controls
- **⏹ Exit game (keep room)** – leave the running game and return to the lobby; everyone stays in the room and the host can change settings.
- **✖ Close room** – closes the room for everyone (asks for confirmation).
- **🚪 Leave room** (guests) – asks for confirmation, then removes you from the room.
- Players who disconnect can rejoin with the room code while the room is open.

## Technical notes
- Online play uses [PeerJS](https://peerjs.com) (WebRTC). The **host's browser acts as the server** – the host must keep the tab open and in front. Secret words/roles are only sent to the player they belong to.
- If friends can't connect (e.g. mobile data vs Wi-Fi, strict firewalls), use **Connection help** on the entry screen to add a free TURN relay (e.g. from metered.ca). Everyone in the room should enter the same details.
- The email games use [EmailJS](https://www.emailjs.com). Enter your Service ID, Template ID and Public key in the email settings. In your EmailJS template set **To Email** to `{{to_email}}` and put `{{{message_html}}}` (three braces) in the body.
- Pop-ups (confirmations and notifications) live in their own layer above the page, so they always respond to clicks, the Esc key and clicks on the dark backdrop.
- Scribblio drawing strokes are sent as small batches straight to the host and relayed to everyone; they are not part of the full game-state update, which keeps drawing smooth.
- Names, rosters and settings are stored in your browser (localStorage) only.
- Requires an internet connection (PeerJS and EmailJS are loaded/used online).

## Files
- `index.html` – the entire app (HTML, CSS and JavaScript).
- `README.md` – this file.
