# Terraform actions in GitHub to Deploy Resources in Azure

Terraform actions are performed in the GitHub repository to create a resource group in Azure account by authorizing the action. Terraform code file .tf is pushed to GitHub repository, where the Terraform workflow is created to execute the terraform init and apply command accordingly.  GitHub action plan connects to the terraform to create the respective resources in Azure cloud account.
Implementing Steps for creating azure resources using GitHub action plans and terraform. 

1.	Create a new GitHub repo for terraform configuration files and the Terraform configuration file contains following code.

            terraform {
             required_providers {
              azurerm = {
                source  = "hashicorp/azurerm"
                version = "2.84.0"
               }
              }
             }
           # Configure the Microsoft Azure Provider
           provider "azurerm" {
            features {}    
           }
           # Create a resource group
           resource "azurerm_resource_group" "TResource" {
             name     = "Terraform_Resource"
             location = "East US"
             tags = {
               environment = "TerraformDemo" 
               }
           }
  
2.	Save Service Principal credentials within GitHub Repository as secrets.

3.	A new work flow is created in GitHub actions, where it automatically creates an yaml file.

 
4.	Terraform Yaml File generated contains following Code.

                  name: 'Terraform'
                   on:
                    push:
                      branches:
                      - main
                    pull_request:
                  jobs:
                    terraform:
                      name: 'Terraform'
                      env:
                        ARM_CLIENT_ID: ${{ secrets.AZURE_AD_CLIENT_ID }}
                        ARM_CLIENT_SECRET: ${{ secrets.AZURE_AD_CLIENT_SECRET }}
                        ARM_SUBSCRIPTION_ID: ${{ secrets.AZURE_SUBSCRIPTION_ID }}
                        ARM_TENANT_ID: ${{ secrets.AZURE_AD_TENANT_ID }}
                      runs-on: ubuntu-latest
                      environment: production
                      # Use the Bash shell regardless whether the GitHub Actions runner is ubuntu-latest, macos-latest, or windows-latest
                      defaults:
                        run:
                          shell: bash
                      steps:
                      # Checkout the repository to the GitHub Actions runner
                      - name: Checkout
                        uses: actions/checkout@v2
                      - name: 'Terraform Format'
                        uses: hashicorp/terraform-github-actions@master
                        with:
                          tf_actions_version: 0.14.8
                          tf_actions_subcommand: 'fmt'
                         tf_actions_working_dir: "./terraform"
                      - name: 'Terraform Init'
                        uses: hashicorp/terraform-github-actions@master
      
5.	Once the Action has been completed, each step is reviewed to completion.
 


6.	Select any of the workflow to view the execution details.



7.	Verify the Azure Resource group created in the Azure cloud account.


 
