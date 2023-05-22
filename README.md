
#include <iostream>
#include <string>
#include <limits>
#include <iomanip>

using namespace std;
char Private ();
char Business ();
char Regular ();
char travelType, x;
bool invalidInput = true;

int main() {
    char travelType, destination, insuranceSelection;
    int numBags = 0, baggageFee = 0, insuranceFee = 0, maxCapacity, headCount, availableSeats, fare, numPassengers[120], extraBaggage, extraBaggageCost, seniorDiscount, totalCost, extraFee;
    double travelfare = 0.0, transactionFee, travelTax, totalFare, farePerPassenger;
    string airplaneType;

    cout << "\nWelcome to COMPFUNION AIRLINE TICKETING SERVICE!\n" << endl;
    cout << "Please press any key to continue...";
    cout << endl;
    
	cout << "\n\"1\" for Local Flight\n\"2\" for International Flight" << endl;
	int travType;
	cout << "\n Please input Travel Type [1/2]: ";
	cin >> travType;
	
	while (cin.fail() || travType < 1 || travType > 2) {
	    cout << "Invalid input! Please enter 1 for Local Flight or 2 for International Flight: ";
	    cin.clear();
	    cin.ignore(numeric_limits<streamsize>::max(), '\n');
	    cin >> travType;
	}

type:
	
	if (travType ==1){
	
	// Display the travel destinations
	cout << "\n                      TRAVEL DESTINATION\n";
    cout << "\n__________________________________________________________________";
    cout << "\n| OPTION |      FROM      |       TO         |     TRAVEL TYPE    |";
    cout << "\n|````````|````````````````|``````````````````|````````````````````|";
    cout << "\n|   A    |     MANILA     |     BATANES      |                    |";
    cout << "\n|````````|````````````````|``````````````````|                    |";
    cout << "\n|   B    |     BATANES    |      MANILA      |     LOCAL FLIGHT   |";
    cout << "\n|````````|````````````````|``````````````````|                    |";
    cout << "\n|   C    |     MANILA     |     PALAWAN      |                    |";
    cout << "\n|````````|````````````````|``````````````````|                    |";
    cout << "\n|   D    |     PALAWAN    |      MANILA      |                    |";
    cout << "\n|________|________________|__________________|____________________|";
	cout << "\n\nPlease select your travel destination: ";
	cin >> destination;
	
		// Prompt the user for their travel type
	cout << "\nChoose your travel type. " << endl;
	cout << "  (P) Private \n  (B) Business \n  (R) Regular " << endl;
	cout << "Enter your travel type (P/B/R): ";
	cin >> travelType;
	
	// Define constants for the fare rates
	const double A_P = 8000.00;
	const double A_B = 12500.00;
	const double A_R = 3500.00;
	const double B_P = 9800.00;
	const double B_B = 12950.00;
	const double B_R = 3900.00;
	const double C_P = 9100.00;
	const double C_B = 10500.00;
	const double C_R = 3200.00;
	const double D_P = 9850.00;
	const double D_B = 10975.00;
	const double D_R = 3575.00;
	
	
	// Calculate fare based on destination and travel type
	double travelfare;
	switch(destination) {
		case 'A':
		case 'a':
	switch(travelType) {
		case 'P': fare = A_P; break;
		case 'p': fare = A_P; break;
		case 'B': fare = A_B; break;
		case 'b': fare = A_B; break;
		case 'R': fare = A_R; break;
		case 'r': fare = A_R; break;
		}
		cout << "\nYou have chosen Local Flight from Manila to Batanes.\n"<< endl;
		break;
	case 'B':
	case 'b':
	switch(travelType) {
		case 'P': fare = B_P; break;
		case 'p': fare = B_P; break;
		case 'B': fare = B_B; break;
		case 'b': fare = B_B; break;
		case 'R': fare = B_R; break;
		case 'r': fare = B_R; break;
		}
		cout << "\nYou have chosen Local Flight from Batanes to Manila.\n"<< endl;
		break;
	case 'C':
	case 'c':
	switch(travelType) {
		case 'P': fare = C_P; break;
		case 'p': fare = C_P; break;
		case 'B': fare = C_B; break;
		case 'b': fare = C_B; break;
		case 'R': fare = C_R; break;
		case 'r': fare = C_R; break;
		}
		cout << "\nYou have chosen Local Flight from Manila to Palawan.\n"<< endl;
		break;
	case 'D':
	case 'd':
	switch(travelType) {
		case 'P': fare = D_P; break;
		case 'p': fare = D_P; break;
		case 'B': fare = D_B; break;
		case 'b': fare = D_B; break;
		case 'R': fare = D_R; break;
		case 'r': fare = D_R; break;
		}
		cout << "\nYou have chosen Local Flight from Palawan to Manila.\n"<< endl;
		break;
	default:
        cout << "Invalid Input\n";
    }
    
	// Use a switch statement to execute different code based on the user's input
	// Set variables based on airplane type
	switch(travelType) {
    case 'P':
    case 'p':
        maxCapacity = 20;
        headCount = 6; // 2 pilots and 4 stewardesses
        transactionFee = 550.00;
        travelTax = 4260.00;
        cout << "You have selected Private." << endl;
        break;
    case 'B':
    case 'b':
        maxCapacity = 30;
        headCount = 7; // 2 pilots, 1 assistant pilot, and 4 stewardesses
        transactionFee = 550.00;
        travelTax = 5700.00;
        cout << "You have selected Business." << endl;
        break;
    case 'R':
    case 'r':
        maxCapacity = 100;
        headCount = 52; // 2 pilots, 2 assistant pilots, 8 stewardesses, and 40 reserved/taken seats
        transactionFee = 255.00;
        travelTax = 2500.00;
        cout << "You have selected Regular." << endl;
        break;
    default:
        // Invalid airplane type
        cout << "Invalid airplane type entered." << endl;
}

	// Calculate available seats
	availableSeats = maxCapacity - headCount;
	
	// Input the number of available seats for chosen Airline Type
	cout << "\nAvailable Seats: " << availableSeats << endl;

  cout << "\nHow many passengers are travelling? ";
    cin >> headCount;

    // Create a loop to iterate through the number of passengers
    for (int i = 0; i < headCount; i++) {

        // Prompt the user for the passenger's name
        string firstName, middleInitial, lastName;
        cout << "\nEnter Passenger " << i + 1 << "'s Name: ";
        cin >> firstName >> middleInitial >> lastName;

        // Check if the name contains any numerics
        bool isNumeric = false;
        for (int j = 0; j < firstName.length(); j++) {
            if (isdigit(firstName[j])) {
                isNumeric = true;
                break;
            }
        }
        for (int j = 0; j < middleInitial.length(); j++) {
            if (isdigit(middleInitial[j])) {
                isNumeric = true;
                break;
            }
        }
        for (int j = 0; j < lastName.length(); j++) {
            if (isdigit(lastName[j])) {
                isNumeric = true;
                break;
            }
        }
        if (isNumeric) {
            cout << "Invalid name. Please enter a name without any numerics." << endl;
            i--;
            continue;
        }

        // Prompt the user for the passenger's age
        int passengerAge;
        cout << "\nEnter " << firstName << " " << middleInitial << " " << lastName << "'s Age: ";
        cin >> passengerAge;

        // Check if the age contains any letters
        if (cin.fail()) {
            cout << "Invalid age. Please enter a valid age." << endl;
            cin.clear();
            cin.ignore(10000, '\n');
            i--;
            continue;
        }

        // Apply child discount
        if (passengerAge >= 1 && passengerAge < 18) {
            cout << "\nPassenger " << i+1 << " is a child and cannot travel alone." << endl;
        }

        // Apply senior discount
        else if (passengerAge >= 59) {
            // 20% senior discount
            cout << "\nPassenger " << i+1 << " is eligible for a 20% senior discount." << endl;
    		 seniorDiscount = 20;    
		}

		// Calculate baggage fee based on class type
	switch(travelType) {
	    case 'P': baggageFee = 1250; extraBaggageCost = 1250; break;
	    case 'p': baggageFee = 1250; extraBaggageCost = 1250; break;
	    case 'B': baggageFee = 2850; extraBaggageCost = 2850; break;
	    case 'b': baggageFee = 2850; extraBaggageCost = 2800; break;
	    case 'R': baggageFee = 950; extraBaggageCost = 950; break;
	    case 'r': baggageFee = 950; extraBaggageCost = 950; break;
	    default: 
	        cout << "Invalid travel class\n"; 
	        return 0;
	
	// Prompt the user for extra baggage
	cout << "\nDo you want check in extra baggage?\n";
	cout << "  (Y) Yes \n  (N) No" << endl;
	cout << "Enter your choice (Y/N): ";
	cin >> extraBaggage;
	
		
	// Calculate insurance fee based on user selection
	switch (extraBaggage) {
	    case 'Y': extraFee = baggageFee + extraBaggageCost; break;
	    case 'N': extraFee = 0; break;
	    cout << "Extra Baggage Fee: \n" << extraFee; break;
	
	}

	}

	// Calculate insuranceFee based on class type
	switch(travelType) {
    	case 'P': insuranceFee = 4500; break;
    	case 'p': insuranceFee = 4500; break;
    	case 'B': insuranceFee = 6500; break;
    	case 'b': insuranceFee = 6500; break;
    	case 'R': insuranceFee = 950; break;
    	case 'r': insuranceFee = 950; break;
    	default:
			cout << "Invalid travel class\n"; break;
	}
	
	// Prompt the user for insurance selection
	cout << "\nDo you want to purchase travel insurance?\n";
	cout << "  (Y) Yes \n  (N) No" << endl;
	cout << "Enter your choice (Y/N): ";
	cin >> insuranceSelection;

	// Calculate insurance fee based on user selection
	switch (insuranceSelection) {
    	case 'Y': insuranceFee *= 1; break;
    	case 'N': insuranceFee = 0; break;
    	default:
			cout << "Invalid insurance selection\n"; return 0;
	}

	// Print the final receipt
	cout << "\n=========================================================" << endl;
	cout << "                \nCOMPFUNIONS AIRLINE RECEIPT\n                 ";
	
	// Display passenger information and fare
	cout << "\nPassenger " << i+1 << " Receipt" << endl;
	cout << "\nPassenger Name:                                  " << firstName << " " << middleInitial << " " << lastName << endl;
	cout << "Passenger Age:                                     " << passengerAge << endl;
	// Check if the passenger is eligible for a senior discount
	if (passengerAge >= 59) {
	    cout << "\nSenior Discount:                                   " << seniorDiscount * 1 << "%" << endl;
	}
	cout << "Travel Type:                                       " << travelType << endl;
	cout << "Travel Fare:                                       " << fare << endl;
	cout << "Transaction Fee:                                   " << transactionFee << endl;
	cout << "Travel Tax:                                        " << travelTax << endl;
	cout << "Baggage Fee:                                       " << baggageFee << endl;
	cout << "Extra Baggage Fee:                                 " << extraBaggageCost << endl;
	cout << "Travel Insurance:                                  " << insuranceFee << endl;
	
	// Calculate total cost with the senior discount
	double totalCostWithDiscount = totalCost * (1 - seniorDiscount);
	
	// Calculate total cost
	double totalCost = fare + transactionFee + travelTax + baggageFee + extraBaggageCost + insuranceFee;
	
	cout << "\nTotal Cost:                                        " << totalCost << endl;
	
	cout << "\nTotal Cost with Discount:                          " << totalCostWithDiscount << endl;

	
	return 0;
	}}}

	
	
		
		
		
