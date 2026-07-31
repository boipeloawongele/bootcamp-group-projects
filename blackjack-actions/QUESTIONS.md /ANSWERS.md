- Does the parse_state function return enough information to generate legal actions and apply one?
Yes. The parse_state function should return:

The player's hand (a list of card ranks).
The dealer's up card.
Whether this is the first or later decision.

This information is enough because:

The hand determines the hand value and whether the cards can be split.
The dealer's card determines whether Insurance is available.
The decision stage determines whether Double Down, Split, Surrender, and Insurance are legal.

- Is it easy to check whether an action is currently legal given the decision point?
- Yes. Once the state has been parsed into a structured format (such as a dictionary or class), checking legality is straightforward.

For example:

Hit and Stand are always legal.
Double Down is legal only if it is the first decision.
Split requires the first decision and two cards of the same rank.
Surrender requires the first decision.
Insurance requires the first decision and the dealer showing an Ace.

Because all the required information is stored in one place, each condition is simple to check.

- Can every member of the team explain why Double Down, Split, Surrender, and Insurance all share the same "first decision only" restriction?
- Yes.

These actions are special opening decisions in Blackjack.

Double Down commits you to taking exactly one more card before standing.
Split changes one hand into two separate hands before any additional cards are drawn.
Surrender immediately ends the hand for half your bet.
Insurance is a side bet offered only before play continues when the dealer shows an Ace.

Once you've already hit, the game has moved beyond the opening decision, so these options are no longer allowed

- Does the apply_action function cleanly handle the fact that Split returns two hands while every other action returns one?
- A clean approach is for apply_action to return:

A single hand for Hit, Stand, Double Down, and Surrender.
Two separate hands for Split.

For example, the function can consistently return a list of hands:

Normal actions return a list containing one hand.
Split returns a list containing two hands.

This keeps the interface consistent and avoids special-case code elsewhere

- What was your approach to teamwork?
- Our team first agreed on a common data model for representing the game state before writing any code. This ensured everyone was working with the same structures.

After agreeing on the design, we divided the work so each member implemented specific actions while following the shared model. We regularly discussed progress, tested our functions together, and reviewed each other's code to make sure everyone understood the complete project, not just their own part.

- What improvements remain?
- Adding full dealer gameplay.
Supporting multiple splits and re-splitting.
Allowing double down after a split if desired.
Tracking bets and bankroll.
Determining the winner at the end of each round.
Adding more automated tests for edge cases.
Creating a graphical or command-line interface for playing the game.
