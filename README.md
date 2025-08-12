# Grocigo - Grocery Management System

Grocigo is a full-stack web application for managing a grocery store, supporting both admin and customer roles. It provides features for product catalog management, stock updates, customer registration, cart and order management, transaction tracking, and more.

---

## Features

### Admin

- Login as admin (`mak` / `mak123`)
- View all products and categories
- Add new products
- Update stock for products
- View depleted products (low stock)
- View all customers
- View all transactions

### Customer

- Register and login
- Browse products by category
- Add products to cart
- Remove products from cart
- Place orders (with address, phone, payment mode)
- View own transactions

---

## Project Structure

```
├── addProduct.html
├── addStock.html
├── adminHome.html
├── cart.html
├── customerHome.html
├── customers.html
├── customerViewTransactions.html
├── depleted.html
├── index.html
├── login.html
├── logout.html
├── order.html
├── placeOrder.html
├── README.md
├── style.css
├── transactions.html
├── viewProducts.html
├── viewProductsCustomer.html
├── js/
│   ├── api.js
│   ├── common.js
│   ├── storage.js
│   ├── ui.js
├── normalization/
│   ├── cart.nrm
│   ├── categories.nrm
│   ├── customer.nrm
│   ├── depleted_products.nrm
│   ├── products.nrm
│   ├── transaction.nrm
├── server/
│   ├── server.js
│   ├── package.json
│   └── package-lock.json
├── sql/
│   └── wholesale.sql
```

---

## Database Schema

The database is defined in `sql/wholesale.sql`:

- **customer**: Stores user accounts (admin and customers)
- **categories**: Product categories
- **products**: Product catalog
- **cart**: Shopping cart per customer
- **transaction**: Orders placed by customers
- **depleted_products**: Tracks products with low stock (via trigger)

Refer to `sql/wholesale.sql` for table definitions, sample data, and triggers.

---

## Installation & Setup

### Prerequisites

- Node.js (v16+ recommended)
- MySQL Server

### 1. Clone the Repository

```sh
git clone <repo-url>
cd grocigo
```

### 2. Install Server Dependencies

```sh
cd server
npm install
```

### 3. Setup MySQL Database

- Create a database named `wholesale`.
- Import the schema and seed data:

```sh
mysql -u root -p wholesale < sql/wholesale.sql
```

- Update MySQL credentials in `server/server.js` if needed:
  - `DB_HOST`, `DB_USER`, `DB_PASS`, `DB_NAME`, `DB_PORT`

---

## Running the Project

### 1. Start the Backend Server

```sh
cd server
npm start
```

The server will run at [http://localhost:5500](http://localhost:5500).

### 2. Access the Web Application

Open [http://localhost:5500/index.html](http://localhost:5500/index.html) in your browser.

---

## Usage Guide

### Login

- **Admin:** Username: `mak`, Password: `mak123`
- **Customer:** Register via "Create New Account" on the login page.

### Admin Features

- **Home:** Overview of admin options.
- **View Products:** Browse all products by category.
- **Add Stock:** Update quantity for existing products.
- **Add New Product:** Add new products to the catalog.
- **Depleted Products:** View products with low stock (<=10 units).
- **Customers:** View all registered customers.
- **Transactions:** View all orders placed.

### Customer Features

- **Home:** Overview of customer options.
- **View Products:** Browse products by category.
- **Order:** Add products to cart and place orders.
- **Cart:** View and manage cart items.
- **My Transactions:** View order history.

---

## API Endpoints

The backend exposes RESTful endpoints (see `server/server.js`):

- `POST /api/login` - Login
- `POST /api/logout` - Logout
- `POST /api/create-account` - Register
- `GET /api/session` - Get current session
- `GET /api/categories` - List categories
- `GET /api/products` - List products (optionally by category)
- `POST /api/products` - Add product
- `POST /api/stock/update` - Update product stock
- `GET /api/cart` - Get cart items
- `POST /api/cart/add` - Add to cart
- `POST /api/cart/remove` - Remove from cart
- `GET /api/transactions` - List transactions (admin/all or customer)
- `POST /api/order` - Place order
- `GET /api/customers` - List customers (admin only)
- `GET /api/depleted` - List depleted products (admin only)

---

## Normalization Files

The `normalization/` directory contains `.nrm` files describing the normalization and functional dependencies for each table, useful for database design documentation.

---

## Credits

Developed by Mukund Sarda, Dhiren Pradhan, Purvi Hegde, Kshitij Singh, Sai Sathwik Kosuru.

---

## Troubleshooting

- Ensure MySQL server is running and accessible.
- Check credentials in `server/server.js`.
- For port conflicts, change the `PORT` variable in the server code.