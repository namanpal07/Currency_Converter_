# Currency_Converter_ code:-
import java.util.HashMap;
import java.util.Scanner;

public class CurrencyConverter {
    // exchange rates (Base: USD)
    private static final HashMap<String, Double> exchangeRates = new HashMap<>();
    static {
        exchangeRates.put("USD", 1.0);       // US Dollar
        exchangeRates.put("INR", 83.0);      // Indian Rupee
        exchangeRates.put("EUR", 0.92);      // Euro
        exchangeRates.put("GBP", 0.78);      // British Pound
        exchangeRates.put("JPY", 140.0);     // Japanese Yen
    }
    //  Currency Conversion
    public static double convert(String base, String target, double amount) {
        double baseRate = exchangeRates.get(base);
        double targetRate = exchangeRates.get(target);
        return (amount / baseRate) * targetRate;
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println(" Welcome to the Currency Converter!");
        System.out.println("Available currencies: USD, INR, EUR, GBP, JPY");
        //  Select base and target currencies
        System.out.print("Enter base currency: ");
        String base = scanner.next().toUpperCase();
        System.out.print("Enter target currency: ");
        String target = scanner.next().toUpperCase();
        // Check if currencies are valid
        if (!exchangeRates.containsKey(base) || !exchangeRates.containsKey(target)) {
            System.out.println(" Invalid currency code entered.");
            return;
        }
        // Amount Input:-
        System.out.print("Enter amount to convert: ");
        double amount = scanner.nextDouble();
        //  Conversion:-
        double converted = convert(base, target, amount);
        //  Display  the result:-
        System.out.printf("%.2f %s = %.2f %s%n", amount, base, converted, target);
        scanner.close();
    }
}
