## Challenge Tasks

### Task 1: The Problem
Think about a team of 5 developers all pushing code to the same repo manually deploying to production.

Write in your notes:
1. What can go wrong?
- versions can be in improper manner, Production goes down due to manual mistake, each machine have different dependencies version on different machines, Production goes down due to manual mistake.

2. What does "it works on my machine" mean and why is it a real problem?
- When the code runs correctly on the developer’s local system but fails in another environment.
because if its manual work it will create a problem as environment will be different for both developer and staging/production.If environments are not consistent, bugs will appear only after deployment.

3. How many times a day can a team safely deploy manually?
If we go with manual deployment chances of human errors, slow deployment due to manual steps, or resolving any issues and again do steps manually with this 1 or 2 deployment a day can be possible.
---

### Task 2: CI vs CD
Research and write short definitions (2-3 lines each):
1. **Continuous Integration** — what happens, how often, what it catches
- In continues integration a developers frequently merge code into a shared repository. Each push automatically triggers build and tests. it includes code, build, test these stages. 
It helps to catch-
Build errors
Test failures
Broken integrations

Example:
You push code → GitHub Actions runs tests automatically.

2. **Continuous Delivery** — how it's different from CI, what "delivery" means
- After CI passes, the application is automatically prepared and kept ready for production, but someone has to click "Deploy".
So:
CI = build + test
Delivery = ready for release
Example:
Code passes all tests → Docker image is built → It waits for manual approval to deploy.

3. **Continuous Deployment** — how it differs from Delivery, when teams use it
- Every successful change is automatically deployed to production without human approval.
Write one real-world example for each.
- No manual approval.
Example:
You push → Tests pass → App gets deployed to production automatically.

Used mostly by:
Big tech companies or teams with very strong testing systems.
---

### Task 3: Pipeline Anatomy
A pipeline has these parts — write what each one does:
- **Trigger** — what starts the pipeline
Example:
git push
Pull request
Manual button
Scheduled run

- **Stage** — a logical phase (build, test, deploy)
Example:
Build stage
Test stage
Deploy stage
Stages organize workflow.

- **Job** — a unit of work inside a stage
Example:
In “Test” stage:
unit-tests job
integration-tests job
Jobs can run in parallel.

- **Step** — a single command or action inside a job
Example:
Install dependencies
Run tests
Build Docker image
Very small action.

- **Runner** — the machine that executes the job
It can be:
GitHub’s server
Your own VM
A Docker container
Without runner → nothing executes.


- **Artifact** — output produced by a job
Example:
JAR file
Docker image
Test report
This output is passed to next stage.
---

### Task 4: Draw a Pipeline
Draw a CI/CD pipeline for this scenario:
> A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server.
1. Developer pushes code to GitHub
2. Pipeline starts automatically
3. First stage installs dependencies and builds app
4. Second stage runs tests
5. Third stage builds Docker image
6. Image is pushed to registry
7. Staging server pulls image and runs container

Include at least 3 stages. Hand-drawn and photographed is perfectly fine.

---

### Task 5: Explore in the Wild
1. Open any popular open-source repo on GitHub (Kubernetes, React, FastAPI — pick one you know)
2. Find their `.github/workflows/` folder
3. Open one workflow YAML file
4. Write in your notes:
   - What triggers it?
   - It runs when someone pushes code to master brach, So this one is automatic — it runs after every push to master.
   on:
  push:
    branches:
      - master
    It runs automatically when someone pushes code to the master branch.
    So whenever new code is merged or directly pushed to master, this deployment process starts.
    It will not run for other branches like dev or feature/*.

   - How many jobs does it have?
   jobs:
  deploy:
  There is only one job in this workflow: deploy
  Push → Deploy
  No separate build/test stages here.

   - What does it do? (best guess)
   
   - Pulls the latest code from GitHub
     Builds Docker containers using docker compose
     Starts (or restarts) the containers in detached mode
     Deploys the application to the staging environment
     It runs on a self-hosted staging server, which means the deployment happens directly on that machine.
     There is no testing stage here — it directly builds and deploys when code is pushed.