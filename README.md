# notification-service

The **notification-service** manages the shopping cart, order placement, and order tracking functionalities within the e-commerce platform.

## Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [API Endpoints](#api-endpoints)
- [Testing](#testing)


## Features

- **Email Notifications:** Sends emails to users based on specific events (e.g., order confirmations).
- **SMS Notifications:** Sends SMS messages for important events (e.g., payment confirmations).
- **Event-Driven Architecture:** Listens for events such as order_placed and order_shipped to trigger notifications.

## Technology Stack

- **Language:** Python
- **Framework:** Celery, Flask or FastAPI
- **Database:** Apache Kafka
- **Containerization:** Docker

## Prerequisites

Before you begin, ensure you have met the following requirements:

* Python 3.8 or higher
* pip package installer
* RabbitMQ or Kafka
* Docker 
* Git for version control

## Installation

Follow these steps to set up the notification-service on your local machine:

1. ***Clone the repository:***

```bash
git clone https://github.com/your-username/notification-service.git
cd notification-service
```
2. ***Create and activiate a virtual environment:***

```bash
python3 -m venv venv
source venv/bin/activate
```
3. ***Install Dependencies:***

```bash
pip install -r requirements.txt
```

4. ***Environment Variables:***

Create a .env file in the root directory and add the following environment variables:

```properties
BROKER_URL=amqp://guest:guest@localhost:5672//
EMAIL_HOST=smtp.example.com
EMAIL_PORT=587
EMAIL_HOST_USER=your_email@example.com
EMAIL_HOST_PASSWORD=your_email_password
SMS_API_KEY=your_sms_api_key
```
* BROKER_URL: The URL of the message broker (e.g., RabbitMQ or Kafka).
* EMAIL_HOST: The SMTP server for sending emails.
* EMAIL_PORT: The SMTP server port.
* EMAIL_HOST_USER: The username for the SMTP server.
* EMAIL_HOST_PASSWORD: The password for the SMTP server.
* SMS_API_KEY: The API key for the SMS gateway.
  
5. ***Running Docker:***

Build the Docker image:

```bash
docker build -t notification-service:latest .
```

6. ***Run the Docker container:***

```bash
docker run -p 8000:8000 --env-file .env notification-service:latest
```
The service should now be accessible at http://localhost:8000

## API Endpoints

**Send email notification**
* Endpoint: POST /api/v1/notifications/email
* Description: Sends an email notification to the specified user.
* Request Body:
```json
  {
   "email": "user@example.com",
   "subject": "Order Confirmation",
   "message": "Your order has been placed successfully!"
}
```
**Send SMS notification**
* Endpoint: POST /api/v1/notifications/sms
* Description: Sends an SMS notification to the specified phone number.
* Request Body:
```json
{
   "phone_number": "+1234567890",
   "message": "Your order has been shipped!"
}

```

## Testing
Run unit tests using:

```bash
pytest
```
This command will execute all tests located in the tests directory.
