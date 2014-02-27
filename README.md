Projects
========

Learning Java

import java.util.Random;

import javax.swing.JOptionPane;

class FindASix{
	
	public static void main(String[] args){
    	
    int[] dice = new int[5];
    int rollsRemaining = 3, totalRolls = 0;
    boolean isSix = false, isFive = false, isFour = false;
	
	do {
		dice = makeDice(dice);
		isSix = checkSix(dice, isSix, isFive, isFour);
		isFive = checkFive(dice, isSix, isFive, isFour);
		isFour = checkFour(dice, isSix, isFive, isFour);
		rollsRemaining = rollsRemaining - 1;
		totalRolls = totalRolls + 1;
	} // end do
	
	while ((rollsRemaining > 0) && (isSix == false || isFive == false || isFour == false));

	int score = dice[3]  + dice[4];
	System.out.println(score);	

	if (rollsRemaining > 0 && isSix == true && isFive == true && isFour == true) {
	String s = "After " + totalRolls + " roll(s) you have a Ship, Captain, & Crew" + "\n" + "You have " + rollsRemaining + " roll(s) left" + "\n" + "Your remaining dice are:  " + dice[3] + " & " + dice[4];
	JOptionPane.showMessageDialog(null,  s, "Dice Game", JOptionPane.INFORMATION_MESSAGE);
	int x = JOptionPane.showConfirmDialog(null, " Would you like to roll again?"); {
		if (x == 0) {
			
			dice = makeDice(dice);
			isSix = checkSix(dice, isSix, isFive, isFour);
			isFive = checkFive(dice, isSix, isFive, isFour);
			isFour = checkFour(dice, isSix, isFive, isFour);
			rollsRemaining = rollsRemaining - 1;
			totalRolls = totalRolls + 1;
			
			String u = "Your remaining dice are:  " + dice[3] + " & " + dice[4] + "\n" + "Your score is " + score + "\n" + "You have " + rollsRemaining + " roll(s) left";// MOVE ME SOMEWHERE
			JOptionPane.showMessageDialog(null,  u, "Dice Game", JOptionPane.INFORMATION_MESSAGE);// MOVE ME SOMEWHERE
			
			if (rollsRemaining > 0) {
				JOptionPane.showConfirmDialog(null, " Would you like to roll again?");
						if (x == 0) {
							dice = makeDice(dice);
							isSix = checkSix(dice, isSix, isFive, isFour);
							isFive = checkFive(dice, isSix, isFive, isFour);
							isFour = checkFour(dice, isSix, isFive, isFour);
							rollsRemaining = rollsRemaining - 1;
							totalRolls = totalRolls + 1;
			
							String w = "Your remaining dice are:  " + dice[3] + " & " + dice[4] + "\n" + "Your score is " + score;
							JOptionPane.showMessageDialog(null, w, "Dice Game", JOptionPane.INFORMATION_MESSAGE);
						}
						else if (x == 1) {
							String t = "Your remaining dice are:  " + dice[3] + " & " + dice[4] + "\n" + "Your score is " + score;
							JOptionPane.showMessageDialog(null, t, "Dice Game", JOptionPane.INFORMATION_MESSAGE);	
						}
				}
			else if (rollsRemaining == 0) {
				String v = "Your remaining dice are:  " + dice[3] + " & " + dice[4] + "\n" + "Your score is " + score;
				JOptionPane.showMessageDialog(null, v, "Dice Game", JOptionPane.INFORMATION_MESSAGE);
				}
			}
		else if (x == 1) {
			String b = "Your remaining dice are:  " + dice[3] + " & " + dice[4] + "\n" + "Your score is " + score;
			JOptionPane.showMessageDialog(null, b, "Dice Game", JOptionPane.INFORMATION_MESSAGE);	
		}
	}
	}
	else if (rollsRemaining == 0 && isSix == true && isFive == true && isFour == true) {
		String e = "After " + totalRolls + " rolls you have a Ship, Captain, & Crew" + "\n" + "You have " + rollsRemaining + " rolls left" + "\n" + "Your remaining dice are:  " + dice[3] + " & " + dice[4] + "\n" + "Your score is " + score;
		JOptionPane.showMessageDialog(null,  e, "Dice Game", JOptionPane.INFORMATION_MESSAGE);
	}
	else if ((rollsRemaining == 0) && (isSix == false || isFive == false || isFour == false)) {
		String c = "After " + totalRolls + " roll(s) you have not acquired a Ship, Captain, & Crew" + "\n" + "Thanks for playing!";
		JOptionPane.showMessageDialog(null,  c, "Dice Game", JOptionPane.INFORMATION_MESSAGE);
	}
}
	//does not affect scope of input variables. Try a non void method
	public static void checkRoll(int[] dice, boolean isSix, boolean isFive, boolean isFour){
		
		for(int i = 0; i < dice.length; i++){
			if (dice[i] == 6 && isSix == false && isFive == false && isFour == false) {
				isSix = true;
				}
			else if (dice[i] == 5 && isSix == true && isFive == false && isFour == false) { 
				isFive = true;
				}
			else if (dice[i] == 4 && isSix == true && isFive == true && isFour == false) {
				isFour = true;
				}	 
		}
		
	}
	
	public static boolean checkSix(int[]dice, boolean six, boolean five, boolean four){
		for(int i = 0; i < dice.length; i++){
			if (dice[i] == 6 && six == false && five == false && four == false) {
				six = true;
				}	
	}
		return six;
	}
	
	public static boolean checkFive(int[]dice, boolean six, boolean five, boolean four){
		for(int i = 0; i < dice.length; i++){
			if (dice[i] == 5 && six == true && five == false && four == false) {
				five = true;
				}	
	}
		return five;
	}
	
	public static boolean checkFour(int[]dice, boolean six, boolean five, boolean four){
		for(int i = 0; i < dice.length; i++){
			if (dice[i] == 4 && six == true && five == true && four == false) {
				four = true;
				}	
	}
		return four;
	}
	
	public static int[] makeDice(int[]dice){
		 Random rand = new Random();
		for(int i = 0; i < dice.length; i++){
			dice[i] = (int) (6*rand.nextDouble() + 1);
	}
		return dice;
}}
