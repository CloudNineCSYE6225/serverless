# Email Verification Service

## Overview

This Python-based project automates the process of sending email verification links to users. It leverages Google Cloud's Pub/Sub for event-driven architecture, generating secure verification links with unique tokens and expiration times. The emails are dispatched through the Mailgun API, ensuring reliable delivery.

## Features

- **Event-Driven Architecture**: Utilizes Google Cloud Pub/Sub to trigger email sending based on published messages.
- **Secure Verification Link Generation**: Creates verification links that are both secure and unique, including a token and an expiration time.
- **Mailgun Email Dispatch**: Leverages Mailgun for email sending, offering robustness and reliability.

## Prerequisites

Before you start, ensure you have the following:
- Python 3.x installed.
- An active Google Cloud project with Pub/Sub enabled and a topic created.
- A Mailgun account with an obtained domain and API key.

## Environment Setup

Set up your environment by configuring the following environment variables:
- `MAILGUN_DOMAIN`: Your Mailgun domain.
- `MAILGUN_API_KEY`: Your Mailgun API key.

## Deployment

To deploy and use the email verification service, follow these steps:

### 1. Deploy the Function

Deploy the `send_verification_email` function as a Cloud Function in Google Cloud, setting the trigger to the Pub/Sub topic you have prepared.

### 2. Publish Pub/Sub Messages

Publish messages to your Pub/Sub topic containing the user's email in the JSON format as shown below:
```json
{
  "email": "user@example.com"
}


##Function Details
Sending Verification Emails
Upon receiving a Pub/Sub message, the function:
Extracts the user's email.
Generates a secure verification link.
Sends an email with the verification link using Mailgun.

##Verification Link Generation
The generated verification link includes:
A unique token for security.
An expiration time of 2 minutes to ensure timely verification.
URL-encoded email and expiration time for safe inclusion in query parameters.




