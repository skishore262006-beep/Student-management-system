#include <iostream>
#include <fstream>
#include <string>
using namespace std;

class Student {
public:
    int rollNo;
    string name;
    int age;

    void addStudent() {
        ofstream file("students.txt", ios::app);

        cout << "Enter Roll No: ";
        cin >> rollNo;
        cin.ignore();

        cout << "Enter Name: ";
        getline(cin, name);

        cout << "Enter Age: ";
        cin >> age;

        file << rollNo << " " << name << " " << age << endl;
        file.close();

        cout << "\nStudent Added Successfully!\n";
    }

    void displayStudents() {
        ifstream file("students.txt");

        string line;
        cout << "\nStudent Records:\n";
        while (getline(file, line)) {
            cout << line << endl;
        }

        file.close();
    }
};

int main() {
    Student s;
    int choice;

    do {
        cout << "\n===== Student Management System =====\n";
        cout << "1. Add Student\n";
        cout << "2. Display Students\n";
        cout << "3. Exit\n";
        cout << "Enter Choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                s.addStudent();
                break;

            case 2:
                s.displayStudents();
                break;

            case 3:
                cout << "Exiting...\n";
                break;

            default:
                cout << "Invalid Choice!\n";
        }

    } while (choice != 3);

    return 0;
}
