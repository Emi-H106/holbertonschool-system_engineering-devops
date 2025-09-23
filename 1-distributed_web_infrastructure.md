# 📘 README – Distributed Web Infrastructure  

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

![Distributed web infrastructure](image)
