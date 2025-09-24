# Simple Web Stack

## Overview
This project demonstrates a very basic web infrastructure where a website is hosted on a single server using a LAMP-style stack. The website is reachable at **www.foobar.com**, which points to the server's IP address (8.8.8.8).

The purpose of this task is to understand how different components of a simple infrastructure work together, and to identify potential weaknesses of such a setup.

---

## Infrastructure Diagram
![Simple web stack](https://private-user-images.githubusercontent.com/190116966/492802911-73513309-1648-41f9-9492-295eaabbbe1b.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTg3MDQxMDQsIm5iZiI6MTc1ODcwMzgwNCwicGF0aCI6Ii8xOTAxMTY5NjYvNDkyODAyOTExLTczNTEzMzA5LTE2NDgtNDFmOS05NDkyLTI5NWVhYWJiYmUxYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwOTI0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDkyNFQwODUwMDRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00MDQ2ZGMzMTc2NDA0NjU0ODIwNDkyYWY1NDk0NzkxZmI2ZmI1N2E1ZGEyODI3YWFkYTU4ZGE5OTNiNWQ0YjM4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Ht8iMLIabpa3O93X9u2mJ5qPi5mVmPmBFE_eBrayuqI)

---

## Components

- **Domain name (foobar.com)**  
  - Human-friendly name that maps to the server’s IP address.  
  - The record `www.foobar.com` is configured as a **DNS A record** pointing to `8.8.8.8`.

- **Server (IP: 8.8.8.8)**  
  - Physical or virtual machine running the web infrastructure.

- **Web server (Nginx)**  
  - Receives HTTP/HTTPS requests from the user’s browser.  
  - Serves static content (HTML, CSS, JS).  
  - Passes dynamic requests to the application server.

- **Application server**  
  - Runs the application code.  
  - Handles logic for generating dynamic content.

- **Application files (code base)**  
  - The actual source code of the web application.

- **Database (MySQL)**  
  - Stores persistent data such as user accounts, posts, or product information.  
  - Responds to queries from the application server.

- **User (client)**  
  - Accesses the website using a browser.  
  - Communicates with the server over **HTTP/HTTPS**.

---

## Data Flow
1. User enters `www.foobar.com` in their browser.  
2. DNS resolves `www.foobar.com` to `8.8.8.8`.  
3. The browser sends an HTTP request to the server.  
4. Nginx (web server) receives the request.  
5. If static content is requested, Nginx serves it directly.  
6. If dynamic content is requested, Nginx forwards the request to the application server.  
7. The application server may query the MySQL database.  
8. A response is generated and sent back through Nginx to the user’s browser.

---

## Issues with this Infrastructure

- **SPOF (Single Point of Failure):**  
  Only one server is used. If it goes down, the entire website becomes unavailable.

- **Downtime during maintenance:**  
  Restarting services (e.g., Nginx, application updates) causes temporary unavailability.

- **Scalability limitations:**  
  One server cannot handle large amounts of traffic. As traffic increases, performance degrades or the server crashes.

---

## Acronyms

- **LAMP:** Linux, Apache/Nginx, MySQL, PHP/Python (technology stack)  
- **SPOF:** Single Point of Failure  

---
