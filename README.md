# Multi-Agent AI System Using Amazon Bedrock

This project demonstrates a **multi-agent AI system** built with **Amazon Bedrock**, **AWS Lambda**, and a **serverless architecture**. The system processes requests for **restaurants** and **accommodations** (e.g., **hotels** and **Airbnbs**) by routing them through specialized AI agents that access data stored in **Amazon S3**.

---

## Architecture

1. **API Gateway**: Receives incoming POST requests.
2. **Lambda Function 1**: Routes requests to the **supervisor agent**.
3. **Amazon Bedrock (ClaudeSonnet v2)**: Routes requests to either the **accommodation agent** or **restaurant agent** based on the input.
4. **Accommodation Agent**: Handles hotel and Airbnb queries by invoking Lambda functions to fetch data from CSV files stored on **Amazon S3**.
5. **Restaurant Agent**: Handles restaurant queries similarly.

---

## Technologies

- **AWS Lambda**
- **Amazon S3** (for storing CSV data)
- **Amazon API Gateway**
- **Amazon Bedrock** (ClaudeSonnet v2)
- **Postman** (for testing)

---

## How It Works

1. **User submits a request** via the API Gateway.
2. The **supervisor agent** (via Lambda) uses **ClaudeSonnet v2** to determine if the request is for accommodation or restaurants.
3. Relevant agents fetch data from **Amazon S3** (hotel, Airbnb, or restaurant CSV files) and return the results.

---

## Setup

1. **S3 Buckets**: Create buckets and upload `hotel.csv`, `airbnb.csv`, and `restaurant.csv`.
2. **API Gateway**: Create a POST endpoint integrated with Lambda.
3. **Lambda Functions**: Deploy functions to handle routing and data processing.
4. **Amazon Bedrock**: Set up **ClaudeSonnet v2** for request routing.

---

## Testing

Use **Postman** to test the API Gateway endpoint with sample POST requests to query hotels, Airbnbs, or restaurants.

Example request body:

```json
{
  "agent": "supervisor",
  "function": "list-hotels",
  "parameters": [{ "name": "location", "value": "New York" }]
}
```

---

## Contributing

Feel free to fork the repository, improve the system, and submit a pull request!
