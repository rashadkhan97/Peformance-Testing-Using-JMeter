# **Performance Testing Using JMeter -  Testing Project**

## **Content**
- [Introduction](#introduction)
- [Test Cases Scenario - Restful-Booker](#test-cases-scenario-restful-booker)
- [API Endpoint Details](#api-endpoint-details)
- [How to run the project](#How-to-run-the-project)
- [Postman API Documentation](#postman-api-documentation)
- [Technology Used](#Technology-Used)
- [Test Case Writing](#test-case-writing)
- [Bug Reporting](#bug-reporting)
- [Newman Report](#newman-report)
    - [Report Summary](#report-summary)
    - [Total Requests](#total-requests)
 


## **Introduction**
In the Performance testing test project - I have taken 2 APIs - 
- **Restful-Booker:** A Books API for load testing and Stress testing
- **Dmoney** A Website Transaction API for API Chainning (JMeter Collection).
Also, I have taken CSV data files to run multiple APIs using Three Threads (Deposit, SendMoney, and Payment) in Jmeter, For Transaction APIs.


## **Test Cases Scenario - Restful-Booker**
Create a Collectio of APIs (JMeter Collection) of Login API, Create Booking API, and Search API HTTP requests
### _**1. Add the following properties to the Header Controller:**_ 
```console  
Accept: */*
```

### _**2. Login**_

#### Request URL: **https://restful-booker.herokuapp.com/auth**
#### Pre-request Script:
```console
body:
    {
        "username": "admin",
        "password": "password123"
    }
```

### _**3.Create Booking**_

#### Request URL: **https://restful-booker.herokuapp.com/booking**
#### Pre-request Script:
```console
body:
   {
    "firstname": "Generate Random FirstName",
    "lastname": "Generate Random LastName",
    "totalprice": Generate random amount,
    "depositpaid": true,
    "bookingdates": {
    "checkin": "2024-01-01",
    "checkout": "2024-01-02"
    }
}
```

### _**4.Search Booking**_

#### Request URL: **https://restful-booker.herokuapp.com/booking/bookingid**

and **Scenario:** **120,000 users** over a **12-hour** period log in, create a booking, and search for the booking. 

