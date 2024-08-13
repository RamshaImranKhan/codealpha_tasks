import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

//1)Stock class: Represents a stock with a company name (company) and a price (price).
//Constructor: Initializes the company and price fields.
//Getters (getCompany, getPrice): These methods return the company name and price.
//Setter (setPrice): This method allows the price to be updated.

class Stock {
    private String company;
    private double price;
    public Stock(String company,double price) {
        this.company=company;
        this.price = price;
    }
    public String getCompany() {
        return company;}
    public double getPrice() {
        return price;
    }
    public void setPrice(double price) {
        this.price = price;
    }}

//2)Portfolio class: Manages a list of stock holdings.
//holdings: A list of StockHolding objects representing the stocks held in the portfolio.
//Constructor: Initializes the holdings list.
//addStock method: Adds stock to the portfolio.
//It checks if the stock already exists in the portfolio. If it does, it increases the quantity of that stock.
//If the stock does not exist, it creates a new StockHolding and adds it to the portfolio.
//removeStock method: Removes a certain quantity of stock from the portfolio.
//It checks if the stock exists in the portfolio and decreases the quantity. If the quantity reaches zero, it removes the stock from the list.
//If the stock is not found, it prints a message.
//getHoldings method: Returns the list of stock holdings.
class Portfolio {
    private List<StockHolding> holdings;
    public Portfolio() {

        holdings = new ArrayList<>();
    }
    public void addStock(String symbol, double price, int quantity) {
        for (int i = 0; i < holdings.size(); i++) {
            StockHolding holding = holdings.get(i);
            if (holding.getStock().getCompany().equals(symbol)) {
                holding.addQuantity(quantity);
                return;
            }}
        holdings.add(new StockHolding(new Stock(symbol, price), quantity));
    }
    public void removeStock(String symbol, int quantity) {
        for (int i = 0; i < holdings.size(); i++) {
            StockHolding holding = holdings.get(i);
            if (holding.getStock().getCompany().equals(symbol)) {
                holding.removeQuantity(quantity);
                if (holding.getQuantity() == 0) {
                    holdings.remove(i);
                }
                return;
            }}
        System.out.println("Stock not found in portfolio.");
    }
    public List<StockHolding> getHoldings() {
        return holdings;
    }}

//3)StockHolding class: Represents the holding of a particular stock in the portfolio.
//stock: A Stock object representing the stock.
//quantity: The number of shares of the stock.
//Constructor: Initializes the stock and quantity fields.
//Getters (getStock, getQuantity): Return the stock and quantity held.
//addQuantity method: Adds more shares to the existing stock holding.
//removeQuantity method: Removes shares from the holding, checking if enough shares are available.
class StockHolding {
    private Stock stock;
    private int quantity;
    public StockHolding(Stock stock, int quantity) {
        this.stock = stock;
        this.quantity = quantity;
    }
    public Stock getStock() {

        return stock;
    }
    public int getQuantity()
    {
        return quantity;
    }
    public void addQuantity(int quantity) {

        this.quantity += quantity;
    }
    public void removeQuantity(int quantity) {
        if (this.quantity>=quantity) {
            this.quantity-=quantity;
        } else {
            System.out.println("Not enough shares to sell.");
        }}}

//4)SimpleStockTrading class: The main class that contains the program logic.
//marketData: A static list containing the available stocks in the market.
//portfolio: A static Portfolio object to manage the user's stock holdings.
//main method: The entry point of the program.
//Initializes marketData with some predefined stocks.
//Creates a Scanner object to read user input.
//The program runs in an infinite loop (while (true)), presenting the user with a menu to choose an option:
//Case 1: Displays the market data.
//Case 2: Allows the user to buy a stock by entering the symbol, price, and quantity.
//Case 3: Allows the user to sell a stock by entering the symbol and quantity.
//Case 4: Displays the current portfolio.
//Case 5: Exits the program.
//If the user inputs an invalid choice, the program informs them and re-displays the menu.

public class SimpleStockTrading {
    private static List<Stock> marketData;
    private static Portfolio portfolio;
    public static void main(String[] args) {
        marketData = new ArrayList<>();
        portfolio = new Portfolio();

        marketData.add(new Stock("Tesla", 200.30));
        marketData.add(new Stock("Amazon", 3020.42));
        marketData.add(new Stock("Meta", 980.88));

        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("\nMenu:");
            System.out.println("1. Display Market Data");
            System.out.println("2. Buy Stock");
            System.out.println("3. Sell Stock");
            System.out.println("4. Display Portfolio");
            System.out.println("5. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            switch (choice) {
                case 1:
                    displayMarketData();
                    break;
                case 2:
                    System.out.print("Enter stock symbol to buy: ");
                    String buySymbol = scanner.nextLine();
                    System.out.print("Enter stock price: ");
                    double buyPrice = scanner.nextDouble();
                    System.out.print("Enter quantity to buy: ");
                    int buyQuantity = scanner.nextInt();
                    scanner.nextLine();
                    buyStock(buySymbol, buyPrice, buyQuantity);
                    break;
                case 3:
                    System.out.print("Enter stock symbol to sell: ");
                    String sellSymbol = scanner.nextLine();
                    System.out.print("Enter quantity to sell: ");
                    int sellQuantity = scanner.nextInt();
                    scanner.nextLine(); // Consume newline
                    sellStock(sellSymbol, sellQuantity);
                    break;
                case 4:
                    displayPortfolio();
                    break;
                case 5:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }}

    //6)displayMarketData method: Displays the list of available stocks in the market, showing the company name and price.
    private static void displayMarketData() {
        System.out.println("Market Data:");
        for (int i = 0; i < marketData.size(); i++) {
            Stock stock = marketData.get(i);
            System.out.printf("%s: $%.2f%n", stock.getCompany(), stock.getPrice());
        }}
    //7)buyStock method: Adds the specified stock to the portfolio and confirms the purchase by printing a message.
    private static void buyStock(String symbol, double price, int quantity) {
        portfolio.addStock(symbol, price, quantity);
        System.out.println("Bought " + quantity + " shares of " + symbol);
    }

    //8)sellStock method: Removes the specified stock from the portfolio and confirms the sale by printing a message.
    private static void sellStock(String symbol, int quantity) {
        portfolio.removeStock(symbol, quantity);
        System.out.println("Sold " + quantity + " shares of " + symbol);
    }
    //9)displayPortfolio method: Displays the user's current stock holdings, including the company name, quantity of shares, and the price of each share.
    private static void displayPortfolio() {
        System.out.println("Portfolio:");
        List<StockHolding> holdings = portfolio.getHoldings();
        for (int i = 0; i < holdings.size(); i++) {
            StockHolding holding = holdings.get(i);
            Stock stock = holding.getStock();
            System.out.printf("%s: %d shares @ $%.2f each%n", stock.getCompany(), holding.getQuantity(), stock.getPrice());
        }}}
