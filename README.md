# Project-Hotel-booking-management-system-
This project is a simple console baa e hotel booking system built using Java.
import java.util.Scanner;

public class HotelBookingSystem {

    // Total rooms in the hotel
    static final int TOTAL_ROOMS = 10;

    // Array to store room status (false = available, true = booked)
    static boolean[] rooms = new boolean[TOTAL_ROOMS];

    static Scanner sc = new Scanner(System.in);

    public static void viewAvailableRooms() {
        System.out.println("\nAvailable Rooms:");
        boolean available = false;

        for (int i = 0; i < TOTAL_ROOMS; i++) {
            if (!rooms[i]) {
                System.out.println("Room " + (i + 1));
                available = true;
            }
        }

        if (!available) {
            System.out.println("No rooms available.");
        }
    }

    public static void bookRoom() {
        viewAvailableRooms();
        System.out.print("\nEnter room number to book: ");

        try {
            int roomNo = sc.nextInt();

            if (roomNo < 1 || roomNo > TOTAL_ROOMS) {
                System.out.println("Invalid room number.");
            } else if (rooms[roomNo - 1]) {
                System.out.println("Room already booked.");
            } else {
                rooms[roomNo - 1] = true;
                System.out.println("Room " + roomNo + " booked successfully.");
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter a number.");
            sc.next(); // clear invalid input
        }
    }

    public static void cancelBooking() {
        System.out.print("\nEnter room number to cancel booking: ");

        try {
            int roomNo = sc.nextInt();

            if (roomNo < 1 || roomNo > TOTAL_ROOMS) {
                System.out.println("Invalid room number.");
            } else if (!rooms[roomNo - 1]) {
                System.out.println("Room is not booked.");
            } else {
                rooms[roomNo - 1] = false;
                System.out.println("Booking for Room " + roomNo + " cancelled successfully.");
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter a number.");
            sc.next();
        }
    }

    public static void main(String[] args) {

        while (true) {
            System.out.println("\n--- Hotel Booking Management System ---");
            System.out.println("1. View Available Rooms");
            System.out.println("2. Book Room");
            System.out.println("3. Cancel Booking");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            try {
                int choice = sc.nextInt();

                switch (choice) {
                    case 1:
                        viewAvailableRooms();
                        break;
                    case 2:
                        bookRoom();
                        break;
                    case 3:
                        cancelBooking();
                        break;
                    case 4:
                        System.out.println("Thank you for using the system.");
                        sc.close();
                        return;
                    default:
                        System.out.println("Invalid choice. Try again.");
                }
            } catch (Exception e) {
                System.out.println("Invalid input. Please enter a number.");
                sc.next();
            }
        }
    }
}
