Task 1: The Problem
1. What can go wrong?

When 5 developers push code to the same repository and deploy manually, several problems can happen:

Code conflicts

Multiple developers may modify the same files.

Changes can overwrite each other or break existing functionality.

Unstable production releases

Code may be deployed without proper testing.

Bugs can go directly to production.

Human errors

Someone may forget a deployment step.

Wrong configuration or environment variables might be used.

Inconsistent deployments

Each developer might deploy slightly differently.

Different commands, scripts, or processes may be used.

Downtime

A bad deployment could crash the application.

Without rollback procedures, fixing it takes longer.

Lack of tracking

It becomes difficult to know:

Who deployed

What code was deployed

When it was deployed

2. What does “It works on my machine” mean?

“It works on my machine” means:

A developer’s code runs perfectly on their personal computer, but fails on another developer’s machine or on the production server.

This usually happens because of environment differences, such as:

Different OS (Windows vs Linux)

Different library versions

Missing dependencies

Different environment variables

Different database versions

Why it is a real problem

Bugs appear only after deployment

Time is wasted trying to reproduce the issue

Developers blame the environment instead of fixing the root cause

Production becomes unstable

This is why consistent environments and automated builds are important.

3. How many times a day can a team safely deploy manually?

Usually very few times, often:

1–2 deployments per day at most

Reasons:

Manual deployments take time

They require coordination between developers

Each deployment has risk of human error

Teams often wait to bundle multiple changes into one release

Without automation, frequent deployments become slow, risky, and stressful.


Task 2: CI vs CD
1. Continuous Integration (CI)

Definition:
Continuous Integration is the practice where developers frequently merge their code into a shared repository. Each change automatically triggers builds and tests to make sure the new code doesn’t break the project.

How often:
Usually multiple times a day.

What it catches:

Bugs

Failed builds

Code conflicts between developers

Test failures

Real-world example:
A developer pushes code to GitHub and a tool like GitHub Actions automatically runs tests to check if the code works.

2. Continuous Delivery (CD)

Definition:
Continuous Delivery means that after CI passes, the application is automatically prepared and ready for release to production, but the actual deployment still requires manual approval.

What “delivery” means:
The software is always ready to be deployed, but a human decides when to release it.

How it’s different from CI:
CI only tests and integrates code, while Continuous Delivery prepares the code for release.

Real-world example:
After tests pass in CI, the system builds a deployable version and stores it using a tool like Jenkins, and a team member clicks “Deploy” when ready.

3. Continuous Deployment

Definition:
Continuous Deployment automatically deploys every change that passes tests directly to production without manual approval.

How it differs from Continuous Delivery:

Delivery → manual approval to deploy

Deployment → automatic deployment

When teams use it:
Teams use it when they have very strong automated testing and monitoring.

Real-world example:
A company pushes code, tests pass, and the system automatically deploys it using a platform like GitLab CI/CD.

Task 3: Pipeline Anatomy
1. Trigger

Definition:
A trigger is the event that starts the pipeline automatically.

Common triggers include:

Pushing code to a repository

Creating a pull request

Scheduling a build

Example:
When a developer pushes code to GitHub, a pipeline starts in GitHub Actions.

2. Stage

Definition:
A stage is a major phase of the pipeline that groups related jobs together.

Common stages:

Build

Test

Deploy

Stages usually run in order, and the next stage starts only if the previous one succeeds.

Example:
A pipeline may have three stages:

Build the app

Run tests

Deploy to production

3. Job

Definition:
A job is a specific task inside a stage that runs a series of steps.

Jobs can run:

Sequentially

Or in parallel

Example:
Inside the Test stage, one job might test the backend and another might test the frontend.

4. Step

Definition:
A step is a single command or action inside a job.

Steps are the smallest unit in the pipeline.

Example steps:

Install dependencies

Run unit tests

Build the application

Example command:

npm install
npm test
5. Runner

Definition:
A runner is the machine or environment that executes the pipeline jobs.

It can be:

A cloud machine

A local server

A container

Example:
A runner provided by GitLab CI/CD executes the jobs defined in the pipeline.

6. Artifact

Definition:
An artifact is a file or output produced by a job that can be used later in the pipeline.

Artifacts help pass results between stages.

Examples:

Compiled application files

Test reports

Build packages

Example:
A build stage creates a .zip file that the deploy stage later uploads to a server.

✅ Simple Flow Example

Trigger → Stage → Job → Step
              ↓
           Runner executes
              ↓
           Artifact created

Example:

Trigger: Developer pushes code

Stage: Build

Job: Build backend

Steps: install dependencies → compile code

Runner: CI server executes job

Artifact: compiled application files
