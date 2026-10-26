<p align="right"><sub><a href="https://github.com/criguex/criguex/blob/main/README.es.md">Leer en español</a></sub></p>

<p align="center">
  <img src="assets/banner-navy.svg" alt="Cristian Guerra — Senior SDET · WAR Paradigm" width="100%"/>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/criguex"><img src="https://img.shields.io/badge/LinkedIn-criguex-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <img src="https://img.shields.io/badge/Based_in-Medellín,_Colombia_(GMT--5)-071B2B?style=flat-square" alt="Location"/>
  <a href="https://wa.me/573106344106?text=Hi%20Cristian%2C%20I%20saw%20your%20GitHub%20profile%20and%20would%20like%20to%20talk%20about%20a%20remote%20contract%20role"><img src="https://img.shields.io/badge/Open_to-remote_contract_roles-55DFBD?style=flat-square&labelColor=071B2B&logo=whatsapp&logoColor=071B2B" alt="Open to remote contract roles — message me on WhatsApp"/></a>
</p>

## In simple words

I make sure software does what it promises. I build automated checks that use an app the way a person would and raise a flag the moment something breaks, and I wire them into the pipeline so they run on every change. Lately I also check AI: I test what it builds and how it is graded, and I break things on purpose to prove the checks really notice.

## Three cases

Three projects, one per kind of work. Each one says the problem, what I built, how to check it yourself and what was measured. The numbers come from lab runs, not from production systems.

**1 · Test automation for a release: [restful-booker-quality-suite](https://github.com/criguex/restful-booker-quality-suite)**
- **Problem:** decide whether an API can ship, and keep known bugs visible instead of hiding them.
- **What I built:** risk-based Playwright API suite with Zod contracts and latency budgets, run in four CI gates against a pinned Docker copy of the app.
- **Check it:** `docker compose up --build -d && npm ci && npm run quality`
- **Measured (lab):** 43 checks pass in 2.0 s; 8 confirmed defects kept as expected failures, so a fix turns the suite red until it is acknowledged.

**2 · Evaluating an AI agent: [agent-eval-jev](https://github.com/criguex/agent-eval-jev)**
- **Problem:** know when a tool-using agent invents numbers or skips a step, without trusting one LLM judge.
- **What I built:** code checks first, a calibrated Jev judge second, an LLM judge only for comparison, and a CI gate with a human-review band.
- **Check it:** `python -m agenteval evaluate && python -m agenteval gate`
- **Measured (lab):** the evaluator agrees with human labels on 93.1% of 29 held-out cases (kappa 0.86); the same gate passes agent v2 and blocks v1.

**3 · Scientific QA: [predictor-debugger](https://github.com/criguex/predictor-debugger)**
- **Problem:** check whether a neural network that predicts a 3D fluid respects physics, without moving the goalposts after seeing the data.
- **What I built:** a physics debugger with hypotheses and thresholds committed before each round, run on several machines.
- **Check it:** `uv run --locked verify.py --saved mac` (minutes, no data download)
- **Measured:** 49 pre-registered hypotheses over four rounds, 48 pass and one (H14) failed and is published as such; the same fingerprints in six environments.

## About

Senior SDET with 7+ years in test automation, mostly in fintech and banking. I design automation frameworks from zero, test APIs and web apps end to end, and put quality gates into CI.

Lately most of my work is **testing what AI builds**: making verdicts measurable when outputs are not deterministic, and using AI assistants to design and explore tests faster while a person still signs off.

## Featured work

Ordered from most to least important.

### Flagship · verifying science and AI results

| Project | What it shows | Stack |
|---|---|---|
| **[scientific-qa-evidence](https://github.com/criguex/scientific-qa-evidence)** | Independent, reproducible QA audit of OpenAI's Lean 4 proofs for Navier–Stokes and Euler: rebuilt from source, rechecked with two independent proof checkers, and mutation-tested on purpose. [Read the site](https://criguex.github.io/scientific-qa-evidence/) | Lean 4 · Python · CI |
| **[predictor-debugger](https://github.com/criguex/predictor-debugger)** | A pre-registered physics debugger for a neural network that predicts a 3D fluid: thresholds committed before the data, verdicts reproduced on three machines, and failed hypotheses published too | Python · numpy · uv · CI |

### Teaching

| Project | What it shows | Stack |
|---|---|---|
| **[qa-automation-course](https://github.com/criguex/qa-automation-course)** | Free interactive QA Automation course (content in Spanish): 35 modules in 4 levels, from test oracles and Playwright to AI evaluation, mutation testing and scientific QA, each with a self-graded quiz, a verifiable challenge and a rubric. [Take the course](https://criguex.github.io/qa-automation-course/) | HTML · JavaScript · GitHub Pages |

### Evaluating AI

| Project | What it shows | Stack |
|---|---|---|
| **[qa-eval-lab](https://github.com/criguex/qa-eval-lab)** | Playwright UI tests **and** LLM evaluation (DeepEval + Promptfoo) wired into one CI eval-gate | Playwright · TypeScript · DeepEval · Promptfoo · CI |
| **[agent-eval-jev](https://github.com/criguex/agent-eval-jev)** | Evaluating a real tool-using AI agent with code checks, a calibrated Jev judge and an LLM judge, wired into a CI gate | Python · Jev · LLM judge · CI |
| **[jev-ci-triage](https://github.com/criguex/jev-ci-triage)** | Sorts every failing CI test into regression, flaky, environment, test-data or unknown: rules first, Jev only for the ambiguous rest; never re-runs or hides a failure | TypeScript · Playwright/JUnit · Jev |
| **[playwright-jev](https://github.com/criguex/playwright-jev)** | Semantic assertions for Playwright Test (`toMean`, `toChoose`, `toBeScored`) powered by Jev, recorded once and replayed in CI | Playwright · TypeScript · Jev |
| **[jev-test-impact](https://github.com/criguex/jev-test-impact)** | Runs only the tests a change touched: import graph and ownership rules first, Jev for the ambiguous rest, the full suite on any doubt | TypeScript · Vitest · Playwright · Jev |
| **[laya-server](https://github.com/criguex/laya-server)** | A free local judge (the Laya model, on CPU) behind the Jev contract, with a cascade to the cloud for doubtful cases | Node.js · Laya · Windows |

### Testing the tester · mutation

| Project | What it shows | Stack |
|---|---|---|
| **[war-paradigm](https://github.com/criguex/war-paradigm)** | WAR Paradigm: test the tester. Break reality on purpose (a physical law in a simulation, a step of a flow, an AI answer) and check whether the checks notice. Runnable experiments behind my posts | Playwright · TypeScript · CI |
| **[civica-playwright-challenge](https://github.com/criguex/civica-playwright-challenge)** | Production-shaped framework: Page Object Model, semantic locators, deterministic mock layer, accessibility checks, self-learning mutant scenarios | Playwright · TypeScript · GitHub Actions |

### Requirements QA

| Project | What it shows | Stack |
|---|---|---|
| **[spec-review-case-study](https://github.com/criguex/spec-review-case-study)** | How I review a spec before anyone builds: 19 findings (numbers that do not add up, costs stated as facts, rules nobody could test), a reusable checklist and a script that recomputes the numbers | Markdown · Python |

### Test automation frameworks

| Project | What it shows | Stack |
|---|---|---|
| **[restful-booker-quality-suite](https://github.com/criguex/restful-booker-quality-suite)** | Release-style API testing for Restful Booker: lifecycle, auth, Zod contracts and latency budgets in four CI gates, with eight confirmed defects kept visible | Playwright · TypeScript · Zod · Docker |
| **[playwright-saucedemo-e2e](https://github.com/criguex/playwright-saucedemo-e2e)** | Cross-browser E2E suite with POM and CI on every push | Playwright · TypeScript |
| **[karate-api-testing](https://github.com/criguex/karate-api-testing)** | Data-driven REST API testing with happy and failure paths | Karate DSL · Java · Maven |
| **[serenity-screenplay-salesforce](https://github.com/criguex/serenity-screenplay-salesforce)** | Screenplay pattern for business web flows with living documentation | Serenity BDD · Java · Cucumber |
| **[selenium-cucumber-pom](https://github.com/criguex/selenium-cucumber-pom)** | Classic layered web framework: drivers, hooks, page objects, test data | Selenium · Java 17 · Cucumber |

## How I work

- **Golden flows first, then mutate them.** One change per mutant; if the suite stays green, that's a finding.
- **API first, UI for evidence.** Fast, stable checks at the service layer; the browser proves the user journey.
- **Deterministic verdicts for non-deterministic systems.** Pass/fail where the spec allows it, scores against acceptance criteria where it doesn't, and the same input run 3 times.
- **Hard rules live in code, not in prompts.** Hooks, CI gates and reviews that can't be forgotten.

## Toolbox

**Web & mobile:** Playwright · Selenium · Cypress · Serenity BDD (Screenplay) · Appium
**API & performance:** Karate DSL · REST Assured · Postman · k6 · JMeter
**Languages:** TypeScript · JavaScript · Java · SQL
**CI & infra:** GitHub Actions · GitLab CI · Jenkins · Docker
**Practices:** BDD (Cucumber/Gherkin) · contract testing · test management with Jira/Xray · AI-assisted testing (Claude Code, Copilot, MCP)

## Contact

Reach me on [WhatsApp](https://wa.me/573106344106?text=Hi%20Cristian%2C%20I%20saw%20your%20GitHub%20profile%20and%20would%20like%20to%20talk%20about%20a%20remote%20contract%20role) or [LinkedIn](https://www.linkedin.com/in/criguex). Open to [remote contract roles](https://wa.me/573106344106?text=Hi%20Cristian%2C%20I%20saw%20your%20GitHub%20profile%20and%20would%20like%20to%20talk%20about%20a%20remote%20contract%20role) in QA automation and SDET.
