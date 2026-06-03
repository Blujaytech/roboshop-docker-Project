RoboShop Docker Deployment Commands
1. Build Frontend Image
``
docker build -t frontend:v1 .

```
Explanation:

Builds a Docker image from the Dockerfile in the current directory.
-t frontend:v1 assigns the image name frontend and tag v1.
. means use the current directory as the build context.
2. Create Docker Network
docker network create roboshop

Explanation:

Creates a custom bridge network named roboshop.
Allows containers to communicate using container names instead of IP addresses.
3. Start MongoDB Container
```
docker run -d --name mongodb --network roboshop mongodb:v1
```
Explanation:

Runs MongoDB in detached mode.
Container name: mongodb
Connected to the roboshop network.
Uses image mongodb:v1.
4. Start MySQL Container
```
docker run -d --name mysql --network roboshop mysql:v1
```
Explanation:

Runs MySQL container.
Accessible to other containers as mysql.
5. Start Catalogue Service
```
docker run -d --name catalogue --network roboshop catalogue:v1
```
Explanation:

Runs the Catalogue microservice.
Connected to the roboshop network.
6. Start User Service
```
docker run -d --name user --network roboshop user:v1
```
Explanation:

Runs the User microservice.
Communicates with MongoDB through the Docker network.
7. Start Cart Service
```
docker run -d --name cart --network roboshop cart:v1
```
Explanation:

Runs the Cart microservice.
Connected to the same network as other services.
8. Start Shipping Service
docker run -d --name shipping --network roboshop shipping:v1

Explanation:

Runs the Shipping microservice.
Uses MySQL for backend data storage.
9. Start Payment Service
docker run -d --name payment --network roboshop payment:v1

Explanation:

Runs the Payment microservice.
Handles payment processing requests.
10. Start Frontend Service
docker run -d --name frontend --network roboshop -p 80:80 frontend:v1

Explanation:

Runs the Frontend container.
Maps:
Host Port: 80
Container Port: 80
Makes the application accessible from the browser.
Verify Running Containers
docker ps

Explanation:

Displays all running containers.
Access Application
http://<EC2-Public-IP>

Example:

http://34.207.138.52
