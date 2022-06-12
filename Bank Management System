#include<iostream>
#include<string>
#include<fstream>
#include<cstdlib>
#include<cstring>
#include<ctime>
using namespace std;
//------------------------structure-----------------------------------//
struct data1
{
	int account_no;
	char name[30];
	char city[30];
	char state[30];
	char zip[6];
	char phone_no[12];
	double account_balance;
	int date;
	int month;
	int year;
};
//--------------------function for adding new account-----------------//
void add_account()
{
	srand(time(NULL));
	data1 add;
	ofstream datafile;
	datafile.open("ACCOUNT.txt", ios::out | ios::app);//opening file to write data to file
	add.account_no = rand();
	cout << "\t\tYOUR ACCOUNT ID IS : " << add.account_no;
	cin.ignore();
	cout<<endl;
	cout<<endl;
	cout << "\t\tENTER YOUR FULL NAME :  ";
	cin.getline(add.name, 30);
	while (strlen(add.name) == 0)//user must enter the name field
	{
		cout << "\t\tYOU CANNOT LEFT THE FIELD (NAME) BLANK : ";
		cin.getline(add.name, 30);
	}
	cout << "\t\tENTER THE CITY NAME :  ";
	cin.getline(add.city, 30);
	while (strlen(add.city) == 0)//user must enter the city field
	{
		cout << "\t\tYOU CANNOT LEFT THE FIELD (CITY) BLANK : ";
		cin.getline(add.city, 30);
	}
	cout << "\t\tENTER THE STATE :  ";
	cin.getline(add.state, 30);
	while (strlen(add.state) == 0)//user must enter the state field
	{
		cout << "\t\tYOU CANNOT LEFT THIS FIELD (STATE) BLANK : ";
		cin.getline(add.state, 30);
	}
	cout << "\t\tENTER THE ZIP-CODE :  ";
	cin.getline(add.zip, 6);
	while (strlen(add.zip) == 0)//user must enter the zip code field
	{
		cout << "\t\tYOU CANNOT LEFT THIS FIELD (ZIP-CODE) BLANK : ";
		cin.getline(add.zip, 6);
	}
	cout << "\t\tENTER THE PHONE NUMBER :  ";
	cin.getline(add.phone_no, 12);
	while (strlen(add.phone_no) == 0)//user must enter the phone number field
	{
		cout << "\t\tYOU CANNOT LEFT THIS FIELD (PHONE-NO) BLANK : ";
		cin.getline(add.phone_no, 12);
	}
	cout << "\t\tENTER THE ACCOUNT BALANCE $ :  ";
	cin >> add.account_balance;
	while (add.account_balance<0)//balance cant be negative
	{
		cout << "\t\tACCOUNT BALANCE CAN'T BE NEGATIVE\n";
		cin >> add.account_balance;
	}
	cin.ignore();
	label:
	cout << "\t\tENTER THE LAST PAYMENT DATE (DATE) :  ";
	cin>>add.date;
	cin.ignore();
	while(add.date>31 || add.date <1)
	{
		cout<<"\t\tERROR IN DATE (DATE)  !!"<<endl;
		cin>>add.date;
	}
	label1:
	cout << "\t\tENTER THE LAST PAYMENT DATE (MONTH) :  ";
	cin>>add.month;
	cin.ignore();
	if(add.month>12 ||add.month <1)
	{
		cout<<"\t\tERROR IN DATE (MONTH) !!  ";
		goto label1;
	}
	cout << "\t\tENTER THE LAST PAYMENT DATE (YEAR) :  ";
	cin>>add.year;
	cout << endl;
	cout << endl;
	//witing structure to file
	datafile.write(reinterpret_cast<char *>(&add), sizeof(add));
	cout << "\t\tACCOUNT SUCCESFULLY CREATED !! " << endl;
	datafile.close();
}
//--------------------function to view all records------------------------------------------------
void view_all()
{
	data1 view;
	char again;
	ifstream datafile;//opening file to read the file
	datafile.open("ACCOUNT.txt", ios::in);
	if (!datafile)//checking if file exist
	{
		cout << endl;
		cout << "\t\tERROR !! IN OPENING FILE " << endl;
		cout << endl;
	}
	else//if file exist then reading struture from the file
	{
		datafile.read(reinterpret_cast<char *>(&view), sizeof(view));
		int i = 1;
		while (!datafile.eof())
		{
			cout << "\t\t\t\tRECORD # " << i << endl;
			cout << "\t\t============================================" << endl;
			cout << "\t\tACCOUNT-NUMBER : " << view.account_no << endl;
			cout << "\t\tNAME : " << view.name << endl;
			cout << "\t\tCITY : " << view.city << endl;
			cout << "\t\tSTATE : " << view.state << endl;
			cout << "\t\tZIP-CODE : " << view.zip << endl;
			cout << "\t\tPHONE-NUMBER : " << view.phone_no << endl;
			cout << "\t\tACCOUNT BALANCE $ : " << view.account_balance << endl;
			cout << "\t\tLAST PAYMENT DATE : " << view.date<<"-"<<view.month<<"-"<<view.year << endl;;
			cout << endl;
			cout << "\t\t============================================" << endl;
			i++;
			datafile.read(reinterpret_cast<char *>(&view), sizeof(view));
		}
		cout << "\t\tTHIS IS ALL THE RECORD WE HAVE . THANK YOU !!" << endl;
		cout << "\t\t============================================" << endl;
	}
	datafile.close();
}
//------------------------------------function to delete all records----------------------------
void delete_all()
{
	fstream datafile;
	if (datafile)//if exist exist del all records
	{
		remove("ACCOUNT.txt");
		cout << endl;
		cout << "\t\tRECORD DELETED SUCCESSFULLY !! " << endl;
	}
	else// if file doesnt exist
	{
		cout << endl;
		cout << "\t\tERROR !! IN OPENING FILE " << endl;
	}
}
//-----------------------------function for search specific record------------------------------
void specific_search()
{
	data1 search;
	int num;
	int temp;
	cout << "\t\tENTER THE ID YOU WANT TO SEARCH FOR RECORD :  ";
	cin >> num;
	ifstream datafile;
	datafile.open("ACCOUNT.txt");
	datafile.read(reinterpret_cast<char *>(&search), sizeof(search));
	if (!datafile)
	{
		cout << "\t\tERROR !! IN OPENING FILE : " << endl;
	}
	while (!datafile.eof())
	{
		temp = search.account_no;
		if (num == search.account_no)
		{
			cout << endl;
			cout << "\t\t============================================" << endl;
			cout << "\t\tACCOUNT NO :  " << search.account_no << endl;
			cout << "\t\tNAME :  " << search.name << endl;
			cout << "\t\tCITY :  " << search.city << endl;
			cout << "\t\tSTATE :  " << search.state << endl;
			cout << "\t\tZIP-CODE :  " << search.zip << endl;
			cout << "\t\tPHONE-NUMBER :  " << search.phone_no << endl;
			cout << "\t\tACCOUNT BALANCE :  " << search.account_balance << endl;
			cout << "\t\tLAST PAYMENT DATE :  " << search.date<<"-"<<search.month<<"-"<<search.year << endl;
			cout << "\t\t============================================" << endl;
		}
		datafile.read(reinterpret_cast<char *>(&search), sizeof(search));
	}
	datafile.close();
	if (num != temp)
	{
		cout << endl;
		cout << "\t\tRECORD NOT FOUND !! " << endl;
	}
}
void balance_inquiry()
{
	data1 inquiry;
	int num;
	int temp;
	cout << "\t\tENTER THE ACCOUNT NUMBER FOR WHICH YOU WANT" << endl;
	cout << "\t\tTO PERFORM BALANCE INQUIRY !! ";
	cin >> num;
	ifstream datafile;
	datafile.open("ACCOUNT.txt");
	datafile.read(reinterpret_cast<char *>(&inquiry), sizeof(inquiry));
	while (!datafile.eof())
	{
		temp = inquiry.account_no;
		if (num == inquiry.account_no)
		{
			cout << endl;
			cout << "\t\t============================================" << endl;
			cout << "\t\tDEAR !! " << inquiry.name << ". " << endl;
			cout << endl;
			cout << "\t\tYOU ACCOUNT BALANCE IS : " << inquiry.account_balance << "$" << endl;
			cout << "\t\tYOUR LAST PAYMENT DATE IS : " << inquiry.date<<"-"<<inquiry.month<<"-"<<inquiry.year << endl;
			cout << "\t\t============================================" << endl;
		}
		datafile.read(reinterpret_cast<char *>(&inquiry), sizeof(inquiry));
	}
	datafile.close();
	if (num != temp)
	{
		cout << endl;
		cout << "\t\tRECORD NOT FOUND !! " << endl;
	}
}
void delete_record()
{
	data1 del;
	int num;
	int temp;
	cout << "\t\tENTER YOUR ACCOUNT NUMBER FOR WHICH YOU WANT TO DELETE RECORD !!  ";
	cin >> num;
	ifstream infile;
	ofstream outfile;
	infile.open("ACCOUNT.txt", ios::in);
	if (!infile)
	{
		cout << "\t\tERROR !! IN OPENING FILE " << endl;
	}
	if (infile)
	{
		outfile.open("TEMP.txt", ios::out);
		infile.read(reinterpret_cast<char *>(&del), sizeof(del));
		while (!infile.eof())
		{
			temp = del.account_no;
			if (num == del.account_no)
			{
				cout << endl;
				cout << "\t\tRECORD DELETED SUCCESSFULLY !! " << endl;
			}
			if (num != del.account_no)
			{
				outfile.write(reinterpret_cast<char *>(&del), sizeof(del));
			}
			infile.read(reinterpret_cast<char *>(&del), sizeof(del));
		}
		infile.close();
		outfile.close();
		remove("ACCOUNT.txt");
		rename("TEMP.txt", "ACCOUNT.txt");
	}
	if (num != temp)
	{
		cout << endl;
		cout << "\t\tRECORD NOT FOUND !! " << endl;
	}
}
void deposit_amount()
{
	data1 deposit;
	int num;
	int temp;
	int amount;
	int sum;
	cout << "\t\tENTER YOUR ACCOUNT NUMBER FOR WHICH YOU WANT TO DEPOSIT MONEY !!  ";
	cin >> num;
	ifstream infile;
	ofstream outfile;
	infile.open("ACCOUNT.txt", ios::in);
	if (!infile)
	{
		cout << "\t\tFILE OPENING ERROR !! " << endl;
	}
	if (infile)
	{
		outfile.open("TEMP.txt", ios::out);
		infile.read(reinterpret_cast<char *>(&deposit), sizeof(deposit));
		while (!infile.eof())
		{
			temp = deposit.account_no;
			if (num == deposit.account_no)
			{
				cout << endl;
				cout << "\t\tENTER THE AMOUNT YOU WANT TO DEPOSIT !!  ";
				cin >> amount;
				deposit.account_balance = amount + deposit.account_balance;
				cout << "\t\t============================================" << endl;
				cout << "\t\tDEAR !! " << deposit.name << " ." << endl;
				cout << endl;
				cout << "\t\tYOUR CURRENT ACCOUNT BALANCE IS NOW :  " << deposit.account_balance << "$" << endl;
				cout << "\t\t============================================" << endl;
				outfile.write(reinterpret_cast<char *>(&deposit), sizeof(deposit));
			}
			if (num != deposit.account_no)
			{
				outfile.write(reinterpret_cast<char *>(&deposit), sizeof(deposit));
			}
			infile.read(reinterpret_cast<char *>(&deposit), sizeof(deposit));
		}
		infile.close();
		outfile.close();
		remove("ACCOUNT.txt");
		rename("TEMP.txt", "ACCOUNT.txt");
	}
	if (num != temp)
	{
		cout << endl;
		cout << "\t\tRECORD NOT FOUND !! " << endl;
	}
}
void amount_withdraw()
{
	data1 withdraw;
	int num;
	int temp;
	int amount;
	int sum;
	cout << "\t\tENTER YOUR ACCOUNT NUMBER FOR WHICH YOU WANT TO WITHDRAW MONEY !!  ";
	cin >> num;
	ifstream infile;
	ofstream outfile;
	infile.open("ACCOUNT.txt", ios::in);
	if (!infile)
	{
		cout << "\t\tERROR !! IN FILE OPENING " << endl;
	}
	if (infile)
	{
		outfile.open("TEMP.txt", ios::out);
		infile.read(reinterpret_cast<char *>(&withdraw), sizeof(withdraw));
		while (!infile.eof())
		{
			temp = withdraw.account_no;
			if (num == withdraw.account_no)
			{
				cout << endl;
				label0:
				cout << "\t\tENTER THE AMOUNT YOU WANT TO WITHDRAW !!  ";
				cin >> amount;
				if (amount > withdraw.account_balance)
				{
					cout << endl;
					cout << "\t\tINSUFFIANCE BALANCE !! " << endl;
					cout << endl;
					goto label0;
				}
				withdraw.account_balance = withdraw.account_balance - amount;
				cout << "\t\t============================================" << endl;
				cout << "\t\tDEAR !! " << withdraw.name << " ." << endl;
				cout << endl;
				cout << "\t\tYOUR CURRENT REMAINING ACCOUNT BALANCE IS NOW :  " << withdraw.account_balance << "$" << endl;
				cout << "\t\t============================================" << endl;
				outfile.write(reinterpret_cast<char *>(&withdraw), sizeof(withdraw));
			}
			if (num != withdraw.account_no)
			{
				outfile.write(reinterpret_cast<char *>(&withdraw), sizeof(withdraw));
			}
			infile.read(reinterpret_cast<char *>(&withdraw), sizeof(withdraw));
		}
		infile.close();
		outfile.close();
		remove("ACCOUNT.txt");
		rename("TEMP.txt", "ACCOUNT.txt");
	}
	if (num != temp)
	{
		cout << endl;
		cout << "\t\tRECORD NOT FOUND !! " << endl;
	}
	
}
void update_record()
{
	data1 update;
	int num;
	cout<<endl;
	cout<<"\t\tENTER THE ACCOUNT NUMBER TO UPDATE RECORD :  ";
	cin>>num;
	ifstream infile;
	ofstream outfile;
	infile.open("ACCOUNT.txt" , ios::in);
	if(!infile)
	{
		cout<<endl;
		cout<<"ERROR !! IN OPENING FILE "<<endl;;
	}
	if(infile)
	{
		outfile.open("TEMP.txt" , ios::out);
		infile.read(reinterpret_cast<char *>(&update) , sizeof(update));
		while(!infile.eof())
		{
			if(num==update.account_no)
			{
				cin.ignore();
				cout << "\t\tENTER YOUR FULL NAME :  ";
				cin.getline(update.name, 30);
				while (strlen(update.name) == 0)//user must enter the name field
				{
					cout << "\t\tYOU CANNOT LEFT THE FIELD (NAME) BLANK : ";
					cin.getline(update.name, 30);
				}
				cout << "\t\tENTER THE CITY NAME :  ";
				cin.getline(update.city, 30);
				while (strlen(update.city) == 0)//user must enter the city field
				{
					cout << "\t\tYOU CANNOT LEFT THE FIELD (CITY) BLANK : ";
					cin.getline(update.city, 30);
				}
				cout << "\t\tENTER THE STATE :  ";
				cin.getline(update.state, 30);
				while(strlen(update.state) == 0)//user must enter the state field
				{
					cout << "\t\tYOU CANNOT LEFT THIS FIELD (STATE) BLANK : ";
					cin.getline(update.state, 30);
				}
				cout << "\t\tENTER THE ZIP-CODE :  ";
				cin.getline(update.zip, 6);
				while (strlen(update.zip) == 0)//user must enter the zip code field
				{
					cout << "\t\tYOU CANNOT LEFT THIS FIELD (ZIP-CODE) BLANK : ";
					cin.getline(update.zip, 6);
				}
				cout << "\t\tENTER THE PHONE NUMBER :  ";
				cin.getline(update.phone_no, 12);
				while (strlen(update.phone_no) == 0)//user must enter the phone number field
				{
					cout << "\t\tYOU CANNOT LEFT THIS FIELD (PHONE-NO) BLANK : ";
					cin.getline(update.phone_no, 12);
				}
				cout << "\t\tENTER THE ACCOUNT BALANCE $ :  ";
				cin >> update.account_balance;
				while (update.account_balance<0)//balance cant be negative
				{
					cout << "\t\tACCOUNT BALANCE CAN'T BE NEGATIVE\n";
					cin >> update.account_balance;
				}
				cin.ignore();
				label:
				cout << "\t\tENTER THE LAST PAYMENT DATE (DATE) :  ";
				cin>>update.date;
				cin.ignore();
				if(update.date>31 || update.date <1)
				{
					cout<<"\t\tERROR IN DATE (DATE)  !!"<<endl;//DATE VALIDATION ACCORDING TO DATE
					goto label;
				}
				label1:
				cout << "\t\tENTER THE LAST PAYMENT DATE (MONTH) :  ";
				cin>>update.month;
				cin.ignore();
				if(update.month>12 ||update.month <1)
				{
					cout<<"\t\tERROR IN DATE (MONTH) !!  "<<endl;//DATE VALIDATION ACCORDING TO MONTH
					goto label1;
				}
				cout << "\t\tENTER THE LAST PAYMENT DATE (YEAR) :  ";
				cin>>update.year;
			}
				outfile.write(reinterpret_cast<char *>(&update) , sizeof(update));
				infile.read(reinterpret_cast<char *>(&update) , sizeof(update));
		}
		infile.close();
		outfile.close();
		remove("ACCOUNT.txt");
		rename("TEMP.txt" , "ACCOUNT.txt");
	}
}
int amount_transfer()
{
	data1 transfer;
label:
	int acc1;
	int acc2;
	int temp1;
	int temp2;
	int amount;
	cout << "\t\tENTER THE ACCOUNT # OF SENDER :  ";
	cin >> acc1;
	cout << "\t\tENTER THE ACCOUNT # OF RECEIVER :  ";
	cin >> acc2;
	if (acc1 == acc2)
	{
		cout << endl;
		cout << "\t\tACCOUNT # CANNOT BE SAME !! " << endl;
		cout << endl;
		goto label;
	}
	cout << endl;
	cout << "\t\tENTER THE AMOUNT TO DEPOSIT :  ";
	cin >> amount;
	ifstream infile;
	ofstream outfile;
	infile.open("ACCOUNT.txt", ios::in);
	if (!infile)
	{
		cout << "ERROR !! IN OPENING FILE " << endl;
		cout << endl;
	}
	if (infile)
	{
		outfile.open("TEMP.txt", ios::out);
		infile.read(reinterpret_cast<char *>(&transfer), sizeof(transfer));
		while (!infile.eof())
		{
			temp1 = transfer.account_no;
			if (acc1 == transfer.account_no)
			{//CHECK FOR THE SENDER ACCOUNT NUMBER 
				if (amount > transfer.account_balance)
				{
					cout << endl;
					cout << "\t\tINSUFFIANT BALANCE !! " << endl;
					return 0;
				}
				transfer.account_balance = transfer.account_balance - amount;
			}
			else if (acc2 == transfer.account_no)
			{
				//CHECK FOR THE RECEIVER ACCOUNT NUMBER
				temp2 = transfer.account_no;
				transfer.account_balance = transfer.account_balance + amount;
			}
			outfile.write(reinterpret_cast<char *>(&transfer), sizeof(transfer));
			infile.read(reinterpret_cast<char *>(&transfer), sizeof(transfer));
		}
		if (acc1 != temp1)
		{
			cout << endl;
			cout << "\t\tRECORD NOT FOUND !! ";
			cout << endl;
			return 0;
		}
		if (acc2 != temp2)
		{
			cout << endl;
			cout << "\t\tRECORD NOT FOUND !! ";
			cout << endl;
			return 0;
		}
	}
	infile.close();
	outfile.close();
	remove("ACCOUNT.txt");
	rename("TEMP.txt", "ACCOUNT.txt");
	return 0;
}
int main()
{
label:
	system("cls");
	int choice;
	char choices;
	cout << endl;
	cout << "\t\t============================================" << endl;
	cout << "\t\t     CUSTOMER ACCOUNT MANAGEMENT SYSTEM" << endl;
	cout << "\t\t============================================" << endl;
	cout << endl;
	cout << "\t\t<ENTER 0>  TO ADD A NEW RECORD" << endl;
	cout << "\t\t<ENTER 1>  TO SEARCH FOR RECORD TO DISPLAY" << endl;
	cout << "\t\t<ENTER 2>  TO SEARCH FOR RECORD TO DELETE" << endl;
	cout << "\t\t<ENTER 3>  TO SEARCH FOR RECORD TO UPDATE " << endl;
	cout << "\t\t<ENTER 4>  TO VIEW ALL RECORDS LIST" << endl;
	cout << "\t\t<ENTER 5>  TO DELETE ALL RECORDS COMPLTELY" << endl;
	cout << "\t\t<ENTER 6>  TO BALANCE INQUIRY" << endl;
	cout << "\t\t<ENTER 7>  TO DEPOSIT AMMOUNT" << endl;
	cout << "\t\t<ENTER 8>  TO WITHDRAW AMOUNT" << endl;
	cout << "\t\t<ENTER 9>  TO TRANSFER AMOUNT TO ANOTHER ACCOUNT" << endl;
	cout << "\t\t<ENTER 10> TO EXIT FROM MENU " << endl;
	cout << endl;
	cout << "\t\t============================================" << endl;
	cout << endl;
	cout << "\t\tENTER YOUR CHOICE <0-10> !!   ";
	cin >> choice;
	cout << endl;
	if (choice == 0)
	{
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\t     YOU ARE GOING TO ADD A NEW RECORD !! " << endl;
		cout << "\t\t============================================" << endl;
		cout << endl;
		add_account();//FUNCTION FOR ADDING NEW ACCOUNT 
		cout << endl;
	label1:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label1;
		}
	}
	else if (choice == 1)
	{
		char choices;
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\tYOUR ARE GOING TO DISPLAY SPECIFIC RECORD !! " << endl;
		cout << "\t\t============================================" << endl;
		cout << endl;
		specific_search();//FUNCTION FOR SPECIFICALLY SEARCHING AN ACCOUNT
		cout << endl;
	label2:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !! " << endl;
			goto label2;
		}
	}
	else if (choice == 2)
	{
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\t     YOU ARE GOING TO DELETE THE RECORD !! " << endl;
		cout << "\t\t============================================" << endl;
		cout << endl;
		delete_record();//FUNCTION FOR DELETING A SPECIFIC ACCOUNT
		cout << endl;
	label5:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label5;
		}
	}
	else if (choice == 3)
	{
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\t     YOU ARE GOING TO UPDATE THE RECORD !! " << endl;
		cout << "\t\t============================================" << endl;
		update_record();//FUNCTION FOR UPDATING A RECORD SPECIFIC ACCOUNT
		cout << endl;
	label9:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label9;
		}
	}
	else if (choice == 4)
	{
		char choices;
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\t     YOU ARE GOING TO VIEW ALL RECORD !! " << endl;
		cout << "\t\t============================================" << endl;
		view_all();//FUNCTION FOR VIEWING ALL ACCOUNTS IN THE FILE 
		label3:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label3;
		}
	}
	else if (choice == 5)
	{
		system("cls");
		char choice1;
		char choice2;
		cout << "\t\t============================================" << endl;
		cout << "\t\t     YOU ARE GOING TO DELETE ALL RECORDS " << endl;
		cout << "\t\t============================================" << endl;
		cout << endl;
		cout << "\t\tARE YOU SURE YOU WANT TO DELETE ALL RECORDS (Y/N) !!  ";
		cin >> choice1;
		if (choice1 == 'Y' || choice1 == 'y')
		{
			delete_all();//FUNCTION FOR DELETING ALL THE  ACCOUNTS IN THE FILE 
			cout << endl;
			cout << "\t\tDO YOU WANT TO GO BACK (Y/N) !! ";
			cin >> choice2;
			if (choice2 == 'Y' || choice2 == 'y')
			{
				goto label;
			}
			else
			{
				exit(0);
			}
		}
		else if (choice1 == 'N' || choice1 == 'n')
		{
			cout << endl;
			cout << "\t\tDO YOU WANT TO GO BACK (Y/N) !! ";
			cin >> choice2;
			if (choice2 == 'Y' || choice2 == 'y')
			{
				goto label;
			}
			else
			{
				exit(0);
			}
		}
		else
		{
			exit(0);
		}

	}
	else if (choice == 6)
	{
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\tYOU ARE GOING TO ATTEMPT THE BALANCE INQUIRY !! " << endl;
		cout << "\t\t============================================" << endl;
		cout << endl;
		balance_inquiry();//FUNCTION FOR BALANCE INQUIRY
		cout << endl;
	label4:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label4;
		}
	}
	else if (choice == 7)
	{
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\t     YOU ARE GOING TO DEPOSIT AMOUNT !! " << endl;
		cout << "\t\t============================================" << endl;
		cout << endl;
		deposit_amount();
		cout << endl;
	label6:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label6;
		}
	}
	else if (choice == 8)
	{
		system("cls");
		cout << "\t\t============================================" << endl;
		cout << "\t\tYOU ARE GOING TO WITHDRAW AMOUNT !! " << endl;
		cout << "\t\t============================================" << endl;
		amount_withdraw();//FUNCTION FOR WITHDRAW THE AMMOUNT FROM ACCOUNT
		cout << endl;
	label7:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label7;
		}
	}
	else if (choice == 9)
	{
		system("cls");
		cout << "\t\t============================================================" << endl;
		cout << "\t\t   YOU ARE GOING TO TRANSFER AMOUNT TO ANOTHER ACCOUNT !! " << endl;
		cout << "\t\t============================================================" << endl;
		cout << endl;
		amount_transfer();
		cout << endl;
	label8:
		cout << "\t\tDO YOU WANT TO GO BACK (Y/N) ? ";
		cin >> choices;
		if (choices == 'Y' || choices == 'y')
		{
			goto label;
		}
		else if (choices == 'N' || choices == 'n')
		{
			exit(0);
		}
		else
		{
			cout << "\t\tINVALID CHOICE !!" << endl;;
			goto label8;
		}
	}
	else if (choice == 10)
	{
		cout << "\t\tTHANK YOU !! FOR VISITING THE MENU " << endl;
		exit(0);
	}
	else
	{
		cout << "\t\tINVALID CHOICE !! " << endl;
	}
}
