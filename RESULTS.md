# UI lab results

Tool parts that I chose: (Part 3) Robot Framework, (Part 4) Cypress

## Part 0
- Step 0.1, Chrome version: 157.0.8103.51
- Step 0.3, ChromeDriver version: 157.0.8103.51
- Step 0.4, locator of Pizza, Please!: Please!: button[name="pizza-please"]
- Step 0.4, locator of Excluded tools: select
- Step 0.4, locator of Must be vegetarian: #default-checkbox
- Step 0.4, locator of Custom Pizza Name: input#pizza-name
- Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261113-001600, Pizza cutter, 400 calories

| Step | Actual result | Pass or fail |
| --- | --- | --- |
| 1 | Heading "Looking to break out of your pizza routine?" appeared | Pass |
| 2 | All four advanced fields appeared | Pass |
| 3 | Fields showed 600, Knife selected, vegetarian checked, and Lab Pizza 20261113-001600 | Pass |
| 4 | Recommended Lab Pizza 20261113-001600 with Tool: Pizza cutter and Calories per slice: 400 | Pass |
| 5 | Message "Please log in first." appeared | Pass |
| 6 | Signed in as admin and saw "Latest pizza recommendations" | Pass |
| 7 | Checked admin list for Lab Pizza 20261113-001600 (tool=Pizza cutter) | Pass |

## Part 3: Robot Framework
- robot --version: Robot Framework 7.5.1 (Python 3.13.0 on darwin)
- Step 3.2, failure message for the wrong title: Title should have been 'Web Form' but was 'Web form'.
- Step 3.8, run 1, result, elapsed time and pizza name: PASS, 00:00:16, Lab Pizza 20261113-155632
- Step 3.8, run 2, result, elapsed time and pizza name: PASS, 00:00:13, Lab Pizza 20261113-155711

## Part 4: Cypress
- node --version, npm --version and npx cypress version: v22.15.0, 10.9.2, Cypress package version: 16.2.1 (Cypress binary version: 16.2.1)
- Step 4.3, failure message for the wrong title: Timed out retrying after 10000ms: expected 'Web form' to equal 'Web Form'
- Step 4.6, tool and calories in the answer of POST /api/pizza: Stuffed, 300
- Step 4.7, the line of the admin list that shows your pizza: Lab Pizza 20261113-180442 (tool=Pizza cutter, ingredients_number=5)
- Step 4.8, run 1, result, duration and pizza name: All specs passed (2 tests), 21 seconds; Lab Pizza 20261113-181936
- Step 4.8, run 2, result, duration and pizza name: All specs passed (2 tests), 17 seconds; Lab Pizza 20261113-182606
- Step 4.9 (optional), browser and result: Firefox 160, both specs passed (2 tests), 24 seconds.

## Part B
1. The tests locate Max Calories per Slice through its label because all three number inputs share the same id, `floating_filled`. Using that id alone would not uniquely identify the calories field and could cause the test to interact with the wrong input. The test instead finds the label and locates its associated input. The page could be improved by assigning each input a unique and stable id, such as `max-calories`, to make the tests easier to read and maintain.

2. This is a consistency test oracle because it compares the same information in two parts of the application. The test gets the tool from the pizza recommendation and checks that the admin list shows the same tool for the new pizza. It would catch a fault where the recommendation shows one tool but the server saves or displays a different tool in the admin list. In my runs, the test passed and the pizza appeared in the admin list with its tool.

3. I would add a check that verifies the recommended pizza is vegetarian. The test could inspect the response from POST /api/pizza and check that its vegetarian field is true. It could also check that the vegetarian option was selected before requesting the pizza. The test would need access to the response data or a clear vegetarian status displayed on the page. Checking only the checkbox would not prove that the returned pizza is actually vegetarian.

4. Robot Framework uses SeleniumLibrary to interact with the browser and wait for page elements, while Cypress retries commands and assertions until they succeed or the timeout is reached. Cypress also lets the test wait for the POST /api/pizza response with cy.intercept() and cy.wait(). My Robot Framework runs passed in 16 and 13 seconds, while my Cypress runs passed in 21 and 17 seconds. Robot Framework provides HTML logs and reports with screenshots, while Cypress provides a Command Log and recorded videos. I found Cypress's test steps readable because the JavaScript commands and assertions are close to the actions being tested.

5. I would choose Cypress for the automated UI tests in Project 2. First, Cypress automatically retries element queries and assertions, so I do not need to add fixed pauses while waiting for the page. Second, cy.intercept() lets me check server responses as well as what appears on the page. My two full Chrome runs and the optional Firefox run all passed. The screenshots and videos also make it easier to review what happened during a test.

6. (Part 3) If QuickPizza changed the locator of the calories box, I would update it in the quickpizza.resource file. The test file uses keywords from this resource file to interact with the page. Keeping the locator in the resource file means that I would not need to change every test step that uses the calories box. I would update the locator in one place and then run the tests again to verify the change.

7. (Part 4) QP-01 has to be a single test because Cypress clears cookies before each test. The pizza is created in steps 1 to 5, and steps 6 and 7 must use the same browser session to find that pizza in the admin list. If steps 6 and 7 were a second test, Cypress would clear the cookies and the browser could connect to a different QuickPizza server. The admin list might then not contain the pizza created by the first test. Keeping all seven steps in one test allows the pizza creation and admin checks to use the same session.