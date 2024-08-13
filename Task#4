import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

//1)Room class: Represents a room in the hotel with a room number (roomNumber), type (type), price (price), and availability status (Available).
//Constructor: Initializes the room with a number, type, price, and sets it as available by default.
//Getters (getRoomNumber, getType, getPrice): Return the room's number, type, and price.
//Available method: Checks if the room is available.
//setAvailable method: Sets the room's availability status.
//toString method: Returns a string representation of the room, useful for printing its details.

class Room {
    public int roomNumber;
    public String type;
    public double price;
    public boolean Available;

    public Room(int roomNumber,String type,double price) {
        this.roomNumber=roomNumber;
        this.type =type;
        this.price=price;
        this.Available=true;
    }
    public int getRoomNumber()
    {
        return roomNumber;
    }

    public String getType()
    {
        return type;
    }

    public double getPrice()
    {
        return price;
    }

    public boolean Available() {
        return Available;
    }

    public void setAvailable(boolean Available) {
        this.Available = Available;
    }

    @Override
    public String toString() {
        return "Room{" +
                "roomNumber=" + roomNumber +
                ", type='" + type + '\'' +
                ", price=" + price +
                ", Available=" + Available +
                '}';}}

//2)Reservation class: Represents a reservation made by a customer.
//Fields: customerName, room (which is a Room object), checkInDate, checkOutDate, and amountPaid.
//Constructor: Initializes all the fields when a reservation is made.
//toString method: Returns a string representation of the reservation, which is useful for displaying reservation details.

class Reservation {
    private String customerName;
    private Room room;
    private String checkInDate;
    private String checkOutDate;
    private double amountPaid;

    public Reservation(String customerName, Room room, String checkInDate, String checkOutDate, double amountPaid) {
        this.customerName = customerName;
        this.room = room;
        this.checkInDate = checkInDate;
        this.checkOutDate = checkOutDate;
        this.amountPaid = amountPaid;
    }

    @Override
    public String toString() {
        return "Reservation{" +
                "customerName='" + customerName + '\'' +
                ", room=" + room +
                ", checkInDate='" + checkInDate + '\'' +
                ", checkOutDate='" + checkOutDate + '\'' +
                ", amountPaid=" + amountPaid +
                '}';
    }}

//3)Hotel class: Manages rooms and reservations in the hotel.
//rooms: A list of all the rooms in the hotel.
//reservations: A list of all reservations made by customers.
//Constructor: Initializes the room and reservation lists, then populates the room list with predefined rooms.
//initializeRooms method: Adds a set of predefined rooms to the hotel with specific room numbers, types, and prices

public class Hotel {
    private List<Room> rooms;
    private List<Reservation> reservations;

    public Hotel() {
        rooms = new ArrayList<>();
        reservations = new ArrayList<>();
        initializeRooms();
    }

    private void initializeRooms() {
        rooms.add(new Room(101, "Single", 50));
        rooms.add(new Room(102, "Single", 50));
        rooms.add(new Room(201, "Double", 80));
        rooms.add(new Room(202, "Double", 80));
        rooms.add(new Room(301, "Suite", 120));
        rooms.add(new Room(302, "Suite", 120));
    }

    public List<Room> searchAvailableRooms(String type) {
        List<Room> availableRooms = new ArrayList<>();
        for (int i = 0; i < rooms.size(); i++) {
            Room room = rooms.get(i);
            if (room.getType().equalsIgnoreCase(type) && room.Available()) {
                availableRooms.add(room);
            }
        }
        return availableRooms;
    }
//4)makeReservation method: Creates a reservation for a customer.
//It first finds the room by its number using the findRoomByNumber method.
//If the room is found and available, it sets the room to unavailable, creates a new reservation, and adds it to the reservation list.
//If the room is not found or unavailable, it displays an error message.
    public void makeReservation(String customerName, int roomNumber, String checkInDate, String checkOutDate, double amountPaid) {
        Room room = findRoomByNumber(roomNumber);
        if (room != null && room.Available()) {
            room.setAvailable(false);
            Reservation reservation = new Reservation(customerName, room, checkInDate, checkOutDate, amountPaid);
            reservations.add(reservation);
            System.out.println("Reservation made successfully!");
        } else {
            System.out.println("Room not available or invalid room number.");
        }
    }
//5)viewReservations method: Displays all reservations made so far.
//It loops through the list of reservations and prints each one using the toString method of the Reservation class.
    public void viewReservations() {
        for (int i = 0; i < reservations.size(); i++) {
            System.out.println(reservations.get(i));
        }
    }
//6)findRoomByNumber method: Looks for a room by its room number.
//It loops through all the rooms and returns the room with the matching number. If no room is found, it returns null.
    private Room findRoomByNumber(int roomNumber) {
        for (int i = 0; i < rooms.size(); i++) {
            Room room = rooms.get(i);
            if (room.getRoomNumber() == roomNumber) {
                return room;
            }
        }
        return null;
    }
//main method: The entry point of the program.
//Hotel Initialization: Creates an instance of the Hotel class.
//User Interaction: Runs a loop that continuously asks the user to choose an option from the menu:
//Search available rooms: Asks for the room type and displays available rooms of that type.
//Make a reservation: Collects customer details and makes a reservation.
//View reservations: Displays all reservations made so far.
//Exit: Exits the program.
//Scanner: Used to read the user's input for each option.

    public static void main(String[] args) {
        Hotel hotel = new Hotel();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nHotel Reservation System");
            System.out.println("1. Search available rooms");
            System.out.println("2. Make a reservation");
            System.out.println("3. View reservations");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int option = scanner.nextInt();
            scanner.nextLine();

            switch (option) {
                case 1:
                    System.out.print("Enter room type (Single/Double/Suite):");
                    String type = scanner.nextLine();
                    List<Room> availableRooms = hotel.searchAvailableRooms(type);
                    if (availableRooms.isEmpty()) {
                        System.out.println("No rooms available.");
                    } else {
                        for (int i = 0; i < availableRooms.size(); i++) {
                            System.out.println(availableRooms.get(i));
                        }
                    }
                    break;
                case 2:
                    System.out.print("Enter customer name: ");
                    String customerName = scanner.nextLine();
                    System.out.print("Enter room number: ");
                    int roomNumber = scanner.nextInt();
                    scanner.nextLine();
                    System.out.print("Enter check-in date (DD-MM-YYYY): ");
                    String checkInDate = scanner.nextLine();
                    System.out.print("Enter check-out date (DD-MM-YYYY): ");
                    String checkOutDate = scanner.nextLine();
                    System.out.print("Enter amount to pay: ");
                    double amountPaid = scanner.nextDouble();
                    scanner.nextLine();
                    hotel.makeReservation(customerName, roomNumber, checkInDate, checkOutDate, amountPaid);
                    break;
                case 3:
                    hotel.viewReservations();
                    break;
                case 4:
                    System.out.println("EXIT.Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Please try again.");
            }
        }}}
