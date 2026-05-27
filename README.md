# Agentic AI E2E QA Workflow with Playwright + MCP

A QA workflow that combines Playwright with MCP-based AI agents to automate end-to-end test planning, execution, healing, reporting, and Git operations.

## What this project is

This repository is a working example of an agentic QA pipeline for a checkout workflow on SauceDemo. It shows how AI agents can coordinate across multiple testing phases to:

- analyze a user story
- define a test plan
- perform exploratory testing
- generate reliable Playwright automation scripts
- execute tests and heal failures
- document results and commit artifacts to Git

The goal is not only to automate tests, but to demonstrate a repeatable AI-assisted QA flow.

## Why agentic AI is used here

This workflow uses agentic AI to split QA into smaller, specialized tasks handled by multiple agents.
Each agent is responsible for a distinct phase, such as planning, test generation, exploration, and healing.
This creates a more adaptable and maintainable process compared to a single monolithic automation script.

Key benefits:
- AI extracts requirements from user stories
- Test plans are created in natural language and then converted to code
- Exploratory findings inform stronger selectors and assertions
- Failures are analyzed and fixed automatically when possible
- The workflow can be extended to new stories and applications with minimal manual effort

## Technologies used

- **Playwright**: browser automation and cross-browser test execution
- **MCP servers**: agent orchestration using Playwright MCP and GitHub MCP
- **JavaScript / TypeScript**: test scripts and config
- **GitHub**: version control and remote repository integration
- **SauceDemo**: target web app for checkout test coverage

## How the flow works

1. **Read the user story**
   - The agent reads `user-stories/SCRUM-101-ecommerce-checkout.md` and extracts acceptance criteria, test scope, and credentials.

2. **Create the test plan**
   - The planner agent generates a structured, automation-ready test plan in `specs/saucedemo-checkout-test-plan.md`.

3. **Exploratory testing**
   - The agent uses Playwright tools to inspect the app, verify behavior, and collect stable element selectors and UI observations.
   - Results are saved in `specs/exploratory-results.md`.

4. **Generate automation scripts**
   - A generator agent creates Playwright test files under `tests/saucedemo-checkout/` based on the plan and exploratory findings.

5. **Execute and heal tests**
   - The workflow runs the generated tests.
   - A healer agent analyzes failures, updates selectors or waits, and then re-runs tests until they pass.

6. **Create the report**
   - Results from manual exploration and automated execution are compiled into `test-results/SCRUM-101-checkout-test-report.md`.

7. **Commit to Git**
   - The workflow stages and commits the relevant test artifacts to the configured Git repository.

## Getting started

### Install dependencies

```bash
npm install
```

### Install Playwright browsers

```bash
npx playwright install --with-deps
```

### Run the tests

```bash
npx playwright test --project=chromium
```

### Push changes to GitHub

If you need to push updates to a remote repo, use a GitHub Personal Access Token (PAT) when prompted.
Do not store the PAT in the repository.

```bash
git push origin main
```

## Important files

- `user-stories/SCRUM-101-ecommerce-checkout.md` — user story and acceptance criteria
- `specs/saucedemo-checkout-test-plan.md` — generated test plan
- `specs/exploratory-results.md` — findings from manual exploration
- `tests/saucedemo-checkout/` — generated Playwright test suites
- `test-results/SCRUM-101-checkout-test-report.md` — execution report and summary
- `.vscode/mcp.json` — MCP server configuration

## Notes

- The app under test is `https://www.saucedemo.com`
- Use the built-in credentials: `standard_user` / `secret_sauce`
- This repository is meant to show an AI-driven test workflow, not a production-grade test suite
