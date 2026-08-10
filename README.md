# Website-Uptime-Monitor
# Azure Website Uptime Monitor

## Overview

This project is a cloud-based website monitoring solution built in Microsoft Azure. It automatically checks the availability of multiple websites every five minutes, records the results in Azure monitoring services, and sends an email alert when a monitored website becomes unavailable.

The project demonstrates cloud automation, monitoring, alerting, logging, and troubleshooting using Azure services.

## Architecture

The solution uses the following Azure services:

* Azure Function App
* Timer Trigger
* Azure Logic Apps
* Azure Log Analytics Workspace
* Azure Application Insights
* Azure Storage Account
* Azure Workbooks

### Workflow

1. An Azure Function runs every five minutes.
2. The function checks the availability of configured websites.
3. HTTP response results are recorded in Azure monitoring services.
4. Failure events can be queried through Log Analytics.
5. A Logic App sends an email notification when a website failure is detected.
6. Azure Workbooks provide a dashboard for monitoring uptime and failures.

## Websites Monitored

The initial configuration monitors:

* Google
* Microsoft
* Example.com

Additional websites can easily be added to the Function configuration.

## Project Architecture Diagram

[Insert architecture diagram here]

Example flow:

Websites → Azure Function → Application Insights / Log Analytics → Logic App → Email Alert

## Technologies Used

* Microsoft Azure
* Azure Functions
* Azure Logic Apps
* Azure Monitor
* Log Analytics
* Application Insights
* Azure Workbooks
* Python
* HTTP/HTTPS
* KQL

## Implementation

### 1. Resource Group

Created a dedicated Azure resource group to organize the monitoring infrastructure.

`rg-uptime-monitor`

### 2. Azure Function

Created an Azure Function App containing a Timer Trigger.

The function executes every five minutes using the following schedule:

`0 */5 * * * *`

The script sends HTTP requests to each configured website and records whether the request succeeds or fails.

### 3. Website Availability Checks

The Function checks each website and evaluates the HTTP response.

Successful responses indicate that the website is reachable.

Failed requests, timeouts, or unsuccessful HTTP responses generate failure information that can be used for alerting and troubleshooting.

### 4. Application Insights

Application Insights was enabled for the Function App to provide:

* Function execution monitoring
* Performance information
* Failure tracking
* Request telemetry
* Application diagnostics

### 5. Log Analytics

A Log Analytics Workspace was configured to centralize monitoring data.

KQL queries were used to investigate:

* Function executions
* Website failures
* Availability events
* Application errors

### 6. Logic App Email Alerts

An Azure Logic App was created to automate failure notifications.

When the monitoring workflow detects an outage, the Logic App sends an email notification so the issue can be investigated quickly.

### 7. Monitoring Dashboard

Azure Workbooks were used to create a visual monitoring dashboard displaying website availability and monitoring information.

The dashboard provides a centralized view of the health of the monitored websites.

## Screenshots

### Azure Resources

[Insert screenshot of resource group]

### Function App

[Insert screenshot of Function App]

### Timer Trigger

[Insert screenshot showing the five-minute schedule]

### Function Code

[Insert screenshot of Python monitoring code]

### Successful Function Execution

[Insert screenshot of test/run result]

### Log Analytics

[Insert screenshot of KQL query/results]

### Logic App

[Insert screenshot of Logic App designer]

### Email Alert

[Insert screenshot of successful outage notification]

### Monitoring Dashboard

[Insert screenshot of Azure Workbook]

## Challenges and Troubleshooting

During the project, I encountered and resolved several issues.

### Function Runtime Configuration

The Function App initially required troubleshooting around the Python runtime and Azure Function configuration.

### Logic App Authentication

The email alert workflow required configuring the appropriate connector and authentication before notifications could be sent successfully.

### Alert Testing

Initial alert tests did not trigger correctly. I reviewed the workflow execution history, corrected the configuration, and successfully generated an email notification.

These troubleshooting steps helped reinforce the importance of reviewing logs, validating workflow conditions, and testing cloud automation components independently.

## Skills Demonstrated

This project demonstrates experience with:

* Cloud infrastructure deployment
* Azure monitoring
* Serverless computing
* Python automation
* HTTP availability monitoring
* Log analysis
* KQL
* Event-driven automation
* Email alerting
* Troubleshooting
* Dashboard creation
* Azure resource management

## Future Improvements

Possible improvements include:

* Monitoring additional websites
* Measuring website response times
* Adding SSL certificate expiration monitoring
* Creating severity levels for different failures
* Adding Microsoft Teams or Slack notifications
* Deploying resources with Terraform or Bicep
* Storing historical uptime statistics
* Creating SLA and uptime percentage reports
* Adding geographic availability tests

## Project Outcome

The completed system automatically monitors website availability every five minutes, records monitoring information in Azure, provides a centralized dashboard, and generates email notifications when failures occur.

The project demonstrates how Azure serverless and monitoring services can be combined to build a practical cloud operations monitoring solution.















1
<img width="1383" height="429" alt="Screenshot 1 — Resource Group Overview" src="https://github.com/user-attachments/assets/c77e1dcf-ee65-4e62-b62e-f07ba193c3cd" />

2
<img width="2047" height="159" alt="Screenshot 2 — Function App Overview" src="https://github.com/user-attachments/assets/7db9d1d7-8822-40b5-85a4-60fc31ed8ed3" />

3
<img width="1077" height="841" alt="Screenshot 3 — VS Code Code Screenshot" src="https://github.com/user-attachments/assets/db724245-843e-4a6b-b6e2-26ca556ee834" />
<img width="246" height="58" alt="Screenshot 3 — VS Code Code Screenshot1" src="https://github.com/user-attachments/assets/68cd5043-12f0-40cc-9643-d0f7e64aa0f6" />

4
<img width="1313" height="77" alt="Screenshot 4 — Function Execution Logs" src="https://github.com/user-attachments/assets/c5b748cf-5977-41b3-9c3b-9d6fdd563c17" />

5
<img width="2048" height="192" alt="Screenshot 5 — Failure Detection" src="https://github.com/user-attachments/assets/e09146de-3a45-4e05-8c3c-ecccb123eb46" />

6
<img width="400" height="374" alt="06 - Logic App Designer" src="https://github.com/user-attachments/assets/d187527d-9438-47ba-b2ba-1d449204be74" />

6
<img width="528" height="403" alt="Screenshot 7 — Logic App Run History" src="https://github.com/user-attachments/assets/3f51bedf-53ed-4e69-b544-86eaf2e07c10" />

7
<img width="1692" height="298" alt="Screenshot 8 — Email Alert" src="https://github.com/user-attachments/assets/42fa0dae-5b6e-4ad9-8a64-deaf3631582e" />

8
<img width="2048" height="1076" alt="Screenshot 9 — Log Analytics Query Results" src="https://github.com/user-attachments/assets/fc9c2d9e-1f05-4ac2-b125-9b1ae8a29e99" />

9
<img width="1720" height="1106" alt="Website Uptime Dashboard 10" src="https://github.com/user-attachments/assets/8d397cd0-18ef-445d-998c-f87d09cdab5b" />

