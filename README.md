#include<iostream>
#include<string>
#include<stdlib.h>
#include<iomanip>
using namespace std;

class Profile
{
protected:
    int age;
    string username;
    string password;

public:
    string name;

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
        cout << "Enter name: "; obj >> p1.name;
        cout << "Enter age: "; obj >> p1.age;
        cout << "Enter username: "; obj >> p1.username;
        cout << "Enter password: "; obj >> p1.password;

        return obj;
    }

    friend ostream& operator <<(ostream& obj, Profile p1)
    {
        obj << "Name: " << p1.name << endl;
        obj << "Age: " << p1.age << endl;
        obj << "Username: " << p1.username << endl;
        obj << "Password: " << p1.password << endl;

        return obj;
    }
};


class Item
{
public:
    string itemName;
    double itemPrice;
    string itemDescription;
    string shopOwner;

    void setItem(string itemName, double itemPrice, string itemDescription, string shopOwner)
    {
        this->itemName = itemName;
        this->itemPrice = itemPrice;
        this->itemDescription = itemDescription;
        this->shopOwner = shopOwner;
    }

    friend ostream& operator <<(ostream& obj, Item item)
    {
        obj << "Item name is: " << item.itemName << endl;
        obj << "Item price is: " << item.itemPrice << endl;
        obj << "Item Description is: " << item.itemDescription << endl;

        return obj;
    }

    friend istream& operator >>(istream& obj, Item& item)
    {
        cout << "Enter name: "; obj >> item.itemName;
        cout << "Enter price: "; obj >> item.itemPrice;
        cout << "Enter description: "; obj >> item.itemDescription;

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
    Admin admin[5];
    shopOwner owner[5];
    Customer customer[5];
    Item item[5];

    admin[0].registration("ammar", 20, "ammar1", "password1");
    owner[0].registration("hamza", 19, "hamza2", "password2");
    customer[0].registration("sajid", 19, "sajid3", "password3");

    item[0].setItem("Earphones", 500, "Best audio ever", owner[0].name);

    int numberOfAdmins = 1;
    int numberOfOwners = 1;
    int numberOfCustomers = 1;
    int numberOfItems = 1;

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
            int adminOption;
            cout << "\tADMIN\n1. View Profile\n2. Reset Profile\n3. Delete Profile\n4. Back To Main Menu\nOPTION: ";
            cin >> adminOption;

            switch (adminOption)
            {
            case 1:
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
            int ownerOption;
            cout << "\tSHOP OWNER\n1. Display Items\n2. Add Item\n3. Remove Item\n4. Back To Main Menu\nOPTION: ";
            cin >> ownerOption;

            switch (ownerOption)
            {
            case 1:
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

        case 'C':
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

    case 2:
    c:

        int option;
        cout << "\tACCOUNT CREATION\n";
        cout << "Do you want to make an account for: \n1. Admin\n2. Shop Owner\n3. Customer\nOPTION: ";
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

        default:
            system("cls");
            cout << "Invalid option please select one of the options below\n";
            goto c;
        }
    default:
        system("cls");
        cout << "Invalid option\n";
        goto a;
    }
}

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
