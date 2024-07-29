# CashCard API

This project provides a RESTful API for managing cash cards, allowing users to create, retrieve, update, and delete cash
cards associated with their account.

## Features

- **Create Cash Card:** Create a new cash card.
- **Retrieve Cash Card:** Retrieve a specific cash card by ID.
- **List Cash Cards:** List all cash cards for the authenticated user with pagination.
- **Update Cash Card:** Update the details of an existing cash card.
- **Delete Cash Card:** Delete a specific cash card by ID.

## Getting Started

### Prerequisites

- Java 17 or higher
- Gradle
- Spring Boot

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/nathsagar96/cashcard.git
   cd cashcard
   ```

2. **Build the project:**
   ```bash
   ./gradlew build
   ```

3. **Run the application:**
   ```bash
   ./gradlew bootRun
   ```

### Usage

Once the application is running, you can interact with the API using tools like `curl` or Postman.

#### Endpoints

1. **Create a Cash Card**

    - **URL:** `/cashcards`
    - **Method:** `POST`
    - **Request Body:**
      ```json
      {
        "amount": 100.0
      }
      ```
    - **Response:** `201 Created`

2. **Retrieve a Cash Card**

    - **URL:** `/cashcards/{id}`
    - **Method:** `GET`
    - **Response:** `200 OK` with cash card details or `404 Not Found`

3. **List All Cash Cards**

    - **URL:** `/cashcards`
    - **Method:** `GET`
    - **Parameters:**
        - `page`: Page number (default is 0)
        - `size`: Page size (default is 20)
        - `sort`: Sorting criteria (e.g., `amount,asc`)
    - **Response:** `200 OK` with a list of cash cards

4. **Update a Cash Card**

    - **URL:** `/cashcards/{id}`
    - **Method:** `PUT`
    - **Request Body:**
      ```json
      {
        "amount": 150.0
      }
      ```
    - **Response:** `204 No Content` or `404 Not Found`

5. **Delete a Cash Card**

    - **URL:** `/cashcards/{id}`
    - **Method:** `DELETE`
    - **Response:** `204 No Content` or `404 Not Found`

### Security

The API uses Spring Security to authenticate users. Each cash card is associated with the authenticated user. Ensure you
have configured your security settings appropriately.

### Data Model

The CashCard entity consists of the following fields:

- `id`: Unique identifier for the cash card (generated automatically).
- `amount`: The amount of money in the cash card.
- `owner`: The username of the owner of the cash card.

### Example

To create a new cash card:

```bash
curl -X POST http://localhost:8080/cashcards \
     -H "Content-Type: application/json" \
     -d '{"amount": 100.0}' \
     -u username:password
```

To list all cash cards for the authenticated user:

```bash
curl -X GET http://localhost:8080/cashcards \
     -u username:password
```
