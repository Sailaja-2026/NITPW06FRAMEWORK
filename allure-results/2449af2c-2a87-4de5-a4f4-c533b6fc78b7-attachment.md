# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: dashboardPageTest.spec.ts >> View product
- Location: tests\dashboardPageTest.spec.ts:29:5

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
  2  | // Page layers -- what all things will be present inside the page
  3  | /*
  4  | Locators and methods should be present inside this layer. 
  5  | class >> page properties >> constructor >> methods
  6  | */
  7  | import { Locator, Page } from "@playwright/test";
  8  | 
  9  | export class LoginPage {
  10 |     // class consists of properties :: locators and methods
  11 |     // locators when passed inside the class will be acting as properties of an object
  12 |     // create all the  properties of the page inside the class
  13 |     page:Page
  14 |     email:Locator
  15 |     password:Locator
  16 |     loginButton:Locator
  17 |     errorMessage: Locator
  18 |     homePageIdentifier:Locator
  19 | 
  20 |         constructor(page:Page){
  21 |             this.page = page
  22 |             this.email = this.page.getByPlaceholder('email@example.com')
  23 |             this.password = this.page.locator('#userPassword')
  24 |             this.loginButton = this.page.locator('#login')
  25 |             this.errorMessage= this.page.locator('#toast-container')
  26 |             this.homePageIdentifier= this.page.locator('[routerlink="/dashboard/"]')
  27 | 
  28 |         }
  29 |         // create the methods:: 
  30 |         // launch url  and  loginIntoApplication
  31 | 
  32 |         async launchUrl(url:string){
> 33 |             await this.page.goto(url)
     |                             ^ Error: page.goto: Test timeout of 30000ms exceeded.
  34 |         }
  35 | 
  36 |         async loginIntoApplication(username:string , password:string){
  37 |             await this.email.fill(username)
  38 |             await this.password.fill(password)
  39 |             await this.loginButton.click()
  40 |         }
  41 | }
```