# Incident-Driven Phase 5: Hotfix Workflow

## Summary
This repository contains a YAML-based CI/CD pipeline designed to handle emergency hotfixes for the `sample-app`. The workflow ensures rapid deployment of critical fixes to production while maintaining stability through monitoring and rollback mechanisms.

## Detailed Structure

### Why
The hotfix workflow is designed to address critical production issues that require immediate attention. It prioritizes:
- **Speed**: Rapid deployment to minimize downtime.
- **Stability**: Automated monitoring and rollback to ensure production remains stable.
- **Integration**: Merging fixes back to the main branch to maintain code consistency.

### What
The pipeline consists of the following stages:

1. **Hotfix CI Build**
   - Builds the hotfix artifact.
   - Runs smoke tests to ensure basic functionality.
   - Publishes the artifact for deployment.

2. **Deploy Hotfix to Production**
   - Deploys the hotfix artifact directly to production.
   - Skips traffic isolation to expedite the fix.

3. **Post-Deploy Monitoring**
   - Monitors production metrics to detect any instability caused by the hotfix.
   - Compares observed error rates against a predefined threshold.

4. **Auto Rollback**
   - Automatically rolls back the hotfix if monitoring detects instability.
   - Restores the previous stable version of the application.

5. **Merge Back to Main**
   - Merges the hotfix changes back into the main branch.
   - Ensures no code drift between branches.

### When
This workflow is triggered under the following conditions:
- A branch matching the pattern `hotfix/*` is pushed to the repository.
- Critical production issues are identified that require immediate resolution.

## Workflow Stages

### Stage 1: Hotfix CI Build
- **Trigger**: Push to `hotfix/*` branch.
- **Steps**:
  1. Checkout code.
  2. Build the hotfix artifact.
  3. Run smoke tests.
  4. Publish the artifact.

### Stage 2: Deploy Hotfix to Production
- **Trigger**: Successful completion of Stage 1.
- **Steps**:
  1. Download the hotfix artifact.
  2. Deploy the artifact to production.

### Stage 3: Post-Deploy Monitoring
- **Trigger**: Successful completion of Stage 2.
- **Steps**:
  1. Monitor production metrics.
  2. Compare error rates against the threshold.

### Stage 4: Auto Rollback
- **Trigger**: Failure in Stage 3.
- **Steps**:
  1. Rollback to the previous stable version.

### Stage 5: Merge Back to Main
- **Trigger**: Success in Stage 3.
- **Steps**:
  1. Merge hotfix changes back to the main branch.

## Key Features
- **Error Threshold**: Ensures stricter monitoring for hotfixes.
- **Automated Rollback**: Minimizes downtime in case of instability.
- **Branch Integration**: Maintains code consistency across branches.

## Conclusion
This hotfix workflow is a robust solution for managing critical production issues. It balances the need for rapid deployment with mechanisms to ensure stability and maintain code integrity.