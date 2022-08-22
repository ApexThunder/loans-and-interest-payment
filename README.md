#include<iostream>
#include<fstream>
using namespace std;

int main()
{
//these are variables for principle amount ,time , rate and result;
float arr[3], I, J;

/* Step 2: Declare new variables */
ofstream outfile;
ifstream infile;
string line;

//this is for storing the choice of user
int choice;
cout << "..........................................................................." << endl;
cout << "-------------------------------EMI CALCULATOR------------------------------" << endl;
cout << "..........................................................................." << endl;
//while loop used for validation and generate menu for the program.
while (1)
{

// this is the menu
cout << "\nMENU :- \n";
cout << "1.Press '1' to use EMI calculator \n";
cout << "2.Press '2' to Save Data \n";
cout << "3.Press '3' to Retrieve Data \n";
cout << "4.Press '4' to exit\n";

cin >> choice; //entering choice

  /* Step 3: Add new switch case statement replacing if-then-else */
   switch(choice) {
   case 1:
       cout << "Enter the Rate of Interest : " << endl;
       cin >> arr[0];
       cout << "Enter the Lenght of Loan : " << endl;
       cin >> arr[1];
       cout << "Enter the Amount of Loan : " << endl;
       cin >> arr[2];

       //conditional statement added
       if (arr[2] > 100000) {
       // if amount is greater then 10 Lac(100000) we reduce rate by 10%
       arr[0] = 0.9 * arr[0];
       }

       I = (arr[2] * arr[0] * arr[1]) / (100 * 12 * arr[1]);
       J = arr[2] / (arr[1] * 12);
       cout << "Monthly Payment is : " << I + J << endl;
       break;

/* Step 4: Add new switch case for saving Data */
   case 2:
       outfile.open ("Loan.txt");
       outfile << "Monthly Payment is : " << I + J << endl;
       outfile.close();
       break;

   /* Step 5: Add new switch case for rerieving Data */
   case 3:
       infile.open("Loan.txt");
       if(infile.is_open())
       {
       while ( getline (infile,line) ;
       {
       cout << line << '\n';
       }
       infile.close();
       }
       break;
   case 4: default:
cout << "Thank You !!\n";
   exit(0);
   }
}
return 0;
}
