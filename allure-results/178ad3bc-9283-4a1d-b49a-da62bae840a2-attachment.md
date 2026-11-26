# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: loginPage.spec.js >> valid login user
- Location: tests\loginPage.spec.js:14:5

# Error details

```
Test timeout of 30000ms exceeded while running "beforeEach" hook.
```

```
Error: page.goto: Test timeout of 30000ms exceeded.
Call log:
  - navigating to "https://rahulshettyacademy.com/client/#/auth/login", waiting until "load"

```

# Test source

```ts
  1  | 
  2  | import { Locator, Page } from "@playwright/test";
  3  | 
  4  | export class pageLogin {
  5  | 
  6  |         constructor(page){
  7  |             this.page = page
  8  |             this.email = this.page.getByPlaceholder('email@example.com')
  9  |             this.password = this.page.locator('#userPassword')
  10 |             this.loginButtons = this.page.locator('#login')
  11 |             this.errorMessages= this.page.locator('#toast-container')
  12 |             this.homePageIdentifiers= this.page.locator('[routerlink="/dashboard/"]')
  13 | 
  14 |         }
  15 |         // create the methods:: 
  16 |         // launch url  and  loginIntoApplication
  17 | 
  18 |         async launchUrls(url){
> 19 |             await this.page.goto(url)
     |                             ^ Error: page.goto: Test timeout of 30000ms exceeded.
  20 |         }
  21 | 
  22 |         async loginIntoApplicationss(username , password){
  23 |             await this.email.fill(username)
  24 |             await this.password.fill(password)
  25 |             await this.loginButtons.click()
  26 |         }
  27 | }
  28 | 
  29 | 
```