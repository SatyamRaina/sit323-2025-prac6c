📚 Overview

This project continues from Task 6.1P by demonstrating direct interaction with a Kubernetes cluster, deploying a simple Calculator Microservice built using Node.js, Docker, and Kubernetes, and exposing it through port forwarding for local testing.

You will verify deployments, forward ports to your local machine, access the service through a web browser, and observe resource management using the Kubernetes Dashboard.

🧩 Project Structure
```
week6taskC/
├── deployment.yaml          # Kubernetes Deployment configuration
├── Dockerfile                # Docker build file
├── package.json              # Node.js project metadata
├── package-lock.json         # Node.js dependency lock file
├── service.yaml              # Kubernetes Service configuration
├── test.js                   # Calculator microservice source code
└── README.md                 # Project documentation (this file)
```

🛠️ How to Run

1. Clone the Repository
```
git clone https://github.com/SatyamRaina/sit323-2025-prac6c.git
cd sit323-2025-prac6c/week6taskC
```
3. Build and Push Docker Image
```
docker build -t satyamraina/week6task-calculator:latest .
docker push satyamraina/week6task-calculator:latest
```
5. Deploy Application to Kubernetes
```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```
7. Verify Deployment
```
kubectl get pods
kubectl get services
```
✅ You should see the pod and service calculator-service exposed internally.

🌐 Access the Application via Port Forwarding

5. Forward Port
```
kubectl port-forward svc/calculator-service 8080:80
```
This forwards local port 8080 to service port 80 inside the Kubernetes cluster.

7. Test Endpoints
Open your browser and use the following URLs:
```
Endpoint Example	Operation
http://localhost:8080/add?n1=5&n2=3	Addition
http://localhost:8080/subtract?n1=10&n2=4	Subtraction
http://localhost:8080/multiply?n1=7&n2=6	Multiplication
http://localhost:8080/divide?n1=20&n2=4	Division
http://localhost:8080/power?n1=2&n2=3	Power
http://localhost:8080/mod?n1=10&n2=3	Modulus
http://localhost:8080/sqrt?n1=16	Square Root
http://localhost:8080/calculate?n1=5&n2=3&operation=add	Dynamic Operation
```
📚 Learning Outcomes

1. Deploying containerized Node.js applications to Kubernetes.
2. Exposing services using NodePort and port-forward techniques.
3. Interacting with Kubernetes clusters through kubectl and Dashboard.
4. Understanding service-to-local port mapping.
5. Monitoring deployments visually with Kubernetes Dashboard.

🔥 Future Improvements (Optional Ideas)

1. Configure an Ingress Controller for better routing.
2. Add Horizontal Pod Autoscaling.
3. Secure API endpoints with basic authentication.
4. Automate deployment using a CI/CD pipeline (e.g., GitHub Actions).

👨‍💻 Author

Satyam Raina
Bachelor of Software Engineering (Honours) - Cloud Computing Major
Deakin University, Australia

