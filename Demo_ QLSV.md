# BTL-NHOM-33
#include<conio.h>
#include <iostream>
#include <string>

using namespace std;

class Person{
	private:
		string Name, Date, Address, Sex;
	public:
		void Input();
		string getname();
		string getdate();
		string getaddress();
		string getsex();
};

string Person::getname(){
	return Name;
}
string Person::getdate(){
	return Date;
}
string Person::getaddress(){
	return Address;
}
string Person::getsex(){
	return Sex;
}

class Student:public Person{
	private:
		string Code, Class;
		float score;
	public:
		string getcode();
		string getclass();
		float getscore();
		void Input2();
		void Output();
};

string Student::getcode(){
	return Code;
}

void Student::Input2(){
	cout<<"\tCode: "; fflush(stdin); getline(cin,Code);
	cout<<"\tClass: "; fflush(stdin); getline(cin,Class);
	cout<<"\tmedium score: "; cin>>score;
}

void Person::Input(){
	cout<<"\tName: "; fflush(stdin); getline(cin,Name);
	cout<<"\tSex: "; fflush(stdin); getline(cin,Sex);
	cout<<"\tDate: "; fflush(stdin); getline(cin,Date);
	cout<<"\tAddress: ";fflush(stdin); getline(cin,Address);
	
}

void Student::Output(){
	cout<<"\tName: "<<getname()<<endl;
	cout<<"\tCode: "<<Code<<endl;
	cout<<"\tClass: "<<Class<<endl;
	cout<<"\tSex: "<<getsex()<<endl;
	cout<<"\tDate: "<<getdate()<<endl;
	cout<<"\tAddress: "<<getaddress()<<endl;
	cout<<"\tmedium score: "<<score<<endl;
}

int main(){
	
	bool Selection = false;
	string Find1, Find2, Erase;
	system("color A");
	int n;
	do{
		cout<<"\tEnter the number of students (Number > 0): "; cin>>n;
	}while(n<=0);
    Student *sv = new Student[n];
	while(true){
		cout<<"\n\t\t\t\t*********************************************************";
    	cout<<"\n\t\t\t\t**              STUDENT MANAGEMENT PROGRAM             **";
    	cout<<"\n\t\t\t\t**                                                     **";
    	cout<<"\n\t\t\t\t**  1. Enter student list                              **";
    	cout<<"\n\t\t\t\t**  2. Show list                                       **";
   		cout<<"\n\t\t\t\t**  3. Find student                                    **";
    	cout<<"\n\t\t\t\t**  4. Sort student                                    **";
    	cout<<"\n\t\t\t\t**  5. Delete student                                  **";
    	cout<<"\n\t\t\t\t**  6. Add student                                     **";
    	cout<<"\n\t\t\t\t**  7. Exit                                            **";
    	cout<<"\n\t\t\t\t**                                                     **";
    	cout<<"\n\t\t\t\t*********************************************************";
    	
    	int choose;
    	
    	cout<<"\n\tEnter your selection: "; cin>>choose;
   		switch(choose){
    		case 1:
    			Selection = true;
    			cout<<"\nYou have selected the function of entering student information."<<endl;
    			for(int i=0; i<n; i++){
	    			cout<<"\n\tEnter information of student "<<i+1<<":"<<endl;
	    			sv[i].Input();
    				sv[i].Input2();
				}
				cout<<"\nSuccessfully entered."<<endl;
				
				cout<<"\nPress any key to return to the menu.\n";
				getch();
				break;
    		case 2:
    			if(Selection){
    				cout<<"\nYou have selected the function to display student information."<<endl;
    				for (int i=0; i<n; i++){
    				cout<<"\n\tInformation of student "<<i+1<<":"<<endl;
    				sv[i].Output();
					}
				}else{
					cout<<"\nPlease select the function to enter the list of students first!!!"<<endl;
				}
    			
    			cout<<"\nPress any key to return to the menu.\n";
				getch();
				break;
			case 3:
				if(Selection){
					cout<<"\nYou have selected the student information search function."<<endl;
					cout<<"\n\t\t\t\t********************************************";
   				 	cout<<"\n\t\t\t\t**           FUNCTION SEARCH              **";
  				  	cout<<"\n\t\t\t\t**                                        **";
  				  	cout<<"\n\t\t\t\t**  1. By name                            **";
    				cout<<"\n\t\t\t\t**  2. By code                            **";
					cout<<"\n\t\t\t\t**  3. By medium score                    **";
					cout<<"\n\t\t\t\t**                                        **";
    				cout<<"\n\t\t\t\t********************************************";
					int m;
					cout<<"\n\tEnter your selection: "; cin>>m;
					switch(m){
						case 1:
							cout<<"\n\tEnter name of student: "; fflush(stdin); getline (cin,Find1);
    						for (int i=0; i<n; i++){
    							if (Find1 == sv[i].getname()){
    								cout<<"\n\t___Student found___ "<<endl;
									sv[i].Output();
								}
							}
							cout<<"\nPress any key to return to the menu.\n";
							getch();
							break;
							
						case 2:
							cout<<"\n\tEnter code of student: "; fflush(stdin); getline (cin,Find2);
    						for (int i=0; i<n; i++){
    							if (Find2 == sv[i].getcode()){
    								cout<<"\n\t___Student found___ "<<endl;
									sv[i].Output();
								}
							}
							cout<<"\nPress any key to return to the menu.\n";
							getch();
							break;
					}
    				
				}else{
					cout<<"\nPlease select the function to enter the list of students first!!!"<<endl;
				}	
				
			case 4:
				if(Selection){
					cout<<"\nYou have selected the function to sort student information."<<endl;
    				cout<<"\nSort by last name: "<<endl;
    				for(int i=0; i<n-1; i++){
    					for(int j=1; j<n; j++){
    						if (sv[i].getname() > sv[j].getname()){
    							Student temp = sv[i];
    							sv[i] = sv[j];
    							sv[j] = temp;
							}
						}
					}
					for (int i=0; i<n; i++){
						cout<<"\n\tInformation of student "<<i+1<<":"<<endl;
    					sv[i].Output();
					}
				}else{
					cout<<"\nPlease select the function to enter the list of students first!!!"<<endl;
				}
    			
    			cout<<"\nPress any key to return to the menu.\n";
				getch();
				break;
			case 5:
				if(Selection){
					cout<<"\n\tYou have selected the function to delete student"<<endl;
    				cout<<"\n\tEnter code of student: "; fflush(stdin); getline (cin,Erase);
    				for (int i=0; i<n; i++){
    					if (Erase == sv[i].getcode()){
    						for (; i<n-1; i++){
    							for(int j=i+1; j<n; j++){
    								sv[i] = sv[j];
								}
							}
						}
					}
					cout<<"\nSuccessfully deleted."<<endl;
					n = n - 1;
				}else{
					cout<<"\nPlease select the function to enter the list of students first!!!"<<endl;
				}
    			
    			cout<<"\nPress any key to return to the menu.\n";
				getch();
				break;
			case 6:
				if(Selection){
					cout<<"\nYou have selected the function to add students."<<endl;
    				Student *t = new Student [n];
    				for (int i=0; i<n; i++){
    					t[i] = sv[i];
					}
					sv = new Student [n*2];
					for (int i=0; i<n; i++){
    					sv[i] = t[i];
					}
					cout<<"\n\tAdd information of student "<<n+1<<":"<<endl;
    				sv[n].Input();
    				sv[n].Input2();
    				
    				cout<<"\nSuccessfully added."<<endl;
    				n++;
    				delete [] t;
				}else{
					cout<<"\nPlease select the function to enter the list of students first!!!"<<endl;
				}
    			
    			cout<<"\nPress any key to return to the menu.\n";
				getch();
				break;
			case 7:
				cout<<"\nYou chose to exit the program"<<endl;
				return 0;
			default:
				cout<<"\nThis function is not available! Please choose again!!!"<<endl;
				cout<<"\nPress any key to return to the menu.\n";
				getch();
				break;
			
		}
	}
	delete [] sv;
}
