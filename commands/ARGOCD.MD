Here’s a **complete list of all Argo CD commands** — from beginner to advanced — covering everything you need for **DevOps interviews and practical use** 👇

---

# 🚀 **Argo CD CLI Commands (Full Reference)**

---

## 🧩 **1. Argo CD CLI Basics**

| Command                             | Description                             |
| ----------------------------------- | --------------------------------------- |
| `argocd version`                    | Show Argo CD client and server versions |
| `argocd help`                       | Show help for all commands              |
| `argocd login <ARGOCD_SERVER>`      | Log in to Argo CD API server            |
| `argocd logout <ARGOCD_SERVER>`     | Log out from the Argo CD API server     |
| `argocd context`                    | View or switch between Argo CD contexts |
| `argocd cluster list`               | List all connected clusters             |
| `argocd cluster add <context-name>` | Connect a Kubernetes cluster to Argo CD |
| `argocd cluster rm <name>`          | Remove a cluster from Argo CD           |

---

## 🧱 **2. Application Management**

| Command                                                          | Description                                    |
| ---------------------------------------------------------------- | ---------------------------------------------- |
| `argocd app list`                                                | List all applications                          |
| `argocd app get <APP_NAME>`                                      | Get details of an application                  |
| `argocd app create <APP_NAME>`                                   | Create a new Argo CD application               |
| `argocd app delete <APP_NAME>`                                   | Delete an application                          |
| `argocd app edit <APP_NAME>`                                     | Edit an application’s configuration            |
| `argocd app set <APP_NAME>`                                      | Modify application settings (repo, path, etc.) |
| `argocd app history <APP_NAME>`                                  | Show application deployment history            |
| `argocd app rollback <APP_NAME> <REVISION>`                      | Roll back app to a previous revision           |
| `argocd app sync <APP_NAME>`                                     | Synchronize app with the Git repository        |
| `argocd app sync <APP_NAME> --prune`                             | Sync and remove resources not in Git           |
| `argocd app sync <APP_NAME> --force`                             | Force sync even if out of sync                 |
| `argocd app wait <APP_NAME>`                                     | Wait until app is healthy and synced           |
| `argocd app terminate-op <APP_NAME>`                             | Terminate a running operation (sync, rollback) |
| `argocd app actions list <APP_NAME>`                             | List resource-specific actions                 |
| `argocd app actions run <APP_NAME> <GROUP_KIND> <NAME> <ACTION>` | Run custom action on a resource                |

---

## 🌱 **3. Repository (Git) Management**

| Command                                                | Description                                |
| ------------------------------------------------------ | ------------------------------------------ |
| `argocd repo list`                                     | List all repositories connected to Argo CD |
| `argocd repo add <REPO_URL>`                           | Add a Git repository                       |
| `argocd repo rm <REPO_URL>`                            | Remove a Git repository                    |
| `argocd repo get <REPO_URL>`                           | Show details of a repository               |
| `argocd repo update-project <REPO_URL> <PROJECT_NAME>` | Associate repo with a project              |
| `argocd repo list-credentials`                         | List repo credentials                      |
| `argocd repo add-credentials`                          | Add repo credentials                       |

---

## 🧭 **4. Project Management**

| Command                                                              | Description                       |
| -------------------------------------------------------------------- | --------------------------------- |
| `argocd proj list`                                                   | List all Argo CD projects         |
| `argocd proj get <PROJECT_NAME>`                                     | Get project details               |
| `argocd proj create <PROJECT_NAME>`                                  | Create a new project              |
| `argocd proj delete <PROJECT_NAME>`                                  | Delete a project                  |
| `argocd proj add-source <PROJECT_NAME> <REPO_URL>`                   | Add source repo to a project      |
| `argocd proj remove-source <PROJECT_NAME> <REPO_URL>`                | Remove source repo                |
| `argocd proj add-destination <PROJECT_NAME> <SERVER> <NAMESPACE>`    | Add cluster/namespace destination |
| `argocd proj remove-destination <PROJECT_NAME> <SERVER> <NAMESPACE>` | Remove destination                |
| `argocd proj role list <PROJECT_NAME>`                               | List all roles in a project       |
| `argocd proj role create <PROJECT_NAME> <ROLE>`                      | Create role within project        |
| `argocd proj role delete <PROJECT_NAME> <ROLE>`                      | Delete a role                     |
| `argocd proj role add-policy`                                        | Add RBAC policy to a project role |
| `argocd proj role add-group`                                         | Add group to a role               |
| `argocd proj role get-token`                                         | Generate JWT token for role       |

---

## 🧰 **5. User & Account Management**

| Command                          | Description                         |
| -------------------------------- | ----------------------------------- |
| `argocd account list`            | List user accounts                  |
| `argocd account get-user-info`   | Display info about current user     |
| `argocd account update-password` | Change your Argo CD password        |
| `argocd account generate-token`  | Generate a JWT authentication token |
| `argocd proj role get-token`     | Generate token for a role           |
| `argocd cert list`               | List TLS certificates               |
| `argocd cert add-tls`            | Add a new TLS certificate           |
| `argocd cert rm`                 | Remove a TLS certificate            |

---

## ⚙️ **6. Application Sync & Diff**

| Command                                            | Description                           |
| -------------------------------------------------- | ------------------------------------- |
| `argocd app diff <APP_NAME>`                       | Compare live vs Git configuration     |
| `argocd app diff <APP_NAME> --revision <REVISION>` | Compare specific Git revision         |
| `argocd app sync <APP_NAME>`                       | Sync app (deploy latest Git changes)  |
| `argocd app sync <APP_NAME> --async`               | Run sync asynchronously               |
| `argocd app sync <APP_NAME> --dry-run`             | Preview sync without applying changes |
| `argocd app sync <APP_NAME> --retry`               | Retry failed syncs automatically      |

---

## 🧩 **7. Application Rollback**

| Command                                           | Description                       |
| ------------------------------------------------- | --------------------------------- |
| `argocd app history <APP_NAME>`                   | View application revision history |
| `argocd app rollback <APP_NAME> <ID>`             | Roll back to a specific version   |
| `argocd app rollback <APP_NAME> --revision <REV>` | Roll back to Git revision         |

---

## 🧾 **8. Application Health & Monitoring**

| Command                              | Description                                          |
| ------------------------------------ | ---------------------------------------------------- |
| `argocd app list`                    | List all applications with health/sync status        |
| `argocd app get <APP_NAME>`          | Get detailed app info (health, sync, repo, revision) |
| `argocd app wait <APP_NAME>`         | Wait until app is healthy & synced                   |
| `argocd app logs <APP_NAME>`         | Show logs for app pods (if supported)                |
| `argocd app resources <APP_NAME>`    | Show Kubernetes resources under management           |
| `argocd app terminate-op <APP_NAME>` | Terminate running sync/rollback ops                  |

---

## 🔐 **9. RBAC, Policies, and Roles**

| Command                                         | Description                       |
| ----------------------------------------------- | --------------------------------- |
| `argocd proj role list <PROJECT_NAME>`          | List roles under a project        |
| `argocd proj role create <PROJECT_NAME> <ROLE>` | Create a new project role         |
| `argocd proj role add-policy`                   | Assign permissions to a role      |
| `argocd proj role get-token`                    | Get token for role authentication |

---

## 🧮 **10. Admin & Maintenance**

| Command                      | Description                       |
| ---------------------------- | --------------------------------- |
| `argocd admin settings dump` | Export Argo CD settings           |
| `argocd admin settings load` | Load settings from file           |
| `argocd admin export`        | Export full Argo CD configuration |
| `argocd admin import`        | Import Argo CD configuration      |
| `argocd admin dashboard`     | Start local dashboard session     |
| `argocd admin repo list`     | List repositories (admin scope)   |
| `argocd admin cluster list`  | List clusters (admin scope)       |

---

## 🧾 **11. Useful Combined Commands**

| Command                                                                                                                                                 | Description                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| `argocd login <ARGOCD_SERVER> --username admin --password <PASSWORD> --insecure`                                                                        | Login without TLS verification     |
| `argocd app create nginx-app --repo https://github.com/devops/nginx.git --path . --dest-server https://kubernetes.default.svc --dest-namespace default` | Create app from Git repo           |
| `argocd app sync nginx-app --prune`                                                                                                                     | Sync app and remove old resources  |
| `argocd app delete nginx-app --cascade`                                                                                                                 | Delete app and its resources       |
| `argocd app diff nginx-app`                                                                                                                             | Compare live and Git configuration |

---

## ✅ **12. Common Daily Use Command Flow**

```bash
# Login
argocd login <ARGOCD_SERVER> --username admin --password <PASSWORD>

# Check cluster and apps
argocd cluster list
argocd app list

# Create & sync app
argocd app create myapp \
  --repo https://github.com/user/repo.git \
  --path manifests \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace default

argocd app sync myapp --prune
argocd app get myapp

# Rollback or delete
argocd app history myapp
argocd app rollback myapp 1
argocd app delete myapp
```

---

Would you like me to generate a **1-page PDF cheat sheet** (like DevOps interview-ready format) that includes **all Argo CD + kubectl + Helm + Docker commands** in a clean table format for printing or study use?
