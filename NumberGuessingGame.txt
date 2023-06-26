import java.util.Random;
import javax.swing.JOptionPane;
import javax.swing.JFrame;
//import java.lang.*;
import java.util.Scanner;

public class NumberGuessing {
	static int lefts = 0;
	static int total = 0;	
	Scanner sc = new Scanner(System.in);

	void addAttempts() {
		int l = 0 , total = 0;
	
		JFrame frame = new JFrame();
	    int answer = JOptionPane.showConfirmDialog(frame, "Do you want to add more Attempts");
	    if (answer == JOptionPane.YES_OPTION) {
	    	String remaining = JOptionPane.showInputDialog("Number of Attempts you want to add: ");
	    	guess(l,remaining);
	    } 
	    else if (answer == JOptionPane.NO_OPTION) {
	    	if (total == 0) {
	    		JOptionPane.showMessageDialog(null,"Result Not Generated because, \n User didn't guess the number");
	    	}
	    	else {
	    		displayScore(lefts,total);
	    	}
	    	
	    }
	}
	
	
	void guess(int l ,String remaining) {
	 
		total = Integer.parseInt(remaining);
		
		System.out.print("Random value from 1 to 100 is: ");
	    int random_num = (int)(Math.random()*100+1);
	    System.out.println(random_num);
	    lefts = Integer.parseInt(remaining);
	    
		while(l < lefts) {
		    String num = JOptionPane.showInputDialog("Guess the number: ");
		    
			if(random_num == Integer.parseInt(num)) {
				JOptionPane.showMessageDialog(null,"Entered/Guessed number matches the Random Number!!!");
				break;
		    }
		    else if(random_num > Integer.parseInt(num)) {
		    	JOptionPane.showMessageDialog(null,"Try Again!!! \n Entered/Guessed number is smaller than the Random number");
		    	JOptionPane.showMessageDialog(null,lefts-1 + " attempts left.");
		    }
		    else if(random_num < Integer.parseInt(num)) {
		    	JOptionPane.showMessageDialog(null,"Try Again!!! \n Entered/Guessed number is greater than the Random number");
		    	JOptionPane.showMessageDialog(null,lefts-1 + " attempts left.");
		    }
		    else {
		    	JOptionPane.showMessageDialog(null,"Try Again!!! \n Enter the number between 1 to 100.");
		    	JOptionPane.showMessageDialog(null,lefts-1 + " attempts left.");
		    }
			l++;
			lefts--;
		}
		displayScore(lefts,total);
	}
	
	void displayScore(int left, int total) {
		double score = (left * 100)/total;
		JOptionPane.showMessageDialog(null,"You got "+ score + "%");
	}
	
	public static void main(String[] args) {
		NumberGuessing n1 = new NumberGuessing();   
	    n1.addAttempts();
		
	}

}