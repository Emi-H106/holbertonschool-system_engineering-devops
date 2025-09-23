# Distributed Web Infrastructure  

## Infrastructure Design  

The infrastructure consists of **three servers** that host the website `www.foobar.com`:  

- **1 Load Balancer (HAProxy)**  
- **2 Web/Application/Database servers**  

Each of the two servers contains:  
- A **Web server (Nginx)**  
- An **Application server**  
- A set of **Application files (the code base)**  
- A **Database (MySQL)**  

---

## Elements and Purpose  

- **Load Balancer (HAProxy):**  
  Distributes incoming requests across the two servers to improve availability and scalability.  

- **Web Server (Nginx):**  
  Handles HTTP requests from clients and forwards them to the application server.  

- **Application Server:**  
  Executes the application logic using the code base.  

- **Application Files:**  
  The source code of the application.  

- **Database (MySQL):**  
  Stores and manages the application’s data.  

---

## Load Balancer Configuration  

- **Distribution algorithm:** Round Robin  
  - Requests are distributed sequentially between servers, ensuring equal load.  

- **Setup type:** Active-Active  
  - Both servers are active and handle traffic simultaneously.  
  - (In contrast, an **Active-Passive** setup would have one active server and one standby server that only activates when the active server fails.)  

---

## Database Architecture  

- **Primary-Replica (Master-Slave) cluster:**  
  - **Primary node:** Handles all write operations (INSERT, UPDATE, DELETE).  
  - **Replica node:** Read-only copy of the Primary, used for SELECT queries.  
  - Purpose: Improves read performance and provides redundancy.  

---

## Issues with this Infrastructure  

1. **Single Point of Failure (SPOF):**  
   - The Load Balancer is a single instance. If it goes down, the entire system is unavailable.  
   - The Database has only one Primary; if it fails, no writes are possible.  

2. **Security issues:**  
   - No firewall → servers are directly exposed to the internet.  
   - No HTTPS → traffic is unencrypted and vulnerable to interception.  

3. **Lack of monitoring:**  
   - No way to track server health, performance, or errors.  
   - Difficult to detect or respond quickly to incidents.  

---

## Diagram  

![Distributed web infrastructure](https://private-user-images.githubusercontent.com/190116966/492831648-b121c7af-2e56-4c2b-9232-69e31c94f383.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTg2MzI4OTIsIm5iZiI6MTc1ODYzMjU5MiwicGF0aCI6Ii8xOTAxMTY5NjYvNDkyODMxNjQ4LWIxMjFjN2FmLTJlNTYtNGMyYi05MjMyLTY5ZTMxYzk0ZjM4My5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwOTIzJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDkyM1QxMzAzMTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mYmMwZDBmNTFjNWIwZjg2YjIwNjgxNTgzMmQ1OTI2ODA0ZTkwZWQ2ZmE3MWI1NzcxNTc5NDE0YjM0MmM3MzBhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.9-L0OpmeURzQwWOVQaYh-LXn4k2GLj3HY2RtAdJ9c18)
