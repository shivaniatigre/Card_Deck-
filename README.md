# Card_Deck-
A menu driven java program about the deck of cards following it's respective functions 
    import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

//Class to represent a card
class Card {
private String suit;
private String rank;
public Card(String suit, String rank) {
    this.suit = suit;
    this.rank = rank;
}

//Getter method for suit
public String getSuit() {
    return suit;
}

//Getter method for rank
public String getRank() {
    return rank;
}

//Method to check if two cards are from the same suit
public boolean sameCard(Card c) {
    return this.suit.equals(c.getSuit());
}

//Method to check if two cards have the same rank
public boolean compareCard(Card c) {
    return this.rank.equals(c.getRank());
}

//Method to print the card
public void printCard() {
    System.out.println(this.rank + " of " + this.suit);
}
}

//Class to represent a deck of cards
class Deck {
private ArrayList<Card> deck;
//Constructor to create the deck
public Deck() {
    deck = new ArrayList<Card>();
    createDeck();
}

//Method to create the deck
public void createDeck() {
    String[] suits = {"Hearts", "Diamonds", "Clubs", "Spades"};
    String[] ranks = {"Ace", "2", "3", "4", "5", "6", "7", "8", "9", "10", "Jack", "Queen", "King"};

    for (String suit : suits) {
        for (String rank : ranks) {
            deck.add(new Card(suit, rank));
        }
    }
}

//Method to print the deck
public void printDeck() {
    for (Card card : deck) {
        card.printCard();
    }
}

//Method to print a single card
public void printCard(int index) {
    deck.get(index).printCard();
}

//Method to check if two cards are from the same suit
public boolean sameCard(int index1, int index2) {
    return deck.get(index1).sameCard(deck.get(index2));
}

//Method to check if two cards have the same rank
public boolean compareCard(int index1, int index2) {
    return deck.get(index1).compareCard(deck.get(index2));
}

//Method to find a card
public int findCard(String suit, String rank) {
    for (int i = 0; i < deck.size(); i++) {
        Card card = deck.get(i);
        if (card.getSuit().equals(suit) && card.getRank().equals(rank)) {
            return i;
        }
    }
    return -1;
}

//Method to deal 5 random cards
public void dealCard() {
    Collections.shuffle(deck);
    for (int i = 0; i < 5; i++) {
        deck.get(i).printCard();
    }
}

//Method to shuffle the deck
public void shuffleDeck() {
    Collections.shuffle(deck);
}
}

//Main class
public class CardGame {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
Deck deck = new Deck();

    int choice;
    do {
        System.out.println("\n1. Create Deck");
        System.out.println("2. Print Deck");
        System.out.println("3. Print a Card");
        System.out.println("4. Check");
