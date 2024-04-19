//base code for starting 

//libraries that will be used and possibly more
#include<iostream>
#include<string>
#include<stdlib.h>
using namespace std;

//classes that will be used and possibly more
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
	
	void shopManagement()
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

class Shop_Owner: public Profile
{
public:
	string shopName;
	string shopDescription;
	int contact;
	string businessEmail;
	string businessAddress;
	int inventory;
};

class Customer: public Profile
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

//our main
int main()
{

}
