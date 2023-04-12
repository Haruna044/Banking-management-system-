 
import java.util.Scanner;

// create a class for user accounts
class Account {
    int accountNumber;
    String accountHolderName;
    double accountBalance;

    // constructor for initializing account properties
    Account(int num, String name) {
        accountNumber = num;
        accountHolderName = name;
        accountBalance = 0.0;
    }

    // method for depositing money to account
    void deposit(double amount) {
        accountBalance += amount;
    }

    // method for withdrawing money from account
    void withdraw(double amount) {
        accountBalance -= amount;
    }

    // method for printing the account balance
    void balance() {
        System.out.println("Account balance: $" + accountBalance);
    }
}

// create a class for banking system with main method
public class BankingSystem {
    public static void main(String[] args) {
        // create scanner object for taking user input
        Scanner input = new Scanner(System.in);

        // welcoming message
        System.out.println("Welcome to XYZ Bank!");

        // create an account object for user
        Account userAccount = new Account(1234, "John Doe");

        // menu for user to choose options
        while (true) {
            System.out.println("\nSelect an option:");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");

            // take user input for option
            int option = input.nextInt();

            // switch case for each option
            switch (option) {
                case 1:
                    System.out.print("Enter deposit amount: $");
                    double depositAmount = input.nextDouble();
                    userAccount.deposit(depositAmount);
                    System.out.println("Deposited $" + depositAmount);
                    userAccount.balance();
                    break;

                case 2:
                    System.out.print("Enter withdrawal amount: $");
                    double withdrawalAmount = input.nextDouble();
                    if (withdrawalAmount > userAccount.accountBalance) {
                        System.out.println("Insufficient balance!");
                    } else {
                        userAccount.withdraw(withdrawalAmount);
                        System.out.println("Withdrawn $" + withdrawalAmount);
                        userAccount.balance();
                    }
                    break;

                case 3:
                    userAccount.balance();
                    break;

                case 4:
                    System.out.println("Thank you for using XYZ Bank!");
                    System.exit(0);
                    break;

                default:
                    System.out.println("Invalid option!");
                    break;
            }
        }
    }
}
 
