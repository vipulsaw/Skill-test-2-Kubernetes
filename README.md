# Microservices Deployment on Kubernetes with Minikube
This project demonstrates how to deploy a microservices-based Node.js application using Kubernetes and Minikube. The application includes the following services:

- **User Service** (Port 3000)
- **Product Service** (Port 3001)
- **Order Service** (Port 3002)
- **Gateway Service** (Port 3003)
---

## Prerequisites
- Docker
- Minikube
- kubectl
- Docker Hub account (or another container registry)
---

## Step-by-Step Instructions
### 1. Create Dockerfile for each micorservice individually. Use below for your reference.
```bash
FROM node:22
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 3002
CMD [ "npm", "start" ]
```
Repeat for each service.

### 2. Build & Push Docker Images
For each microservice (`user-service`, `product-service`, `order-service`, `gateway-service`), navigate to the folder and run:
```bash
cd .\Microservices\<service-folder>
docker build -t your-dockerhub-username\<service-name>:latest .
docker push your-dockerhub-username/<service-name>:latest
```
Example:
```bash
cd .\Microservices\user-service
docker build -t your-dockerhub-username/user-service:latest .
docker push your-dockerhub-username/user-service:latest
```
Repeat for each service.

### 3. Start Minikube
```bash
minikube start
```
(Optional for Ingress):
```bash
minikube addons enable ingress
```

### 4. Deploy Services and Deployments
From the root directory:
```bash
kubectl apply -f deployments/
kubectl apply -f services/
```
Check status:
```bash
kubectl get pods
kubectl get services
```

### 5. Testing Services
- A. Port-forward Service
```bash
kubectl port-forward svc/servicename PORT:SVCPORT
```
Then open your browser:
```bash
http://localhost:PORT/
```
EXAMPLE
Gateway Service
```bash
kubectl port-forward svc/gateway-service 3003:3003
```
open your browser and hit "http://localhost:3003/"

- B. Inter-service Communication (Inside Pod)
```bash
kubectl exec -it <some-pod-name> -- sh
curl http://user-service:3000/health
curl http://product-service:3001/health
```

### 6. (Optional) Ingress Setup
If you attempted the bonus task:
```bash
kubectl apply -f ingress/
minikube tunnel
```
Then add this to your /etc/hosts file:
```bash
127.0.0.1 microservices.local
```
Test
```bash
http://microservices.local/api/users
```
---

## Troubleshooting Tips<br>
- Pod CrashLoopBackOff: Check logs with kubectl logs <pod-name><br>
- Image Pull Error: Ensure your image name is correct and pushed to Docker Hub<br>
- Service Unreachable: Verify correct port and service name in your requests<br>
---

## Screenshots
- Docker images snapshot<br>
<img  alt="image" src="https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Repository.png" /><br>

- Minikube running snapshot<br>
<img  alt="image" src="https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/minikube_start.png" /><br>

- Applying deployment snapshot<br><br>
<img  alt="image" src="https://github.com/user-attachments/assets/927780c9-8a59-449c-b94d-0f8a56e41248" /><br>

- Applying services snapshot<br><br>
<img  alt="image" src="https://github.com/user-attachments/assets/040694c8-882c-4871-bb39-dc03b304f245" /><br>

- kubectl services status snapshot<br><br>
<img alt="image" src="https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/kubectl-get-service.png" /><br>

- kubectl pods status snapshot<br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/kubectl-get-pods.png)<br>

- minikube Product service snaphsot<br><br>
<img alt="image" src="https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/product-service.png" /><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/product-output.png)<br>

- minikube User service snaphsot<br><br>
<img  alt="image" src="https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/user-service.png" /><br>
<img  alt="image" src="https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/user-output.png" /><br>

- minikube Gateway service snaphsot<br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/gateway-service.png)<br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/gateway-output.png)<br>

- minikube Order service snaphsot<br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/order-service.png)<br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/order-output.png)<br>

- Dokcer build and Push order Service <br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Docker-build-o.png)<br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Dokcer-order.png)<br>

- Dokcer build and Push product Service <br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Docker-build-p.png)<br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Docker-product.png)<br>

- Dokcer build and Push user Service <br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Docker-build-u.png)<br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Docker-user.png)<br>

- Dokcer build and Push gateway Service <br><br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Docker-build-g.png)<br>
![image](https://github.com/praysap/Skill-Test2-Container-Orchestration/blob/main/screenshot/Dokcer-gateway.png)<br>
---


