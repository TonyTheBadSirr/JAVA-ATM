# JAVA-ATM
Practice ATM applicaiton

package com.Williford;

import java.lang.System;

public class Main {

    public static void main(String[] args) {
        BankingInfo y = new BankingInfo();
        BankingMethods a = new BankingMethods();
        System.out.println("Welcome to Tony's national bank: \n");

        a.mainMenu();






        }


}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

package com.Williford;

public class BankingMethods {

    private BankingInfo z = new BankingInfo();
    public char userChoice;

    public void deposit() {

        String depoCall = "How much would you like to deposit today?\n";
        System.out.println(depoCall);
        System.out.println("Please remember that your deposit must be at least $20.00");
        z.setUpdateBalance(z.getBank().nextDouble());

        if (z.getUpdateBalance() < 20.00) {
            System.out.println("That is an invalid input, please try another entry\n");
            deposit();
        } else if (z.getUpdateBalance() >= 20.00) {

            System.out.println("Your balance was: " + z.getCurrentBalance() + "\n");
            System.out.println("You deposited: " + z.getUpdateBalance());
            z.setCurrentBalance(z.getCurrentBalance() + z.getUpdateBalance());
            System.out.println("Your new balance is: " + z.getCurrentBalance() + "\n");
            mainMenu();
        }
    }

    public void withdrawal() {
        String withCall = "How much would you like to withdraw today?\n ";
        System.out.println("Your current balance is: " + z.getCurrentBalance());
        System.out.println("Please remember that your withdrawal must be at least $20.00");
        System.out.println(withCall);
        z.setUpdateBalance(z.getBank().nextDouble());
        if (z.getCurrentBalance() <= z.getUpdateBalance() || z.getUpdateBalance() < 20.00) {
            System.out.println("Sorry, that is an invalid amount, please try another input:  ");
            withdrawal();
        } else {
            System.out.println("You withdrew: " + z.getUpdateBalance());
            z.setCurrentBalance(z.getCurrentBalance() - z.getUpdateBalance());
            System.out.println("Your new balance is now: " + z.getCurrentBalance());
            mainMenu();
        }
    }

    public void balance() {

        System.out.println("Your current balance is: " + z.getCurrentBalance());

        mainMenu();

    }

    public void mainMenu() {
        try {
            System.out.println("If you would like to make a DEPOSIT, please enter the letter: D\n"
                    + "If you would like to make a WITHDRAWAL, please enter the letter: W\n"
                    + "If you would like to check your BALANCE, please enter the letter: B\n"
                    + "If you would like to QUIT, please enter the letter: Q\n");
            System.out.println("Please enter a letter to continue: \n");
            userChoice = z.getBank().next().toUpperCase().charAt(0);
            if (userChoice == 'D') {
                System.out.println("You selected: " + userChoice + " \n for DEPOSIT \n");
                deposit();
            }
            if (userChoice == 'W') {
                System.out.println("You selected: " + userChoice + " \n for WITHDRAWAL: \n");
                withdrawal();
            }
            if (userChoice == 'B') {
                System.out.println("You selected: " + userChoice + " \n for BALANCE: \n");
                balance();
            }
            if (userChoice == 'Q') {
                System.out.println("You selected: " + userChoice + " \n to QUIT: \n");
                System.out.println("Are you sure you want to quit? \n enter Y for yes, and N for no");
                userChoice = z.getBank().next().toUpperCase().charAt(0);
                if (userChoice == 'Y') {
                    System.out.println("Thank you for using Tony's banking system please come back anytime!!!");
                    System.exit(0);
                }
                if (userChoice == 'N') {
                    System.out.println("Okay, what would you like to do today?");
                    mainMenu();
                } else {
                    System.out.println("That was an invalid selection, please try another: \n");

                    mainMenu();
                }
            } else {
                System.out.println("That was an invalid selection, please try another: \n");

                mainMenu();
            }

        }catch(Exception error) {
            System.out.println("You encountered an error: Exception " + error.getMessage());
            mainMenu();

            return;
        }

    }

}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

package com.Williford;

import java.util.Scanner;

public class BankingInfo {
    public int getPin() {   // The pin feature is a work in progress, I havent got around to doing a final implementation and incorporating it into the main design/functionality
        return pin;
    }

    public void setPin(int pin) {
        this.pin = pin;
    }

    private int pin;
    private double currentBalance = 535.90;
    private double updateBalance;
    private Scanner Bank = new Scanner(System.in);

    public double getCurrentBalance() {
        return currentBalance;
    }

    public void setCurrentBalance(double currentBalance) {
        this.currentBalance = currentBalance;
    }

    public double getUpdateBalance() {
        return updateBalance;
    }

    public void setUpdateBalance(double updateBalance) {
        this.updateBalance = updateBalance;
    }

    public Scanner getBank() {
        return Bank;
    }










}
