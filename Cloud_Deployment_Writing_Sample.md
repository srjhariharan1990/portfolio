# Deploy an Analytics Application on a Cloud Platform

**Technical writing portfolio sample**  
**Audience:** System administrators and database administrators  
**Sample type:** Adapted and generalized deployment procedure

> **About this sample:** This example has been adapted from a product deployment procedure. Product and organization names, internal links, release details, and environment-specific identifiers have been removed. The application, interface labels, and workflow below are illustrative; this is not a validated deployment guide for a real platform. Publication permission must be confirmed before this adapted material is shared externally.

## Overview

Use a deployment stack to provision the resources required by an analytics application. A stack groups the infrastructure configuration used to create and manage an application environment.

This sample illustrates a new deployment with compute resources, a metadata database, identity integration, networking, and an optional load balancer. Upgrade and access-policy automation workflows are outside its scope.

## Before you begin

Confirm that the deployment team has completed the following preparation.

| Area | Preparation |
| --- | --- |
| Access | Identify the administrators responsible for cloud resources, application administration, database administration, and identity configuration. Confirm the required permissions. |
| Resource placement | Identify the target project, deployment region, and available compute capacity. |
| Network | Prepare the virtual network, application subnet, database connectivity, and approved administrative access method. |
| Identity | Register the application with the identity provider and identify the application administrator account. |
| Secrets | Store the required passwords and application client secret in the approved secrets service. Confirm that the deployment can access them. |
| Compute and storage | Select capacity appropriate for the workload using the applicable product sizing guidance. |
| Administrative access | Prepare an SSH public key if the deployment requires one. Keep the private key separate. |
| Database | Decide whether to provision a metadata database or connect to an existing compatible database. |
| Monitoring | Identify the monitoring configuration and notification destination, if required. |

**Important:** This sample intentionally omits real credentials, resource identifiers, network addresses, sizing limits, and production endpoints.

## 1. Start a deployment stack

1. Sign in to the cloud management console with an account authorized to create deployment resources.
2. Open the application catalog and select the approved analytics application package.
3. Select the deployment package version approved for the environment.
4. Choose the target project or resource container.
5. Review the applicable deployment terms and select **Create Stack**.
6. Enter a stack name and a description that explain the purpose of the environment.
7. Select **Next** to configure the deployment.

**Expected result:** The console displays the deployment configuration form.

## 2. Configure the application instance

1. Select **New Deployment** as the deployment workflow.
2. Confirm the target region and resource container.
3. Enter a resource label, such as `analytics-demo`, if the form supports one.
4. Select the compute profile and storage capacity specified in the deployment plan.
5. Provide the SSH public key if required for administrative access.
6. Enter the application administrator username.
7. Set the instance time zone if the default does not meet the deployment requirements.

**Note:** Account mappings and capacity requirements depend on the actual product. Confirm them before deploying a real system.

## 3. Select catalog storage

1. Review the storage options supported by the application.
2. Select local storage or an object storage location, as appropriate for the deployment.
3. Confirm which application artifacts will use the selected storage option.
4. Confirm whether the storage choice can be changed after deployment.

**Important:** Do not assume that selecting object storage moves every application file off the compute instance. Verify the supported artifact types and storage behavior in the applicable product documentation.

Use the supported application interface or API to manage application-owned catalog content.

## 4. Configure identity and secrets

1. Select the approved identity provider.
2. Enter the registered application identifier and identity endpoint required by the deployment form.
3. Select or enter the identity account that will administer the application.
4. Verify that the account exists and that the required role mapping has been configured.
5. Select references to the secrets containing the following values:
   - Application administrator password.
   - Database administrator password, if required.
   - Identity application client secret.
6. If the secrets are stored in a different resource container, select that location and confirm the required access permissions.

**Security note:** Select secret references where supported. Do not include passwords, private keys, or client secrets in documentation, screenshots, or shared deployment notes.

## 5. Configure network connectivity

1. Choose whether to use an existing virtual network or create a new one.
2. Select the application subnet and the resource container that owns it.
3. If creating a network, enter the address ranges approved in the network plan.
4. Confirm the required connectivity between the application subnet, metadata database, and identity service.
5. Configure public or private access according to the approved architecture.
6. For a private application instance, confirm the administrative access method, such as a managed bastion connection.

**Expected result:** The selected network configuration supports the required application connections and administrative access.

## 6. Configure the metadata database

Coordinate this step with the database administrator.

1. Choose whether to create a new metadata database or use an existing compatible database.
2. For a new database, select the supported database configuration and applicable licensing option.
3. For an existing database, select the database resource and provide the connection details required by the deployment form.
4. Confirm that the application instance can reach the database endpoint through the approved network path.
5. Review database access restrictions and the credentials or secret references used during setup.

**Note:** Database compatibility, schema requirements, and supported endpoint options are product-specific and are not defined by this sample.

## 7. Configure optional services

### Load balancing

If the deployment requires a load balancer:

1. Enable the load balancer option.
2. Select public or private visibility according to the access requirements.
3. Choose the required capacity and listener configuration, where available.
4. Configure the approved certificate for encrypted connections.

**Important:** A demonstration certificate is not a substitute for the certificate required by the production deployment plan.

### Monitoring and notifications

1. Enable metrics collection if required.
2. Select the approved notification destination.
3. Confirm that the deployment has permission to publish metrics and notifications.

## 8. Review and provision resources

1. Select **Next** to open the configuration summary.
2. Review resource placement, compute capacity, storage, network access, database settings, identity configuration, and secret references.
3. Correct any configuration errors before proceeding.
4. Select **Create** to save the stack.
5. Run the provisioning job, either during stack creation or as a separate action, according to the platform workflow.
6. Monitor the job status and review any reported errors.

**Important:** A successful infrastructure job does not by itself confirm that the application is ready. Complete the application checks below.

## 9. Verify the deployment

| Check | Expected result |
| --- | --- |
| Provisioning job | The job completes without unresolved errors. |
| Resources | The expected compute, storage, network, and database resources are present. |
| Application startup | Application health information or startup logs indicate successful initialization. |
| Connectivity | The application can reach its metadata database and identity service. |
| Sign-in | The designated administrator can sign in through the approved application endpoint. |
| Access controls | Administrative and user access match the intended role assignments. |
| Monitoring | Metrics and notifications are available when enabled. |

If a check fails, review the relevant logs and configuration before treating the deployment as complete.

## 10. Complete post-deployment tasks

1. Complete any remaining identity integration and role-mapping tasks.
2. Assign users the required application roles.
3. Review network access, certificates, and administrative access settings.
4. Confirm backup, maintenance, and monitoring responsibilities.
5. Record the approved application endpoint and deployment details in the designated operational record.
6. Remove temporary access or setup resources according to the deployment plan.

## Review deployment output

Use the stack details and job history to review resource information, configuration values, and deployment logs. Review identity registration details in the identity administration interface when necessary.

Keep operational records within the approved environment. Before sharing diagnostic output, remove credentials, tokens, internal addresses, and other restricted information.

## Troubleshooting checklist

| Symptom | Initial checks |
| --- | --- |
| Provisioning fails | Review the failed job step, resource permissions, available capacity, and required configuration values. |
| Application does not start | Check startup logs, database connectivity, and access to required secrets. |
| Administrator cannot sign in | Check the identity registration, account status, and role mapping. |
| Application endpoint is unreachable | Check the approved access path, subnet rules, and load balancer configuration if used. |
| Metrics are unavailable | Check whether monitoring is enabled and whether the resource can publish metrics. |

These are illustrative starting points. Follow the troubleshooting guidance for the actual product when diagnosing a real deployment.
