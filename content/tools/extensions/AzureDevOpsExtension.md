<!--
title: "Contrast Integration for Azure DevOps" 
description: "Extension to integrate Contrast in your deployment workflow"
tags: "tools azure devops integration extension deployment"
-->


Use the the Azure DevOps extension to integrate Contrast with your deployment workflow. The following instructions guide you through the steps to set up and configure the extension for your Contrast instance. 

## Before You Start 

Before you begin to set up the extension, make sure that you have the privileges to install a Microsoft extension. If you lack the necessary privileges, you can [request the extension](https://docs.microsoft.com/en-us/azure/devops/marketplace/request-extensions?view=azure-devops-2019) for a project.

## Setup and Configuration

### Step one

* Follow [Microsoft's instructions](https://docs.microsoft.com/en-us/azure/devops/marketplace/install-extension?view=azure-devops-2019) to install the Contrast extension, **Contrast Integration**. 

### Step two

* Go to your [Project Settings](https://docs.microsoft.com/en-us/azure/devops/project/navigation/go-to-service-page?view=azure-devops#open-project-settings) at the bottom of you side bar. You'll need to be part of the Project administration group or have enough permissions to alter the settings.

* In the **Pipelines** section of the settings menu, select **Service connections**.

 <a href="assets/images/AzureDevOps_connection_settings.png" rel="lightbox" title="Service Connection Settings"><img class="thumbnail" src="assets/images/AzureDevOps_service_connection_settings.png"/></a>

### Step three

* Click over the **+ New Service connection** button (shown in the image in the previous step), and select **Contrast Server Connection**.
* Complete all the fields with the required data. You can find the values for all the fields in the Contrast UI by going to the [**user menu > Your Account > Profile** page](user-account.html#profile).

<a href="assets/images/AzureDevOps_service_connection.png" rel="lightbox" title="Service Connection fields"><img class="thumbnail" src="assets/images/AzureDevOps_service_connection.png"/></a>

> **Note: ** Your **Contrast URL** should not include */Contrast* at the end; only the host is required.

## Configuration for Release Gate

### Step one

* Now that you have at least one service connection, enter on **Edit** mode for the release pipeline you wish to include the gate.
* Select a pre- or post-deployment condition.

<a href="assets/images/AzureDevOps_deployment_conditions.png" rel="lightbox" title="Deployment conditions"><img class="thumbnail" src="assets/images/AzureDevOps_deployment_conditions.png"/></a>

* Enable the **Gates** section if you haven't already. 
* Click on the **+ Add** button to select the **Verify application vulnerabilities** option.

<a href="assets/images/AzureDevOps_gates_section.png" rel="lightbox" title="Gates section"><img class="thumbnail" src="assets/images/AzureDevOps_gates_section.png"/></a>

<a href="assets/images/AzureDevOps_select_gate.png" rel="lightbox" title="Select gate"><img class="thumbnail" src="assets/images/AzureDevOps_select_gate.png"/></a>

### Step two

* Select a **Service Connection** from the **Contrast Service Connection** field. You can also click on the **Manage** option to go to the **Service connections** settings in your **Project Settings**.
* Select one of your applications from the **Application** dropdown. This enables more fields for configuring the gate.

<a href="assets/images/AzureDevOps_gate_part1.png" rel="lightbox" title="Azure DevOps Gate Part 1"><img class="thumbnail" src="assets/images/AzureDevOps_gate_part1.png"/></a>

### Step three

* You can use the **Allowed Status** and **Build Number** fields to filter your results from Contrast. The values set in these fields will be validated against the conditions you configure in the following fields.

<a href="assets/images/AzureDevOps_gate_part2.png" rel="lightbox" title="Azure DevOps Gate Part 2"><img class="thumbnail" src="assets/images/AzureDevOps_gate_part2.png"/></a>

* Proceed to your severity counters, where you must set the maximum number of vulnerabilities allowed per severity. If your selected application has more vulnerabilities than allowed for that severity level, your gate will fail.

<a href="assets/images/AzureDevOps_gate_part3.png" rel="lightbox" title="Azure DevOps Gate Part 3"><img class="thumbnail" src="assets/images/AzureDevOps_gate_part3.png"/></a>

> **Note:** Remember that your gates evaluation settings affect all the gates on the current stage for the pre- or post-deployment conditions.

