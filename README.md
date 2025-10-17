🚚 SmartSupplyApp

A desktop-based Smart Supply Chain Tracker built using Java Swing and MySQL, designed to simulate blockchain-inspired product tracking with QR codes, role-based access (Customer/Delivery), dark/light themes, and persistent ledger storage.

🧩 Features

✅ Two Role Modes:

Customer – Scan QR, track product journey, flag fake products, live chat support.

Delivery Person – Generate QR codes, update delivery status (“Picked Up”, “In Transit”, “Delivered”).

✅ Blockchain-like Ledger:

Maintains a timestamped log of all product events (registrations, deliveries, flags, etc.).

Viewable in-app via the “View Ledger” option.

✅ Smart QR Integration:

Each product has a unique QR hash (SHA-256-based).

QR code generation simulated visually.

✅ MySQL Integration:

Auto-creates products and ledger tables if missing.

All transactions, updates, and product states persist to DB.

✅ Modern UI:

Swing GUI with gradient login, responsive panels, and a Dark/Light Theme toggle.

✅ Simulated Map View:

Displays product’s last known (simulated) coordinates.

🗄️ Database Schema (Auto-created)
CREATE TABLE IF NOT EXISTS products (
  id VARCHAR(64) PRIMARY KEY,
  name VARCHAR(255),
  batchNo VARCHAR(64),
  manufacturer VARCHAR(255),
  distributor VARCHAR(255),
  retailer VARCHAR(255),
  status VARCHAR(64),
  assignedDelivery VARCHAR(128),
  lat DOUBLE,
  lon DOUBLE,
  flagged BOOLEAN DEFAULT FALSE,
  timeline TEXT,
  last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS ledger (
  id BIGINT AUTO_INCREMENT PRIMARY KEY,
  entry TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

⚙️ Requirements

Java JDK 17+

MySQL Server 8.0+

MySQL Connector/J (JDBC driver) — add to classpath
(mysql-connector-java-8.x.x.jar)

🧠 Setup Instructions

Clone this repo:

git clone https://github.com/<your-username>/SmartSupplyApp.git
cd SmartSupplyApp


Configure Database:

Open SmartSupplyApp.java

Find and update:

private static final String DB_URL = "jdbc:mysql://localhost:3306/smartsupply?useSSL=false&serverTimezone=UTC";
private static final String DB_USER = "root";
private static final String DB_PASS = "your_password";


Compile & Run:

javac -cp ".;mysql-connector-java-8.0.xx.jar" SmartSupplyApp.java
java -cp ".;mysql-connector-java-8.0.xx.jar" SmartSupplyApp


(Optional - IntelliJ Setup):

Open IntelliJ → New Project → Java → Load Existing File

Add MySQL connector to Project Structure → Libraries

Run SmartSupplyApp.java

🖥️ Roles Overview
👩‍💼 Customer Mode

Scan QR (via simulated input)

Track delivery status on map

Chat with support

Flag fake products

🚛 Delivery Person Mode

Generate product QR codes

Update delivery status

Submit updates to ledger (simulated blockchain)

📊 Ledger Example
2025-10-17 09:24:12 - REGISTERED - PROD001 by ABC Pharma
2025-10-17 09:26:05 - PICKED UP - PROD001 by DeliveryGuy1
2025-10-17 09:29:44 - IN TRANSIT - PROD001 by DeliveryGuy1
2025-10-17 09:35:22 - DELIVERED - PROD001 by DeliveryGuy1

🌗 Themes
Mode	Preview
Light	☀️ Bright UI with white panels
Dark	🌙 Sleek modern dark mode

Switch easily via Theme dropdown in the top-right header.

🧾 Future Enhancements

Blockchain integration using Solidity + Web3J

QR scanning via webcam (ZXing library)

Cloud DB (e.g., AWS RDS)

Role-based authentication with encrypted credentials

📜 License

This project is licensed under the MIT License — you are free to modify, distribute, and use for learning or production with attribution.

