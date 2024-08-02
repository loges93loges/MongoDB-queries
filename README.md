# MongoDB-queries

// Connect to your database (if not already connected)
// Use the appropriate database
use yourDatabaseName;

// Find all the information about each product
db.products.find({}).forEach(printjson);

// Find the product prices which are between 400 and 800
print("Products with price between 400 and 800:");
db.products.find({ product_price: { $gte: 400, $lte: 800 } }).forEach(printjson);

// Find the product prices which are not between 400 and 600
print("Products with price not between 400 and 600:");
db.products.find({ product_price: { $lt: 400, $gt: 600 } }).forEach(printjson);

// List the four products which are greater than 500 in price
print("Four products with price greater than 500:");
db.products.find({ product_price: { $gt: 500 } }).limit(4).forEach(printjson);

// Find the product name and product material of each product
print("Product names and materials:");
db.products.find({}, { _id: 0, product_name: 1, product_material: 1 }).forEach(printjson);

// Find the product with a row id of 10
print("Product with id 10:");
db.products.find({ id: "10" }).forEach(printjson);

// Find only the product name and product material
print("Product names and materials:");
db.products.find({}, { _id: 0, product_name: 1, product_material: 1 }).forEach(printjson);

// Find all products which contain the value of "Soft" in product material
print("Products with 'Soft' in material:");
db.products.find({ product_material: "Soft" }).forEach(printjson);

// Find products which contain product color "indigo" and product price 492.00
print("Products with color 'indigo' and price 492.00:");
db.products.find({ product_color: "indigo", product_price: 492.00 }).forEach(printjson);

// Delete the products which have a product price value of 28
print("Deleting products with price 28:");
db.products.deleteMany({ product_price: 28 });
