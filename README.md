# 🧪 API Automation Project – Restful Booker (Postman)

This repository contains a fully automated **API Testing Framework** built using **Postman**, featuring data-driven execution, environment-based configuration, request chaining, and script-level assertions.  
It is designed as a practical automation project for validating the complete CRUD workflow of the **Restful Booker API**.

---

## 📌 Project Overview

The goal of this project is to demonstrate structured API testing using:

- **Postman Collection** (Automation scripts)
- **Environment Variables** (Dynamic data handling)
- **CSV Data File** (Data-driven testing)
- **Chained Requests** (ID and Token forwarding)
- **Automated Assertions** (Validation at each step)

This framework ensures full coverage of booking operations including **Create → Retrieve → Authenticate → Update → Delete → Verify Deletion**.

---

## 📁 Project Structure

├── Practice_01.postman_collection.json # Main Postman Collection
├── Practice_01.postman_environment.json # Environment Variables
├── Data.csv # Data-Driven Testing File
└── README.md

---

## 🚀 Key Features

### 🔹 **1. Create Booking**
- Sends a POST request with dynamic data.
- Extracts and stores `bookingid` into environment variable `id`.
- Validates successful creation.

### 🔹 **2. Retrieve Booking**
- GET request using the generated booking ID.
- Comprehensive field-level validations:
  - firstname  
  - lastname  
  - totalprice  
  - depositpaid  
  - bookingdates  
  - additionalneeds  

### 🔹 **3. Generate Token**
- Authenticates via `/auth` endpoint.
- Stores token into `token` environment variable.
- Confirms token validity through assertions.

### 🔹 **4. Update Booking**
- PUT request with updated payload.
- Token-based authentication using `Cookie: token={{token}}`.

### 🔹 **5. Validate Updated Data**
- Ensures the updated booking matches expected values.

### 🔹 **6. Delete Booking**
- Deletes the existing booking using the token.

### 🔹 **7. Verify Deletion**
- GET request expected to return:
Practice_01

---

### **3️⃣ Run Using Postman Collection Runner**

1. Open **Runner**
2. Select:
   - Collection: _Practice_01_
   - Environment: _Practice_01_
   - Data File: _Data.csv_
3. Click **Run Collection**

All scripts will execute automatically, including:
- ID extraction  
- Token extraction  
- Field validations  
- CRUD sequence  

---

## 📜 Example Test Scripts

### 🔸 Extract Booking ID
```javascript
var jsondata = pm.response.json();
pm.environment.set("id", jsondata.bookingid);
🔸 Validate First Name
pm.test("First Name Validation", function () {
  pm.expect(pm.iterationData.get("firstname")).to.equal(jsondata.firstname);
});
🔸 Store Token
var jsondata = pm.response.json();
pm.environment.set("token", jsondata.token);
🌐 Base URL
https://restful-booker.herokuapp.com

🎯 Learning Outcomes

By working through this project, you gain hands-on experience with:

Building API automation from scratch

Using environment variables & token chaining

Data-driven testing via CSV

Writing JavaScript-based Postman test scripts

Validating complex JSON structures

Complete CRUD testing workflow
