# B2B Marketplace

A business-to-business marketplace developed as a **2024 bachelor's final group project** for *Laboratório de Projeto* at Universidade Autónoma de Lisboa. The application lets companies showcase products, manage their catalogues, communicate with other businesses, and place wholesale orders.

This repository preserves the original academic project for **portfolio and local demonstration purposes**.

## Features

- **Company accounts and supplier profiles.** Businesses can register, sign in, and maintain a company profile with contact information, a description, and an image. Each account can act as both a buyer and a supplier, with a public company page showcasing its products.

- **Product catalogue and discovery.** Products are organised into departments and subdepartments, with search, filtering, and price-ordering controls to help users browse the catalogue. Product pages bring together descriptions, image galleries, supplier links, stock information, and minimum-order quantities.

- **Supplier catalogue and promotional displays.** Suppliers can add product listings with pricing, stock, minimum-order quantities, and multiple images through their dashboard. They can also configure promotional prices, which appear on product listings and detail pages.

- **Business-to-business communication.** Companies can send messages to other businesses and reply through the dashboard. Separate inbox and sent-message views keep conversations accessible alongside the company's other marketplace activity.

- **Saved products.** Signed-in companies can add products to a wishlist and access them from the dashboard's Liked Products section. Each saved entry links back to the product page for further browsing or purchasing.

- **Wholesale cart and delivery selection.** The shopping cart supports ordering in multiples of each product's minimum-order quantity. Buyers can select a destination, delivery speed, address, and delivery date, with national or international shipping calculated from the sellers' countries and the destination. Cart totals and test payments use the base catalogue prices.

- **Stripe test checkout and order history.** The application creates a hosted Stripe Checkout session for sandbox payments. After a successful test payment and return to the application, the purchase is recorded with its products, quantities, delivery details, and total; buyers can view their orders and suppliers can view the corresponding sales in their dashboards.

## Tech stack

**JavaScript · Node.js · Express · EJS · CSS · MySQL · Stripe**

The Express application serves the frontend and backend; no separate frontend build is required.

## Run locally

**Requirements:** Node.js 22, npm, MySQL 8.0, and a Stripe **test-mode** secret key. The recovered project was tested locally on Ubuntu 24.04 using Node.js 22.23.2 and MySQL 8.0.46.

**1. Create and import the demonstration database.** From the repository root:

```bash
sudo mysql -e "CREATE DATABASE marketplace_b2b CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci;"
sudo mysql marketplace_b2b < database/demo.sql
```

These commands assume a new local database named `marketplace_b2b`. Do not import the file over a database containing data you want to keep. The dataset contains fictional demonstration records; its original account passwords have been replaced, so **register a new fictional company account** to log in.

**2. Create a local MySQL account** with a password of your choice:

```sql
CREATE USER 'marketplace_app'@'localhost'
  IDENTIFIED WITH mysql_native_password BY 'REPLACE_WITH_YOUR_OWN_PASSWORD';
GRANT SELECT, INSERT, UPDATE, DELETE
  ON marketplace_b2b.* TO 'marketplace_app'@'localhost';
```

Run these statements as a MySQL administrator (for example, with `sudo mysql`). This authentication method reflects the tested MySQL 8.0 setup.

**3. Install dependencies and configure the application:**

```bash
cd LabFinal/LabB2B_Team-master
npm ci
cp .env.example .env
chmod 600 .env
```

Edit `.env` to set the database account and password, a random `SESSION_SECRET`, and your own Stripe **test-mode** `STRIPE_SECRET_KEY`. Keep `.env` private; it is excluded from Git.

**4. Start the application:**

```bash
node app.js
```

Open **http://localhost:3000** on the same machine. Use fictional information and Stripe test cards only; do not use this prototype for real payments.

## Documentation

The [original user manual](Manual%20de%20Utlizador%20-%20B2B.pdf) provides a walkthrough of the academic project's interface. For the configuration used by this repository, follow the setup instructions above.

## Educational use and image disclaimer

This application and its demonstration content were assembled for a university final project and are shared for educational, portfolio, and local demonstration purposes only. They are not intended for real-world commercial operation or real transactions.

The visual assets include AI-generated company branding and third-party product photographs and other imagery used to illustrate the demonstration catalogue and interface. Third-party images, brand names, and trademarks remain the property of their respective owners; their inclusion does not imply affiliation, endorsement, or a grant of permission to reuse them. This notice explains the project's context and does not replace any permission or licence required from the relevant rights holders.

## Project credits

**Group members:** Rodrigo Anjos · Tiago Sousa · Tiago Lança · Daniel Martins  
**Supervisor:** Adrian Dediu  
**Institution:** Universidade Autónoma de Lisboa · *Laboratório de Projeto* · 2024
