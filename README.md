Download Link: https://assignmentchef.com/product/solved-swen221-assignment-4-the-card-game
<br>
<h1>The Card Game</h1>

The CardGame system is a simple card game written in Java. The game implements some variations on the well-known <em>trick-taking card game</em>. For more on this style of game, see this:

http://en.wikipedia.org/wiki/Trick-taking_game

There are four players (North, East, South and West) who are dealt exactly 13 cards each (i.e. the whole deck). The game then proceeds in a series of <em>tricks</em>. In each trick the <em>leader </em>lays a card, and then the next player (following clockwise rotation) plays a card, and so on until four cards have been played. The following illustrates:

Here, we see that North and East have played and, hence, South is next to play. Since North lead with a Heart, and South has a Heart, then he/she must play one of the available hearts.

If a player has a card of the same suit as that played by the leader, <em>then he/she must follow suit</em>. The winner of a trick is the player who played the highest card <em>in the same suit as the leader</em>. The winner of the game is the player who, after every card is played, has won the most tricks.

Every round either has a single suit of <em>trumps </em>or has <em>no trumps</em>. The sequence of trumps is <em>Hearts</em>, <em>Clubs</em>, <em>Diamonds</em>, <em>Spades</em>, <em>No Trumps </em>and this is repeated for the duration. The current suit of trumps (if applicable) is always the highest suit with respect to the ordering of cards.

<h1>Part 1: Card Comparisons</h1>

The CardGame system is almost fully functioning! To start off, you should implement the methods

Card.equals(), Card.hashCode() and Card.compareTo. The latter method should sort cards by their suit and rank, such that Hearts <em>&lt; </em>Clubs <em>&lt; </em>Diamonds <em>&lt; </em>Spades. In other words, any card in hearts is always less than any card in clubs, etc. However, the 6 of hearts is greater than the 2 of hearts. For picture cards we have that: Ace <em>&gt; </em>King <em>&gt; </em>Queen <em>&gt; </em>Jack <em>&gt; </em>10.

There are several JUnit tests provided with the CardGame system for this part (testCardEquals(), testCardNotEquals() and testCardCompareTo()). You should ensure that all of these tests now pass correctly. You should also find that, having implemented the required classes and methods, you can now play the game by running the method cards.Main.main(), and choose all human players. If the Card.compareTo() method is implemented correctly, the hand of each player should be sorted by suit in increasing order, starting with hearts.

<h1>Part 2: Illegal Moves</h1>

This part is concerned with the method Trick.play(Player,Card). When a player plays a card, this method is called to update the current trick being played. Unfortunately, it is possible for players to play <em>invalid cards </em>(e.g. cards not present in their hand, or not following suit), or to try and play <em>out of sequence</em>. This happens when a human player does something out of sequence.

You should implement the method Trick.play(Player,Card) to ensure that any attempt to play an invalid card, or to play out of sequence results in an IllegalMove exception being raised.

There are several JUnit tests provided with the CardGame system for this part (testInvalidPlay 1(), …, testInvalidPlay 5(). You should ensure that all of these tests now pass correctly. You should also find that, when playing the game, trying to play an invalid card does not work (and, instead, an error is reported on the status bar).

<h1>Part 3: Cloning</h1>

This part is concerned with the method CardGame.clone() and its implementation. The “duplicate” button in the Graphical User Interface employs this method to duplicate the current game:

Unfortunately, this method is not currently implemented correctly. In particular, this method is implemented in AbstractCardGame using a <em>shallow clone</em>. However, in order to properly duplicate a game a <em>deep clone </em>is required. Therefore, you need to replace and/or override the method in AbstractCardGame with appropriate implementations in its subclass(es).

There are several JUnit tests provided with the CardGame system for this part (i.e. testValidClone 1(), …, testValidClone 5()). You should ensure that all of these tests now pass correctly.

<h1>Part 4: Artificial Intelligence</h1>

This part is concerned with the class SimpleComputerPlayer, which is currently mostly unimplemented. This player chooses what card to play based on the following rules:

<ul>

 <li>If the AI player can <em>potentially win </em>the trick, then it plays the <em>highest eligible card</em>.</li>

 <li>If the AI player <em>cannot win </em>the trick, then it <em>discards </em>the lowest eligible card.</li>

 <li>In the special case that the AI player <em>must win </em>the trick, then it conservatively plays the <em>least card </em>needed to win.</li>

</ul>

An important concept for understanding these rules is the <em>ordering of eligible cards</em>. A card is eligible if it may be played according to the rules of the game (e.g. if the AI player can follow suit then it must, etc). The highest eligible card is then the card with the <em>highest rank and suit</em>, where the current suit of trumps (if applicable) is always the highest suit. In the case of two equally ranked cards of non-trump suit, then the underlying ordering implied by Card.compareTo() (as discussed above) should be used to chose.

There are several JUnit tests provided with the CardGame system for this part (testSimpleAI 1(), …, testSimpleAI 19()). You should ensure that all of these tests now pass correctly. You should also find that you’re now able to play the game against computer players.