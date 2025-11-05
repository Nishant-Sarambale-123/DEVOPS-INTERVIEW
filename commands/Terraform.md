Here’s a **complete list of Terraform commands** — from basic to advanced — with short explanations so you can use them easily for **DevOps interviews and practical work** 👇

---

## 🧩 **1. Terraform Setup & Initialization**

| Command                       | Description                                                                |
| ----------------------------- | -------------------------------------------------------------------------- |
| `terraform -version`          | Check Terraform version                                                    |
| `terraform version`           | Same as above                                                              |
| `terraform -help`             | Show help for Terraform                                                    |
| `terraform init`              | Initialize Terraform working directory (downloads providers, sets backend) |
| `terraform init -reconfigure` | Reinitialize backend configuration                                         |
| `terraform init -upgrade`     | Upgrade modules and providers to newer versions                            |
| `terraform validate`          | Validate syntax and configuration                                          |
| `terraform fmt`               | Format Terraform files for consistency                                     |
| `terraform fmt -recursive`    | Format all `.tf` files in subdirectories                                   |

---

## 🧱 **2. Terraform Plan & Apply**

| Command                           | Description                                            |
| --------------------------------- | ------------------------------------------------------ |
| `terraform plan`                  | Show what will be created, changed, or destroyed       |
| `terraform plan -out=planfile`    | Save execution plan to a file                          |
| `terraform show planfile`         | Display saved plan details                             |
| `terraform apply`                 | Apply configuration to create or modify infrastructure |
| `terraform apply planfile`        | Apply previously saved plan                            |
| `terraform apply -auto-approve`   | Apply without asking for confirmation                  |
| `terraform destroy`               | Destroy all managed infrastructure                     |
| `terraform destroy -auto-approve` | Destroy without confirmation                           |

---

## 🗂️ **3. Terraform State Commands**

| Command                           | Description                                               |
| --------------------------------- | --------------------------------------------------------- |
| `terraform state list`            | List all resources tracked in state file                  |
| `terraform state show <resource>` | Show attributes of a resource                             |
| `terraform state mv <src> <dest>` | Move items within the state file                          |
| `terraform state rm <resource>`   | Remove resource from state file (won’t delete real infra) |
| `terraform state pull`            | Pull current state and print to stdout                    |
| `terraform state push`            | Push local state to remote backend                        |

---

## 📦 **4. Terraform Providers & Modules**

| Command                            | Description                                 |
| ---------------------------------- | ------------------------------------------- |
| `terraform providers`              | List providers used in configuration        |
| `terraform providers mirror <DIR>` | Download provider plugins to local dir      |
| `terraform get`                    | Download or update modules                  |
| `terraform get -update`            | Update all modules to latest source version |

---

## 🧠 **5. Terraform Output & Variables**

| Command                   | Description                                              |
| ------------------------- | -------------------------------------------------------- |
| `terraform output`        | Show all outputs                                         |
| `terraform output <name>` | Show specific output                                     |
| `terraform output -json`  | Show outputs in JSON format                              |
| `terraform console`       | Open interactive console to evaluate expressions         |
| `terraform variables`     | (New in TF 1.10+) List variable values used in workspace |

---

## ⚙️ **6. Terraform Workspace Commands**

| Command                             | Description               |
| ----------------------------------- | ------------------------- |
| `terraform workspace list`          | List all workspaces       |
| `terraform workspace new <name>`    | Create new workspace      |
| `terraform workspace select <name>` | Switch workspace          |
| `terraform workspace show`          | Display current workspace |
| `terraform workspace delete <name>` | Delete a workspace        |

---

## 🔍 **7. Terraform Inspect & Graph**

| Command           | Description                           |                                  |
| ----------------- | ------------------------------------- | -------------------------------- |
| `terraform show`  | Show current state or plan summary    |                                  |
| `terraform graph` | Generate visual graph of dependencies |                                  |
| `terraform graph  | dot -Tpng > graph.png`                | Export dependency graph as image |

---

## 🌐 **8. Terraform Login & Logout**

| Command            | Description                                         |
| ------------------ | --------------------------------------------------- |
| `terraform login`  | Authenticate to Terraform Cloud / Enterprise        |
| `terraform logout` | Remove credentials for Terraform Cloud / Enterprise |

---

## 🧰 **9. Terraform Import & Refresh**

| Command                            | Description                                         |
| ---------------------------------- | --------------------------------------------------- |
| `terraform import <resource> <id>` | Import existing real-world resource into state      |
| `terraform refresh`                | Update local state with remote changes (deprecated) |
| `terraform apply -refresh-only`    | Refresh only without changing infra                 |

---

## 🧾 **10. Terraform Configuration File Commands**

| Command                            | Description                         |
| ---------------------------------- | ----------------------------------- |
| `terraform providers schema -json` | Print provider schema in JSON       |
| `terraform version -json`          | Print version details in JSON       |
| `terraform config inspect`         | Inspect configuration directory     |
| `terraform force-unlock <LOCK_ID>` | Manually unlock a locked state file |

---

## ⚡ **11. Terraform Cloud / Remote Backend**

| Command                                      | Description                         |
| -------------------------------------------- | ----------------------------------- |
| `terraform login`                            | Authenticate to Terraform Cloud     |
| `terraform logout`                           | Logout from Terraform Cloud         |
| `terraform init -backend-config="key=value"` | Override backend config during init |

---

## 🧩 **12. Debugging & Environment Variables**

| Command                        | Description                            |
| ------------------------------ | -------------------------------------- |
| `TF_LOG=TRACE terraform apply` | Enable detailed debug logs             |
| `TF_LOG_PATH=log.txt`          | Save Terraform logs to a file          |
| `TF_VAR_<variable_name>=value` | Pass variable through environment      |
| `export TF_LOG=DEBUG`          | Persistent logging for troubleshooting |

---

## 🧾 **13. File & State Management**

| Command                                | Description                         |
| -------------------------------------- | ----------------------------------- |
| `terraform show -json > state.json`    | Export state as JSON                |
| `terraform output -json > output.json` | Export outputs to JSON              |
| `terraform plan -destroy`              | Show plan to destroy infrastructure |

---

## ✅ **Common Command Sequence for Daily Use**

```bash
terraform init
terraform validate
terraform fmt
terraform plan
terraform apply -auto-approve
terraform output
terraform destroy -auto-approve
```

---

Would you like me to give you a **one-page summarized cheat sheet (PDF)** with all these Terraform commands — formatted for quick interview reference?
