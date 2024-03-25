# medication-tracking-app
---
# AugMend Health Medication Tracking App - DevOps Coding Challenge

## Overview

This repository contains the infrastructure as code (IaC), deployment pipeline, and monitoring setup for the AugMend Health medication tracking application. Developed in Flask, the application is designed to be automatically deployed to Azure App Service (Linux) with its data stored in a PostgreSQL Flexible Server. Monitoring is facilitated through Azure Application Insights to ensure optimal performance and reliability.

### Architecture

The application is structured as follows:
- **Web Application**: A Flask-based Python application serving the frontend and API.
- **Database**: PostgreSQL Flexible Server on Azure, chosen for its scalability and flexibility.
- **Monitoring**: Azure Application Insights, providing insights into application performance and user metrics.

All infrastructure components are provisioned using Terraform, ensuring consistency and repeatability across environments. Sensitive information, such as database passwords, is securely stored in Azure Key Vault.

## Prerequisites

- Azure account with an active subscription.
- Azure CLI installed and configured.
- Terraform installed.
- GitHub account for CI/CD pipeline configuration.

## Infrastructure Setup

1. **Terraform Initialization**
   
   Navigate to the `https://github.com/akhil8521/medication-app-infrastructure` directory and initialize the Terraform environment:
   ```sh
   cd medication-app-infrastructure/
   az login 
   terraform init
   ```

2. **Infrastructure Provisioning**

   Apply the Terraform configuration to provision the Azure resources:
   ```sh
   terraform apply
   ```
   
   Confirm the action by typing `yes` when prompted.

## CI/CD Pipeline

The CI/CD pipeline is managed through GitHub Actions, automating the deployment of the application upon each commit to the `main` branch or through manual triggers for staging or production environments.

1. **GitHub Secrets Setup**

   Configure the following secrets in your GitHub repository:
   - `AZURE_AD_CLIENT_ID`: Azure AD application client ID.
   - `AZURE_AD_TENANT_ID`: Azure AD tenant ID.
   - `AZURE_SUBSCRIPTION_ID`: Azure subscription ID.
   - `AZURE_CREDENTIALS`: Service principal credentials for Terraform.

2. **Workflow Configuration**

   The `.github/workflows/main_augmend.yml` file contains the pipeline configuration, outlining steps for building, testing, and deploying the application.

## Database Management

Scripts for managing the PostgreSQL database, including migrations and backups, are located in the `db_scripts` directory.

1. **Database Migration**

   Run the migration script to initialize the database schema:

    ```/db-migration-script.md```

2. **Backup and Restore**

   Backup and restore scripts are provided for managing database backups.

## Monitoring Setup

Monitoring is configured to use Azure Application Insights for real-time performance monitoring.

