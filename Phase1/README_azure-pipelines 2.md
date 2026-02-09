# Azure Pipelines for `sample-app`

This repository contains the Azure Pipelines configuration for automating the build, test, and deployment readiness process for the `sample-app`. The pipeline is triggered by changes to the `main` branch and runs on a self-hosted agent.

## Pipeline Overview

The pipeline is divided into six stages:

1. **Agent & Environment Validation**:
   - Validates the self-hosted agent by checking system information (e.g., hostname, disk usage, memory, CPU).

2. **Toolchain Validation**:
   - Verifies the availability of essential tools like Git, Docker, Python, Node.js, and Go.

3. **Code Quality Checks**:
   - Runs linting and unit tests for Go and Node.js projects if respective files (`go.mod`, `package.json`) are detected.

4. **Security Scanning**:
   - Placeholder for security scans, suggesting tools like Trivy, Snyk, and SonarQube.

5. **Build & Package**:
   - Creates a build output directory.
   - Builds Go applications and Docker images if respective files (`go.mod`, `Dockerfile`) are present.
   - Publishes build artifacts to a container.

6. **Deployment Readiness**:
   - Ensures the application is ready for deployment by verifying artifacts, security, and test results.

## Technical Concepts

- **Pipeline Triggers**:
  - The pipeline is triggered by changes to the `main` branch.

- **Variables**:
  - `APP_NAME`: Name of the application.
  - `ENVIRONMENT`: Deployment environment (e.g., `dev`).
  - `BUILD_OUTPUT`: Directory for build artifacts.
  - `PIPELINE_TYPE`: Type of pipeline (e.g., `SelfHosted-Enterprise`).

- **Tools**:
  - Git, Docker, Python, Node.js, Go.

- **Artifacts**:
  - Build outputs are published for deployment.

## How to Contribute

1. **Code Quality**:
   - Ensure your code passes linting and unit tests.
   - Add tests for new features.

2. **Security**:
   - Integrate security tools like Trivy or Snyk for scans.

3. **Build**:
   - Ensure `go.mod` or `Dockerfile` is updated for Go/Docker projects.

4. **Deployment**:
   - Verify readiness checks before deployment.

## Future Enhancements

- Integrate security tools like Trivy, Snyk, and SonarQube.
- Add automated deployment to environments like DEV, QA, and PROD with manual approvals for production.

## Step-by-Step Code Flow and Key Points for Coders

### Step-by-Step Pipeline Flow
1. **Trigger**:
   - The pipeline starts when changes are pushed to the `main` branch.

2. **Stage 1: Agent & Environment Validation**:
   - Validates the self-hosted agent by checking system information (e.g., hostname, disk usage, memory, CPU).
   - Outcome: Ensures the agent is ready for subsequent stages.

3. **Stage 2: Toolchain Validation**:
   - Verifies the availability of essential tools like Git, Docker, Python, Node.js, and Go.
   - Outcome: Confirms that all required tools are installed and functional.

4. **Stage 3: Code Quality Checks**:
   - Runs linting and unit tests for Go and Node.js projects if respective files (`go.mod`, `package.json`) are detected.
   - Outcome: Ensures code quality and identifies any issues early.

5. **Stage 4: Security Scanning**:
   - Placeholder for security scans, suggesting tools like Trivy, Snyk, and SonarQube.
   - Outcome: Highlights potential security vulnerabilities.

6. **Stage 5: Build & Package**:
   - Creates a build output directory.
   - Builds Go applications and Docker images if respective files (`go.mod`, `Dockerfile`) are present.
   - Publishes build artifacts to a container.
   - Outcome: Produces build artifacts ready for deployment.

7. **Stage 6: Deployment Readiness**:
   - Ensures the application is ready for deployment by verifying artifacts, security, and test results.
   - Outcome: Confirms readiness for deployment to environments like DEV, QA, and PROD.

### Key Points for Coders to Remember
- **Pipeline Variables**:
  - Use variables like `APP_NAME`, `ENVIRONMENT`, and `BUILD_OUTPUT` to make the pipeline dynamic and reusable.

- **Toolchain Requirements**:
  - Ensure tools like Git, Docker, Python, Node.js, and Go are installed and up-to-date.

- **Code Quality**:
  - Add linting and unit tests for your code.
  - Ensure `go.mod` or `package.json` is present for Go/Node.js projects.

- **Security**:
  - Integrate security tools like Trivy, Snyk, and SonarQube for comprehensive scans.

- **Build Process**:
  - Update `go.mod` or `Dockerfile` as needed for Go/Docker projects.
  - Ensure the build output directory is correctly configured.

- **Deployment Readiness**:
  - Verify that all checks (artifacts, security, tests) pass before deployment.

By following these steps and key points, coders can ensure a smooth and efficient pipeline execution.