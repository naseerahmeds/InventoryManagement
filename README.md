# InventoryManagement



# Screenshot

![image](https://github.com/user-attachments/assets/b17a81a1-e0fb-40b5-85c7-100d32c2b23c)


# MySQL

-- Database: inventory_app
CREATE DATABASE inventory_app;
USE inventory_app;

-- Table: locations
CREATE TABLE IF NOT EXISTS locations (
    id INT AUTO_INCREMENT PRIMARY KEY,
    location_id VARCHAR(50) NOT NULL UNIQUE,
    name VARCHAR(100) NOT NULL
);

-- Table: products
CREATE TABLE IF NOT EXISTS products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id VARCHAR(50) NOT NULL UNIQUE,
    name VARCHAR(100) NOT NULL,
    quantity INT NOT NULL DEFAULT 0
);

-- Table: product_movements
CREATE TABLE IF NOT EXISTS product_movements (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT NOT NULL,
    from_location_id INT DEFAULT NULL,
    to_location_id INT DEFAULT NULL,
    quantity INT NOT NULL,
    movement_type ENUM('import', 'export', 'transfer') NOT NULL,
    movement_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES products(id) ON DELETE CASCADE,
    FOREIGN KEY (from_location_id) REFERENCES locations(id) ON DELETE SET NULL,
    FOREIGN KEY (to_location_id) REFERENCES locations(id) ON DELETE SET NULL
);


# Libraries

pip install mysql-connector-python
pip install Flask

