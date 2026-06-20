# A-Library Managment System using C++

#include <iostream>
#include <string>
using namespace std;

class Book {
public:
    int id;
    string title;
    string author;
    bool issued;
};

Book books[100];
int totalBooks = 0;

void addBook() {
    cout << "\nEnter Book ID: ";
    cin >> books[totalBooks].id;
    cin.ignore();

    cout << "Enter Book Title: ";
    getline(cin, books[totalBooks].title);

    cout << "Enter Author Name: ";
    getline(cin, books[totalBooks].author);

    books[totalBooks].issued = false;
    totalBooks++;

    cout << "Book Added Successfully!\n";
}

void viewBooks() {
    if (totalBooks == 0) {
        cout << "\nNo Books Available!\n";
        return;
    }

    cout << "\n===== Book List =====\n";

    for (int i = 0; i < totalBooks; i++) {
        cout << "\nID: " << books[i].id;
        cout << "\nTitle: " << books[i].title;
        cout << "\nAuthor: " << books[i].author;
        cout << "\nStatus: "
             << (books[i].issued ? "Issued" : "Available");
        cout << "\n-------------------\n";
    }
}

void searchBook() {
    int id;
    cout << "\nEnter Book ID: ";
    cin >> id;

    for (int i = 0; i < totalBooks; i++) {
        if (books[i].id == id) {
            cout << "\nBook Found!\n";
            cout << "Title: " << books[i].title << endl;
            cout << "Author: " << books[i].author << endl;
            return;
        }
    }

    cout << "Book Not Found!\n";
}

void issueBook() {
    int id;
    cout << "\nEnter Book ID: ";
    cin >> id;

    for (int i = 0; i < totalBooks; i++) {
        if (books[i].id == id) {

            if (books[i].issued) {
                cout << "Book Already Issued!\n";
            } else {
                books[i].issued = true;
                cout << "Book Issued Successfully!\n";
            }
            return;
        }
    }

    cout << "Book Not Found!\n";
}

void returnBook() {
    int id;
    cout << "\nEnter Book ID: ";
    cin >> id;

    for (int i = 0; i < totalBooks; i++) {
        if (books[i].id == id) {

            if (!books[i].issued) {
                cout << "Book Was Not Issued!\n";
            } else {
                books[i].issued = false;
                cout << "Book Returned Successfully!\n";
            }
            return;
        }
    }

    cout << "Book Not Found!\n";
}

int main() {
    int choice;

    do {
        cout << "\n===== Library Management System =====";
        cout << "\n1. Add Book";
        cout << "\n2. View Books";
        cout << "\n3. Search Book";
        cout << "\n4. Issue Book";
        cout << "\n5. Return Book";
        cout << "\n6. Exit";
        cout << "\nEnter Choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                addBook();
                break;

            case 2:
                viewBooks();
                break;

            case 3:
                searchBook();
                break;

            case 4:
                issueBook();
                break;

            case 5:
                returnBook();
                break;

            case 6:
                cout << "Goodbye!\n";
                break;

            default:
                cout << "Invalid Choice!\n";
        }

    } while (choice != 6);

    return 0;
}
