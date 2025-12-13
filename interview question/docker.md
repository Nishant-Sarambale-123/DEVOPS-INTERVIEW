To **come out of a Docker container without stopping (exiting) it**, use this key sequence 👇

---

## ✅ **Correct Way**

While inside the container terminal:

```
Ctrl + P  then  Ctrl + Q
```

👉 This **detaches** you from the container
👉 Container **keeps running in background**

---

## ❌ What NOT to do

```bash
exit
```

or

```
Ctrl + D
```

❌ These will **stop the container** (if attached to main process)

---

## 🔹 Interview One-Liner (IMPORTANT)

> “To exit a Docker container without stopping it, use `Ctrl + P` followed by `Ctrl + Q` to detach.”

---

## 🔹 Verify Container Is Still Running

```bash
docker ps
```

---

## 🔹 Alternative (Best Practice)

Instead of attaching directly:

```bash
docker exec -it <container> /bin/bash
```

Then:

```bash
exit
```

✔ Container continues running because you exited the shell, not the main process

---

## 🔹 Bonus Tip (Interview Gold)

Run container in detached mode:

```bash
docker run -d nginx
```

---

## 🔹 Summary Table

| Action                 | Result                          |
| ---------------------- | ------------------------------- |
| `Ctrl + P + Q`         | Detach, container keeps running |
| `exit`                 | Container stops (if PID 1)      |
| `docker exec` + `exit` | Safe exit                       |

---

If you want:
✅ Docker attach vs exec difference
✅ Kubernetes equivalent (`kubectl exec`)
✅ Common Docker interview traps

Just tell me 👍
