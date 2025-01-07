# travel
import java.util.ArrayList;
import java.util.Scanner;

class Destination {
    private String name;
    private String startDate;
    private String endDate;
    private double budget;

    public Destination(String name, String startDate, String endDate, double budget) {
        this.name = name;
        this.startDate = startDate;
        this.endDate = endDate;
        this.budget = budget;
    }

    public String getName() {
        return name;
    }

    public String getStartDate() {
        return startDate;
    }

    public String getEndDate() {
        return endDate;
    }

    public double getBudget() {
        return budget;
    }

    @Override
    public String toString() {
        return "Destination: " + name + "\n" +
               "Travel Dates: " + startDate + " to " + endDate + "\n" +
               "Budget: ₹" + budget + "\n";
    }
}

public class TravelItineraryPlanner {
    private static ArrayList<Destination> itinerary = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("\nTravel Itinerary Planner");
            System.out.println("1. Add a Destination");
            System.out.println("2. View Itinerary");
            System.out.println("3. Calculate Total Budget");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume the newline character

            switch (choice) {
                case 1: // Add a Destination
                    System.out.print("Enter destination name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter start date (YYYY-MM-DD): ");
                    String startDate = scanner.nextLine();
                    System.out.print("Enter end date (YYYY-MM-DD): ");
                    String endDate = scanner.nextLine();
                    System.out.print("Enter budget for this destination: ₹");
                    double budget = scanner.nextDouble();

                    itinerary.add(new Destination(name, startDate, endDate, budget));
                    System.out.println("Destination added successfully!");
                    break;

                case 2: // View Itinerary
                    if (itinerary.isEmpty()) {
                        System.out.println("Your itinerary is empty.");
                    } else {
                        System.out.println("\nYour Travel Itinerary:");
                        for (Destination dest : itinerary) {
                            System.out.println(dest);
                        }
                    }
                    break;

                case 3: // Calculate Total Budget
                    double totalBudget = 0;
                    for (Destination dest : itinerary) {
                        totalBudget += dest.getBudget();
                    }
                    System.out.println("Total budget for your trip: ₹" + totalBudget);
                    break;

                case 4: // Exit
                    System.out.println("Thank you for using the Travel Itinerary Planner. Happy travels!");
                    scanner.close();
                    return;

                default:
                    System.out.println("Invalid choice! Please select a valid option.");
            }
        }
    }
}
