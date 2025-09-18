# Playwright-Demo

---

# 📘 Day 1 – Playwright for Web Automation: Setup & First Test

---

## 🎯 Learning Objectives

By the end of Day 1, learners will be able to:

* Understand **Playwright’s architecture** & how it differs from Selenium and Cypress.
* Set up Playwright on **Windows + VS Code**.
* Run their **first Playwright test** in headless and headed mode.
* Generate and view Playwright **test reports**.
* Get a **real-world perspective** with example sites.

---

## 1️⃣ Introduction: Why Playwright?

### 🔹 Playwright vs Selenium vs Cypress

| Feature            | Selenium              | Cypress               | Playwright                   |
| ------------------ | --------------------- | --------------------- | ---------------------------- |
| Language Support   | Java, Python, C#, JS  | JavaScript only       | JS/TS, Python, Java, .NET    |
| Browser Support    | Chrome, Firefox, etc. | Chromium-based only   | Chromium, Firefox, WebKit    |
| Auto-waiting       | ❌ Manual waits        | ✅ Retry mechanism     | ✅ Smart auto-waiting         |
| Parallel Execution | Complex setup         | Limited (per browser) | ✅ Built-in parallel          |
| API Testing        | ❌                     | ✅                     | ✅                            |
| Mobile Emulation   | Limited               | ✅                     | ✅ (real devices + emulation) |

👉 **Key takeaway for learners:** Playwright combines **best of both Selenium and Cypress**, making it **fast, reliable, and developer-friendly**.

---

## 2️⃣ Environment Setup (Windows + VS Code)

### Prerequisites

* **Install Node.js LTS** → [https://nodejs.org/en/download](https://nodejs.org/en/download)
  Verify:

  ```powershell
  node -v
  npm -v
  ```
* **Install VS Code** → [https://code.visualstudio.com/download](https://code.visualstudio.com/download)
* Recommended Extensions:

  * Playwright Test for VS Code (Microsoft)
  * ESLint

---

### Step 1: Create a Project Folder

```powershell
mkdir playwright-qa
cd playwright-qa
```

### Step 2: Initialize Playwright Project

```powershell
npm init playwright@latest
```

* Choose → **TypeScript or JavaScript** (for beginners: JavaScript).
* Choose → Add GitHub Actions? → (Y/N as needed).
* Choose → Install browsers? → Yes.

This will generate:

```
playwright-qa/
 ├── tests/
 │    └── example.spec.js
 ├── playwright.config.js
 ├── package.json
 └── test-results/
```

### Step 3: Verify Installation

```powershell
npx playwright test
```

* Runs the sample `example.spec.js`
* Opens **headed** mode if configured

---

## 3️⃣ First Playwright Test (Hands-On)

### Example: Verify Page Title

```javascript
// tests/firstTest.spec.js
import { test, expect } from '@playwright/test';

test('Verify Playwright website title', async ({ page }) => {
  await page.goto('https://playwright.dev/');
  await expect(page).toHaveTitle(/Playwright/);
});
```

👉 Run in **headless** (default):

```powershell
npx playwright test
```

👉 Run in **headed mode** (see browser actions):

```powershell
npx playwright test --headed
```

👉 Run a **specific test file**:

```powershell
npx playwright test tests/firstTest.spec.js
```

---

## 4️⃣ Reports, Screenshots & Logs

### HTML Report

After tests:

```powershell
npx playwright show-report
```

Opens an interactive **HTML report**.

### Test Artifacts

On failures, Playwright automatically stores:

* **Screenshots** → `test-results/`
* **Trace files** (step-by-step logs with DOM snapshots)

👉 Open trace:

```powershell
npx playwright show-trace test-results/trace.zip
```

---

## 5️⃣ Real-World Examples

### 🔹 Example 1: Login Page (SauceDemo)

```javascript
test('Login page validation', async ({ page }) => {
  await page.goto('https://www.saucedemo.com/');
  await page.fill('#user-name', 'standard_user');
  await page.fill('#password', 'secret_sauce');
  await page.click('#login-button');
  await expect(page).toHaveURL(/inventory/);
});
```

👉 Why useful?

* **Real login flow**
* Works across browsers
* Immediate comparison with Selenium (`sendKeys`, `click`) and Cypress (`cy.get().type()`).

---

### 🔹 Example 2: ToDo App (Playwright Demo)

```javascript
test('Add a todo item', async ({ page }) => {
  await page.goto('https://demo.playwright.dev/todomvc');
  await page.locator('.new-todo').fill('Learn Playwright');
  await page.keyboard.press('Enter');
  await expect(page.locator('.todo-list li')).toContainText('Learn Playwright');
});
```

👉 Why useful?

* Demonstrates **locators** (`locator('.new-todo')`)
* Real-world **form interaction**
* Shows how **auto-waiting** avoids flakiness.

---

## 6️⃣ Assignments for Learners

### 📝 Assignment 1: Setup & First Test

* Install Playwright and run sample test.
* Create a test for `https://playwright.dev` and assert:

  * Page title contains *Playwright*
  * Navbar is visible

### 📝 Assignment 2: Real Website Validation

* Write a test for `https://www.saucedemo.com` to:

  * Open login page
  * Enter username/password
  * Click login and assert URL contains `/inventory`

### 📝 Assignment 3: Todo App Automation

* Automate `https://demo.playwright.dev/todomvc`:

  * Add 2 todo items
  * Mark one as completed
  * Assert the completed item is marked correctly

---

## 7️⃣ Takeaways from Day 1

✅ You can **install and configure** Playwright in Windows + VS Code.
✅ You can run tests in **headless and headed** browsers.
✅ You know how to use **basic locators and assertions**.
✅ You can generate **reports, screenshots, and logs**.
✅ You worked with **real-world sites** (SauceDemo, ToDo app).

---


Would you like me to **format this as a “trainer-friendly slide deck outline + demo script”** (like PPT slides + live demo instructions + Q\&A prompts), so you can directly present it in class?
