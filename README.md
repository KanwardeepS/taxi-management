Build the application

##requirements -

Apache Maven 3.0.2 

Java version: 1.8.0_101

##Build App -

mvn clean install -X - in debug mode

##To start the application

To start the application we need to run to services


`java -jar cab-management-portal-1.1.0.RELEASE.jar cmp-server 8080` - after this command wait for the server to up completely

Or you can Import the project as maven project and start the ProductsServer as SpringBoot Applications and test using POSTMAN/BROWSER/SOAP UI

##NOTE:
In memory database has been created with tables and there could be more columns added to add details to existing functionality. Tables are populated with  dummy rows using data-cmpschema-data.sql
The Output of the program is in list for difference services exposed as controllers.
The Data access Repository is directly exposed , however, can be decoupled based on requirements and more layers can be added. I choose to do this way to build this quickly. Offcourse, we can add abstraction layers on top or create composition.

ValidationUtil.java is created to  validate business Rules. Rules can be stored in database or in memory which can be computed later on the fly. 

SecurityConfig has been implemented for authenication/authorisation use from spring boot security module.
Couple of roles have been registered for the moment.
ADMIN role credentails: 
username-admin
password-admin
User role credentails:
username-user1
password-user1
##Search  Booking by  bookingId
http://localhost:8080/booking/bookingid/1
[
  {
    "bookingid": 1,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 590.00
  }
]


##Delete  Booking by  bookingId
http://localhost:8080/booking/delete/1
Response
[
  {
    "bookingid": 0,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 390.00
  },
  {
    "bookingid": 2,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 590.00
  },
  {
    "bookingid": 3,
    "customerid": 2,
    "cabid": 2,
    "distance": 14.00,
    "chargingamount": 510.00
  },
  {
    "bookingid": 4,
    "customerid": 2,
    "cabid": 2,
    "distance": 14.00,
    "chargingamount": 510.00
  },
  {
    "bookingid": 5,
    "customerid": 1,
    "cabid": 4,
    "distance": 4.00,
    "chargingamount": 110.00
  }
]

##Search Booking by cabid
http://localhost:8080/booking/cabid/1
Response:
[
  {
    "bookingid": 0,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 390.00
  },
  {
    "bookingid": 2,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 590.00
  }
]


##Create booking
http://localhost:8080/booking/create

 {
    "bookingid": 0,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 390.00
  }

Response:
[
  {
    "bookingid": 0,
    "customerid": 1,
    "cabid": 1,
    "distance": 15.00,
    "chargingamount": 390.00
  },
  {
    "bookingid": 1,
    "customerid": 1,
    "cabid": 1,
    "distance": 11.00,
    "chargingamount": 340.00
  },
  {
    "bookingid": 2,
    "customerid": 1,
    "cabid": 2,
    "distance": 15.00,
    "chargingamount": 440.00
  },
  {
    "bookingid": 3,
    "customerid": 2,
    "cabid": 1,
    "distance": 7.00,
    "chargingamount": 240.00
  }
]



##Search Booking by customerid

http://localhost:8080/booking/customerid/1
Response
[
  {
    "bookingid": 1,
    "customerid": 1,
    "cabid": 1,
    "distance": 11.00,
    "chargingamount": 340.00
  },
  {
    "bookingid": 2,
    "customerid": 1,
    "cabid": 2,
    "distance": 15.00,
    "chargingamount": 440.00
  }
]

##Search cab by status
http://localhost:8080/cab/status/IDLE
Response:
[
  {
    "cabid": 0,
    "driverName": "Jason",
    "status": "IDLE",
    "latitude": 48.0,
    "longitude": 89.0,
    "assignedcity": "JAIPUR"
  },
  {
    "cabid": 1,
    "driverName": "Sourabh",
    "status": "IDLE",
    "latitude": 69.0,
    "longitude": 88.0,
    "assignedcity": "MUMBAI"
  },
  {
    "cabid": 3,
    "driverName": "Pankaj",
    "status": "IDLE",
    "latitude": 48.0,
    "longitude": 99.0,
    "assignedcity": "MUMBAI"
  },
  {
    "cabid": 4,
    "driverName": "Ravinder",
    "status": "IDLE",
    "latitude": 69.0,
    "longitude": 88.0,
    "assignedcity": "KOLAPUR"
  }
]

##Search cab by driverName
http://localhost:8080/cab/name/Jason
Response:
[
  {
    "driverName": "Jason",
    "status": "IDLE",
    "latitude": 48.0,
    "longitude": 89.0,
    "assignedcity": "JAIPUR"
  }
]


##create cab
http://localhost:8080/cab/create/
{
    "driverName": "Kiran",
    "status": "IDLE",
    "latitude": 30.0,
    "longitude": 30.0,
    "assignedcity": "DELHI"
  }
Response:
[
  {
    "driverName": "Kiran",
    "status": "IDLE",
    "latitude": 30.0,
    "longitude": 30.0,
    "assignedcity": "DELHI"
  },
  {
    "driverName": "Sourabh",
    "status": "IDLE",
    "latitude": 69.0,
    "longitude": 88.0,
    "assignedcity": "MUMBAI"
  },
  {
    "driverName": "Peter",
    "status": "ON_TRIP",
    "latitude": 45.0,
    "longitude": 40.0,
    "assignedcity": "MUMBAI"
  },
  {
    "driverName": "Pankaj",
    "status": "IDLE",
    "latitude": 48.0,
    "longitude": 99.0,
    "assignedcity": "MUMBAI"
  },
  {
    "driverName": "Ravinder",
    "status": "IDLE",
    "latitude": 69.0,
    "longitude": 88.0,
    "assignedcity": "MUMBAI"
  },
  {
    "driverName": "Beny",
    "status": "ON_TRIP",
    "latitude": 48.0,
    "longitude": 49.0,
    "assignedcity": "JAIPUR"
  }
]



##Search city by cityName
http://localhost:8080/city/cityname/Delhi
Response:
[
  {
    "cityid": 2,
    "cityname": "Delhi",
    "pincode": "110001",
    "country": "India",
    "state": "Delhi"
  }
]

##Search city by cityid
http://localhost:8080/city/cityid/1
Response:
[
  {
    "cityid": 1,
    "cityname": "Pune",
    "pincode": "411016",
    "country": "India",
    "state": "Maharashtra"
  }
]

##Delete city
http://localhost:8080/city/delete/1
Response:
[
  {
    "cityid": 2,
    "cityname": "Delhi",
    "pincode": "110001",
    "country": "India",
    "state": "Delhi"
  },
  {
    "cityid": 3,
    "cityname": "Mumbai",
    "pincode": "400001",
    "country": "India",
    "state": "Maharashtra"
  },
  {
    "cityid": 4,
    "cityname": "Jammu",
    "pincode": "180001",
    "country": "India",
    "state": "J&K"
  }
]

##Create city
http://localhost:8080/city/create/
[
  {
    "cityid": 0,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  },
  {
    "cityid": 1,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  },
  {
    "cityid": 2,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  },
  {
    "cityid": 3,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  },
  {
    "cityid": 4,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  },
  {
    "cityid": 5,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  },
  {
    "cityid": 6,
    "cityname": "Kolkata",
    "pincode": "600001",
    "country": "India",
    "state": "West Bengal"
  }
]

##Search customer by email
http://localhost:8080/customer/email/Email1@test
Response:
[
  {
    "customerid": 1,
    "customerName": "Rohan",
    "email": "Email1@test",
    "mobile": "5858585885"
  }
]

http://localhost:8080/customer/customerid/1

Response:
[
  {
    "customerid": 1,
    "customerName": "Rohan",
    "email": "Email1@test",
    "mobile": "5858585885"
  }
]
