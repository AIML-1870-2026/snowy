# Blackjack

## Overview
A classic, single-player browser-based Blackjack game against the house.

## Visual Design
- Purple themed color scheme
- Clear betting display showing current bet and player bankroll

## Core Rules

### Card Values
- Number cards (2-10): Face value
- Face cards (J, Q, K): 10
- Ace: 1 or 11 (whichever benefits the hand)

### Gameplay Flow
1. Player places bet
2. Dealer deals two cards to player (face up) and two to self (one face up, one face down)
3. Player chooses to Hit or Stand
4. If player busts (over 21), player loses immediately
5. Dealer reveals hole card and hits until reaching 17 or higher
6. Compare hands to determine winner

### Dealer Rules
- Dealer must hit on 16 or less
- Dealer must stand on 17 or more

## Betting System
- Bankroll clearly displayed at all times
- Current bet clearly displayed
- Minimum and maximum bet limits

## Payouts
- **Standard win**: 1:1 (bet returned + equal winnings)
- **Player Blackjack (dealer does not have blackjack)**: 3:2 (1.5x the bet)
- **Insurance** (optional): 2:1

## Edge Cases

### Blackjack Scenarios
- **Player gets Blackjack, Dealer does not**: Player wins 1.5x their bet (3:2 payout)
- **Both Player and Dealer get Blackjack**: Push (bet is returned, no winnings or losses)
- **Dealer gets Blackjack, Player does not**: Player loses their bet

### Other Edge Cases
- **Push (tie with same hand value)**: Bet is returned
- **Player busts**: Player loses immediately, regardless of dealer's eventual hand
- **Dealer busts**: Player wins if they haven't already busted

## Features
- [ ] Card deck (standard 52-card deck)
- [ ] Deal cards to player and dealer
- [ ] Hit and Stand actions
- [ ] Automatic Ace value calculation (1 or 11)
- [ ] Betting interface
- [ ] Bankroll tracking
- [ ] Win/loss/push detection
- [ ] Blackjack detection and correct 3:2 payout
- [ ] Push verification when both have Blackjack
