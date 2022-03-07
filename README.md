Database Design
ER Diagram
To prevent data redundancy, a single table will be normalized to multiple tables which are linked up by table relationship. A verb in a relationship indicates how the entities are related. Cardinality and optionality can also be shown in the relationship. Cardinality can be classified into one-to-one, one-to-many or many-to-many.

1.	Client and Room


This is a one to many (1: N) relationship
Client can book many rooms.
Room must be booked by a client.

2.	Booking and services


This is a many to one (N: 1) relationship.
Booking must reserve one service. 
A service can be reserved by a booking


3.	Client and Booking



This is a one to many (1: N) relationship.
A client can make many bookings.
A booking must be made by a client.
4.	Client and order


This is a one to many (1: N) relationship.
A client can place many orders.
Order must be placed by a client.
5.	Rent and services


This is a one to one (1: 1) relationship.
Rent must pay for services.
Services can be paid by rent.
 
6.	Hotel and Room



This is one to many (1: N) relationship.
Hotel can have many rooms.
Room must be owned by a hotel.

7.	Hotel and Services



This is one to many (1: N) relationship.
Hotel can have many services.
Services must be owned by hotel.
 
Full Database Schema
Countries:	Countries	ShortForm	Code

Client:	ID	CName	Password	Username	Sex	Phone	Country	Staff	PassportID	Email

Rooms:	Room	Type	Price

RmBooking:	BookID	MemberID	Rmno	Price	ChkIn	ChkOut

RmService:	FID	Item	Type	Price

RmServiceOrder:	OrderNo	Room	Item	Price	Day	DT

Time Period:	Section	Start	End

Entertainment:	EID	EName	Slots	Price

EBooking:	BookID	EID	Username	Section	BDate	EDate	BTime

Buffet:	ID	Client	BookingDate	Price	no
 
Database Tables
A table in a database management system includes organized collection of data, which provides detailed information of that category. 
1.	Client
Field Name	Type	Field Size	Description	Null?	Remark	Examples
ID	Auto
Number	Long Integer	The unique identity code for a member	No	Primary key	1
Password	Text	8	The password for a member	No		123456
CName	Text	20	The given name of a member	No		Admin
Sex	Text	1	The sex of a member	No		M
Phone	Number	Long Integer	The phone number of a member	No		95279527
Email	Text	50	The email of a member	No		admin@dynastyhotel.com
Staff	Yes/No	Yes/No	The Staff identity of a member	No		 

PassportID	Text	20	The Passport number of a member	No		X480832(6)
Country	Text	60	The country of a member	No		Hong Kong
Username	Text	20	The unique username of a member	No		Admin
Admin	Yes/No	Yes/No	The level of access of a member	No		 


2.	Time Period
Field Name	Type	Width	Description	Null?	Remark	Examples
Session	Text	2	The unique identity code for a time period	No	Primary Key	01
Start	Date/Time	Short Time	The starting time of a section	No		12:00
End	Date/Time	Short Time	The finish time of a section	No		2:00
3.	Entertainment
Field Name	Type	Width	Description	Null?	Remark	Examples
EID	Auto
Number	Long Integer	The unique identity code for an entertainment service	No	Primary Key	1
EName	Text	10	The given name of an entertainment service	No		SPA
Slots	Number	Long Integer	The capacity of an entertainment 	No		20
Price	Currency	Currency	The price of booking an entertainment service	No		HK$400

 
4.	EBooking
Field Name	Type	Width	Description	Null?	Remark	Examples
BookID	Auto
Number	Long
Integer	The unique identity code for a booking	No	Primary Key	1
Username	Text	20	The unique username of a member	No		Admin
EID	Number	Long
Integer	The unique identity code for an entertainment service	No		1
Session	Text	2	The unique identity code for a time period	No		10
BDATE	Date/Time	Short Date	The booking date of an entertainment service	No		2/1/2019
BTIME	Date/Time	Short Time	The booking time of a member	No		6:47
EDate	Date/Time	Short Date	The booked date of a member	No		24/1/2019
Price	Currency	Currency	The price of a booking	No		HK$600

 
5.	RmServiceOrder
Field Name	Type	Width	Description	Null?	Remark	Examples
OrderNo	Auto
Number	Long
Integer	The unique identity code for an order	No	Primary Key	1
Username	Text	20	The unique username of a member	No		Admin
Room	Number	Long
Integer	The unique identity code for a room	No		1
Item	Number	Long Integer	The unique identity code for an item	No		10
DT	Date/Time	Short Date	The booking date of an order	No		2/1/2019
Price	Currency	Currency	The price of an order	No		HK$600
Quantity	Number	Long Integer	The quantity of an order	No		6:47
6.	Countries
Field Name	Type	Width	Description	Null?	Remark	Examples
Countries	Text	60	The name of country	No	Primary Key	Hong Kong
ShortForm	Text	2	The short form of country	No		HK
Code	Text	10	The country code	No		+852

 
7.	Buffet
Field Name	Type	Width	Description	Null?	Remark	Examples
ID	Auto Number	Long
Integer	The unique identity code for a booking	No	Primary Key	1
Client	Text	20	The unique username of a member	No		Admin
BookingDate	Date/Time	Short Date	The booking date of buffet	No		2/1/2019
no	Number	Long
Integer	The number of people for a booking	No		1
Price	Currency	Currency	The price of a booking	No		HK$600
BookedDate	Date/Time	Short Date	The booked date of a member	No		24/1/2019
8.	RmService
Field Name	Type	Width	Description	Null?	Remark	Examples
FID	AutoNumber	Integer	The unique identity code for an item	No	Primary Key	1
Item	Text	20	The name of item	No		Hamburger
Type	Text	20	The type of an item	No		Food
Price	Currency	Currency	The price of an item	No		HK$100
 
9.	 Rooms
Field Name	Type	Width	Description	Null?	Remark	Examples
Room	Number	Long Integer	The unique room number for a room	No	Primary Key	101
Type	Text	20	The type of Room	No		Single
Price	Currency	Currency	The price of the room	No		HK$600
10.	RmBooking
Field Name	Type	Width	Description	Null?	Remark	Examples
BookingID	Auto
Number	Long Integer	The unique identity code for a booking	No	Primary Key	43
Username	Text	20	The unique username of a client	No		Admin
Type	Text	20	The type of a room	No		Single
Rmno	Number	Long Integer	The unique identity code for a room	No		10
ChkIn	Number	Long Integer	The check in date of a booking	No		18/1/2019
ChkOut	Date/Time	Short Time	The check out date of a booking	No		19/1/2019
Breakfast	Yes/No	Yes/No	Whether booking include breakfast	No		No
Price	Currency	Currency	The price of the booking	No		HK$1000

 
Implementation
For Customers
A. The Login Page/ authentication
 The client usernames and passwords are stored in the table “Client” as follows:      
 
1. Login
When a client clicks Login, his/her username and password will be checked to make sure the credentials is valid and determine whether he/she is a staff or admin. If the credentials are incorrect, the system will prompt the client and ask for the correct credentials to login. User will be redirected to different menus based on the his/her identity.
2. Register
For new members, they can register an account by clicking Register. 
3. Forget Password
When the client forgets the password, he/she may enter her registered phone number to reset his/her password.  
B. User Menu
 
1. New Booking
A form will appear to allow user to make a new booking.
2. Booking History
A query will be run in the background and a form will appear to show a user’s booking history. 
3. Spa
A form will appear to allow user to make a new booking for spa.
 
4. Sauna
A form will appear to allow user to make a new booking for sauna.
 
5. Buffet
A form will appear to allow user to make a new booking for buffet.
 
6. Room Services
A Room Service Menu will appear.
 
For Staff
A. Login page/ Authentication
 The client usernames and passwords are stored in the table “Client” as follows:
 
 
1. Login
When a client clicks Login, his/her username and password will be checked to make sure the credentials is valid and determine whether he/she is a staff or admin. If the credentials are incorrect, the system will prompt the client and ask for the correct credentials to login. User will be redirected to different menus based on the his/her identity.
B. Staff Menu
 
1.	 Rooms Available
Staff will be prompted to input the Check In and Check Out date in order to check available rooms in that date range. A query will then be run.
 
2.	 Rooms Reserved
Staff will be prompted to input the Check In and Check Out date in order to check booked rooms in that date range. A query will then be run.  
3.	 Customer Menu
Staff will be redirected to the Customer Services Menu and will be able to gain full access to all functions.  
4.	 Today’s Cleaning
A query will be automatically run in the background. A report including a list will then be shown.
  
 
5.	Cleaning when leave
Staff will be prompted to input the Check In and Check Out Date. A query will be run in the background. A report including a list will then be shown.
 
6.	 Cleaning upon arrival
Staff will be prompted to input the Check In and Check Out Date. A query will be run in the background. A report including a list will then be shown.
 
7.	 Room Services Order
A query will be run, a table will then be shown.
 
 
8.	 Invoice
An Invoice Generator form will be opened. Staff can go through different record by the navigation buttons.
 
By the Generate Invoice button, an invoice will be generated. The report will be shown in print preview so that staff can directly print out the invoice. 
 
9.	 Staffs
A list of staff will be shown in a table.
 
 
10.	Add Staff
The staff register form will be opened.
 
11.	Customers
A list of normal users will be shown in a table.  
 
12.	Add Customers
The register form will be opened.
 
13.	Booking History
A query will be run to list the booking history of the current staff.
 
14.	Spa History
A query will be run to list the spa booking history of the current date.
 
15.	Sauna History
A query will be run to list the sauna booking history of the current date.
 
16.	Buffet History
A query will be run to list the buffet booking history of the current date.
 
17.	Spa Booking
A form will appear to allow user to make a new booking for spa.
 
18.	Sauna Booking
A form will appear to allow user to make a new booking for sauna. 
19.	Buffet Booking
A form will appear to allow user to make a new booking for buffet.
 

For Administrators
A. Login page/ Authentication
 The client usernames and passwords are stored in the table “Client” as follows:
 
 
1. Login
When a client clicks Login, his/her username and password will be checked to make sure the credentials is valid and determine whether he/she is a staff or admin. If the credentials are incorrect, the system will prompt the client and ask for the correct credentials to login. User will be redirected to different menus based on the his/her identity.
B. Admin Menu
 
 
1.	 Forms
A form menu will be opened.
 
 
2.	 Queries
A query menu will be opened.
 
3.	 Reports
A report menu will be opened. 
4.	Customer Menu
Staff will be redirected to the Customer Services Menu and will be able to gain full access to all functions.  
 
5.	Staff Menu
Admin will be redirected to the Staff management System Menu and will be able to gain full access to all functions. 
 
 
6.	 Staff
A list of staff will be shown in a table.
 
 
7.	Add Staff
The staff register form will be opened.
 
 
8.	Customers
A list of normal users will be shown in a table. 
SELECT Client.ID, Client.CName, Client.Country, Client.Phone, Client.Password, Client.Username
FROM Client
WHERE (((Client.Staff)=False) AND ((Client.Admin)=False));
 
 
9.	Add Customers
The register form will be opened.
 
10.	Administrators
A list of Administrators will be shown in a table.
SELECT Client.ID, Client.CName, Client.Country, Client.Phone, Client.Password, Client.Username
FROM Client
WHERE (((Client.Admin)=True));
 
 
11.	Add Administrators
The Admin register form will be opened.
  
Testing & Evaluation
 The client usernames and passwords are stored in the table “Client” as follows:      
 
Login
When a client clicks Login, his/her username and password will be checked to make sure the credentials is valid and determine whether he/she is a staff or admin. If the credentials are incorrect, the system will prompt the client and ask for the correct credentials to login. User will be redirected to different menus based on the his/her identity.
 
Administration Panel
 
The “Forms” button can link to the page of all the forms
The “Queries” button can link to the page of all the queries
The “Reports” button can link to the page of all the reports
The “Customer Menu” button can link to the page of normal user interface
The “Staff Menu” button can link to the page of staff management system
The “Staffs” button can link to the page of a list of staffs
The “Customers” button can link to the page of a list of customers
The “Administrators” button can link to the page of a list of administrators
The “Add Staff” button can link to the page to register staff
The “Add Customer” button can link to the page to register customer
The “Add Admin” button can link to the page to register administrator
A.	Forms
The “Forms” button link to the page of all the forms
 
 
1.	Client
The “Client” button link to the page that show a list of all registered clients
 
2. Room Booking
The “Room Booking” button link to the page that show all booking records
 
3. Room Service Order
The “Room Service Order” button link to the page that show all orders
  
4. Buffet Booking
The “Buffet Booking” button link to the page that show all buffet bookings
 
 
5. Entertainment Booking
The “Entertainment Booking” button link to the page that show all spa and sauna bookings
 
 
6.Invoice
The “Invoice” button link to the page that can generate invoice
 
 
7. Booking History
The “Booking History” button link to the page that show booking history of the current user
 
B.	Queries
The “Queries” button link to the page of all the queries 
 
1.	Client
The “Client” button link to a query that show a list of normal users
SELECT Client.ID, Client.CName, Client.Country, Client.Phone, Client.Password, Client.Username
FROM Client
WHERE (((Client.Staff)=False) AND ((Client.Admin)=False));
 
2.	Room Service Orders
The “Room Service Orders” button link to a query that show today’s orders
SELECT RmServiceOrder.Room, RmServiceOrder.Item, RmServiceOrder.Quantity, RmServiceOrder.DT, RmServiceOrder.Price
FROM RmServiceOrder
WHERE (((RmServiceOrder.DT)=Date()));
 

 
3.	Rooms Reserved
The “Room Reserved” button link to a query that show a list of reserved rooms
PARAMETERS [Please enter Check In date] DateTime, [Please enter Check Out date] DateTime;
SELECT RmBooking.Rmno, RmBooking.ChkIn, RmBooking.ChkOut
FROM RmBooking
WHERE (((RmBooking.ChkIn) Between [Please enter Check In date] And [Please enter Check Out date]-1)) OR ((([ChkOut]-1) Between [Please enter Check In date] And [Please enter Check Out date])) OR (((RmBooking.ChkIn)<[Please enter Check In date]) AND (([ChkOut]-1)>[Please enter Check Out date]-1));
 
4.	Check Availability
The “Check Availability” button link to a query that show available rooms
SELECT Rooms.Room
FROM Rooms LEFT JOIN [Rooms Reserved] ON Rooms.Room=[Rooms Reserved].Rmno
WHERE (([Rooms Reserved].Rmno) Is Null);
 
 
5.	Rooms Available
The “Rooms Available” button link to a query that show available rooms with room type
SELECT [Check Availability].Room, Rooms.Type
FROM [Check Availability] INNER JOIN Rooms ON [Check Availability].Room = Rooms.Room
ORDER BY [Check Availability].Room, Rooms.Type;
 
6.	Rooms Cleaning
The “Rooms Cleaning” button link to a query that show rooms that needs cleaning
SELECT RmBooking.ChkIn, RmBooking.ChkOut, RmBooking.Rmno, Rooms.Type
FROM Rooms INNER JOIN RmBooking ON Rooms.Room = RmBooking.[Rmno]
WHERE (((RmBooking.ChkIn)=Date()))
ORDER BY RmBooking.Rmno;
 
7.	Rooms Clean In
The “Rooms Cleaning” button link to a query that show rooms that needs cleaning for new arrivals
SELECT RmBooking.ChkIn, RmBooking.Rmno, Rooms.Type
FROM Rooms INNER JOIN RmBooking ON Rooms.Room = RmBooking.[Rmno]
WHERE (((RmBooking.ChkIn)=Date()))
ORDER BY RmBooking.Rmno;
 
8.	Rooms Clean Out
The “Rooms Cleaning” button link to a query that show rooms that needs cleaning for leaving
SELECT RmBooking.ChkOut, RmBooking.Rmno, Rooms.Type
FROM Rooms INNER JOIN RmBooking ON Rooms.Room = RmBooking.[Rmno]
WHERE (((RmBooking.ChkOut)=Date()))
ORDER BY RmBooking.Rmno;
 
9.	Booking History
The “Booking History” button link to a query that show booking history of the current user
SELECT RmBooking.BookingID, RmBooking.ChkIn, RmBooking.ChkOut, RmBooking.Rmno, RmBooking.Username
FROM RmBooking
WHERE (((RmBooking.Username)=[Forms]![Dynasty Hotel System]![Username]));
 
 
10.	Invoice
The “Invoice” button link to a query that show information required for invoice
SELECT Client.ID, Client.CName, Client.Phone, Client.Username, Buffet.Price, Ebooking.Price, RmBooking.Price, RmServiceOrder.Price, Ebooking.EID, Entertainment.EName, Buffet.BookedDate, Ebooking.EDate, RmBooking.ChkIn, RmBooking.ChkOut, RmServiceOrder.DT, RmBooking.BookingID, Countries.Code
FROM ((RmService INNER JOIN RmServiceOrder ON RmService.FID = RmServiceOrder.Item) INNER JOIN Rooms ON RmServiceOrder.Room = Rooms.Room) INNER JOIN (Entertainment INNER JOIN (Countries INNER JOIN (((Buffet INNER JOIN Client ON Buffet.ID = Client.ID) INNER JOIN Ebooking ON Client.Username = Ebooking.Username) INNER JOIN RmBooking ON Client.Username = RmBooking.Username) ON Countries.Countries = Client.Country) ON Entertainment.EID = Ebooking.EID) ON Rooms.Room = RmBooking.Rmno
WHERE (((Client.Username)=[Forms]![Invoice]![Username]))
ORDER BY RmBooking.BookingID DESC;
 
C.	Report
The “Reports” button link to the page of all the reports 
1.	Cleaning
The “Cleaning” button link to a report that show rooms that needs cleaning
 
 
2.	Arrival
The “Arrival” button link to a report that show rooms that needs cleaning for new arrivals
 

3.	Departure
The “Rooms Cleaning” button link to a report that show rooms that needs cleaning for leaving
 

4.	Invoice
The “Invoice” button link to a report that show a sample invoice
 
