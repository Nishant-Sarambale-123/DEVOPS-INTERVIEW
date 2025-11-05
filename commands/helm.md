Here’s the **complete list of all Helm commands** — from beginner to advanced — perfect for **DevOps engineers and interviews** 👇

---

# ⚓ **HELM COMMANDS (Full Cheat Sheet)**

Helm is the package manager for Kubernetes — it helps you **install, upgrade, manage, and delete applications** using charts.

---

## 🧩 **1. Helm Setup & Basics**

| Command                     | Description                                  |
| --------------------------- | -------------------------------------------- |
| `helm version`              | Show Helm client and server (Tiller) version |
| `helm help`                 | Display help for Helm commands               |
| `helm env`                  | Show Helm environment information            |
| `helm plugin list`          | List installed Helm plugins                  |
| `helm plugin install <URL>` | Install a Helm plugin                        |
| `helm plugin remove <NAME>` | Remove a plugin                              |
| `helm repo list`            | List all configured Helm repositories        |

---

## 📦 **2. Repository Management**

| Command                      | Description                             |
| ---------------------------- | --------------------------------------- |
| `helm repo add <NAME> <URL>` | Add a Helm chart repository             |
| `helm repo update`           | Update chart info from all repositories |
| `helm repo list`             | List repositories                       |
| `helm repo remove <NAME>`    | Remove a repository                     |
| `helm search hub <KEYWORD>`  | Search for charts on the Artifact Hub   |
| `helm search repo <KEYWORD>` | Search for charts in local repos        |
| `helm repo index <DIR>`      | Generate an index.yaml for a local repo |

---

## 🏗️ **3. Chart Management**

| Command                     | Description                                           |
| --------------------------- | ----------------------------------------------------- |
| `helm create <CHART_NAME>`  | Create a new Helm chart with default structure        |
| `helm lint <CHART_PATH>`    | Check chart for issues (validate syntax, structure)   |
| `helm package <CHART_PATH>` | Package chart directory into a .tgz file              |
| `helm show all <CHART>`     | Show all info (readme, values, templates) for a chart |
| `helm show chart <CHART>`   | Show chart metadata only                              |
| `helm show values <CHART>`  | Show default `values.yaml` file of a chart            |
| `helm dependency list`      | Show chart dependencies                               |
| `helm dependency update`    | Update chart dependencies from requirements.yaml      |
| `helm dependency build`     | Build dependencies locally                            |

---

## 🚀 **4. Installing & Managing Releases**

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `helm install <RELEASE_NAME> <CHART>`                        | Install a chart (deploy app)                                 |
| `helm install <RELEASE> <CHART> --values custom-values.yaml` | Install with custom values file                              |
| `helm install <RELEASE> <CHART> --set key=value`             | Override values inline                                       |
| `helm list`                                                  | List all Helm releases                                       |
| `helm list -A`                                               | List all releases in all namespaces                          |
| `helm status <RELEASE_NAME>`                                 | Show status of a release                                     |
| `helm get all <RELEASE_NAME>`                                | Get all information (values, manifests, notes) about release |
| `helm get values <RELEASE_NAME>`                             | Show user-supplied values                                    |
| `helm get manifest <RELEASE_NAME>`                           | Show Kubernetes manifest applied by Helm                     |
| `helm get notes <RELEASE_NAME>`                              | Show release notes                                           |

---

## 🔄 **5. Upgrading, Rolling Back, and Deleting**

| Command                                          | Description                              |
| ------------------------------------------------ | ---------------------------------------- |
| `helm upgrade <RELEASE> <CHART>`                 | Upgrade a release to a new chart version |
| `helm upgrade <RELEASE> <CHART> --reuse-values`  | Upgrade while reusing existing values    |
| `helm upgrade <RELEASE> <CHART> --set key=value` | Upgrade with overridden values           |
| `helm rollback <RELEASE> <REVISION>`             | Roll back to previous version            |
| `helm history <RELEASE>`                         | Show release revision history            |
| `helm uninstall <RELEASE>`                       | Uninstall a release (delete app)         |
| `helm uninstall <RELEASE> --keep-history`        | Uninstall but keep release history       |

---

## 🧮 **6. Template & Rendering Commands**

| Command                                            | Description                                       |
| -------------------------------------------------- | ------------------------------------------------- |
| `helm template <CHART>`                            | Render chart templates locally                    |
| `helm template <CHART> --values custom.yaml`       | Render using custom values                        |
| `helm template <CHART> --set key=value`            | Render with inline values                         |
| `helm install <RELEASE> <CHART> --dry-run --debug` | Preview Kubernetes manifests without applying     |
| `helm get manifest <RELEASE>`                      | View generated manifests for an installed release |

---

## 🧠 **7. Helm Values Management**

| Command                               | Description                                                     |
| ------------------------------------- | --------------------------------------------------------------- |
| `helm show values <CHART>`            | Show default values.yaml                                        |
| `helm get values <RELEASE>`           | Get current values used in a release                            |
| `helm get values <RELEASE> -o yaml`   | Export values in YAML format                                    |
| `helm diff upgrade <RELEASE> <CHART>` | Compare running release with new version (requires diff plugin) |

---

## ⚙️ **8. Namespace & Kubeconfig Options**

| Command                                         | Description                           |
| ----------------------------------------------- | ------------------------------------- |
| `helm install <RELEASE> <CHART> -n <NAMESPACE>` | Install release in specific namespace |
| `helm list -n <NAMESPACE>`                      | List releases in a specific namespace |
| `helm uninstall <RELEASE> -n <NAMESPACE>`       | Delete release from namespace         |
| `helm upgrade <RELEASE> <CHART> -n <NAMESPACE>` | Upgrade release in namespace          |
| `helm --kubeconfig <FILE>`                      | Use custom kubeconfig file            |

---

## 🔐 **9. Security & Verification**

| Command                                                              | Description                 |
| -------------------------------------------------------------------- | --------------------------- |
| `helm verify <CHART.tgz>`                                            | Verify signed chart package |
| `helm repo add <NAME> <URL> --username <USER> --password <PASS>`     | Add repo with credentials   |
| `helm install <RELEASE> <CHART> --username <USER> --password <PASS>` | Install from private repo   |
| `helm registry login <URL>`                                          | Login to OCI registry       |
| `helm registry logout <URL>`                                         | Logout from OCI registry    |

---

## 🧾 **10. Export, Diff & Debug**

| Command                                  | Description                                    |
| ---------------------------------------- | ---------------------------------------------- |
| `helm get manifest <RELEASE>`            | Print rendered Kubernetes manifests            |
| `helm get hooks <RELEASE>`               | Show chart hooks for a release                 |
| `helm diff upgrade <RELEASE> <CHART>`    | Show changes before upgrade (with diff plugin) |
| `helm uninstall <RELEASE> --dry-run`     | Preview uninstall process                      |
| `helm lint`                              | Validate chart syntax and structure            |
| `helm install <RELEASE> <CHART> --debug` | Enable debug output during install             |

---

## 🧰 **11. Helm Plugins (Optional but Useful)**

| Plugin            | Purpose                                           |
| ----------------- | ------------------------------------------------- |
| `helm diff`       | Show differences between revisions before upgrade |
| `helm secrets`    | Manage encrypted secrets in charts                |
| `helm push`       | Push charts to OCI or chart repo                  |
| `helm unittest`   | Run tests on charts                               |
| `helm schema-gen` | Generate JSON schema for values.yaml              |

---

## ✅ **12. Common Daily Command Flow**

```bash
# Add repo and update
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update

# Search for chart
helm search repo nginx

# Install app
helm install my-nginx bitnami/nginx -n default

# Check release
helm list
helm status my-nginx

# Upgrade app
helm upgrade my-nginx bitnami/nginx --set replicaCount=3

# Rollback app
helm rollback my-nginx 1

# Uninstall app
helm uninstall my-nginx
```

---

Would you like me to prepare a **Helm + Argo CD + kubectl + Docker one-page printable PDF cheat sheet** for DevOps interview and daily reference? It’ll have all commands in neat grouped tables.
