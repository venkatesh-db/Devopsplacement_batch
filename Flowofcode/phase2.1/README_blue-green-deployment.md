# Project Overview

This repository contains multiple Azure DevOps pipelines designed for real-time enterprise use cases. Each pipeline is tailored to specific deployment strategies and automation workflows, ensuring scalability, reliability, and governance.

## Pipelines Included

### 1. **Enterprise Release Pipeline**
- **File**: `enterprise-release-pipeline.yml`
- **Purpose**: Manages the CI/CD lifecycle for enterprise applications.
- **Key Features**:
  - CI → Dev → QA → Manual Approval → Prod.
  - Manual validation ensures governance before production deployment.
  - Modular design for scalability.

### 2. **Blue-Green Deployment Pipeline**
- **File**: `blue-green-deployment.yml`
- **Purpose**: Implements a blue-green deployment strategy for zero-downtime releases.
- **Key Features**:
  - Deploys to a GREEN slot, validates health, and switches traffic.
  - Includes monitoring and automatic rollback to BLUE in case of issues.

### 3. **Blue-Green Rollback Pipeline**
- **File**: `blue-green-rollback.yml`
- **Purpose**: Focuses on rollback strategies for blue-green deployments.
- **Key Features**:
  - Automates rollback to the previous stable version (BLUE).
  - Ensures stability during production incidents.

### 4. **Infrastructure Provisioning Pipeline**
- **File**: `azure-enterprise-platform/pipelines/azure-pipelines.yml`
- **Purpose**: Automates the provisioning of Azure infrastructure.
- **Key Features**:
  - Creates virtual networks, storage accounts, and VM scale sets.
  - Uses isolated Python environments for automation scripts.

### 5. **AI Automation Pipeline**
- **File**: `Enterpriseustcicd/azure-pipelines.yml`
- **Purpose**: Leverages AI/ML for DevOps automation and root cause analysis.
- **Key Features**:
  - Runs AI-based log summarizers and deployment failure predictors.
  - Optimizes DevOps workflows using machine learning.

## Code Flow Summaries

### Enterprise Release Pipeline
- **Stages**:
  1. **Build**: Compiles the application and prepares the build artifact.
  2. **Test**: Runs unit, integration, and smoke tests.
  3. **QA**: Manual validation and feedback.
  4. **Approval**: Manual approval before production deployment.
- **How to Remember**: This is the "build and test" pipeline for enterprise applications.

### Blue-Green Deployment Pipeline
- **Stages**:
  1. **Build**: Compiles the application and prepares the build artifact.
  2. **Deploy to GREEN**: Deploys the application to the GREEN slot for testing.
  3. **GREEN Health Check**: Validates the health of the application in the GREEN slot.
  4. **Switch Traffic to GREEN**: Switches live traffic to the GREEN slot, making it the active version.
  5. **Post-Deploy Monitoring**: Monitors the application for errors after the traffic switch.
  6. **Auto Rollback to BLUE**: Rolls back to the BLUE slot if monitoring detects issues.
- **How to Remember**: This is the "staging and go-live" pipeline for new versions.

### Blue-Green Rollback Pipeline
- **Stages**:
  1. **Monitor**: Continuously monitors the application for issues.
  2. **Rollback**: Automatically rolls back to the BLUE slot if issues are detected.
- **How to Remember**: Think of this as the "safety net" pipeline for production stability.

### Infrastructure Provisioning Pipeline
- **Stages**:
  1. **Provision Resources**: Creates Azure resources like VMs, storage, and networks.
  2. **Run Automation Scripts**: Executes Python scripts for network, storage, and VMSS setup.
- **How to Remember**: This is the "foundation builder" pipeline for infrastructure.

### AI Automation Pipeline
- **Stages**:
  1. **Root Cause Analysis**: Detects issues in failed pipeline runs.
  2. **Log Summarization**: Summarizes logs for debugging.
  3. **ML Optimization**: Applies machine learning to optimize DevOps workflows.
- **How to Remember**: This is the "intelligent assistant" pipeline for DevOps.

## Best Practices

1. **Testing**:
   - Add unit, integration, and smoke tests in CI and QA stages.
2. **Secrets Management**:
   - Use Azure Key Vault for sensitive data.
3. **Caching**:
   - Implement caching for dependencies to speed up builds.
4. **Rollback Strategy**:
   - Test rollback plans regularly to ensure reliability.
5. **Artifact Management**:
   - Use `PublishPipelineArtifact@1` and `DownloadPipelineArtifact@2` for efficient artifact handling.

## How to Use

1. **Set Up Pipelines**:
   - Import the YAML files into your Azure DevOps project.
   - Configure triggers and variables as needed.

2. **Customize Variables**:
   - Update `APP_NAME`, `ENV`, and other variables to match your project.

3. **Run and Monitor**:
   - Trigger pipelines manually or automatically.
   - Monitor progress and address any issues promptly.

4. **Iterate and Improve**:
   - Continuously refine pipelines based on feedback and performance metrics.

## Contact
For any questions or issues, please contact the DevOps team.