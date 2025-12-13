To know **which port is used by a Docker container**, use the following commands. These are **interview-standard and practical**.

---

## ✅ **1️⃣ Best & Most Common Command**

```bash
docker port <container-id or container-name>
```

### Example

```bash
docker port nginx-container
```

### Output

```text
80/tcp -> 0.0.0.0:8080
```

✔ Shows **container port → host port mapping**

---

## ✅ **2️⃣ Using `docker inspect` (Most Detailed)**

```bash
docker inspect <container-id> | grep -i port
```

Better (clean output):

```bash
docker inspect -f '{{.NetworkSettings.Ports}}' <container-id>
```

Example output:

```text
map[80/tcp:[{0.0.0.0 8080}]]
```

---

## ✅ **3️⃣ Using `docker ps` (Quick Check)**

```bash
docker ps
```

Example:

```text
CONTAINER ID   IMAGE   PORTS
abc123         nginx   0.0.0.0:8080->80/tcp
```

✔ Fast way to see exposed ports

---

## ✅ **4️⃣ Inside the Container (Advanced)**

```bash
docker exec -it <container-id> netstat -tulnp
```

or

```bash
docker exec -it <container-id> ss -tulnp
```

✔ Shows **which port application is actually listening on**

---

## 🔹 Interview Comparison

| Command          | Shows                                   |
| ---------------- | --------------------------------------- |
| `docker port`    | Container → host port mapping           |
| `docker ps`      | Published ports summary                 |
| `docker inspect` | Full port configuration                 |
| `netstat / ss`   | Actual listening ports inside container |

---

## 🔹 Interview One-Liner (VERY IMPORTANT)

> “To check which port a Docker container uses, we can use `docker port <container>` or check the PORTS column in `docker ps`.”

---

If you want:
✅ Kubernetes equivalent (`kubectl get svc / pod`)
✅ Port conflict troubleshooting
✅ Docker networking interview Q&A

Just tell me 👍
