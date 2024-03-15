
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace PFProjectFinal
{
    internal class Program
    {
        static string[][] ch1;
        static string[,] name = new string[32, 100];
        static string[,] number = new string[32, 2];
        static int[] num1 = new int[32];
        static void Main()
        {
            int choice;
            Console.WriteLine("\n\n\tBUS RESERVATION SYSTEM");
            Console.WriteLine("\n\n[1] Login As Admin\n\n[2] Login As Passenger\n\n");
            Console.Write("Enter your choice: ");
            choice = int.Parse(Console.ReadLine());

            switch (choice)
            {
                case 1:
                    Admin();
                    break;
                case 2:
                    Passenger();
                    break;
            }

            if (choice > 2)
            {
                Console.Clear();
                Console.WriteLine("\n Entered wrong input, Please enter correct one!");
                Main();              
            }
        }

        static void PassengerLogin()
        {
            int a = 0;
            string uname, pword;
            string user = "admin";
            string pass = "admin";

            do
            {
                Console.Clear();
                Console.WriteLine("\n\n\tBUS RESERVATION");
                Console.WriteLine("\n\nPASSENGER LOGIN FORM");
                Console.Write("\n\nENTER USERNAME: ");
                uname = Console.ReadLine();
                Console.Write("\nENTER PASSWORD: ");
                pword = Console.ReadLine();
                Console.WriteLine();

                if (hihi(uname))
                {
                    if (uname == user && pword == pass)
                    {
                        Console.WriteLine("\nWELCOME USER!!!!!");
                        Console.WriteLine("\n\nPress any key to continue...");
                        Console.ReadKey();
                        break;
                    }
                    else
                    {
                        Console.WriteLine("\nLOGIN IS UNSUCCESSFUL. PLEASE TRY AGAIN...");
                        a++;
                        Console.ReadKey();
                    }
                }
                else
                {
                    Console.WriteLine("\n  Your username contains numbers or invalid inputs! Press any key to try again.");
                    a++;
                    Console.ReadKey();
                }

            } while (a <= 2);

            if (a > 2)
            {
                Console.WriteLine("\nSorry, you have entered the wrong username and password four times!!!");
                Console.ReadKey();
            }
            Console.Clear();
        }

        static void AdminLogin()
        {
            int a = 0;
            string passengerName, password;

            do
            {
                Console.Clear();
                Console.WriteLine("\n\n\tBUS RESERVATION");
                Console.WriteLine("\n\nADMIN LOGIN FORM");
                Console.Write("\n\nENTER USERNAME: ");
                passengerName = Console.ReadLine();
                Console.Write("\nENTER PASSWORD: ");
                password = Console.ReadLine();

                if (hihi(passengerName))
                {
                    if (passengerName == password)
                    {
                        Console.WriteLine("\n\nWELCOME SIR/MAM!");
                        Console.WriteLine("\n\nPLEASE PRESS ANY KEY TO CONTINUE");
                        Console.ReadKey();
                        break;
                    }
                    else
                    {
                        Console.WriteLine("\n\nYOUR PASSWORD IS INCORRECT. PLEASE TRY AGAIN");
                        a++;
                        Console.ReadKey();
                    }
                }
                else
                {
                    Console.WriteLine("\n  Your username contains numbers or invalid inputs! Press any key to try again.");
                    a++;
                    Console.ReadKey();
                }

            } while (a <= 2);

            if (a > 2)
            {
                Console.WriteLine("\nYOU CANNOT LOGIN. YOUR PASSWORD WAS INCORRECT");
                Console.ReadKey();
            }
            Console.Clear();
        }

        static void Admin()
        {
            AdminLogin();
            int num;

            do
            {
                Console.Clear();
                Console.WriteLine("\n\n\tBUS RESERVATION");
                Console.WriteLine("\nMAIN MENU");
                Console.WriteLine("\n[1] Create Bus Schedule\n[2] View Bus Schedule\n[3] View Customer Records\n[4] Back to Login Page\n[5] Exit");
                Console.Write("\nENTER YOUR CHOICE: ");
                num = int.Parse(Console.ReadLine());

                switch (num)
                {
                    case 1:
                        Schedule();
                        break;
                    case 2:
                        Bus();
                        break;
                    case 3:
                        Records();
                        break;
                    case 4:
                        Console.Clear();
                        Main();
                        break;
                }
                Console.ReadKey();
            } while (num != 5);
            Console.Clear();
            Console.WriteLine("\n\nTHANK YOU FOR USING THIS BUS RESERVATION SYSTEM");
            Console.ReadKey();
        }

        static void Passenger()
        {
            PassengerLogin();
            int num;

            do
            {
                Console.Clear();
                Console.WriteLine("\n\n\tBUS RESERVATION");
                Console.WriteLine("\nMAIN MENU");
                Console.WriteLine("\n[1] View Bus List\n[2] Book Tickets\n[3] Cancel Booking\n[4] Bus Status Board\n[5] Back to Login Page\n[6] ROUTES\n[7] Exit");
                Console.Write("\nENTER YOUR CHOICE: ");
                num = int.Parse(Console.ReadLine());

                switch (num)
                {
                    case 1:
                        Bus();
                        break;
                    case 2:
                        Booking();
                        break;
                    case 3:
                        Cancel();
                        break;
                    case 4:
                        Status();
                        break;
                    case 5:
                        Console.Clear();
                        Main();
                        break;
                    case 6:
                        Console.Clear();
                        VRoutes();
                        break;
                }
                Console.ReadKey();
            } while (num != 7);
            Console.Clear();
            Console.WriteLine("\n\nTHANK YOU FOR USING THIS BUS RESERVATION SYSTEM");
            Console.ReadKey();
        }

        static void VRoutes()
        {
            StreamWriter sw = new StreamWriter("routes.txt");
            ch1 = new string[6][];
            ch1[0] = new[] { "      Bus", "               Route", "                  Time" };
            ch1[1] = new[] { "1: Liyari Express", "  Karachi to Lahore", "   Departure time: 4:00am" };
            ch1[2] = new[] { "2: Niazi Travellers", "Karachi to Hyderabad", "Departure time: 7:00am" };
            ch1[3] = new[] { "3: Daewoo", "          Karachi to Thatta", "   Departure time: 8:00am" };
            ch1[4] = new[] { "4: Fast Travellers", " Karachi to Shakhar", "  Departure time: 10:00am" };
            ch1[5] = new[] { "5: Faisal Movers", "   Karachi to Punjab", "   Departure time: 11:30am" };

            for (int i = 0; i < ch1.GetLength(0); i++)
            {
                for (global::System.Int32 j = 0; j < ch1[i].Length; j++)
                {
                    sw.Write(ch1[i][j] + "                 ");
                }
                sw.WriteLine();
                sw.WriteLine();
            }
            sw.Close();

            string routes = "C:/Users/glab/Desktop/BankManagmentSystem/hanitry/hanitry/bin/Debug/routes.txt";
            try
            {
                string[] lines = File.ReadAllLines(routes);

                foreach (string item in lines)
                {
                    Console.WriteLine(item);
                }
            }
            catch (FileNotFoundException)
            {
                Console.WriteLine("File not found: " + routes);
            }

            Console.ReadKey();
        }

        static void Bus()
        {
            Console.Clear();
            Console.WriteLine("\n\n\tBUS RESERVATION");
            Console.WriteLine("\n\nBus List: ");
            for (int i = 1; i <= 5; i++)
            {
                Console.WriteLine("\nBus {0} Name: {1}", i, name[i, 0]);
                Console.WriteLine("Bus {0} Number: {1}", i, number[i, 0]);
                Console.WriteLine("Total number of seats: {0}", num1[i]);
                Console.WriteLine("\n\n");
            }

            Console.ReadKey();
        }

        static void Booking()
        {
            Console.Clear();
            Console.WriteLine("\n\n\tBUS RESERVATION");
            Console.WriteLine("\n\n");
            Console.Write("Enter Bus Number: ");
            string busNo = Console.ReadLine();
            int index = 0;
            for (int i = 1; i <= 5; i++)
            {
                if (number[i, 0] == busNo)
                {
                    index = i;
                    break;
                }
            }

            Console.WriteLine("\n\n");
            Console.Write("Enter number of seats to book: ");
            int seat = int.Parse(Console.ReadLine());

            if (seat <= num1[index])
            {
                num1[index] -= seat;
                Console.WriteLine("\nBooking successful!!!");
                Console.WriteLine("\nYour bus is: {0}", name[index, 0]);
                Console.WriteLine("Bus Number is: {0}", number[index, 0]);
                Console.WriteLine("Total number of seats available now: {0}", num1[index]);
            }
            else
            {
                Console.WriteLine("\nSorry, not enough seats available.");
            }


            Console.ReadKey();
        }

        static void Cancel()
        {
            Console.Clear();
            Console.WriteLine("\n\n\tBUS RESERVATION");
            Console.WriteLine("\n\n");
            Console.Write("Enter Bus Number: ");
            string busNo = Console.ReadLine();
            int index = 0;
            for (int i = 1; i <= 5; i++)
            {
                if (number[i, 0] == busNo)
                {
                    index = i;
                    break;
                }
            }

            Console.WriteLine("\n\n");
            Console.Write("Enter number of seats to cancel: ");
            int seat = int.Parse(Console.ReadLine());

            if ((seat + num1[index]) <= 30)
            {
                num1[index] += seat;
                Console.WriteLine("\nBooking canceled successfully!!!");
                Console.WriteLine("\nYour bus is: {0}", name[index, 0]);
                Console.WriteLine("Bus Number is: {0}", number[index, 0]);
                Console.WriteLine("Total number of seats available now: {0}", num1[index]);
            }
            else
            {
                Console.WriteLine("\nInvalid! Maximum 30 seats are allowed.");
            }

            Console.ReadKey();
        }

        static void Status()
        {
            Console.Clear();
            Console.WriteLine("\n\n\tBUS RESERVATION");
            Console.WriteLine("\n\nBus Status Board: ");
            for (int i = 1; i <= 5; i++)
            {
                Console.WriteLine("\nBus {0} Name: {1}", i, name[i, 0]);
                Console.WriteLine("Bus {0} Number: {1}", i, number[i, 0]);
                Console.WriteLine("Total number of seats: {0}", num1[i]);
                Console.WriteLine("\n\n");
            }
            Console.ReadKey();
        }

        static void Schedule()
        {
            Console.Clear();
            Console.WriteLine("\n\n\tBUS RESERVATION");
            Console.WriteLine("\n\n");
            Console.Write("Enter total number of Buses: ");
            int n = int.Parse(Console.ReadLine());

            Console.WriteLine("\n\n");
            for (int i = 1; i <= n; i++)
            {
                Console.Write("\nEnter Bus {0} Number: ", i);
                number[i, 0] = Console.ReadLine();
                Console.Write("\nEnter Bus {0} Name: ", i);
                name[i, 0] = Console.ReadLine();
                Console.Write("\nEnter total number of seats: ");
                num1[i] = int.Parse(Console.ReadLine());
                Console.WriteLine("\n\n");
            }

            Console.ReadKey();
        }

        static void Records()
        {
            Console.Clear();
            Console.WriteLine("\n\n\tBUS RESERVATION");
            Console.WriteLine("\n\n");
            Console.Write("\nEnter total number of Buses: ");
            int n = int.Parse(Console.ReadLine());

            Console.WriteLine("\n\n");
            for (int i = 1; i <= n; i++)
            {
                Console.WriteLine("\nBus {0} Name: {1}", i, name[i, 0]);
                Console.WriteLine("Bus {0} Number: {1}", i, number[i, 0]);
                Console.WriteLine("Total number of seats: {0}", num1[i]);
                Console.WriteLine("\n\n");
            }

            Console.ReadKey();
        }

        static bool hihi(string uname)
        {
            foreach (char item in uname)
            {
                if (char.IsDigit(item))
                {
                    return false;
                }
            }
            return true;
        }
    }
}

