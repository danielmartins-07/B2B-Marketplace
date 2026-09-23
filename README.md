# B2B Marketplace

A business-to-business marketplace developed as a **2024 bachelor's final group project** for *Laboratório de Projeto* at Universidade Autónoma de Lisboa. The application lets companies showcase products, manage their catalogues, communicate with other businesses, and place wholesale orders.

This repository preserves the original academic project for **portfolio and local demonstration purposes**.

## Features

- Company registration, login, profiles, and supplier pages
- Product catalogue with categories, images, stock, and minimum-order quantities
- Supplier inventory management and promotional product displays
- Company-to-company messaging and wishlists
- Shopping cart, shipping options, and order history
- **Stripe Checkout in test mode**

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

## Known limitations

This is the preserved **2024 academic prototype**, not a production-ready marketplace. Some features are incomplete: promotional prices are displayed but **the cart and checkout charge the original product price**; product editing and some wishlist actions are incomplete. Payment verification, access controls, and dependencies would need further work before any real-world deployment.

The [original user manual](Manual%20de%20Utlizador%20-%20B2B.pdf) provides a more detailed walkthrough of the project interface.

## Project credits

**Group members:** Rodrigo Anjos · Tiago Sousa · Tiago Lança · Daniel Martins  
**Supervisor:** Adrian Dediu  
**Institution:** Universidade Autónoma de Lisboa · *Laboratório de Projeto* · 2024
