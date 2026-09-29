# Wares Ledger Backend

A simple Node.js + Express backend for managing a product catalog. This API is designed for a frontend app such as a React dashboard or e-commerce UI and supports the main CRUD operations for products.

## Features

- Get all products
- Get a single product by ID
- Create a new product
- Update an existing product
- Delete a product
- JSON-based request and response handling
- CORS support for frontend integrations
- In-memory data storage for quick demos and learning

## Tech Stack

- Node.js
- Express.js
- JavaScript
- CORS

## Project Structure

```text
Wares-Ledger-backend/
├── server.js
├── package.json
├── Readme.md
└── node_modules/   (after installation)
```

## Installation

1. Open the project folder
2. Install dependencies:

```bash
npm install
```

3. Start the server:

```bash
npm start
```

The server runs on:

```text
http://localhost:5000
```

## API Endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| GET | /products | Get all products |
| GET | /products/:id | Get a single product by ID |
| POST | /products | Add a new product |
| PUT | /products/:id | Update a product |
| DELETE | /products/:id | Delete a product |

## Example Requests

### Get all products

```http
GET http://localhost:5000/products
```

### Get one product

```http
GET http://localhost:5000/products/2
```

### Create a product

```http
POST http://localhost:5000/products
Content-Type: application/json
```

```json
{
  "name": "Leather Notebook",
  "category": "Stationery",
  "price": 25,
  "stock": 20,
  "color": "#654321",
  "rating": 4
}
```

### Update a product

```http
PUT http://localhost:5000/products/2
Content-Type: application/json
```

```json
{
  "price": 70,
  "stock": 10
}
```

### Delete a product

```http
DELETE http://localhost:5000/products/5
```

## Notes

- Data is stored in memory, so it resets when the server restarts.
- This backend is useful for testing frontend integrations before connecting to a real database.
- The app uses basic validation for required fields like name, category, and price.

## License

This project is licensed under the ISC license.

```text
HTTP 204 No Content
```

## 📦 Product Data Model

Each product contains the following fields:

| Field      | Type   | Description                 |
| ---------- | ------ | --------------------------- |
| `id`       | Number | Unique product identifier   |
| `name`     | String | Product name                |
| `category` | String | Product category            |
| `price`    | Number | Product price               |
| `stock`    | Number | Available quantity          |
| `color`    | String | Product color in HEX format |
| `rating`   | Number | Product rating              |

## ✅ Validation

The `POST /products` endpoint requires:

* `name`
* `category`
* `price`

If any required field is missing, the API returns:

```json
{
  "error": "name, category, and price are required"
}
```

with HTTP status:

```text
400 Bad Request
```

For update and delete operations, if the requested product does not exist, the API returns:

```text
404 Not Found
```

## 🌐 CORS Support

CORS is enabled so that a frontend application running on another port can communicate with this API.

For example:

```text
React Frontend → http://localhost:5173
Express API    → http://localhost:5000
```

The following middleware enables this:

```javascript
app.use(cors());
```

## 💾 Data Storage

This project currently uses an in-memory JavaScript array:

```javascript
let products = [];
```

Therefore:

* Data exists only while the server is running.
* Restarting the server resets the product data.
* No external database is required.

For a production application, this can be replaced with a database such as **MongoDB, PostgreSQL, or MySQL**.

## 🧪 Testing

The API can be tested using tools such as:

* Postman
* Thunder Client
* Insomnia
* REST Client extensions
* Browser for GET requests

Example workflow:

```text
GET     /products
   ↓
POST    /products
   ↓
GET     /products/:id
   ↓
PUT     /products/:id
   ↓
DELETE  /products/:id
```

## 📌 HTTP Status Codes Used

| Status Code | Meaning                                 |
| ----------- | --------------------------------------- |
| `200`       | Request successful                      |
| `201`       | Resource created successfully           |
| `204`       | Resource deleted successfully           |
| `400`       | Invalid request / missing required data |
| `404`       | Product not found                       |

## 🎯 Learning Objectives

This project demonstrates the fundamentals of:

* Node.js backend development
* Express.js
* REST API design
* HTTP methods
* CRUD operations
* Route parameters
* Request bodies
* JSON responses
* Middleware
* CORS
* HTTP status codes
* Basic API validation

## 🔮 Future Improvements

Possible improvements include:

* Add MongoDB/PostgreSQL database
* Add MVC architecture
* Add authentication and authorization
* Add request validation using Joi/Zod
* Add centralized error handling
* Add pagination and filtering
* Add search functionality
* Add automated tests
* Add environment variables with `.env`
* Deploy the API to a cloud platform

## 👨‍💻 Author

**Vaseem Akram**

GitHub: `vaseemakram366`

---

### 📄 License

This project is created for educational and learning purposes.
