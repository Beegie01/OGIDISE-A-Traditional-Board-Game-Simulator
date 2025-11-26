# Ogidise – A Traditional Board Game Simulator

## Overview

This project is an independent Python simulation of *Ogidise*, a traditional board game I played growing up in Benin City. The game is a head-to-head competition between two players who try to capture as many of their opponent’s stones as possible.

The board is made up of two sides with 6 pits each, for a total of 12 pits. There are 48 stones in play, and each pit can hold multiple stones. A coin toss determines which player controls which side of the board and who goes first.

---

## Game Components

- **Board:** 12 pits arranged in a circle, numbered 1–12, 6 per player.
- **Stones:** 48 stones in total.
- **Players:** 2 opponents, each assigned one side of the board.
- **Reservoir:** Each player has a “reserve” or “store” where captured stones are kept.

At the start of the game, all 12 pits contain 4 stones each, so each player effectively has 24 stones on their side.

---

## Core Mechanics

### Pick

- A **pick** occurs when a player chooses a pit on their own side and transfers all the stones from that pit into their hand.

### Cycle of Drop

- After picking, the player **drops** stones one at a time into successive pits in a clockwise direction, moving from pit 1 through pit 12.
- If they still have stones after dropping into pit 12, they continue from pit 1 again, maintaining the same cycle of drop.
- The player’s hand is empty when all stones picked have been dropped.

### Turn Order and Coin Toss

- A **coin toss** determines:
  - Which player takes the first turn.
  - Which side of the board (pits 1–6 or 7–12) belongs to each player.
- On their turn, a player must choose a pit on their own side:
  - Pits 1–6, or
  - Pits 7–12, depending on their assigned side.

---

## Turn Rules

1. **First Player Turn**
   - The player selects a valid pit on their side and performs a **pick**.
   - They then perform a **cycle of drop**, distributing stones one by one into subsequent pits.

2. **Change of Turn**
   - If the **last stone** dropped from the hand lands in an **empty pit**, the player’s turn ends and control passes to the opponent.
   - If the **last stone** lands in a **non-empty pit**, the player immediately **picks** all stones from that pit and continues dropping, maintaining the same cycle, until their hand is empty and one of the end-of-turn conditions is met.

---

## Claiming Stones

- A **claim** occurs when the **last stone** dropped from the hand lands in a pit on the opponent’s side that already contains **three stones**, making it four.
- When this happens:
  - The player collects all four stones from that pit.
  - These stones are moved to that player’s **reservoir**.
  - The total number of stones in active play is reduced by four.
  - After a claim, the turn automatically switches to the other player.

---

## Winning the Game

- Throughout the game, each player accumulates stones in their reservoir.
- The winner is the player with the **greater total number of stones** (including their reserve) at the end.
- An undisputable winner is determined once one player has successfully **claimed** more stones than the opponent by the time the total number of stones still in play has dropped to **16**.

---

## Project Notes

This repository contains a Python implementation of these rules, modelling the board, turns, and capture logic as faithfully as possible to the traditional game of Ogidise.
