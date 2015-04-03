#include <iostream> // header files
#include <fstream> 
#include <cstdlib>
#include <ctime>
using namespace std;

void loadInfo(char symbols[][10], int values[]); // function prototypes
void printMenu(char slotMachine[][3][10], char symbols[][10], int values[]);
void fillMachine(char slotMachine[][3][10], char symbols[][10]);
void ReadFunction(char slotMachine[][3][10]); 
void PrintData(char slotMachine[][3][10]);
void DataToFile(char slotMachine[][3][10]);
void pickAndPrint(char slotMachine[][3][10], char symbols[][10], int values[]);
void strcpy(char dest[], char src[]);
bool strcmp(char str1[], char str2[]);

int main()
{
	srand(time(NULL)); // allows for random number generation
	
	char slotMachine[10][3][10]; // 3-D array to hold symbols in the slot machine
	char symbols[6][10]; // 2-D array 
	int values[6]; // array for bonus values

	loadInfo(symbols, values); // declaration of functions
	printMenu(slotMachine, symbols, values);
	fillMachine(slotMachine, symbols);
	ReadFunction(slotMachine);
	PrintData(slotMachine);
	DataToFile(slotMachine);
	pickAndPrint(slotMachine, symbols, values);	
	return 0;
}

void loadInfo(char symbols[][10], int values[]){ // function to load info into array
	ifstream fin;
	fin.open("symbols");
	for(int i = 0; i < 6; i++){
		fin >> symbols[i] >> values[i]; // gets all info into array
		//cout << symbols[i] << " " << values[i] << endl; //test line, to see if read in info is correct
	}
}

void printMenu(char slotMachine[][3][10], char symbols[][10], int values[]){ // function to print the menu
	char input;
	//bool running = true;
do{
	cout << "-------Menu-------" << endl; 
	cout << "1. Populate the slot machine" << endl; // Menu options to be displayed 
	cout << "2. Read in existing machine configuration from file" << endl;
	cout << "3. Print current configuration" << endl;
	cout << "4. Print and save configuration to file" << endl;
	cout << "5. Pick a reel and stop number" << endl;
	cout << "6. Quit the Program" << endl;
	cout << "Pick a menu option" << endl;
	cin >> input;

	switch(input)
	{
		case '1':
			fillMachine(slotMachine, symbols); // option to populate slot machine
			break;
		case '2':
			ReadFunction(slotMachine); // option to read in data from the file
			break;
		case '3':
			PrintData(slotMachine); // option to print data to the screen
			break;
		case '4':
			DataToFile(slotMachine); // option to print data to a file
			break;
		case '5':
			pickAndPrint(slotMachine, symbols, values); // option for user to pick a reel and stop number
			break;
		case '6': 
			cout << "Quitting Program" << endl; //this option quits the program
			exit(10); //running = false;
			//break;
		
		default: cout << input << " " << "Not a menu Option." << endl;
	}
   }while(input);	
}

void fillMachine(char slotMachine[][3][10], char symbols[][10]){ // function for populating the slot machine
	int num;
	for( int i = 0; i < 10; i++){
		for( int j = 0; j < 3; j++){
			num = rand()%6; // randomly generates numbers
			strcpy(slotMachine[i][j], symbols[num]);	
		}
	}
}

void ReadFunction(char slotMachine[][3][10])  // function to read in data
{
	ifstream file; // input file
	file.open("symbols"); // open and read in file

	for( int i = 0; i < 10; i++ ) // loops through data
	{
		for( int j = 0; j < 3; j++ )
		{
			file >> slotMachine[i][j]; // read in all the data
		}
	} 

	file.close(); // close input file
}

void PrintData(char slotMachine[][3][10]) // function to print data to screen
{
	for( int i = 0; i < 10; i++ ) // loops through data
	{
		for( int j = 0; j < 3; j++ )
		{
			cout << slotMachine[i][j] << " " << endl; // prints data to the screen
		}
	}
}

void DataToFile(char slotMachine[][3][10]) // function to put data into output file
{
	char Filename[10];
	cout << "Enter output filename" << endl; // ask user to create the name of ouput file
	cin >> Filename;
	ofstream fout; // output file
	fout.open(Filename); // opens output file

	for( int i = 0; i < 10; i++ ) // loops through data
	{
		for( int j = 0; j < 3; j++ )
		{
			fout << slotMachine[i][j] << " " << endl; // put data into file
		}
	}
	
	fout.close(); // close output file
}

void pickAndPrint(char slotMachine[][3][10], char symbols[][10], int values[]){ // pick the reel and stop number
	int row;
	int col;
	int i = 0;
	cout << "What Reel and Stop Number? :" << endl;
	cin >> row;
	cin >> col;
	while( i != strcmp(slotMachine[row][col], symbols[i]) ) // cmp value in 3-d array to each value in 2-d array	
	{
		i++;
	}
	cout << symbols[row][col] << " " << values[i] << endl; // prints out data
}


void strcpy(char dest[], char src[]){ // string copy function
	int i = 0;
	while(src[i] != '\0'){
		dest[i] = src[i]; // copies the strings in the array
		i++;
	}
	dest[i] = '\0'; // adds the null character so that it is a string
}

bool strcmp(char str1[], char str2[]) // string compare function
{
	int i = 0;
	bool compare = true; 
	while(str1[i] !='\0' && str2[i] !='\0' && compare){ // loop to compare the two strings
		if(str1[i] != str2[i]){
			compare = false;
		}
		i++;
	}
	if(str1[i] != str2[i]){ // do one last compare to see if one string is longer than the other
		compare = false;
	}
	return compare;
}
	

