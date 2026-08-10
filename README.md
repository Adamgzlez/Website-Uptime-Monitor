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

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/881429c7-8a91-4b95-986e-1939c5bcf71d" />

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

<img width="1383" height="429" alt="Screenshot 1 — Resource Group Overview" src="https://github.com/user-attachments/assets/e71e300e-2a7f-4dc8-82df-1471aceae1ae" />

### Function App

<img width="2047" height="159" alt="Screenshot 2 — Function App Overview" src="https://github.com/user-attachments/assets/939c947d-0370-422f-bcf3-e48eec1562fb" />

### Function Code with Timer Trigger

<img width="1077" height="841" alt="Screenshot 3 — VS Code Code Screenshot" src="https://github.com/user-attachments/assets/e56d3ab8-f693-4e75-bbc9-86edacb7904f" />

<img width="246" height="58" alt="Screenshot 3 — VS Code Code Screenshot1" src="https://github.com/user-attachments/assets/f103a0bb-a434-47c6-ac8d-362d4ecad0be" />

### Successful Function Execution

<img width="1313" height="77" alt="Screenshot 4 — Function Execution Logs" src="https://github.com/user-attachments/assets/a0797d70-3dc2-43e3-99f0-ff6624af5034" />

<img width="528" height="403" alt="Screenshot 7 — Logic App Run History" src="https://github.com/user-attachments/assets/d1b6bb21-af98-4956-815b-682cc8bfdb2f" />

### Log Analytics

<img width="2048" height="1076" alt="Screenshot 9 — Log Analytics Query Results" src="https://github.com/user-attachments/assets/92195792-f971-4976-b5a6-098f5e104eb2" />

### Logic App

<img width="400" height="374" alt="06 - Logic App Designer" src="https://github.com/user-attachments/assets/1de7eb8c-d5cd-42cb-8184-2194c4a141e9" />

### Website Down Failure Detection

<img width="2048" height="192" alt="Screenshot 5 — Failure Detection" src="https://github.com/user-attachments/assets/adc839eb-b7c5-4f54-a1c0-753774487341" />

### Email Alert

<img width="1692" height="298" alt="Screenshot 8 — Email Alert" src="https://github.com/user-attachments/assets/7c00af3b-1983-48eb-afbd-db45d88d5bf5" />

### Monitoring Dashboard

<img width="1720" height="1106" alt="Website Uptime Dashboard 10" src="https://github.com/user-attachments/assets/6112b1b6-3c3d-4504-b57a-4d5042f68a2d" />

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

The completed system automatically monitors website availability every 5 minutes, records monitoring data in Azure, provides a centralized dashboard, and sends email notifications when failures occur.

The project demonstrates how Azure serverless and monitoring services can be combined to build a practical cloud operations monitoring solution.




