# Inventory Management System

A robust, SQL-driven Inventory Management System (IMS) designed to modernize inventory tracking, automate restocking, streamline order management, and deliver actionable business insights for scalable business operations.

---

## Project Overview

Manual inventory methods can lead to inaccurate stock levels, slow order processing, and higher holding costs. This IMS addresses these challenges by enabling real-time inventory visibility, dynamic order processing, automated restocking, comprehensive user management, and rich analytics for business growth and operational efficiency.

---

## Features

- **Real-Time Inventory Tracking:** Instantly add categories and products, monitor stock levels, and maintain inventory accuracy.
- **Order Processing & Modification:** Customers can place and modify orders during the "processing" stage for flexible and efficient fulfillment.
- **Automated Restocking:** System proactively generates supply records when stock falls below minimum thresholds, ensuring timely reordering.
- **Dynamic Pricing & Billing:** Discounts are applied, and final prices and bills are calculated automatically.
- **Comprehensive User Management:** Customers and suppliers can update their information for accurate records.
- **Supplier & Product Analytics:** Comparative analysis of suppliers and products to optimize procurement and sales.
- **Operational Efficiency:** Minimizes holding costs, prevents stockouts, and streamlines supplier relationships.
- **Scalable Design:** Supports business growth and evolving operational needs.

---

## System Architecture

- **Database:** Oracle SQL (all logic implemented with SQL scripts, stored procedures, views, and triggers)
- **Access Control:** Role-based users (IMS_ADMIN, IMS_MANAGER, CUSTOMER, SUPPLIER, LOGISTIC_ADMIN) with fine-grained permissions and procedure-only access for security and compliance.

---

## Entities and Attributes

Key entities include:

- **PRODUCTS:** Product details, pricing, stock, supplier, category, discount info.
- **CATEGORY:** Product categories.
- **SUPPLIER:** Supplier details and contact info.
- **CUSTOMER:** Customer details and contact info.
- **ORDERS:** Order lifecycle, billing, shipping status.
- **PRODUCTORDER:** Product-order relationships.
- **PRODUCTSUPPLY:** Restocking and supply records.
- **DISCOUNT:** Discount rules for dynamic pricing.

---

## Database Views

Oracle views are stored queries that present data from one or more tables in a simplified, business-relevant format[5][8]. This system uses several views to provide actionable insights and user-specific dashboards:

- **Customer Order History View:**  
  Shows all past orders placed by a customer, including order dates, products, quantities, and total amounts.  
  *Purpose:* Enables customers to review their purchase history and reorder efficiently.

- **Customer Shipping Status View:**  
  Displays the current shipping status (processing, in transit, delivered) for each order.  
  *Purpose:* Allows customers to track their orders in real time.

- **Supplier Performance View:**  
  Ranks suppliers based on the quantity of products sold, helping optimize supplier management.  
  *Purpose:* Assists in evaluating supplier effectiveness and negotiating better terms.

- **Product Stock Overview View:**  
  Lists all products with current stock, minimum thresholds, and restock alerts.  
  *Purpose:* Helps managers minimize overstock and stockouts by monitoring inventory health.

- **Product Performance Comparative View:**  
  Provides comparative sales and performance data for products from the same supplier.  
  *Purpose:* Identifies top-performing products and informs inventory and marketing strategies.

- **Sales Insights View:**  
  Aggregates total sales by product, category, and customer for business analytics.  
  *Purpose:* Supports decision-making for promotions, procurement, and customer engagement.

---

## Security & Compliance

- **Procedure-Only Access:** All users interact via stored procedures, ensuring data integrity and minimizing direct table access.
- **Fine-Grained Permissions:** Each user role is granted only the necessary procedure permissions.
- **Secure Data Handling:** Adheres to best practices for storing and managing personal and transactional data.

---

## Setup & Usage Instructions

### Prerequisites

- Oracle Database (local or cloud instance)
- SQL*Plus or compatible SQL client

### Step-by-Step Execution

Each step below is mapped to a specific user role and script, ensuring security and clear separation of duties.

#### 1. Run as Database Admin (e.g., `IMSDB_ADMIN`):

- **Script1.sql:**  
  *Creates the application admin (`IMS_ADMIN`) and grants necessary privileges.*  
  *Note:* This step establishes the top-level admin user who will manage the overall system structure and security.

#### 2. Login as `IMS_ADMIN`:

- **Script2.sql:**  
  *Creates all tables, constraints, sequences, and core views for the IMS.*  
  *Note:* This script defines the database schema—entities, relationships, and business logic—ensuring data integrity and supporting all system features.

- **Script3.sql:**  
  *Creates users for suppliers, customers, IMS_Manager, and logistic_admin, and grants appropriate privileges.*  
  *Note:* This enforces role-based access, restricting users to only their permitted operations.

#### 3. Login as `CUSTOMER`:

- **Script4.sql:**  
  *Inserts new customer records, onboarding customers into the system.*  
  *Note:* This step allows new customers to register and access the IMS.

#### 4. Login as `SUPPLIER`:

- **Script5.sql:**  
  *Inserts new supplier records, onboarding suppliers into the system.*  
  *Note:* Suppliers are added with their details, enabling them to supply products and view analytics.

#### 5. Login as `IMS_MANAGER`:

- **Script6.sql:**  
  *Inserts product, category, and discount records to populate the inventory.*  
  *Note:* Enables the manager to set up the product catalog, categories, and discount rules for dynamic pricing.

#### 6. Login as `IMS_ADMIN`:

- **Script7.sql:**  
  *Inserts new orders and associates products with orders.*  
  *Note:* This script handles order placement, billing, and links products to customer orders.

#### 7. Login as `LOGISTIC_ADMIN`:

- **Script8.sql:**  
  *Updates shipping status of orders to reflect processing, in transit, or delivered.*  
  *Note:* Logistics administrators keep order statuses current for accurate customer tracking.

#### 8. Login as `CUSTOMER`:

- **Script9.sql:**  
  *Generates customer-specific views for order history and shipping status.*  
  *Note:* Customers can view their past orders and track the shipping progress of current orders.

#### 9. Login as `SUPPLIER`:

- **Script10.sql:**  
  *Generates supplier-specific views for performance analytics.*  
  *Note:* Suppliers gain insights into their sales performance and product demand.

---

## Business Process Flow

- **Customer/Supplier Onboarding:** Secure, guided onboarding for new users.
- **Product & Category Management:** Add, update, and monitor products and categories.
- **Order Placement & Modification:** Place new orders, update quantities, and add products to existing orders.
- **Restocking & Inventory Control:** Automated alerts and supply records for low-stock products.
- **Performance & Sales Reporting:** Supplier comparison, product performance, stock overview, sales insights, and order/shipping history.

---

## Example Use Cases

- **A customer places an order:** The system calculates discounts, updates stock, and generates a bill.
- **Stock falls below minimum:** Automated restocking is triggered, and a supply record is created.
- **Supplier views performance:** Supplier logs in to see sales analytics and product performance.
- **Customer tracks shipping:** Customer checks real-time shipping status and past order history.

---

## Notes

- **Views in Oracle:**  
  Views are virtual tables created by stored queries. They simplify data access, support security by exposing only necessary data, and can aggregate or join data from multiple tables for business insights[5][8].
- **Security:**  
  All users are restricted to stored procedure access, which enforces business rules and prevents unauthorized data manipulation.
- **Scalability:**  
  The system is designed to support business growth, with modular scripts and extensible schema.

---

