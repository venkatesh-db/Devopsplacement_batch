# Azure Pipelines Production Workflow

This repository contains the Azure Pipelines YAML configuration for a production-grade CI/CD workflow. The pipeline is designed to ensure smooth deployment, monitoring, and rollback capabilities for the application.

## Pipeline Overview

The pipeline consists of the following stages:

### 1. CI - Build
- **Purpose**: Builds the application and prepares artifacts for deployment.
- **Key Steps**:
  - Checkout the repository.
  - Create build artifacts.
  - Publish build artifacts for later stages.

### 2. Deploy to GREEN
- **Purpose**: Deploys the application to the GREEN slot for testing.
- **Key Steps**:
  - Download the build artifacts.
  - Deploy the application to the GREEN slot.

### 3. GREEN Health Check
- **Purpose**: Validates the health of the application in the GREEN slot.
- **Key Steps**:
  - Run health checks to ensure the application is functioning correctly.

### 4. Switch Traffic to GREEN
- **Purpose**: Switches live traffic to the GREEN slot after successful validation.
- **Key Steps**:
  - Execute traffic switching commands.

### 5. Post-Deploy Monitoring
- **Purpose**: Monitors the application for a defined period to ensure stability.
- **Key Steps**:
  - Monitor application metrics.
  - Validate error rates against the defined threshold.

### 6. Auto Rollback to BLUE
- **Purpose**: Automatically rolls back to the BLUE slot if monitoring detects issues.
- **Key Steps**:
  - Restore the BLUE slot as the live environment.

## Key Variables
- `APP_NAME`: Name of the application.
- `BUILD_OUTPUT`: Directory for storing build artifacts.
- `ERROR_THRESHOLD`: Maximum allowable error rate during monitoring.

## Code Flow Summary
1. **Build Artifacts**: Artifacts are created and published during the CI stage.
2. **Deploy to GREEN**: Artifacts are deployed to the GREEN slot for testing.
3. **Health Check**: Ensures the GREEN slot is stable before switching traffic.
4. **Switch Traffic**: Live traffic is routed to the GREEN slot.
5. **Monitor**: Application metrics are monitored to ensure stability.
6. **Rollback**: If monitoring fails, traffic is rolled back to the BLUE slot.

## Best Practices
- **Use Variables**: Centralize configuration using pipeline variables.
- **Monitor Metrics**: Ensure robust monitoring to detect issues early.
- **Automate Rollbacks**: Use conditions to automate rollback processes.

## How to Use
1. Place this YAML file in your Azure DevOps repository.
2. Update the variables to match your application and environment.
3. Trigger the pipeline from the Azure DevOps interface.

---

This pipeline ensures a reliable and automated deployment process, minimizing downtime and ensuring application stability in production.