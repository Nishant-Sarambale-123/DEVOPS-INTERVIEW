Got it ✅
I’ll break this GitHub Actions workflow into **detailed interview preparation notes** so you understand *why each step is there*, how it connects to **CI/CD best practices**, and finally I’ll rewrite the workflow cleanly in **proper YAML format**.

---

# 📘 Detailed Notes on Workflow

## 1. Workflow Name & Trigger

```yaml
name: Hprofile Actions
on: workflow_dispatch
```

* **Name** → Just a label for identifying the workflow in GitHub Actions UI.
* **Trigger** → `workflow_dispatch` allows running the workflow **manually** from GitHub Actions tab.
  👉 In interviews, they may ask:
* *Why not use `push` or `pull_request`?*
  → Because `workflow_dispatch` is typically used for **manual pipelines** like deployment on demand.

---

## 2. Global Environment

```yaml
env:
  AWS_REGION: us-east-2
```

* Sets AWS region **globally** for all jobs unless overridden.
* Good practice to define shared configs here (e.g., region, registry name).

---

## 3. Jobs

### 🔹 A. `Testing` Job

```yaml
jobs:
  Testing:
    runs-on: ubuntu-latest
```

* Uses Ubuntu as build agent.
* Purpose → Run tests, static analysis, and SonarQube scan before build.

#### Steps:

1. **Checkout Code**

   ```yaml
   - name: Code checkout
     uses: actions/checkout@v4
   ```

   → Pulls repo code into runner.

2. **Run Maven Tests**

   ```yaml
   - name: Maven test
     run: mvn test
   ```

   → Runs JUnit/Integration tests. Ensures code is not broken.

3. **Run Checkstyle**

   ```yaml
   - name: Checkstyle
     run: mvn checkstyle:checkstyle
   ```

   → Enforces Java coding standards.

4. **Set Java 11**

   ```yaml
   - name: Set Java 11
     uses: actions/setup-java@v3
     with:
       distribution: 'temurin'
       java-version: '11'
   ```

   → Ensures Java 11 is available (SonarQube scanner requires this).

5. **Setup SonarQube**

   ```yaml
   - name: Setup SonarQube
     uses: warchant/setup-sonar-scanner@v7
   ```

   → Downloads SonarQube scanner binary.

6. **Run SonarQube Scan**

   ```yaml
   - name: SonarQube Scan
     run: sonar-scanner ...
   ```

   * Checks:

     * Code quality (`checkstyle`)
     * Unit test reports (`surefire-reports`)
     * Coverage (`jacoco`)
   * Credentials from `secrets`.

7. **Check Quality Gate**

   ```yaml
   - name: SonarQube Quality Gate check
     id: sonarqube-quality-gate-check
     uses: sonarsource/sonarqube-quality-gate-action@master
     timeout-minutes: 5
   ```

   → Workflow **fails** if SonarQube quality gate is not passed (like <80% coverage).
   👉 In interviews: "Why is this step important?" → Prevents bad-quality code from being built & deployed.

---

### 🔹 B. `BUILD_AND_PUBLISH` Job

```yaml
BUILD_AND_PUBLISH:
  needs: Testing
  runs-on: ubuntu-latest
```

* Runs only if **Testing job passes**.

#### Steps:

1. **Checkout Code**

   ```yaml
   - name: Code checkout
     uses: actions/checkout@v4
   ```

2. **Update Application Properties**

   ```yaml
   - name: Update application.properties file
     run: |
       sed -i "s/^jdbc.username.*$/jdbc.username=${{ secrets.RDS_USER }}/" src/main/resources/application.properties
       sed -i "s/^jdbc.password.*$/jdbc.password=${{ secrets.RDS_PASS }}/" src/main/resources/application.properties
       sed -i "s/db01/${{ secrets.RDS_ENDPOINT }}/" src/main/resources/application.properties
   ```

   → Injects DB credentials & endpoint dynamically using **GitHub Secrets**.
   👉 This avoids hardcoding sensitive data.

3. **Build & Push Docker Image**

   ```yaml
   - name: Build & Upload image to ECR
     uses: appleboy/docker-ecr-action@master
     with:
       access_key: ${{ secrets.AWS_ACCESS_KEY_ID }}
       secret_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
       registry: ${{ secrets.REGISTRY }}
       repo: actapp
       region: ${{ env.AWS_REGION }}
       tags: latest,${{ github.run_number }}
       daemon_off: false
       dockerfile: ./Dockerfile
       context: ./
   ```

   * Builds Docker image.
   * Pushes to **AWS ECR** repo (`actapp`).
   * Tags image with `latest` and **build number** → helps in rollbacks & tracking.

---

### 🔹 C. `DEPLOY_TO_K8S` Job

```yaml
DEPLOY_TO_K8S:
  needs: BUILD_AND_PUBLISH
  runs-on: ubuntu-latest
```

* Runs only if Docker image build succeeded.

#### Steps:

1. **Checkout Infra Repo**

   ```yaml
   - name: Checkout Infra Repo
     uses: actions/checkout@v4
     with:
       repository: your-org/infra-repo
       token: ${{ secrets.GH_PAT }}
   ```

   * Pulls **infra repo** (GitOps style).
   * Contains Kubernetes manifests.
     👉 Best practice: separate app code and infra repo.

2. **Update Image Tag**

   ```yaml
   - name: Update image tag in manifest
     run: |
       sed -i "s|image: .*$|image: ${{ secrets.REGISTRY }}/actapp:${{ github.run_number }}|" k8s/deployment.yaml
   ```

   → Updates Kubernetes deployment with new Docker image tag.

3. **Commit & Push**

   ```yaml
   - name: Commit & Push manifest
     run: |
       git config user.name "github-actions"
       git config user.email "actions@github.com"
       git commit -am "Update image tag to run ${{ github.run_number }}"
       git push origin main
   ```

   → Pushes manifest changes back to **infra repo**.
   👉 This triggers **Argo CD / Flux** (GitOps tools) to deploy automatically.

---

# 🔑 Interview Highlights

* **CI/CD Flow**: Code → Test → Quality Check → Build → Push → Deploy.
* **SonarQube**: Ensures quality gate before build.
* **Secrets**: Used for DB credentials, AWS keys, SonarQube tokens → secure practice.
* **ECR Integration**: Stores versioned images.
* **GitOps Deployment**: Updating Kubernetes manifests instead of direct `kubectl apply`.
* **Job Dependencies (`needs`)**: Maintains order & prevents bad builds from deploying.
* **Tagging Strategy**: `latest` + `run_number` ensures both stable & traceable builds.

👉 If asked: *“What if SonarQube fails?”* → Deployment won’t happen, ensuring only good quality code reaches prod.

---

# ✅ Final Clean Workflow YAML

```yaml
name: Hprofile Actions

on:
  workflow_dispatch:

env:
  AWS_REGION: us-east-2

jobs:
  Testing:
    runs-on: ubuntu-latest
    steps:
      - name: Code checkout
        uses: actions/checkout@v4

      - name: Maven test
        run: mvn test

      - name: Checkstyle
        run: mvn checkstyle:checkstyle

      - name: Set Java 11
        uses: actions/setup-java@v3
        with:
          distribution: 'temurin'
          java-version: '11'

      - name: Setup SonarQube
        uses: warchant/setup-sonar-scanner@v7

      - name: SonarQube Scan
        run: |
          sonar-scanner \
            -Dsonar.host.url=${{ secrets.SONAR_URL }} \
            -Dsonar.login=${{ secrets.SONAR_TOKEN }} \
            -Dsonar.organization=${{ secrets.SONAR_ORGANIZATION }} \
            -Dsonar.projectKey=${{ secrets.SONAR_PROJECT_KEY }} \
            -Dsonar.sources=src/ \
            -Dsonar.junit.reportsPath=target/surefire-reports/ \
            -Dsonar.jacoco.reportsPath=target/jacoco.exec \
            -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml \
            -Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/

      - name: SonarQube Quality Gate check
        id: sonarqube-quality-gate-check
        uses: sonarsource/sonarqube-quality-gate-action@master
        timeout-minutes: 5
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
          SONAR_HOST_URL: ${{ secrets.SONAR_URL }}

  BUILD_AND_PUBLISH:
    needs: Testing
    runs-on: ubuntu-latest
    steps:
      - name: Code checkout
        uses: actions/checkout@v4

      - name: Update application.properties file
        run: |
          sed -i "s/^jdbc.username.*$/jdbc.username=${{ secrets.RDS_USER }}/" src/main/resources/application.properties
          sed -i "s/^jdbc.password.*$/jdbc.password=${{ secrets.RDS_PASS }}/" src/main/resources/application.properties
          sed -i "s/db01/${{ secrets.RDS_ENDPOINT }}/" src/main/resources/application.properties

      - name: Build & Upload image to ECR
        uses: appleboy/docker-ecr-action@master
        with:
          access_key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          secret_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          registry: ${{ secrets.REGISTRY }}
          repo: actapp
          region: ${{ env.AWS_REGION }}
          tags: latest,${{ github.run_number }}
          daemon_off: false
          dockerfile: ./Dockerfile
          context: ./

  DEPLOY_TO_K8S:
    needs: BUILD_AND_PUBLISH
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Infra Repo
        uses: actions/checkout@v4
        with:
          repository: your-org/infra-repo
          token: ${{ secrets.GH_PAT }}

      - name: Update image tag in manifest
        run: |
          sed -i "s|image: .*$|image: ${{ secrets.REGISTRY }}/actapp:${{ github.run_number }}|" k8s/deployment.yaml

      - name: Commit & Push manifest
        run: |
          git config user.name "github-actions"
          git config user.email "actions@github.com"
          git commit -am "Update image tag to run ${{ github.run_number }}"
          git push origin main
```

---

Do you want me to also create a **diagram (CI/CD flow)** for this so you can quickly explain in interviews?
