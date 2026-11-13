# ui-lab
# UI Lab

This repository contains my work for the UI testing lab. The two tool parts I chose are **Part 3: Robot Framework** and **Part 4: Cypress**.

## Part 3: Robot Framework

The `robot/` folder contains Robot Framework test cases, including `first.robot`, `web_form.robot`, and `pizza_scenario.robot`. It also contains the shared resource file, test requirements, and test evidence from two runs in `results/run1/` and `results/run2/`.

To run the pizza scenario test:

```bash
cd robot
robot --outputdir results/run1 pizza_scenario.robot
```

## Part 4: Cypress

The `cypress/` folder contains the Cypress configuration, end-to-end test specifications, support files, and test evidence. The `cypress/evidence/` folder stores screenshots and videos from the Chrome and Firefox test runs.

To run the tests in Chrome:

```bash
cd cypress
npx cypress run --browser chrome
```