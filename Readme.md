# Product CRUD REST API

A simple RESTful API built with **Node.js, Express.js, and CORS** to perform CRUD (Create, Read, Update, Delete) operations on products.

The project uses an **in-memory JavaScript array** as a temporary database, making it useful for learning and practicing REST API development without requiring a real database.

## 🚀 Features

* RESTful API architecture
* CRUD operations for products
* Express.js server
* JSON request/response handling
* CORS support for frontend applications
* Basic request validation
* Dynamic product IDs
* HTTP status codes for success and error responses
* In-memory data storage

## 🛠️ Tech Stack

* **Node.js**
* **Express.js**
* **CORS**
* **JavaScript**
* **REST API**

## 📁 Project Structure

```text
Product-CRUD-API/
│
├── app.js
├── package.json
├── package-lock.json
└── README.md
```

## ⚙️ Installation & Setup

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd Product-CRUD-API
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the server

```bash
node app.js
```

The server will start on:

```text
http://localhost:5000
```

To verify the API, open:

```text
http://localhost:5000/products
```

## 🔗 API Endpoints

| Method | Endpoint        | Description                |
| ------ | --------------- | -------------------------- |
| GET    | `/products`     | Get all products           |
| GET    | `/products/:id` | Get a single product       |
| POST   | `/products`     | Create a new product       |
| PUT    | `/products/:id` | Update an existing product |
| DELETE | `/products/:id` | Delete a product           |

## 📖 API Usage

### 1. Get All Products

**GET**

```http
GET /products
```

Example:

```text
http://localhost:5000/products
```

Returns the complete list of products.

### 2. Get Product by ID

**GET**

```http
GET /products/:id
```

Example:

```text
http://localhost:5000/products/2
```

Returns the product with the specified ID.

If the product does not exist, the API should return:

```json
{
  "error": "Product not found"
}
```

### 3. Create a Product

**POST**

```http
POST /products
```

Request body:

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

Successful response:

```json
{
  "id": 6,
  "name": "Leather Notebook",
  "category": "Stationery",
  "price": 25,
  "stock": 20,
  "color": "#654321",
  "rating": 4
}
```

The API automatically generates a unique ID for the new product.

### 4. Update a Product

**PUT**

```http
PUT /products/:id
```

Example:

```text
http://localhost:5000/products/2
```

Request body:

```json
{
  "price": 70,
  "stock": 10
}
```

Only the fields provided in the request are updated.

### 5. Delete a Product

**DELETE**

```http
DELETE /products/:id
```

Example:

```text
http://localhost:5000/products/5
```

A successful deletion returns:

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
