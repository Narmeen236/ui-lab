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
- Step 4.3, failure message for the wrong title: 
- Step 4.6, tool and calories in the answer of POST /api/pizza: 
- Step 4.7, the line of the admin list that shows your pizza: 
- Step 4.8, run 1, result, duration and pizza name: 
- Step 4.8, run 2, result, duration and pizza name: 
- Step 4.9 (optional), browser and result: 

## Part B
1. 
2. 
3. 
4. 
5. 
6. 
7.