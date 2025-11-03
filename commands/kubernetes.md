Here’s a **complete Kubernetes commands guide (kubectl cheat sheet)** — organized topic-wise, with short explanations and practical usage examples for interviews and real-world DevOps work 🚀

---

## ☸️ **1. Kubernetes Basic Commands**

| Command                                | Description                                  |
| -------------------------------------- | -------------------------------------------- |
| `kubectl version --short`              | Check client & server (cluster) versions     |
| `kubectl cluster-info`                 | Display cluster master and service endpoints |
| `kubectl get nodes`                    | List all nodes in cluster                    |
| `kubectl describe node <node_name>`    | Show detailed info about a node              |
| `kubectl get componentstatuses`        | Check health of control-plane components     |
| `kubectl config view`                  | Show kubeconfig settings                     |
| `kubectl config current-context`       | Show current cluster context                 |
| `kubectl config use-context <context>` | Switch between clusters/contexts             |

---

## 🧩 **2. Working with Namespaces**

| Command                                                   | Description                               |
| --------------------------------------------------------- | ----------------------------------------- |
| `kubectl get namespaces`                                  | List all namespaces                       |
| `kubectl create namespace <name>`                         | Create new namespace                      |
| `kubectl delete namespace <name>`                         | Delete namespace                          |
| `kubectl config set-context --current --namespace=<name>` | Set default namespace for current session |

---

## 📦 **3. Pods Management**

| Command                                    | Description                                          |
| ------------------------------------------ | ---------------------------------------------------- |
| `kubectl get pods`                         | List pods in current namespace                       |
| `kubectl get pods -A`                      | List pods in all namespaces                          |
| `kubectl describe pod <pod_name>`          | Detailed info about a pod                            |
| `kubectl run <pod_name> --image=<image>`   | Create pod with given image                          |
| `kubectl delete pod <pod_name>`            | Delete a pod                                         |
| `kubectl logs <pod_name>`                  | View logs of a pod                                   |
| `kubectl logs -f <pod_name>`               | Follow live logs                                     |
| `kubectl exec -it <pod_name> -- /bin/bash` | Access pod shell                                     |
| `kubectl port-forward <pod_name> 8080:80`  | Forward port 8080 on local machine to port 80 in pod |

---

## ⚙️ **4. Deployments**

| Command                                            | Description                              |
| -------------------------------------------------- | ---------------------------------------- |
| `kubectl get deployments`                          | List all deployments                     |
| `kubectl create deployment <name> --image=<image>` | Create a new deployment                  |
| `kubectl describe deployment <name>`               | Detailed deployment info                 |
| `kubectl scale deployment <name> --replicas=<n>`   | Scale replicas up/down                   |
| `kubectl rollout status deployment/<name>`         | Check rollout status                     |
| `kubectl rollout history deployment/<name>`        | Check rollout history                    |
| `kubectl rollout undo deployment/<name>`           | Rollback deployment to previous revision |
| `kubectl delete deployment <name>`                 | Delete a deployment                      |

---

## 🧱 **5. ReplicaSets**

| Command                         | Description                |
| ------------------------------- | -------------------------- |
| `kubectl get rs`                | List all ReplicaSets       |
| `kubectl describe rs <rs_name>` | Show details of ReplicaSet |
| `kubectl delete rs <rs_name>`   | Delete ReplicaSet          |

---

## 🌐 **6. Services**

| Command                                                            | Description                  |
| ------------------------------------------------------------------ | ---------------------------- |
| `kubectl get svc`                                                  | List all services            |
| `kubectl expose pod <pod> --type=NodePort --port=80`               | Expose pod as service        |
| `kubectl expose deployment <deploy> --type=LoadBalancer --port=80` | Expose deployment externally |
| `kubectl describe svc <svc_name>`                                  | Show service details         |
| `kubectl delete svc <svc_name>`                                    | Delete service               |

**Service Types:**

* `ClusterIP` → Internal access only
* `NodePort` → Exposes on node IP and port (30000–32767)
* `LoadBalancer` → External access via cloud load balancer

---

## 🧭 **7. ConfigMaps & Secrets**

| Command                                                         | Description                   |
| --------------------------------------------------------------- | ----------------------------- |
| `kubectl create configmap <name> --from-literal=key=value`      | Create ConfigMap from literal |
| `kubectl create configmap <name> --from-file=<path>`            | Create ConfigMap from file    |
| `kubectl get configmap`                                         | List ConfigMaps               |
| `kubectl describe configmap <name>`                             | Show ConfigMap details        |
| `kubectl delete configmap <name>`                               | Delete ConfigMap              |
| `kubectl create secret generic <name> --from-literal=key=value` | Create secret from literal    |
| `kubectl get secrets`                                           | List secrets                  |
| `kubectl describe secret <name>`                                | Show secret details           |
| `kubectl delete secret <name>`                                  | Delete secret                 |

---

## 💾 **8. Persistent Volumes (PV) & Claims (PVC)**

| Command                       | Description                 |
| ----------------------------- | --------------------------- |
| `kubectl get pv`              | List PersistentVolumes      |
| `kubectl get pvc`             | List PersistentVolumeClaims |
| `kubectl describe pv <name>`  | PV details                  |
| `kubectl describe pvc <name>` | PVC details                 |
| `kubectl delete pv <name>`    | Delete PV                   |
| `kubectl delete pvc <name>`   | Delete PVC                  |

---

## 🧍 **9. Service Accounts & RBAC**

| Command                                                                              | Description                  |
| ------------------------------------------------------------------------------------ | ---------------------------- |
| `kubectl get serviceaccounts`                                                        | List service accounts        |
| `kubectl create serviceaccount <name>`                                               | Create service account       |
| `kubectl get roles`                                                                  | List roles                   |
| `kubectl get rolebindings`                                                           | List role bindings           |
| `kubectl describe role <name>`                                                       | Describe role details        |
| `kubectl describe clusterrole <name>`                                                | Show cluster-wide role info  |
| `kubectl create rolebinding <rb_name> --role=<role> --serviceaccount=<ns>:<account>` | Bind role to service account |

---

## 🧭 **10. Labels, Selectors & Annotations**

| Command                                                      | Description              |
| ------------------------------------------------------------ | ------------------------ |
| `kubectl label pod <pod_name> env=prod`                      | Add label to pod         |
| `kubectl get pods --show-labels`                             | Show labels              |
| `kubectl get pods -l env=prod`                               | Filter by label          |
| `kubectl annotate pod <pod_name> description='frontend app'` | Add annotation           |
| `kubectl describe pod <pod_name>`                            | Check labels/annotations |

---

## 🔁 **11. Rolling Updates & Rollbacks**

| Command                                                       | Description                   |
| ------------------------------------------------------------- | ----------------------------- |
| `kubectl set image deployment/<name> <container>=<new_image>` | Update container image        |
| `kubectl rollout status deployment/<name>`                    | Check rollout progress        |
| `kubectl rollout history deployment/<name>`                   | View rollout history          |
| `kubectl rollout undo deployment/<name>`                      | Roll back to previous version |

---

## 🧰 **12. Resource Management**

| Command                       | Description                      |
| ----------------------------- | -------------------------------- |
| `kubectl top node`            | Show CPU & memory usage of nodes |
| `kubectl top pod`             | Show CPU & memory usage of pods  |
| `kubectl describe pod <name>` | Show resource limits/requests    |
| `kubectl get quota`           | Show resource quotas             |

---

## 🧩 **13. Apply YAML Manifests**

| Command                         | Description                           |
| ------------------------------- | ------------------------------------- |
| `kubectl apply -f <file.yaml>`  | Apply configuration                   |
| `kubectl delete -f <file.yaml>` | Delete resources from file            |
| `kubectl get -f <file.yaml>`    | Get resources defined in file         |
| `kubectl diff -f <file.yaml>`   | Compare local YAML with cluster state |

---

## 🧹 **14. Delete Resources**

| Command                            | Description                               |
| ---------------------------------- | ----------------------------------------- |
| `kubectl delete pod <name>`        | Delete specific pod                       |
| `kubectl delete deployment <name>` | Delete deployment                         |
| `kubectl delete svc <name>`        | Delete service                            |
| `kubectl delete all --all`         | Delete all resources in current namespace |

---

## 🧠 **15. Debugging / Troubleshooting**

| Command                                                    | Description                 |
| ---------------------------------------------------------- | --------------------------- |
| `kubectl describe pod <pod>`                               | Check pod events and issues |
| `kubectl get events --sort-by=.metadata.creationTimestamp` | Show events sorted by time  |
| `kubectl logs <pod>`                                       | View pod logs               |
| `kubectl exec -it <pod> -- /bin/bash`                      | Debug inside pod            |
| `kubectl get all`                                          | View all resources          |
| `kubectl get endpoints`                                    | Check service endpoints     |

---

## 🧮 **16. Auto Scaling**

| Command                                                                | Description                     |
| ---------------------------------------------------------------------- | ------------------------------- |
| `kubectl autoscale deployment <name> --min=2 --max=5 --cpu-percent=80` | Enable autoscaling              |
| `kubectl get hpa`                                                      | List Horizontal Pod Autoscalers |

---

## 🔒 **17. DaemonSets, Jobs, CronJobs**

| Command                         | Description     |
| ------------------------------- | --------------- |
| `kubectl get daemonset`         | List DaemonSets |
| `kubectl get jobs`              | List Jobs       |
| `kubectl get cronjobs`          | List CronJobs   |
| `kubectl delete job <name>`     | Delete job      |
| `kubectl delete cronjob <name>` | Delete cronjob  |

---

## 🧾 **18. YAML Generator Shortcuts**

| Command                                                                                         | Description              |
| ----------------------------------------------------------------------------------------------- | ------------------------ |
| `kubectl run nginx --image=nginx --dry-run=client -o yaml > pod.yaml`                           | Generate YAML for a pod  |
| `kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > deploy.yaml`          | Generate deployment YAML |
| `kubectl expose deployment nginx --port=80 --type=NodePort --dry-run=client -o yaml > svc.yaml` | Generate service YAML    |

---

## 🧹 **19. Clean-up Commands**

| Command                         | Description                            |
| ------------------------------- | -------------------------------------- |
| `kubectl delete all --all`      | Delete everything in current namespace |
| `kubectl delete ns <namespace>` | Delete entire namespace                |
| `kubectl delete pvc --all`      | Delete all PVCs                        |

---

## 🔧 **20. Minikube (for Local Testing)**

| Command                       | Description                    |
| ----------------------------- | ------------------------------ |
| `minikube start`              | Start local Kubernetes cluster |
| `minikube status`             | Check status                   |
| `minikube dashboard`          | Open web dashboard             |
| `minikube stop`               | Stop cluster                   |
| `minikube delete`             | Delete cluster                 |
| `minikube service <svc_name>` | Access service in browser      |

---

Would you like me to create a **printable color-coded Kubernetes Command PDF Cheat Sheet** (for quick revision or interview prep)?
I can also include **command output examples** (like what `kubectl get pods` shows).
