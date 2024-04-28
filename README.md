#include<iostream>
#include<string>
#include<stdlib.h>
#include<iomanip>
using namespace std;

class Profile
{
protected:
    int age;
    string name;
    string username;
    string password;

public:
    Profile()
    {
        age = 0;
        name = "";
        username = "";
        password = "";
    }

    void setProfile(int _age, string _name, string _username, string _password)
    {
        age = _age;
        name = _name;
        username = _username;
        password = _password;
    }
    void accountdetails()
    {
        system("cls");
        cout << endl << setfill('=') << setw(132) << "" << setfill(' ') << endl;
        cout << setw(56) << "Personal Information" << setw(56) << endl;
        cout << endl << setfill('=') << setw(132) << "" << setfill(' ') << endl;
        cout << setw(42) << "Name : " << name << endl;
        cout << setw(42) << "Age  : " << age << endl;
        cout << setw(38) << "Username : " << username << endl;
        cout << setw(38) << "Password : " << password << endl;
    }


};

class Item
{
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

class Shop_Owner : public Profile, public Item
{
public:

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

/*// ANUM'S CODE STARTS HERE 

const int MAX_ITEMS = 10;
string itemName;
double itemPrice;
int choice = -1;

class ShopManagement        //should be in Customers class instead of shop management
{
private:
    string itemNames[MAX_ITEMS];
    double itemPrices[MAX_ITEMS];
    int itemNum;

public:
    ShopManagement() : itemNum(0) {}

    void addItem(const string& itemName, double itemPrice)
    {
        if (itemNum < MAX_ITEMS)
        {
            itemNames[itemNum] = itemName;
            itemPrices[itemNum] = itemPrice;
            itemNum++;
            cout << itemName << " has been added to the cart." << endl;
            cout << "Price: $" << itemPrice << endl;
            cout << "Added to cart" << endl;
            cout << endl;
        }
        else
        {
            cout << "Cart is full! Sorry, Cannot add more items." << endl;
        }
    }

    void removeItem(const string& itemName)
    {
        for (int i = 0; i < itemNum; ++i)
        {
            if (itemNames[i] == itemName)
            {
                cout << itemName << " has been removed from the cart." << endl;
                for (int j = i; j < itemNum - 1; ++j)
                {
                    itemNames[j] = itemNames[j + 1];
                    itemPrices[j] = itemPrices[j + 1];
                }
                itemNum--;
                return;
            }
        }
        cout << "Item not found in cart." << endl;
    }

    void viewCart()
    {
        if (itemNum == 0)
        {
            cout << "Your cart is empty." << endl;
            return;
        }
        cout << "Items in your cart:" << endl;
        for (int i = 0; i < itemNum; ++i)
        {
            cout << "- " << itemNames[i] << " : $" << itemPrices[i] << endl;
        }
    }

    double getTotalPrice()
    {
        double total = 0.0;
        for (int i = 0; i < itemNum; ++i)
        {
            total += itemPrices[i];
        }
        return total;
    }
};

void cartOptions()      //should make this function a member function of customer class 
{
    ShopManagement cart;

    while (choice != 4)
    {
        cout << "\n\tTASK LIST" << endl;
        cout << "1. Add item to cart" << endl;
        cout << "2. Delete item from cart" << endl;
        cout << "3. View cart" << endl;
        cout << "4. Back to main menu" << endl;

        cout << "Enter choice: ";
        cin >> choice;

        switch (choice)
        {
        case 1:
        {
            cout << "Enter item name and price (e.g. Laptop 999.99):" << endl;
            cin >> itemName >> itemPrice;
            while (itemName != "done")
            {
                cart.addItem(itemName, itemPrice);
                cout << "Enter item name and price (e.g. Laptop 999.99) or type 'done' to finish:" << endl;
                cin >> itemName;
                if (itemName != "done")
                {
                    cin >> itemPrice;
                }
            }
            break;
        }
        case 2:
        {
            cout << "Enter item name to remove from cart:" << endl;
            cin >> itemName;
            cart.removeItem(itemName);
            cart.viewCart();
            break;
        }
        case 3:
        {
            cart.viewCart();
            break;
        }
        case 4:
        {
            break;
        }
        default:
        {
            cout << "Invalid choice!" << endl;
            cout << "Please enter a valid option" << endl;
            break;
        }
        }
    }
}
// ANUM'S CODE ENDS HERE */

int main() {
    int age;
    string name, username, password;
    Admin ammar;

    cout << endl << setfill('=') << setw(132) << "" << setfill(' ') << endl;
    cout << setw(56) << "" << "ACCOUNT REGISTRATION" << setw(56) << "" << endl;
    cout << setfill('=') << setw(132) << "" << setfill(' ') << endl;
    cout << endl << setw(42) << "" << "Please Enter Your Name : "; getline(cin, name); cout << endl;
    cout << setw(42) << "" << "Please Enter Your Age  : "; cin >> age; cout << endl;
    system("cls"); cout << endl;

    cout << setfill('=') << setw(132) << "" << setfill(' ') << endl;
    cout << setw(60) << "" << "ACCOUNT LOGIN" << setw(60) << "" << endl;
    cout << setfill('=') << setw(132) << "" << setfill(' ') << endl;
    cout << endl << setw(55) << "" << "Username : "; cin >> username; cout << endl;
    cout << setw(66) << "Password : "; cin >> password;
    ammar.setProfile(age, name, username, password);
    cout << "testing" << endl;
    ammar.accountdetails();
}


//a:
//int option;
//cout << "\tMAIN MENU\n1. Manage Cart\n2. Exit\nOption: ";
//cin >> option;
//
// switch (option)
//{
//    case 1:
//        cartOptions();
//        goto a;
//
//    case 2:
//        break;
//
//    default:
//        system("cls");
//        cout << "Invalid option";
//        goto a;
//
//}
//
//return 0;
//}
