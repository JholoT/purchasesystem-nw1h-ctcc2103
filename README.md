# purchasesystem-nw1h-ctcc2103
import java.util.Scanner;

public class RestautantPurchaseSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Define arrays for menu items and their prices
        String[] menuItems = {"SpecialSisig", "LechonManok", "Calamares", "BeefPares"};
        double[] prices = {150.00, 200.00, 120.00, 100.00};

        // Display the menu
        System.out.println("Welcome to Tallado Restaurant!");
        System.out.println("Menu:");

        for (int i = 0; i < menuItems.length; i++) {
            System.out.println(i + 1 + ". " + menuItems[i] + " - ₱" + prices[i]);
        }

        // Initialize variables to store order details
        int[] orderQuantities = new int[menuItems.length];
        double totalCost = 0.0;

        // Ask user for order
        String choice;
        do {
            System.out.print("Enter the number of your order: ");
            int itemNumber = scanner.nextInt();
            System.out.print("Enter the quantity: ");
            int quantity = scanner.nextInt();

            // Update order details
            orderQuantities[itemNumber - 1] += quantity;
            totalCost += prices[itemNumber - 1] * quantity;

            System.out.print("Would you like to order anything else? (yes/no): ");
            choice = scanner.next();
        } while (choice.equalsIgnoreCase("yes"));

        // Display the order summary
        System.out.println("\nOrder Summary:");
        for (int i = 0; i < menuItems.length; i++) {
            if (orderQuantities[i] > 0) {
                System.out.println(menuItems[i] + " - Quantity: " + orderQuantities[i] +
                        ", Subtotal: ₱" + (prices[i] * orderQuantities[i]));
            }
        }
        System.out.println("Total cost: ₱" + totalCost);

        scanner.close();
    }
}
