If you are managing infrastructure with **Terraform** and someone **manually changes something in AWS**, here is exactly what happens:

---

# ✅ **1. Terraform will NOT automatically detect the manual changes**

Terraform only knows the last state stored in:

* **terraform.tfstate** (local or remote backend)

Manual changes in AWS **do not update Terraform state**.

---

# ✅ **2. When you run `terraform plan`, Terraform will detect a drift**

Terraform compares:

* **Actual AWS resources**
* **State file resources**

If something is different → Terraform shows a **drift**.

Example:

If someone manually changes an EC2 instance type from `t2.micro` → `t2.medium`,
Terraform Plan will show:

```
~ aws_instance.web
      instance_type: "t2.micro" => "t2.medium"
```

---

# ✅ **3. Then Terraform decides based on your configuration:**

### **Case A: Change is not in Terraform code**

Terraform will try to **revert** it back to what code says.

Meaning:
Manual change → **overwritten** by Terraform.

---

### **Case B: Resource is deleted manually**

Terraform sees resource missing and tries to **recreate** it.

```
+ aws_instance.web (create)
```

---

### **Case C: Resource changed manually**

Terraform detects drift and tries to **fix it** based on the .tf code.

---

# ✅ **4. Terraform is always SOURCE OF TRUTH**

Whatever is written in the `.tf` files wins.

Terraform will make AWS match the code.

---

# 🧠 **In simple and short**

> If someone manually changes AWS resources, Terraform will detect the drift during `terraform plan` and will try to bring AWS back to the configuration written in Terraform code.

---

# 🧪 **Real-World Example**

You manage security groups with Terraform.
Someone manually opens port 22 to public:

Terraform plan will show:

```
~ aws_security_group.web
    ingress:
      - from_port: 22
        cidr_blocks: ["0.0.0.0/0"] => []
```

Terraform will **remove** the manual rule.

---

# 🚫 **Best Practice**

Never change resources manually when using Terraform — use:

* IAM policies
* CloudTrail alerts
* Terraform Cloud / Sentinel

To **block or detect manual (drift) changes**.

---

If you want, I can explain:

* `terraform import`
* How to handle manual resources safely
* Drift detection tools
* Real interview answers for Terraform drift
