# Skill-Test-Cloud-Containers
# Microservices-Task

## Overview
This document provides details on testing various services after running the `docker-compose` file. These services include User, Product, Order, and Gateway Services. Each service has its own endpoints for testing purposes.

---

## Services and Endpoints

### **User Service**
- **Base URL:** `http://107.21.154.191:3000`
- **Endpoints:**
  - **List Users:**  
    ```
    curl http://107.21.154.191:3000/users
    ```
    Or open in your browser: [http://107.21.154.191:3000/users](http://107.21.154.191:3000/users)

    <img width="501" alt="image" src="https://github.com/user-attachments/assets/8f232bd6-f70d-4218-9537-26755ee33ced" />


---

### **Product Service**
- **Base URL:** `http://107.21.154.191:3001`
- **Endpoints:**
  - **List Products:**  
    ```
    curl http://107.21.154.191:3001/products
    ```
    Or open in your browser: [http://107.21.154.191:3001/products](http://107.21.154.191:3001/products)

    <img width="455" alt="image" src="https://github.com/user-attachments/assets/8fd78e2a-66b1-4751-8790-5b95b52bb808" />


---

### **Order Service**
- **Base URL:** `http://107.21.154.191:3002`
- **Endpoints:**
  - **List Orders:**  
    ```
    curl http://107.21.154.191:3002/orders
    ```
    Or open in your browser: [http://107.21.154.191:3002/orders](http://107.21.154.191:3002/orders)

    <img width="430" alt="image" src="https://github.com/user-attachments/assets/fce958d2-e20d-44bc-9a7f-b9b24c0393a4" />


---

### **Gateway Service**
- **Base URL:** `http://107.21.154.191:3003/api`
- **Endpoints:**
  - **Users:**  
    ```
    curl http://107.21.154.191:3003/api/users
    ```
<img width="427" alt="image" src="https://github.com/user-attachments/assets/b1122566-0041-40ac-bfa6-8c9faf705ea3" />

    
  - **Products:**  
    ```
    curl http://107.21.154.191:3003/api/products
    ```
<img width="417" alt="image" src="https://github.com/user-attachments/assets/537a55a4-8ac2-4d2f-94ec-5246a2695069" />

    
  - **Orders:**  
    ```
    curl http://107.21.154.191:3003/api/orders
    ```
<img width="352" alt="image" src="https://github.com/user-attachments/assets/18392da4-1d2c-4d6c-b257-0e034de2408a" />



---

## Instructions
1. Start all services using the `docker-compose` file:
   ```
   docker-compose up
   ```
<img width="854" alt="image" src="https://github.com/user-attachments/assets/d25f9129-5514-430a-b836-ebc544a573c7" />
<img width="268" alt="image" src="https://github.com/user-attachments/assets/2b49c94a-1dd3-4f1a-bdd0-04a10c1921ac" />


2. Once the services are running, use the above endpoints to verify the functionality.

Happy testing!
