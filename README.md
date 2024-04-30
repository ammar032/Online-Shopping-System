#include<iostream>
#include<string>
#include<stdlib.h>
#include<iomanip>
using namespace std;


class Profile
{
protected:
    int age{};
    string username{};
    string password{};

public:
    string name{};

    void registration(string name, int age, string username, string password)
    {
        this->age = age;
        this->name = name;
        this->username = username;
        this->password = password;
    }

    bool login(string loginUsername, string loginPassword)
    {
        if (loginUsername == username && loginPassword == password)
        {
            return true;
        }
        else
        {
            return false;
        }
    }

    friend istream& operator >>(istream& obj, Profile& p1)
    {
        cin.ignore();
        cout << "Enter name : "; getline(obj, p1.name);
        cout << "Enter age  : "; obj >> p1.age;
        cin.ignore();
        cout << "Enter username : "; getline(obj, p1.username);
        cout << "Enter password : "; obj >> p1.password;

        return obj;
    }

    friend ostream& operator <<(ostream& obj, Profile p1)
    {
        obj << "Name : " << p1.name << endl;
        obj << "Age  : " << p1.age << endl;
        obj << "Username : " << p1.username << endl;
        obj << "Password : " << p1.password << endl<<endl;

        return obj;
    }
};


class Item
{
public:
    string itemName{};
    double itemPrice{};
    string itemDescription{};
    string owner{};

    void setItem(string itemName, double itemPrice, string itemDescription, string owner)
    {
        this->itemName = itemName;
        this->itemPrice = itemPrice;
        this->itemDescription = itemDescription;
        this->owner = owner;
    }

    friend ostream& operator <<(ostream& obj, Item item)
    {
        obj << "Name  : " << item.itemName << endl;
        obj << "Price : " << item.itemPrice << endl;
        obj << "Description : " << item.itemDescription << endl;

        return obj;
    }

    friend istream& operator >>(istream& obj, Item& item)
    {
        cout << "Enter item name  : "; obj >> item.itemName;
        cout << "Enter item price : "; obj >> item.itemPrice;
        cin.ignore();
        cout << "Enter item description : ";getline(obj,item.itemDescription);

        return obj;
    }
};

class Admin : public Profile
{
public:

    void viewProfile()
    {
    }

    void resetProfile()
    {

    }

    void deleteProfile()
    {

    }
};

class shopOwner : public Profile
{

public:

    void displayItem()
    {

    }

    void addItem()
    {

    }

    void removeItem()
    {

    }

    void checkSales()
    {

    }
};

class Customer : public Profile
{
public:

    void buyItem()
    {

    }

    void addToCart()
    {

    }

    void deleteItem()
    {

    }

    void viewCart()
    {

    }

    void buyCart()
    {

    }
};

int main()
{
    int numberOfAdmins = 1;
    int numberOfOwners = 1;
    int numberOfCustomers = 1;
    int numberOfItems = 1;

    Admin admin[5];
    shopOwner owner[5];
    Customer customer[5];
    Item item[5];

    admin[0].registration("ammar", 20, "ammar1", "password1");
    owner[0].registration("hamza", 19, "hamza2", "password2");
    customer[0].registration("sajid", 19, "sajid3", "password3");
    item[0].setItem("Earphones", 500, "Best audio ever", owner[0].name);

a:
    int option;
    cout << "\tMAIN MENU\n1. Login\n2. Create Account\nOPTION: ";
    cin >> option;
    system("cls");

    string loginUsername;
    string loginPassword;
    int user;
    char status = '0';

    switch (option)
    {
    case 1:

        cin.ignore();

        cout << "\tLOGIN\n";

        cout << "Username: "; cin >> loginUsername;
        cout << "Password: "; cin >> loginPassword;

        for (int i = 0; i < numberOfAdmins; i++)
        {
            if (admin[i].login(loginUsername, loginPassword))
            {
                status = 'A';
                user = i;
                goto b;
            }
        }

        for (int i = 0; i < numberOfOwners; i++)
        {
            if (owner[i].login(loginUsername, loginPassword))
            {
                status = 'O';
                user = i;
                goto b;
            }
        }

        for (int i = 0; i < numberOfCustomers; i++)
        {
            if (customer[i].login(loginUsername, loginPassword))
            {
                status = 'C';
                user = i;
            }
        }

    b:
        system("cls");
        cout << "You have successfully logged in\n";

        switch (status)
        {
        case 'A':
        c:

            int adminOption;
            cout << "\tADMIN\n1. View Profile\n2. Reset Profile\n3. Delete Profile\n4. Back To Main Menu\nOPTION: ";
            cin >> adminOption;

            switch (adminOption)
            {
            case 1:

                cout << "SHOP OWNERS\n";
                for (int i = 0; i < numberOfOwners; i++)
                {
                    cout << owner[i];
                }
           
                cout << "CUSTOMERS\n";
                for (int i = 0; i < numberOfCustomers; i++)
                {
                    cout << customer[i];
                }

                break;
            case 2:
            case 3:
            case 4:

                system("cls");
                goto a;

            default:
                system("cls");
                cout << "Invalid option\n";
            }
            break;

        case 'O':
        d:

            int ownerOption;
            cout << "\tSHOP OWNER\n1. Display Items\n2. Add Item\n3. Remove Item\n4. Back To Main Menu\nOPTION: ";
            cin >> ownerOption;

            switch (ownerOption)
            {
            case 1:
                for (int i = 0; i < numberOfItems; i++)
                {
                    if (item[i].owner == owner[user].name)
                    {
                        cout << item[i];
                    }
                }
                break;

            case 2:
                cin >> item[numberOfItems];
                cout << "21312";
                item[numberOfItems].owner = owner[user].name;
                numberOfItems++;
                cout << "sadsad";
                system("cls");
                cout << "Item successfully created!\n";
                goto d;

            case 3:
            case 4:
                system("cls");
                goto a;

            default:
                system("cls");
                cout << "Invalid option\n";
            }
            break;

        case 'C':
        e:

            int customerOption;
            cout << "\tCUSTOMER\n1. Buy Item\n2. Add To Cart\n3. View Cart\n4. Buy Cart\n5. Back To Main Menu\nOPTION: ";
            cin >> customerOption;

            switch (customerOption)
            {
            case 1:
            case 2:
            case 3:
            case 4:
            case 5:
                system("cls");
                goto a;

            default:
                system("cls");
                cout << "Invalid option\n";
            }
            break;

        default:
            system("cls");
            cout << "Invalid credentials please login again\n";
            goto a;
        }
        break;
     
    break;

    case 2:
    f:

        int option;
        cout << "\tACCOUNT CREATION\n";
        cout << "Do you want to make an account for: \n1. Admin\n2. Shop Owner\n3. Customer\n4. Exit\nOPTION: ";
        cin >> option;

        switch (option)
        {
        case 1:
            cin >> admin[numberOfAdmins++];
            system("cls");
            cout << "Account successfully created now please login\n";
            goto a;

        case 2:
            cin >> owner[numberOfOwners++];
            system("cls");
            cout << "Account successfully created now please login\n";
            goto a;

        case 3:
            cin >> customer[numberOfCustomers++];
            system("cls");
            cout << "Account successfully created now please login\n";
            goto a;

        case 4:
            system("cls");
            goto a;

        default:
            system("cls");
            cout << "Invalid option please select one of the options below\n";
            goto f;
        }
    break;

    default:
        system("cls");
        cout << "Invalid option\n";
        goto a;
    }
}


