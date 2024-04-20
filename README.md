//libraries that will be used and possibly more


#include<iostream>
#include<string>
#include<stdlib.h>
using namespace std;

//classes that will be used and possibly more

// Define the maximum number of items that can be held in the shopping cart
namespace cart
{
    const int MAX_ITEMS = 10;
    string itemName;
    double itemPrice;
    int choice = -1; // Initialize choice to ensure the loop runs at least once
}
using namespace cart;

// Class representing a customer's shopping cart
class ShopManagement {
private:
    // Arrays to store item names and prices
    string itemNames[MAX_ITEMS];
    double itemPrices[MAX_ITEMS];
    int itemNum; // Tracks the number of items currently in the cart

public:
    // Default constructor initializes the cart with zero items
    ShopManagement() : itemNum(0) {}

    // Method to add an item to the cart
    void addItem(const string& itemName, double itemPrice)
    {
        // Check if the cart has space for more items
        if (itemNum < MAX_ITEMS)
        {
            // Add the item name and price to the respective arrays
            itemNames[itemNum] = itemName;
            itemPrices[itemNum] = itemPrice;
            // Increment the item count
            itemNum++;
            // Confirmation message for the user
            cout << itemName << " has been added to the cart." << endl;
            cout << "Price: $" << itemPrice << endl;
            cout << "Added to cart" << endl;
            cout << endl;
        }
        else
        {
            // Inform the user if the cart is full
            cout << "Cart is full! Sorry, Cannot add more items." << endl;
        }
    }

    // Method to remove an item from the cart
    void removeItem(const string& itemName)
    {
        // Iterate through the items in the cart
        for (int i = 0; i < itemNum; ++i)
        {
            // If the item name matches, remove the item
            if (itemNames[i] == itemName)
            {
                cout << itemName << " has been removed from the cart." << endl;
                // Shift all subsequent items one position to the left
                for (int j = i; j < itemNum - 1; ++j)
                {
                    itemNames[j] = itemNames[j + 1];
                    itemPrices[j] = itemPrices[j + 1];
                }
                // Decrement the item count
                itemNum--;
                // Exit the loop once the item has been removed
                return;
            }
        }
        // Inform the user if the item was not found in the cart
        cout << "Item not found in cart." << endl;
    }

    // Method to display the contents of the cart
    void viewCart()
    {
        // Check if the cart is empty
        if (itemNum == 0)
        {
            cout << "Your cart is empty." << endl;
            return;
        }
        // Display each item and its price
        cout << "Items in your cart:" << endl;
        for (int i = 0; i < itemNum; ++i)
        {
            cout << "- " << itemNames[i] << " : $" << itemPrices[i] << endl;
        }
    }

    // Method to calculate the total price of all items in the cart
    double getTotalPrice()
    {
        double total = 0.0;
        // Sum up the prices of all items in the cart
        for (int i = 0; i < itemNum; ++i)
        {
            total += itemPrices[i];
        }
        return total;
    }
};


class Profile
{
public:
    string fullName;
    string username;
    string password;

};

class Admin
{
    string permissions;

    //ideas for admin settings


    void userManagement()
    {

    }

    void systemSettings()
    {

    }

    void orderManagement()
    {

    }

    void inventoryManagement()
    {

    }

    void customerSupport()
    {

    }
};

class Shop_Owner : public Profile
{
public:
    string shopName;
    string shopDescription;
    int contact;
    string businessEmail;
    string businessAddress;
    int inventory;
};

class Customer : public Profile
{
public:
    string email;
    int contact;
    string shippingAddress;
    string billingAddress;
    string paymentInformation;
    string wishlist;
};

class Prime_Membership
{

};

class Assistant
{

};

void cartOptions();

int main()
{
    int option=0;

    while (option != 2)
    {
        system("cls");
        cout << "\tMAIN MENU\n1. Manage Cart\n2. Exit\nOption: ";
        cin >> option;
        switch (option)
        {
        case 1:
            cartOptions();
            break;
        case 2:
            break;
        }
    }

    return 0;
}

void cartOptions()
{
    // Create an instance of the ShopManagement class
    ShopManagement cart;


    // Main loop to allow the user to interact with the shopping cart
    while (choice != 4)
    {
        // Display task list
        cout << "\n\tTASK LIST" << endl;
        cout << "1. Add item to cart" << endl;
        cout << "2. Delete item from cart" << endl;
        cout << "3. View cart" << endl;
        cout << "4. Back to main menu" << endl;

        cout << "Enter choice: ";
        cin >> choice;

        // Execute the corresponding action based on the user's choice
        switch (choice)
        {
        case 1:
        {
            // Add items to cart
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
            // Remove item from cart
            cout << "Enter item name to remove from cart:" << endl;
            cin >> itemName;
            cart.removeItem(itemName);
            cart.viewCart();
            break;
        }
        case 3:
        {
            // View cart
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
