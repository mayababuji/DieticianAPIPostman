

---

````markdown
# 🥗 Dietician API Testing Project

This project contains automated API tests for a Dietician system using Postman collections and Newman. Reports are generated using both CLI and Allure. It can be integrated with CI/CD pipelines like Jenkins.

---

## 📁 Project Structure

```bash
.
├── Dietician.json
├── DieticianHackathonEnvironment.postman_environment.json
├── testDataDietician copy.csv
├── README.md
````

---

## 🧪 Tech Stack

* [Postman](https://www.postman.com/) – API test creation
* [Newman](https://www.npmjs.com/package/newman) – Postman collection runner
* [Allure](https://docs.qameta.io/allure/) – HTML test report
* [Jenkins](https://www.jenkins.io/) – CI/CD integration

---

## 🛠️ How to Run Locally

### 1️⃣ Prerequisites

Ensure these are installed globally:

```bash
node -v
npm -v
newman -v
allure --version
```

> Install if missing:

```bash
npm install -g newman newman-reporter-allure
```

---

### 2️⃣ Run the Postman Collection

```bash
newman run "Dietician.json" \
  --environment "DieticianHackathonEnvironment.postman_environment.json" \
  --iteration-data "testDataDietician copy.csv" \
  --reporters cli,allure \
  --reporter-allure-export "allure-results"
```

---

### 3️⃣ Generate Allure Report

```bash
allure generate allure-results --clean -o allure-report
allure open allure-report
```

---

## ⚙️ Jenkins Integration

1. Create a **Freestyle Project**
2. Add GitHub repo in **Source Code Management**
3. In **Build Steps**, use:

```bash
npm install -g newman newman-reporter-allure
newman run "Dietician.json" \
  --environment "DieticianHackathonEnvironment.postman_environment.json" \
  --iteration-data "testDataDietician copy.csv" \
  --reporters cli,allure \
  --reporter-allure-export "allure-results"
```

4. Add **Post-build Action → Allure Report** with path: `allure-results`

---

## ✅ Validations Performed

* Field-level validations for response data using `pm.expect()`
* Iteration-level dynamic data through CSV
* Token/session creation prior to test
* Response code and schema checks
* Attachment download and MIME type validations

---

## 📌 Notes

* Designed for iterative testing using Postman Runner / Newman
* Compatible with local and CI/CD environments
* Allure report gives HTML-based summary and trend tracking

---
## Html report
<img width="760" height="716" alt="image" src="https://github.com/user-attachments/assets/8c8c218c-113a-499f-82b9-70e92c34133c" />

## Allure report
<img width="1333" height="713" alt="image" src="https://github.com/user-attachments/assets/a94161fa-b72c-40d4-826c-18d54427ea6d" />



