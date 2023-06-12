"# Week06" 
package Week6Final;

public class GameApp {

	public static void main(String[] args) {
		
		Player player1 = new Player("Jose");
		Player player2 = new Player("Kate");
		Deck deck = new Deck();
		
		deck.shuffle();
		
		
		for (int i = 0; i < 26; i++) {
			player1.hand.add(deck.draw());
			player2.hand.add(deck.draw());
		}
		for (int i = 0; i < 26; i++) {
			Card player1Card = player1.flip();
			Card player2Card = player2.flip();	
			System.out.println(player1.getName() + " plays ");
			player1Card.describe();
			System.out.println(player2.getName() + " plays ");
			player2Card.describe();
			
			if (player1Card.getRank() > player2Card.getRank()) {
				player1.incrementScore();
				System.out.println(player1.getName() + " Wins Round ");
				System.out.println();
			} else if (player1Card.getRank() < player2Card.getRank()) {
				player2.incrementScore();
				System.out.println(player2.getName() + " Wins ");
				System.out.println();
			} else {
				System.out.println("Draw!");
				System.out.println();
			}
				
			
			System.out.println("Final Score " + player1.getName() + ": " + player1.getScore() + " " + player2.getName() + ": " +player2.getScore());
			if (player1.getScore() > player2.getScore()) {
				System.out.println(player1.getName() + " Wins Round! ");
				System.out.println(" ");
			} else if (player2.getScore() > player1.getScore()) {
				System.out.println(player2.getName() + " Wins Round! ");
				System.out.println("");
			} else {
				System.out.println(" This game was a Draw! ");
				System.out.println();
			}
		
		}

			
			
			
		}
	}
  package Week6Final;

public class Card {

		
		//Step 1. Card Values and Names
		String name;
		String value;
		int rank;
		
		
		Card (String name, String value, int rank) {
			this.name= name;
			this.value = value;
			this.rank = rank;
			
		}
			
		//Step 2. Getters and Setters
		public int getRank() {
			return rank;
		}
		public void setRank(int rank) {
			this.rank = rank;
		}
		
		public String getName() {
			return name;
		}
		public void setName(String name) {
			this.name = name;
		}
		public String getValue() {
			return value;
		}
		public void setValue(String value) {
			this.value = value;
		}
		
		//Prints Card Info
		public void describe() {
			System.out.println(this.name + " of " + this.value);
		}

		
}
package Week6Final;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Deck {
	//List of Card
	List<Card> cards = new ArrayList<Card>();
	
	
	Deck () {
		String[] suits = {"Clubs", "Diamonds", "Hearts", "Spades"};
		String[] numbers = {"Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Jack", "Queen", "King", "Ace"};
		
		for ( String suit : suits) {
			int count = 2;
			for (String number : numbers) {
				Card card = new Card(number, suit, count);
				this.cards.add(card);
				count++;
			}
		}
		
		
	}
	
	//Getters & Setters
	public List<Card> getCards() {
		return cards;
	}
	public void setCards(List<Card> cards) {
		this.cards = cards;
	}
	public void describe() {
		for (Card card : this.cards) {
			card.describe();
		}
	}
	//Shuffle
	public void shuffle() {
		Collections.shuffle(this.cards);
	}
	
	public Card draw() {
		Card card = this.cards.remove(0);
		return card;
	}
}
  package Week6Final;
import java.util.List;
import java.util.ArrayList;

	public class Player {
		List<Card> hand = new ArrayList<Card>();
	
	int score = 0;
	String name;
	
	public Player(String name ) {
		this.name = name;
		this.score = 0;
	}
	 public void describe() {
		 System.out.println(name);
		 for (Card card : hand) {
			card.describe();
		
		 }
	 }

	 public Card flip() {
		 Card card = hand.get(0);
		 hand.remove(0);
		 return card;
		 
	 }
	 
	 
	public void draw (Deck deck) {
		Card drawnCard = deck.draw();
		hand.add(drawnCard);
	}
	
	public void incrementScore() {
		this.score++;
	}
	
	public String getName() {
		return name;
	}
	public int getScore() {
		return score;
	}
}



