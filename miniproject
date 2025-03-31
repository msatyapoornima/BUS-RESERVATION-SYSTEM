package sp_pack;
import java.util.*;

class Seat 
{
		    int seatNumber;
		    int age;
		    String gender;
		    String name;
		    long phoneNo;
		    String board;
		    String dest;
		    String tim;
		    int cost;
		    boolean isBooked;
		    Seat next;

		    public Seat(int seatNumber)
		    {
		        this.seatNumber = seatNumber;
		        this.isBooked = false;
		        this.next = null;
		    }
}

public class BusReservationSystem 
{
		    private static Seat head = null;
		    private static Scanner scanner = new Scanner(System.in);
		    private static Random random = new Random();
		    private static int totalSeats = 0;

		    public static void addSeat(int seatNumber) {
		        Seat newSeat = new Seat(seatNumber);
		        if (head == null) {
		            head = newSeat;
		        } else {
		            Seat temp = head;
		            while (temp.next != null) {
		                temp = temp.next;
		            }
		            temp.next = newSeat;
		        }
		    }

		    public static boolean payment(int rate) {
		        System.out.println("\nENTER\n[1]:UPI\n[2]:Credit/ATM/Debit card\n[3]:Net banking\n[4]:Exit");
		        int choice = scanner.nextInt();
		        scanner.nextLine();

		        switch (choice) {
		            case 1:
		            case 2:
		            case 3:
		                if (captcha()) {
		                    System.out.println("\nPayment successful");
		                    return true;
		                } else {
		                    System.out.println("\nPayment not successful");
		                    return false;
		                }
		            case 4:
		                System.out.println("\nThis mode of payment is not available");
		                return false;
		            default:
		                return false;
		        }
		    }

		    public static boolean captcha() {
		        int id = random.nextInt(40001) + 1000;
		        System.out.println("CAPTCHA: " + id);
		        System.out.print("Enter the CAPTCHA: ");
		        int captchaInput = scanner.nextInt();
		        
		        for (int i = 0; i < 2; i++) {
		            if (id == captchaInput) {
		                return true;
		            } else {
		                System.out.println("Incorrect CAPTCHA..please try again");
		                captchaInput = scanner.nextInt();
		            }
		        }
		        return false;
		    }

		    public static void bookSeat(int seatNumber) {
		        Seat current = head;
		        while (current != null) {
		            if (current.seatNumber == seatNumber && !current.isBooked) {
		                current.isBooked = true;

		                scanner.nextLine(); 
		                System.out.print("Enter name: ");
		                current.name = scanner.nextLine();  
		                System.out.print("Enter age: ");
		                current.age = scanner.nextInt();
		                System.out.print("Enter gender: ");
		                current.gender = scanner.next();
		                System.out.print("Enter phone number: ");
		                current.phoneNo = scanner.nextLong();

		                System.out.println("\n[1] Bangalore to Tumkur\n[2] Bangalore to Hiriyur\n[3] Bangalore to Chitradurga\n[4] Bangalore to Ballary");
		                System.out.print("Enter your choice: ");
		                int ch = scanner.nextInt();

		                switch (ch) {
		                    case 1:
		                        current.board = "Bangalore";
		                        current.dest = "Tumkur";
		                        current.cost = 200;
		                        current.tim = "10 AM to 12 PM";
		                        break;
		                    case 2:
		                        current.board = "Bangalore";
		                        current.dest = "Hiriyur";
		                        current.cost = 300;
		                        current.tim = "10 AM to 1 PM";
		                        break;
		                    case 3:
		                        current.board = "Bangalore";
		                        current.dest = "Chitradurga";
		                        current.cost = 400;
		                        current.tim = "10 AM to 2 PM";
		                        break;
		                    case 4:
		                        current.board = "Bangalore";
		                        current.dest = "Ballary";
		                        current.cost = 600;
		                        current.tim = "10 AM to 4 PM";
		                        break;
		                    default:
		                        System.out.println("Service not available!!");
		                        return;
		                }

		                if (payment(current.cost)) {
		                    System.out.println("Seat no " + seatNumber + " has been successfully booked!");
		                } else {
		                    System.out.println("Seat no " + seatNumber + " has not been booked");
		                    current.isBooked = false;
		                }
		                return;
		            }
		            current = current.next;
		        }
		        System.out.println("\nSorry, Seat " + seatNumber + " is not available for booking.");
		    }

		    public static void viewAvailableSeats() {
		        Seat current = head;
		        System.out.println("\nThe following seats are available: ");
		        while (current != null) {
		            if (!current.isBooked) {
		                System.out.print(current.seatNumber + " ");
		            }
		            current = current.next;
		        }
		        System.out.println();
		    }

		    public static void cancelBooking(int seatNumber) {
		        Seat current = head;
		        while (current != null) {
		            if (current.seatNumber == seatNumber && current.isBooked) {
		                current.isBooked = false;
		                System.out.println("\nBooking for Seat " + seatNumber + " has been successfully cancelled!");
		                System.out.println("Refund is not available.");
		                return;
		            }
		            current = current.next;
		        }
		        System.out.println("\nNo booking was found for Seat " + seatNumber + ".");
		    }

		    public static void displaySeats() {
		        Seat current = head;
		        System.out.println("\n------------------------------------------------------------");
		        System.out.println("\t**KSP TRAVELS**");
		        System.out.println("Seat Number (Booking Status)");
		        
		        int count = 0;
		        while (current != null) {
		            System.out.printf("  %02d(%d) ", current.seatNumber, current.isBooked ? 1 : 0);
		            count++;
		            if (count % 4 == 0) {
		                System.out.println();  
		            }
		            current = current.next;
		        }
		        System.out.println("\n------------------------------------------------------------");
		    }

		    public static void displayDetails(int seatNumber) {
		        Seat current = head;
		        while (current != null) {
		            if (current.seatNumber == seatNumber && current.isBooked) {
		                System.out.println("\n**");
		                System.out.println("~KSP TRAVELS");
		                System.out.println("--------------------------------------");
		                System.out.println("Name: " + current.name);
		                System.out.println("Age: " + current.age);
		                System.out.println("Gender: " + current.gender);
		                System.out.println("Phone: " + current.phoneNo);
		                System.out.println("Seat Number: " + current.seatNumber);
		                System.out.println("Boarding Point: " + current.board);
		                System.out.println("Destination: " + current.dest);
		                System.out.println("Time: " + current.tim);
		                System.out.println("Cost: " + current.cost);
		                System.out.println("Payment: Successful");
		                System.out.println("--------------------------------------");
		                System.out.println("**\n");
		                return;
		            }
		            current = current.next;
		        }
		        System.out.println("\nSeat not booked!!!");
		    }

		    public static void main(String[] args) {
		        while (true) {
		            System.out.println("\n\n~~\nBus Reservation System");
		            System.out.println("[1] Add Seat");
		            System.out.println("[2] Book Seat");
		            System.out.println("[3] View Available Seats");
		            System.out.println("[4] Cancel Booking");
		            System.out.println("[5] Display Seats");
		            System.out.println("[6] Display Details");
		            System.out.print("Enter your choice: ");
		            int choice = scanner.nextInt();

		            switch (choice) {
		                case 1:
		                    System.out.print("Enter number of seats: ");
		                    totalSeats = scanner.nextInt();
		                    for (int i = 1; i <= totalSeats; i++) addSeat(i);
		                    break;
		                case 2:
		                    System.out.print("Enter seat number to be booked: ");
		                    bookSeat(scanner.nextInt());
		                    break;
		                case 3:
		                    viewAvailableSeats();
		                    break;
		                case 4:
		                    System.out.print("Enter seat number to cancel: ");
		                    cancelBooking(scanner.nextInt());
		                    break;
		                case 5:
		                    displaySeats();
		                    break;
		                case 6:
		                    System.out.print("Enter seat number: ");
		                    displayDetails(scanner.nextInt());
		                    break;
		                default:
		                    System.exit(0);
		            }
		        }
		    }
}
		



