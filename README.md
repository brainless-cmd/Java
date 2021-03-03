# Java
Subtractio_Qui_ for Grade School Students
import java.util.Random;
import java.util.Scanner;

public class Subtraction_Quiz {
    //declaring and defining variables
    static int rand1 = 0, rand2 = 0, probno = 1;
    static int randNumSub = 0, answerInput = 0, numCorrect = 0, numIncorrect = 0;
    static final int PROB = 10;

    final static Scanner input = new Scanner(System.in);
    final static Random rand = new Random();

    public static void main(String[] args) {
        System.out.println("CPS 501 Assignment 1 by **KARTHI_BALASUNDARAM** \n");
        System.out.print("Welcome to the Subtraction Quiz \n");
        System.out.print("Enter your name: ");
        String name = input.nextLine();
        System.out.println("\nGreetings " + name + "! " + "\nYou will be asked with 10 problems, Kindly go through it and answer wisely, \n" + "Ready, Set, Go! \n");
        while (probno <= PROB) {
            oneProblem();
            probno++;
        }
        float percentage = ((float) numCorrect / PROB) * 100;
        report(name, PROB, numCorrect, numIncorrect, percentage);

        System.out.print("\nAssignment 1 complete\n\n");
    }

    // function to present one problem to the quiz taker
    static void oneProblem() {
        System.out.print("Question " + probno + ": ");
        rand1 = 10 + rand.nextInt(90);
        rand2 = 10 + rand.nextInt(90);
        /*Since a grade school doesn’t understands the negative results, using a simple if statement to
        get positive results*/
        int temp;
        if (rand1<rand2) {
            temp = rand1;
            rand1 = rand2;
            rand2 = temp;
            randNumSub = rand1 - rand2;
        }
        else
            randNumSub = rand1 - rand2;
        System.out.print(rand1 + " - " + rand2 + " = ");
        answerInput = input.nextInt();
        if (answerInput == randNumSub) {
            System.out.println("Your answer is correct!\n");
            numCorrect++;
        } else {
            System.out.print("Sorry, Your answer is wrong! ");
            System.out.println("The correct answer is: " + randNumSub + "\n");
            numIncorrect++;
        }
    }
    static char getLetterGrade(double percentage) {
        char result;
        if (percentage >= 90) { result = 'A'; }
        else if (percentage >= 80) { result = 'B';}
        else if (percentage >= 70) { result = 'C';}
        else if (percentage >=60) { result = 'D';}
        else if (percentage >=50) { result = 'E';}
        else { result = 'F'; }
        return result;
    }
    static String Message(double percentage) {
        if (percentage == 100)
            return "Congratulations! You got a perfect score!";

        else if(percentage >= 80)
            return  "You did alright!";

        else if(percentage >= 70)
            return "You pass but should try to do better!";
        else
            return "You really need to study harder!";
    }
    static void report(String name, int numProbs, int numCorrect, int numIncorrect, double percent) {

        System.out.println("Test report for " + name + "\n");
        System.out.println("Problems attempted: " + numProbs );
        System.out.println("Correct answers: "+ numCorrect );
        System.out.println("Incorrect answers: "+ numIncorrect );
        System.out.println(Message(percent));
        System.out.println("Your overall grade is:"+ getLetterGrade(percent));
    }
}
