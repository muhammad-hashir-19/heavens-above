ASSIGNMENT 2
I233047
Muhammad Hashir
SCD
SE-B
Repo link:
https://github.com/muhammad-hashir-19/heavens-above

Deployment link on vercel:
http://heavens-above-alpha.vercel.app/

1. Continuous Integration (ci.yml)
Purpose:
Automatically runs tests using Jest whenever new code is pushed or a pull request is created. Ensures that existing functionality still works.

Trigger:
on: push and on: pull request to the main branch.

Configuration:
Uses actions/checkout to pull the repository.
Installs dependencies with `npm ci`.
Runs Jest tests with:
npm test --if-present 
Builds the project using `npm run build`.

Interpreting Results:
All tests passed: The Jest log section in the Actions tab will show “Tests: 0 failed.”
Failure: Check “Run Jest tests” logs for failed test names or syntax errors.


2. Deployment Pipeline (deploy.yml)
Purpose:
Simulates an automated build–test–deploy process to mimic a real continuous deployment setup.

Trigger:
Runs automatically on every `push` to the `main` branch.

Configuration:
Check out code.
Installs dependencies and builds with `npm run build`.
Runs Jest tests (using --passWithNoTests for safety).
Simulates deployment by copying files to a mock folder: mock-server/.
Uploads the mock deployment as an artifact using actions/upload-artifact.


3. Scheduled Tasks (scheduled-tasks.yml)
Purpose:
Automates maintenance tasks (like backups or cleanup) at a fixed time every day.

Trigger:
schedule: cron: "0 2 * * *"  Runs daily at 2:00 UTC.
workflow_dispatch Can also be triggered manually.

Configuration:
Prints simulated backup messages in logs.
Demonstrates use of cron jobs in GitHub Actions.

Interpreting Results:
View “Run maintenance script” step in logs.
You’ll see “Running daily maintenance...” and “Maintenance completed successfully!”.


4. Dependency Updates (dependency-updates.yml)
Purpose:
Checks for outdated npm dependencies weekly to maintain security and stability.

Trigger:
schedule: cron: "0 5 * * 1" Runs every Monday at 5:00 UTC.
Can also be triggered manually.

Configuration:
Runs `npm outdated` to check package versions.

Interpreting Results:
The logs show outdated packages  with their current and latest versions.


5. Code Review Workflow (code-review.yml)
Purpose:
Improves code quality by testing and scanning pull requests before merge.

Trigger:
On every pull request to main.

Configuration:
Runs Jest tests.
Prints simulated static code analysis and security scan results.
Ensures quality before merging.

Interpreting Results:
echo "Code review checks passed."


6. Documentation Deployment (documentation.yml)
Purpose:
Automatically builds and deploys documentation when the docs/ folder changes.

Trigger:
on: push → only if docs/** or documentation.yml changes.

Configuration:
Runs npm run docs:build.
Simulates publishing docs to GitHub Pages.

Interpreting Results:
Log will show “Building docs...” and “Docs deployment complete!”.


7. Custom Workflow Integration (custom.yml)
Purpose:
Automatically generates release notes when a new version tag is pushed.

Trigger:
on: push when tag name starts with v

Configuration:
Runs git commands to collect the last 5 commits.
saves output in release-notes.txt.
Uploads it as an artifact.





