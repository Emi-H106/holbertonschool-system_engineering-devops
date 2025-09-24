# Scale up Infrastructure

## Additional Elements

- **1 new server**: Increases the capacity of the infrastructure.  
- **Load Balancer Cluster (HAProxy x2)**: Ensures redundancy; if one load balancer fails, the other can continue to serve requests.  
- **Split components**:  
  - **Web Server (Nginx)**: Handles HTTP requests, serves static files, forwards dynamic requests to the application server.  
  - **Application Server**: Processes business logic, interacts with the database.  
  - **Database Server (MySQL)**: Stores and retrieves persistent data.  

---

## Why these elements are added

- **New server**: To handle more traffic and improve reliability.  
- **Load Balancer Cluster**: Avoids SPOF (Single Point of Failure).  
- **Component separation**: Improves scalability, maintainability, and performance by dedicating each server to a specific role.  

---

## Key Concepts

### Web Server vs Application Server
- **Web Server**: Delivers static content and forwards requests for dynamic content.  
- **Application Server**: Runs the application code and generates dynamic content.  

### Database Server
- Dedicated machine for handling queries and storing data.  

---

## Benefits of this Architecture

- **Scalability**: Each component can be scaled independently.  
- **Reliability**: Redundancy with multiple load balancers.  
- **Maintainability**: Easier to manage and troubleshoot when roles are separated.

---

## Diagram  

![Scale up](https://private-user-images.githubusercontent.com/190116966/493325168-40695598-5b08-47e8-a05d-90ef541a9c3a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTg3MTYzNTksIm5iZiI6MTc1ODcxNjA1OSwicGF0aCI6Ii8xOTAxMTY5NjYvNDkzMzI1MTY4LTQwNjk1NTk4LTViMDgtNDdlOC1hMDVkLTkwZWY1NDFhOWMzYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwOTI0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDkyNFQxMjE0MTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03YzJiYTkxMjZkMDU0ODRhZDJhMmRiMzc5OWM5NjI3YTNlZDQ1Y2UyY2E2MjRjYjdmYTk1MDZiZTNmOTVjMzllJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.IZinFqmDWT50k_pvbdL9LY4EsyMD6VbFDkd6CLg6PxA)

