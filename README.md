**Ecommerce App**

This is a microservices-based Ecommerce application with the following services:

Services
1. Customers Service
Endpoints:

GET /customers: Get all customers.

GET /customers/{id}: Get a customer by ID.

POST /customers: Add a new customer.

PUT /customers/{id}: Update a customer.

DELETE /customers/{id}: Delete a customer.

Customer Schema:

json
Copy
{
  "customernumber": "string",
  "name": "string",
  "phone": "string",
  "email": "string",
  "street": "string",
  "city": "string",
  "zip": "string"
}
2. Products Service
Endpoints:

GET /products: Get all products.

GET /products/{id}: Get a product by ID.

POST /products: Add a new product.

PUT /products/{id}: Update a product.

DELETE /products/{id}: Delete a product.

Product Schema:

json
Copy
{
  "productnumber": "string",
  "name": "string",
  "price": "number",
  "description": "string",
  "supplierName": "string",
  "supplierPhone": "string"
}
Load Balancing: Two instances of this service run behind the API Gateway for high availability.

3. Payments Service
Endpoints:

GET /payments: Get all payments.

GET /payments/{id}: Get a payment by ID.

POST /payments: Add a new payment.

PUT /payments/{id}: Update a payment.

DELETE /payments/{id}: Delete a payment.

Payment Schema:

json
Copy
{
  "date": "date",
  "amount": "number",
  "ordernumber": "string",
  "customernumber": "string"
}
4. OrdersCommand Service
Endpoints:

POST /orders: Place a new order.

GET /orders/{id}: Get an order by ID.

Order Schema:

json
Copy
{
  "ordernumber": "string",
  "date": "date",
  "totalPrice": "number",
  "products": [
    {
      "productnumber": "string",
      "quantity": "number"
    }
  ],
  "customernumber": "string",
  "customerName": "string"
}
5. OrdersQuery Service
Endpoints:

GET /orders/{id}: Get detailed order information, including customer, products, and payment details.

Database
All services use MongoDB for data storage.

API Gateway
Routes requests to the appropriate service.

Load balances between two instances of the Products Service.

How to Run
Clone the repository.

Install dependencies:

bash
Copy
npm install
Start MongoDB:

bash
Copy
mongod
Run each service:

bash
Copy
npm start --prefix <service-folder>
Start the API Gateway:

bash
Copy
npm start --prefix api-gateway
Technologies Used
Node.js

Express.js

MongoDB

API Gateway (e.g., Express Gateway or NGINX)

Contributors

Awet
Mehreteab
