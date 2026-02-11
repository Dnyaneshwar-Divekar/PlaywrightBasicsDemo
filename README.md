# Playwright Framework for QA Engineers – From Manual Testing to Hands-on Automation

---

## Session Objective

After this session, participants will be able to:

- Understand modern UI automation testing
- Install and configure Playwright
- Create and execute automation tests
- Use locators and perform UI actions
- Add validations using assertions
- Debug failures using reports and trace viewer
- Understand how Playwright fits into real company projects

---

## Agenda

1. Modern UI Testing Challenges
2. Introduction to Playwright
3. Playwright Architecture
4. Playwright vs Selenium
5. Installation & Setup
6. Project Structure
7. Writing First Test
8. Core Concepts (Browser, Context, Page)
9. Locators
10. Actions
11. Handling Advanced UI
12. Auto-Wait & Synchronization
13. Assertions
14. Test Organization & Hooks
15. Page Object Model
16. Debugging & Reporting
17. Parallel Execution
18. CI/CD Integration
19. Best Practices
20. Summary

---

## 1. Modern UI Testing Challenges

Modern applications use:
- React
- Angular
- Vue

Common problems faced in automation:

- Dynamic elements
- Changing DOM
- Asynchronous loading
- AJAX requests
- Timing issues
- Flaky tests

Traditional tools struggle due to manual synchronization handling.

---

## 2. Introduction to Playwright

Playwright is an open-source browser automation framework developed by Microsoft to automate modern web applications reliably.

It allows automation of user behavior exactly like a real user.

### Supported Browsers

- Chromium
- Firefox
- WebKit

### Supported Languages

- JavaScript / TypeScript
- Java
- Python
- .NET

---

## 3. Playwright Architecture

Playwright directly communicates with browser engines using browser protocols.

No WebDriver is used.

### Flow

Test Script → Playwright API → Browser Protocol → Browser

Because of this:
- Faster execution
- Stable interaction
- Reliable element handling

---

## 4. Playwright vs Selenium

| Feature | Selenium | Playwright |
|--------|--------|--------|
| Communication | WebDriver | Direct Browser Protocol |
| Wait Handling | Manual | Automatic |
| Speed | Medium | Fast |
| Setup | Driver required | No driver |
| Parallel | Complex | Built-in |
| Debugging | Limited | Advanced |
| Multi-tab | Difficult | Easy |

---

## Advantages of Playwright

- Built-in synchronization
- Cross-browser testing
- Built-in reporters
- Screenshots on failure
- Video recording
- Network monitoring
- API testing support

---

## 5. Installation & Setup

### Prerequisites

Install:
- Node.js
- VS Code

### Create Project

```bash
mkdir PlaywrightDemo
cd PlaywrightDemo
npm init playwright@latest
````

Select:

* JavaScript
* Install browsers: Yes

### Run Default Tests

```bash
npx playwright test
```

### Open Report

```bash
npx playwright show-report
```

---

## 6. Project Structure

```
PlaywrightDemo
 ┣ tests/
 ┣ node_modules/
 ┣ playwright.config.js
 ┣ package.json
```

### File Details

| File         | Description               |
| ------------ | ------------------------- |
| tests        | Automation scripts        |
| config       | Framework configuration   |
| node_modules | Installed libraries       |
| package.json | Dependencies and commands |

---

## 7. Writing First Test

```js
const { test, expect } = require('@playwright/test');

test('Open Website', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveTitle(/Example/);
});
```

### Explanation

* `test()` defines test case
* `page` represents browser tab
* `goto()` navigates
* `expect()` verifies

---

## 8. Core Concepts

### Browser

Actual browser instance

### Context

Isolated session
Equivalent to incognito window

### Page

Single browser tab

### Execution Flow

Browser → Context → Page → Actions → Assertions

### Execution Modes

Headless: Runs without UI
Headed: Runs with visible browser

---

## 9. Locators

Playwright recommends user-visible locators.

### Types

* getByRole()
* getByText()
* getByLabel()
* getByPlaceholder()
* CSS
* XPath (least preferred)

### Example

```js
await page.getByRole('button', { name: 'Login' }).click();
```

---

## 10. Actions

### Input

```js
await page.fill('#username','admin');
```

### Click

```js
await page.click('#loginBtn');
```

### Dropdown

```js
await page.selectOption('#country','India');
```

### Hover

```js
await page.hover('#menu');
```

### Keyboard

```js
await page.keyboard.press('Enter');
```

---

## 11. Handling Advanced UI

### Alerts

Handled automatically.

### Multiple Tabs

```js
const page2 = await context.newPage();
await page2.goto('https://google.com');
```

### Frames

```js
const frame = page.frameLocator('#frameId');
await frame.locator('#submit').click();
```

### File Upload

```js
await page.setInputFiles('#upload','file.txt');
```

---

## 12. Auto-Wait & Synchronization

Playwright automatically waits for:

* Visibility
* Stability
* Enabled state

No need for:

* Thread.sleep
* Hard waits

This eliminates flaky tests.

---

## 13. Assertions

Assertions validate expected behavior.

```js
await expect(locator).toBeVisible();
await expect(locator).toHaveText('Welcome');
await expect(page).toHaveURL(/dashboard/);
await expect(page).toHaveTitle(/Home/);
```

---

## Example Test

```js
test('Search Test', async ({ page }) => {
  await page.goto('https://www.google.com');
  await page.getByRole('textbox').fill('Playwright');
  await page.keyboard.press('Enter');
  await expect(page).toHaveURL(/search/);
});
```

---

## 14. Test Organization & Hooks

### Hooks

* beforeAll
* beforeEach
* afterEach
* afterAll

Example:

```js
test.beforeEach(async ({ page }) => {
  await page.goto('https://example.com');
});
```

Purpose:

* Setup
* Cleanup
* Reusability

---

## 15. Page Object Model (POM)

Separates page actions from tests.

### Benefits

* Maintainability
* Reusability
* Cleaner tests

### Structure

```
pages/
tests/
```

### Example

Test:

```
loginPage.login(user,pass);
```

Page Class handles locators and actions.

---

## 16. Debugging & Reporting

### Run Headed

```bash
npx playwright test --headed
```

### Debug Mode

```bash
npx playwright test --debug
```

### HTML Report

```bash
npx playwright show-report
```

---

## Trace Viewer

```bash
npx playwright test --trace on
```

Shows:

* Step execution
* Screenshots
* Network calls
* Console errors

---

## 17. Parallel Execution

```bash
npx playwright test --workers=3
```

Benefits:

* Faster execution
* Efficient CI pipelines

---

## 18. CI/CD Integration

Playwright works with:

* Jenkins
* GitHub Actions
* Azure DevOps

Automation runs automatically after each code commit.

---

## 19. Best Practices

* Prefer role-based locators
* Avoid XPath when possible
* Avoid hard waits
* Use Page Object Model
* Keep tests independent
* Use meaningful test names
* Add assertions in every test

---

## 20. Summary

* Playwright is a modern automation framework
* Reliable for dynamic web applications
* Built-in wait mechanism
* Strong debugging support
* Easy setup
* High industry adoption

---

## Q&A

Open for questions.



