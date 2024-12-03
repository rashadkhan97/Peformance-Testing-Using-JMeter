# **Performance Testing Using JMeter -  Testing Project**

## **Content**
- [Introduction](#introduction)
- [Test Case Scenario](#Test-case-scenario)
    - [Test Cases Scenario - Restful-Booker](#test-cases-scenario---restful-booker)
    - [Test Cases Scenario - DMoney Transaction APIs](#test-cases-scenario---dmoney-transaction-apis)
- [How to Run This Project](#how-to-run-this-project)
    - [Using JMeter](#using-jmeter)
    - [Using CLI](#using-cli)
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


## **Test Case Scenario**
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


## **Test Cases Scenario - DMoney Transaction APIs**

### The Dmoney API collection: 
1. Admin creates an Agent, 2 random Customers, and a Merchant.  
   - **Admin email**: `admin@roadtocareer.net`  **Password**: `1234`
2. Deposit some money from the SYSTEM account to the Agent.  
   - **System account**: `SYSTEM`  **Range**: 10 TK to 10,000 TK
3. Agent deposits money to one of the Customers.
   - **Hint**: fromAc: `Agent`, toAc: `Customer`     
4. Then, send money from one Customer to another Customer.
   - **Hint**: fromAc: `Customer`, toAc: `Customer`  
5. Make a payment from the second Customer to the Merchant.
   - **Hint**: fromAc: `Customer`, toAc: `Merchant`

### **Scenario**: 
○ 5 agents perform deposits for 10 customers.
○ 5 customers send money to another 10 customers.
○ 5 customers make payments to 2 merchants.


## How to run this project
### Using JMeter:
- clone this project
   ```console
      https://github.com/rashadkhan97/DMoney-REST-API-with-Newman-Report.git
    ``` 
- Open Apache Jmeter 
- From Jmeter Click on Open then open the JMX file
- Run the file

### Using CLI Mode:
- clone this project
   ```console
      https://github.com/rashadkhan97/DMoney-REST-API-with-Newman-Report.git
    ``` 
- **For Booking APIs JMeter Collection:
  ```console
   jmeter -n -t .\Booking.jmx -l .\Booking.jtl -e -o Reports
  ```

 - ***For Booking APIs JMeter Collection:**
 ```console
jmeter -n -t .\Dmoney.jmx -l .\Dmoney.jtl -e -o Reports
 ```



