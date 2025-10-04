# AI-Powered SOC Analyst Assistant for Automated Alert Triage

This project demonstrates a powerful security automation workflow that automates the initial analysis and triage of security alerts. By integrating a SIEM (Splunk), an automation platform (N8N), and a Large Language Model (Google Gemini), this workflow acts as an AI-powered Tier 1 SOC Analyst, providing real-time enrichment and reporting.

The entire lab environment was built from scratch, including setting up virtual machines for Splunk and Windows 10 endpoints.

*Watch the final demonstration video:*

*(Here you can optionally convert the video you sent me (`Screen Recording 2025-10-05 012927.mp4`) to a GIF and embed it)*

### Key Features

- **Automated Alert Ingestion:** Automatically receives security alerts from Splunk via a webhook.
- **AI-Powered Analysis:** Leverages the Google Gemini model to analyze alerts based on a detailed prompt that instructs it to act as a SOC analyst.
- **Threat Intelligence Enrichment:** Uses a connected "Tool" to automatically enrich IP addresses with threat data from AbuseIPDB, providing context like confidence scores and known attack categories.
- **Severity Assessment & MITRE ATT&CK Mapping:** The AI assesses the alert's severity and maps the activity to the relevant MITRE ATT&CK tactics (e.g., T1110 - Brute Force).
- **Real-time Reporting:** Delivers a well-structured and detailed analysis report directly to a Slack channel for immediate review.

### Workflow Breakdown

The automation follows a clear, logical sequence:

1.  **Alert Generation:** A security event (e.g., a brute-force attempt) is detected on an endpoint and logged in Splunk.
2.  **Webhook Trigger:** A Splunk alert is configured to send the event data to an N8N webhook, initiating the workflow.
3.  **AI Analysis & Enrichment:** The JSON data from the alert is passed to a Google Gemini model. The AI, guided by its prompt, performs the initial analysis and uses the AbuseIPDB tool to enrich the source IP address.
4.  **Structured Report Generation:** The Gemini model synthesizes all information into a structured report, including a summary, IOC details, severity assessment, and recommended investigation steps.
5.  **Notification:** The final report is formatted and sent as a message to a dedicated Slack channel.

### Technologies Used

- **Automation Platform:** N8N
- **SIEM:** Splunk Enterprise
- **AI Model:** Google Gemini
- **Threat Intelligence:** AbuseIPDB API
- **Alerting:** Slack
- **Lab Environment:** VMware, Windows 10 (Endpoint), Ubuntu Server (Splunk Host)

### Future Enhancements

This project serves as a strong foundation for a more advanced Security Orchestration, Automation, and Response (SOAR) platform. Future enhancements can include:

- **File Threat Analysis:** Integrating VirusTotal to automatically analyze file hashes from endpoint alerts, generate reports, and send email notifications.
- **Ticketing System Integration:** Connecting the workflow to a case management system like TheHive or DFIR-IRIS to automatically create tickets for incidents.
- **Direct SIEM Querying:** Providing the AI with a tool to run follow-up queries directly against the Splunk API for deeper investigation.
