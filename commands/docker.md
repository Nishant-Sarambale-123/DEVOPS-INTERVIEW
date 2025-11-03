Here’s a **complete Docker commands notes guide** — organized topic-wise and suitable for **interview prep and quick revision** 🚀

---

## 🐳 **1. Docker Basics**

| Command            | Description                      |
| ------------------ | -------------------------------- |
| `docker --version` | Check installed Docker version   |
| `docker info`      | Show system-wide Docker info     |
| `docker help`      | Show help for Docker commands    |
| `docker login`     | Log in to Docker Hub or registry |
| `docker logout`    | Log out from Docker registry     |

---

## 🧱 **2. Working with Images**

| Command                             | Description                       |
| ----------------------------------- | --------------------------------- |
| `docker pull <image>`               | Download an image from Docker Hub |
| `docker images`                     | List all images on the system     |
| `docker rmi <image>`                | Remove an image                   |
| `docker tag <src> <repo>:<tag>`     | Tag image with new name/tag       |
| `docker inspect <image>`            | Show detailed info about image    |
| `docker history <image>`            | Show image build history          |
| `docker save -o <file>.tar <image>` | Save image as tar archive         |
| `docker load -i <file>.tar`         | Load image from tar archive       |

---

## 🧩 **3. Working with Containers**

| Command                                              | Description                             |
| ---------------------------------------------------- | --------------------------------------- |
| `docker run <image>`                                 | Run a container from image              |
| `docker run -it <image> /bin/bash`                   | Start container in interactive shell    |
| `docker run -d <image>`                              | Run container in detached mode          |
| `docker run --name <name> <image>`                   | Assign a name to the container          |
| `docker run -p <host>:<container> <image>`           | Map host port to container port         |
| `docker run -v <host_path>:<container_path> <image>` | Mount a volume                          |
| `docker run --env KEY=value <image>`                 | Pass environment variables              |
| `docker ps`                                          | List running containers                 |
| `docker ps -a`                                       | List all containers (running + stopped) |
| `docker start <container>`                           | Start a stopped container               |
| `docker stop <container>`                            | Stop a running container                |
| `docker restart <container>`                         | Restart a container                     |
| `docker rm <container>`                              | Remove a container                      |
| `docker exec -it <container> <command>`              | Run command inside a running container  |
| `docker attach <container>`                          | Attach to running container’s console   |
| `docker logs <container>`                            | View logs of container                  |
| `docker top <container>`                             | Show processes inside container         |
| `docker stats`                                       | Show resource usage (CPU, RAM, etc.)    |
| `docker inspect <container>`                         | Show detailed container info            |

---

## 🧺 **4. Container Lifecycle Shortcuts**

| Command                  | Description                                             |
| ------------------------ | ------------------------------------------------------- |
| `docker container ls`    | Same as `docker ps`                                     |
| `docker container prune` | Remove all stopped containers                           |
| `docker image prune`     | Remove unused images                                    |
| `docker system prune`    | Remove unused containers, networks, images, and volumes |

---

## 🧑‍🍳 **5. Building Docker Images**

| Command                                    | Description                         |
| ------------------------------------------ | ----------------------------------- |
| `docker build -t <name>:<tag> .`           | Build image from Dockerfile         |
| `docker build -f <Dockerfile> -t <name> .` | Specify Dockerfile name             |
| `docker commit <container> <image_name>`   | Create image from container changes |

---

## 🌐 **6. Networking Commands**

| Command                                           | Description                         |
| ------------------------------------------------- | ----------------------------------- |
| `docker network ls`                               | List networks                       |
| `docker network create <name>`                    | Create a network                    |
| `docker network inspect <name>`                   | Inspect network details             |
| `docker network connect <network> <container>`    | Connect container to a network      |
| `docker network disconnect <network> <container>` | Disconnect container from a network |
| `docker network rm <name>`                        | Remove a network                    |

---

## 📦 **7. Volumes (Storage)**

| Command                                                | Description               |
| ------------------------------------------------------ | ------------------------- |
| `docker volume create <name>`                          | Create volume             |
| `docker volume ls`                                     | List volumes              |
| `docker volume inspect <name>`                         | Inspect volume            |
| `docker volume rm <name>`                              | Remove volume             |
| `docker volume prune`                                  | Remove all unused volumes |
| `docker run -v <volume_name>:<container_path> <image>` | Mount volume to container |

---

## 🛠️ **8. Docker Compose**

| Command                               | Description                                |
| ------------------------------------- | ------------------------------------------ |
| `docker-compose up`                   | Start all services                         |
| `docker-compose up -d`                | Start in detached mode                     |
| `docker-compose down`                 | Stop and remove containers, networks, etc. |
| `docker-compose ps`                   | List containers in Compose                 |
| `docker-compose logs`                 | View logs                                  |
| `docker-compose build`                | Build or rebuild services                  |
| `docker-compose restart`              | Restart all services                       |
| `docker-compose exec <service> <cmd>` | Run command inside a service container     |

---

## 🧰 **9. Docker System Management**

| Command               | Description                   |
| --------------------- | ----------------------------- |
| `docker system df`    | Show Docker disk usage        |
| `docker system prune` | Clean up unused data          |
| `docker info`         | Show detailed system info     |
| `docker version`      | Display client/server version |

---

## 🧑‍💻 **10. Docker Registry (Push/Pull Custom Images)**

| Command                                      | Description              |
| -------------------------------------------- | ------------------------ |
| `docker tag <image> <username>/<repo>:<tag>` | Tag image for Docker Hub |
| `docker push <username>/<repo>:<tag>`        | Push image to registry   |
| `docker pull <username>/<repo>:<tag>`        | Pull image from registry |
| `docker login`                               | Log in to registry       |
| `docker logout`                              | Log out from registry    |

---

## ⚙️ **11. Troubleshooting & Debugging**

| Command                            | Description                    |
| ---------------------------------- | ------------------------------ |
| `docker inspect <container>`       | Show container details         |
| `docker logs <container>`          | Show container logs            |
| `docker exec -it <container> bash` | Access container shell         |
| `docker events`                    | Stream real-time Docker events |
| `docker system df`                 | Check Docker disk usage        |
| `docker stats`                     | Live container resource usage  |

---

## 🔥 **12. Useful Shortcuts**

| Command                                | Description                    |
| -------------------------------------- | ------------------------------ |
| `docker rm $(docker ps -aq)`           | Remove all containers          |
| `docker rmi $(docker images -q)`       | Remove all images              |
| `docker stop $(docker ps -aq)`         | Stop all containers            |
| `docker system prune -a`               | Remove everything unused       |
| `docker exec -it $(docker ps -q) bash` | Access first running container |

---

Would you like me to make this into a **PDF or printable cheatsheet** (with sections & color formatting for easy revision)?
