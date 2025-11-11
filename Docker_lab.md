Here’s a structured **Docker Lab Exercise Plan** designed for **beginner to intermediate** levels — perfect for hands-on learning and real-world familiarity 👇

---

## 🧩 **Docker Lab Exercises (Beginner → Intermediate)**

### **🟢 LEVEL 1 — Beginner (Basics & Core Commands)**

#### 🧠 Objective

Learn Docker fundamentals — images, containers, and basic commands.

#### 🔧 Prerequisites

* Docker installed on your system (`docker --version`)
* Basic Linux CLI knowledge

#### 🔬 Exercises

1. **Check Docker Installation**

   ```bash
   docker --version
   docker info
   ```

2. **Run Your First Container**

   ```bash
   docker run hello-world
   ```

   ✅ *Confirms Docker works correctly.*

3. **List and Manage Containers**

   ```bash
   docker ps        # Running containers
   docker ps -a     # All containers
   docker stop <container_id>
   docker start <container_id>
   docker rm <container_id>
   ```

4. **Pull and Run a Simple Web Server**

   ```bash
   docker pull nginx
   docker run -d -p 8080:80 nginx
   ```

   🌐 Open `http://localhost:8080` → you should see the Nginx welcome page.

5. **View Logs and Container Shell**

   ```bash
   docker logs <container_id>
   docker exec -it <container_id> /bin/bash
   ```

6. **List and Manage Images**

   ```bash
   docker images
   docker rmi <image_id>
   ```

---

### **🟡 LEVEL 2 — Intermediate (Custom Images & Volumes)**

#### 🧠 Objective

Understand Dockerfiles, volumes, and networking.

#### 🔬 Exercises

1. **Create Your Own Dockerfile**
   Create a simple Python app:

   ```bash
   mkdir myapp && cd myapp
   echo 'print("Hello from Docker!")' > app.py
   ```

   Create a `Dockerfile`:

   ```dockerfile
   FROM python:3.11-slim
   COPY app.py /app/
   WORKDIR /app
   CMD ["python", "app.py"]
   ```

   Build & Run:

   ```bash
   docker build -t mypythonapp .
   docker run mypythonapp
   ```

2. **Use Volumes for Data Persistence**

   ```bash
   docker run -d -p 3306:3306 -v mysql_data:/var/lib/mysql --name mydb mysql:8
   ```

   Check volume:

   ```bash
   docker volume ls
   ```

3. **Connect Containers Using a Network**

   ```bash
   docker network create mynet
   docker run -d --name web --network mynet nginx
   docker run -it --network mynet busybox ping web
   ```

   🧩 *You’ll see “ping” responses proving connectivity.*

4. **Inspect Containers and Networks**

   ```bash
   docker inspect web
   docker network inspect mynet
   ```

5. **Bind Mounts (Code Sharing)**

   ```bash
   mkdir $(pwd)/html
   echo "<h1>Hello Docker Bind Mount</h1>" > html/index.html
   docker run -d -p 8081:80 -v $(pwd)/html:/usr/share/nginx/html nginx
   ```

   🖥️ Visit `http://localhost:8081` — your HTML appears.

---

### **🔵 LEVEL 3 — Intermediate (Docker Compose & Multi-container)**

#### 🧠 Objective

Learn to manage multi-container apps using Docker Compose.

#### 🔬 Exercises

1. **Create a Simple Web + Database Stack**

   Project structure:

   ```
   mycomposeapp/
   ├── docker-compose.yml
   ├── app/
       └── app.py
   └── requirements.txt
   ```

   `app.py`:

   ```python
   from flask import Flask
   app = Flask(__name__)

   @app.route('/')
   def home():
       return "Hello from Flask + Docker Compose!"

   if __name__ == '__main__':
       app.run(host='0.0.0.0', port=5000)
   ```

   `requirements.txt`:

   ```
   flask
   ```

   `docker-compose.yml`:

   ```yaml
   version: "3.8"
   services:
     web:
       build: ./app
       ports:
         - "5000:5000"
       volumes:
         - ./app:/app
     db:
       image: mysql:8
       environment:
         MYSQL_ROOT_PASSWORD: example
   ```

   Commands:

   ```bash
   docker-compose up -d
   docker-compose ps
   docker-compose logs web
   ```

   🌐 Visit `http://localhost:5000` → Flask app should respond.

2. **Scale Services**

   ```bash
   docker-compose up -d --scale web=3
   docker ps
   ```

   Observe multiple containers for the same service.

3. **Tear Down**

   ```bash
   docker-compose down -v
   ```

---

### **🧰 BONUS (Advanced Intermediate Ideas)**

* 🧪 Use **Dockerfile multi-stage builds** for optimized images
* 🔒 Add **environment variables** and `.env` files
* 📦 Push your custom image to **Docker Hub**

  ```bash
  docker login
  docker tag mypythonapp <your_dockerhub_username>/mypythonapp:latest
  docker push <your_dockerhub_username>/mypythonapp:latest
  ```

---

### ✅ **Outcome**

After completing all labs, you’ll know how to:

* Build and manage containers
* Create Dockerfiles
* Use volumes and networks
* Run multi-container apps with Compose
* Push/pull images to Docker Hub

---
