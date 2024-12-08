---
layout: default
title: "Functional and Non-Functional Requirements"
---

<style>
.back-home-link {
  position: fixed;
  bottom: 5px;
  left: 20px;
  color: white;
  padding: 10px;
  border-radius: 5px;
  text-decoration: none;
  font-weight: normal;
}

.back-home-link:hover {
  background-color: #D3D3D3;
}

.next-section-link {
  position: fixed;
  bottom: 20px;
  right: 20px; 
  color: white;
  padding: 10px;
  border-radius: 5px;
  text-decoration: none;
  font-weight: bold;
}

.next-section-link:hover {
  background-color: #D3D3D3;
}

.previous-section-link {
  position: fixed;
  bottom: 20px;
  left: 20px;
  color: white;
  padding: 10px;
  border-radius: 5px;
  text-decoration: none;
  font-weight: bold;
}

.previous-section-link:hover {
  background-color: #D3D3D3;
}

#table-of-contents {
  margin-bottom: 20px;
}
</style>

# Functional and Non-Functional Requirements

Welcome to the **Functional and Non-Functional Requirements** page for IE Bank. This section outlines the key requirements for the project, divided into functional (core features) and non-functional (quality attributes) categories.

---

## **Table of Contents**
- [Functional Requirements](#functional-requirements)
- [Non-Functional Requirements](#non-functional-requirements)

---

## **Functional Requirements**

### **Requirement #1: Admin Portal – Bank Users Management System**
**Description**:  
The IE Bank system will include a **bank user management portal** for administrators. This portal allows admin users to view, create, update, and delete bank users and their credentials.

- **FR 1**: The application must provide a default administrator account (username and password) to access the user management portal upon successful login.  
  - [Related - User Story #12](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/12) 

- **FR 2**: Once logged in, administrators must be able to list, create, update and delete bank users and passwords.
  - [Related - User Story #29](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/29) 

---

### **Requirement #2: User Portal – Bank Account Management System**
**Description**:  
The IE Bank system will provide a **bank account management portal** for users. This portal allows users to manage accounts, view transactions, and perform banking operations.

- **FR 3**: New users must be able to register through a form that includes a username, password, and password confirmation. Upon registration, a new account is automatically created with a unique account number.  
    - [Related - User Story #25](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/25) 

- **FR 4**: Users must be able to log in using their username and password to access their accounts and transactions securely. Once logged in, they can view only their owned bank accounts and transactions.
    - [Related - User Story #6](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/6)   

- **FR 5**: Users must be able to transfer money to other accounts by providing the recipient's account number and the transfer amount. Transfers must be validated against the sender’s available balance.  
  - [Related - User Story #27](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/27)   

---

## **Non-Functional Requirements**

### **Requirement #1: User/Admin Authentication System**
**Description**:  
The application must implement a secure, basic authentication system requiring usernames and passwords for both users and administrators. Credentials must be securely stored using encryption. Advanced methods such as biometrics or OAuth are not required.

- **NFR 1**: Implement a basic user/admin authentication system to secure access to the application.  
  - **The following user stories have acceptance criterions focused on meeting this NFR. Centered on securely handling user credentials and login time.**
  - [Related - User Story #12 ](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/12) 
  - [Related - User Story #6 ](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/6)   
  

---

### **Requirement #2: Simple Frontend User Interface**
**Description**:  
The frontend interface must be simple and functional. Aesthetic details such as advanced styling, animations, or cross-browser responsiveness are not a priority at this stage.

- **NFR 2**: Provide a straightforward user interface focused on functionality rather than aesthetics. 
    - **The following user stories' acceptance criterion direct focus to the accesibility and functionality of key interface components, without placing emphasis on irrelevant advanced details and styling choices**
    - [Related - User Story #25](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/12) 
    - [Related - User Story #6 ](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/6)  
    - [Related - User Story #27 ](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/27) 
    - [Related - User Story #12 ](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/12) 
    - [Related - User Story #29 ](https://dev.azure.com/zalsahebieu2022/ie-bank-2024/_workitems/edit/29) 

---

Feel free to explore each section for more detailed documentation and links to relevant user stories and tests.

<div class="back-home-link">
  <a href="index.html">Back to Home</a>
</div>

