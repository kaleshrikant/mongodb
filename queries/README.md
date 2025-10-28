# MongoDB Queries Learning Path - Complete Guide

## Level 1: Foundation

### Topic 1: Basic CRUD Operations - INSERT
**Problem Statement**: Add new products to an e-commerce inventory system.

**Dummy Data**:
```javascript
// Collection: products
db.products.insertOne({
  name: "Wireless Mouse",
  price: 29.99,
  category: "Electronics",
  stock: 150,
  brand: "TechGear"
});

db.products.insertMany([
  { name: "USB Cable", price: 9.99, category: "Accessories", stock: 500, brand: "ConnectPro" },
  { name: "Laptop Stand", price: 45.00, category: "Accessories", stock: 75, brand: "ErgoDesk" },
  { name: "Bluetooth Speaker", price: 79.99, category: "Electronics", stock: 120, brand: "SoundWave" },
  { name: "Phone Case", price: 15.99, category: "Accessories", stock: 300, brand: "SafeGuard" }
]);
```

**Practice Problems**:
1. Insert a single book product: "The Great Novel", price: $24.99, category: "Books", stock: 200, author: "Jane Doe"
2. Insert 5 clothing items at once with fields: name, price, category, size, color
3. Insert a product with an additional field "releaseDate" set to current date
4. Insert a product with nested object for dimensions (length, width, height)
5. Insert 3 products with an array field for available colors
6. Try inserting a product without the price field (observe MongoDB behavior)
7. Insert a product with _id field manually set to "PROD001"
8. Bulk insert 10 grocery items with fields: name, price, category, expiryDate, organic (boolean)

---

### Topic 2: Basic CRUD Operations - READ (find)
**Problem Statement**: Retrieve products from inventory based on different criteria.

**Dummy Data**: Use products collection from Topic 1

**Practice Problems**:
1. Find all products in the database
2. Find only products in "Electronics" category
3. Find products with price less than $50
4. Find the product with name "Wireless Mouse"
5. Find products where stock is exactly 150
6. Find all products from brand "TechGear"
7. Find products with price equal to $79.99
8. Find the first product in the collection
9. Find products in "Accessories" category with stock greater than 100
10. Find all products and display only the name and price fields
11. Find products but exclude the _id field from results
12. Count how many products are in "Electronics" category
13. Find products where brand is "ConnectPro" or "SafeGuard"
14. Check if any product named "Keyboard" exists
15. Find all unique categories in the products collection

---

### Topic 3: Basic CRUD Operations - UPDATE
**Problem Statement**: Update product information when prices change or stock is replenished.

**Dummy Data**: Use products collection from Topic 1

**Practice Problems**:
1. Update the price of "Wireless Mouse" to $34.99
2. Increase stock of "USB Cable" by 100 units
3. Add a discount field (10% discount) to "Bluetooth Speaker"
4. Update all products in "Accessories" category to have a "onSale" field set to true
5. Change the brand of "Phone Case" to "PremiumGuard"
6. Add a "lastRestocked" field with current date to all products with stock < 100
7. Update multiple fields at once: change price to $12.99 and stock to 600 for "USB Cable"
8. Rename the field "brand" to "manufacturer" for all products
9. Add a rating field (4.5) to products in "Electronics" category
10. Update stock to 0 for products with price greater than $200
11. Add a "warranty" field (2 years) to all products from brand "TechGear"
12. Multiply the price of all products by 1.1 (10% price increase)
13. Add "freeShipping" field set to true for products with price > $50
14. Update the first product found in "Accessories" to have featured: true
15. Set a minimum stock level field (minStock: 50) for all electronics

---

### Topic 4: Basic CRUD Operations - DELETE
**Problem Statement**: Remove discontinued products from inventory.

**Dummy Data**: Use products collection from Topic 1

**Practice Problems**:
1. Delete the product with name "Phone Case"
2. Delete all products with stock equal to 0
3. Delete products from brand "SafeGuard"
4. Delete all products in "Accessories" category with price less than $20
5. Delete the product with the lowest stock level
6. Remove all products that don't have a discount field
7. Delete products with price greater than $1000
8. Delete all products where stock is less than 10
9. Delete one product from "Electronics" category (any one)
10. Delete all products that were added before a specific date
11. Remove products where the brand field doesn't exist
12. Delete all products except those in "Electronics" category
13. Delete products with names starting with "USB"
14. Remove all products and verify collection is empty
15. Delete products where rating is less than 3.0

---

## Level 2: Intermediate Queries

### Topic 5: Query Operators - Comparison
**Problem Statement**: Find products within specific price ranges and stock levels.

**Dummy Data**:
```javascript
// Collection: products (enhanced)
db.products.insertMany([
  { name: "Gaming Keyboard", price: 120.00, category: "Electronics", stock: 45, brand: "GamePro", rating: 4.5 },
  { name: "Office Chair", price: 299.99, category: "Furniture", stock: 20, brand: "ComfortSeat", rating: 4.8 },
  { name: "Desk Lamp", price: 35.50, category: "Furniture", stock: 0, brand: "BrightLight", rating: 4.2 },
  { name: "Webcam", price: 89.99, category: "Electronics", stock: 60, brand: "ClearView", rating: 4.6 },
  { name: "Monitor", price: 250.00, category: "Electronics", stock: 30, brand: "ViewMax", rating: 4.7 }
]);
```

**Practice Problems** ($eq, $ne, $gt, $gte, $lt, $lte, $in, $nin):
1. Find products with price greater than $100
2. Find products with stock less than or equal to 30
3. Find products with rating not equal to 4.5
4. Find products with price greater than or equal to $89.99
5. Find products with stock less than 50
6. Find products where category is in ["Electronics", "Furniture"]
7. Find products where brand is not in ["GamePro", "BrightLight"]
8. Find products with price between $50 and $150 (inclusive)
9. Find products with rating greater than 4.5
10. Find products with stock not equal to 0
11. Find products where price is exactly $299.99
12. Find products with rating between 4.3 and 4.7
13. Find all products NOT in "Accessories" category
14. Find products where stock is in the list [20, 30, 45]
15. Find products with price less than $40 OR greater than $250

---

### Topic 6: Query Operators - Logical
**Problem Statement**: Find products that meet multiple conditions for promotional campaigns.

**Dummy Data**: Use enhanced products collection from Topic 5

**Practice Problems** ($and, $or, $not, $nor):
1. Find products that are Electronics AND have price < $100
2. Find products that are either out of stock OR have rating < 4.3
3. Find products NOT in Furniture category
4. Find products where price > $100 AND stock > 25
5. Find products in Electronics OR Furniture category with rating >= 4.5
6. Find products where brand is GamePro OR rating is greater than 4.7
7. Find products that are NOT (Electronics AND price > $200)
8. Find products where (category is Electronics OR category is Furniture) AND price < $150
9. Find products neither in Electronics category NOR with rating below 4.5
10. Find products where stock is between 20 and 50 AND category is not Furniture
11. Find products where price < $100 OR (stock > 40 AND rating >= 4.5)
12. Find products where brand is NOT GamePro AND price is less than $200
13. Find Electronics with either stock < 50 OR rating > 4.6
14. Find products that satisfy: (price > $200 AND rating > 4.6) OR stock < 30
15. Find products where NOT (stock = 0 OR rating < 4.0)

---

### Topic 7: Array Queries
**Problem Statement**: Manage products with multiple tags, colors, or features.

**Dummy Data**:
```javascript
// Collection: catalog
db.catalog.insertMany([
  {
    name: "Smart Watch",
    price: 199.99,
    tags: ["electronics", "wearable", "fitness"],
    colors: ["black", "silver", "gold"],
    features: ["heart-rate", "gps", "waterproof"]
  },
  {
    name: "Running Shoes",
    price: 89.99,
    tags: ["sports", "footwear", "fitness"],
    colors: ["red", "blue", "white"],
    features: ["cushioned", "breathable", "lightweight"]
  },
  {
    name: "Backpack",
    price: 59.99,
    tags: ["accessories", "travel", "school"],
    colors: ["black", "gray"],
    features: ["waterproof", "laptop-compartment", "usb-port"]
  },
  {
    name: "Water Bottle",
    price: 24.99,
    tags: ["sports", "fitness", "outdoor"],
    colors: ["blue", "green", "pink"],
    features: ["insulated", "leak-proof", "bpa-free"]
  }
]);
```

**Practice Problems** ($all, $elemMatch, $size, $in with arrays):
1. Find products that have the tag "fitness"
2. Find products with ALL tags: ["fitness", "sports"]
3. Find products available in "black" color
4. Find products that have exactly 3 features
5. Find products with exactly 2 colors available
6. Find products where tags include either "electronics" OR "sports"
7. Find products that have "waterproof" in their features array
8. Find products with more than 2 colors available (hint: use $expr and $size)
9. Find products that have both "fitness" and "outdoor" tags
10. Find products where colors array contains "blue"
11. Find products that have ALL colors: ["black", "silver"]
12. Find products with tags array size not equal to 3
13. Find products that have either "gps" or "laptop-compartment" in features
14. Find products where tags contain "electronics" and price > $150
15. Find products that have both "waterproof" feature and price < $100

---

### Topic 8: Projection
**Problem Statement**: Retrieve only specific fields to optimize data transfer.

**Dummy Data**: Use catalog collection from Topic 7

**Practice Problems**:
1. Get only name and price of all products
2. Get all products but exclude the _id field
3. Get name, price, and first color from colors array
4. Get all fields except features array
5. Get only the name field (excluding _id)
6. Project name and the first 2 tags from tags array
7. Get name, price, and count of colors (using $size in projection)
8. Get all products showing only name and whether they have "waterproof" feature
9. Project name and slice the features array to show only first feature
10. Get products with name, price, and a computed field showing if price > $100
11. Exclude both _id and features from results
12. Get only nested fields if you have embedded documents
13. Project name and last element from colors array
14. Show name and number of tags for each product
15. Get all fields but exclude colors and features arrays

---

### Topic 9: Sorting and Limiting
**Problem Statement**: Display top-rated products and implement pagination.

**Dummy Data**: Use enhanced products collection from Topic 5

**Practice Problems**:
1. Sort all products by price in ascending order
2. Sort products by price in descending order
3. Get the 3 most expensive products
4. Get the 5 cheapest products
5. Sort by rating (highest first) and limit to top 5
6. Skip first 2 products and get next 3 (pagination)
7. Sort by stock level (lowest first)
8. Sort by category (alphabetically) then by price (ascending)
9. Get products sorted by rating (descending) and skip first 5
10. Find Electronics, sort by price (descending), limit to 3
11. Sort by brand name alphabetically
12. Get 2nd page of results (assuming 5 items per page)
13. Sort by multiple fields: category ascending, then price descending
14. Get the product with highest rating
15. Get products 6-10 when sorted by price ascending
16. Sort by stock and show only items with stock > 0
17. Implement pagination: page 3 with 4 items per page
18. Sort by price descending and skip the most expensive item
19. Get middle-priced products (skip 2 cheapest and 2 most expensive)
20. Sort by rating, then by price for products with same rating

---

## Level 3: Advanced Queries

### Topic 10: Embedded Documents
**Problem Statement**: Query products with nested specifications and seller information.

**Dummy Data**:
```javascript
// Collection: marketplace
db.marketplace.insertMany([
  {
    name: "Laptop Pro 15",
    price: 1299.99,
    specs: {
      processor: "Intel i7",
      ram: "16GB",
      storage: "512GB SSD",
      screen: "15.6 inch"
    },
    seller: {
      name: "TechStore Inc",
      rating: 4.8,
      location: "New York"
    },
    inStock: true
  },
  {
    name: "Tablet Ultra",
    price: 599.99,
    specs: {
      processor: "A14 Bionic",
      ram: "8GB",
      storage: "256GB",
      screen: "11 inch"
    },
    seller: {
      name: "GadgetHub",
      rating: 4.5,
      location: "California"
    },
    inStock: true
  },
  {
    name: "Budget Phone",
    price: 299.99,
    specs: {
      processor: "Snapdragon 600",
      ram: "4GB",
      storage: "64GB",
      screen: "6.2 inch"
    },
    seller: {
      name: "ValueElectronics",
      rating: 4.2,
      location: "Texas"
    },
    inStock: false
  }
]);
```

**Practice Problems** (Querying nested documents with dot notation):
1. Find products with processor "Intel i7"
2. Find products where seller rating is greater than 4.5
3. Find products sold by seller in "California"
4. Find products with 16GB RAM
5. Find products where seller name is "TechStore Inc"
6. Find in-stock products with seller rating >= 4.6
7. Find products with storage containing "SSD"
8. Find products where seller location is NOT "Texas"
9. Find products with screen size "15.6 inch"
10. Find products where specs.ram is "8GB" AND price < $700
11. Find products with seller rating between 4.3 and 4.7
12. Find all products from sellers rated above 4.4 in stock
13. Update processor to "Intel i9" for products with Intel i7
14. Add a warranty field to seller object for TechStore Inc
15. Find products where nested seller.rating exists and is greater than 4.0

---

### Topic 11: Update Operators
**Problem Statement**: Modify product data using advanced update operations.

**Dummy Data**: Use catalog and marketplace collections from previous topics

**Practice Problems** ($set, $unset, $inc, $push, $pull, $addToSet, $rename):
1. Use $set to update price of "Smart Watch" to $179.99
2. Use $inc to increase stock of a product by 50
3. Use $unset to remove the rating field from a product
4. Use $push to add "wireless" to tags array of Smart Watch
5. Use $pull to remove "gold" from colors array
6. Use $addToSet to add "premium" tag only if it doesn't exist
7. Use $rename to change field "features" to "specifications"
8. Increment price of all electronics by 10 using $inc with multiplier
9. Use $push with $each to add multiple colors at once
10. Use $pull to remove all tags that equal "fitness"
11. Set multiple fields at once using $set: update price and stock
12. Use $inc to decrement stock by 5 for a specific product
13. Remove inStock field from all products using $unset
14. Push a new feature to features array with $position modifier
15. Use $pop to remove first element from tags array
16. Use $pullAll to remove multiple specific colors at once
17. Add seller.verified field set to true using $set with dot notation
18. Use $min to update price only if new value is lower
19. Use $max to update rating only if new value is higher
20. Use $mul to multiply all prices by 0.9 (10% discount)

---

### Topic 12: Aggregation Framework - Basics
**Problem Statement**: Calculate statistics and generate reports from sales data.

**Dummy Data**:
```javascript
// Collection: orders
db.orders.insertMany([
  { orderId: "ORD001", customerId: "C001", product: "Laptop", quantity: 1, price: 1299.99, date: new Date("2024-01-15"), status: "delivered" },
  { orderId: "ORD002", customerId: "C002", product: "Mouse", quantity: 2, price: 29.99, date: new Date("2024-01-16"), status: "delivered" },
  { orderId: "ORD003", customerId: "C001", product: "Keyboard", quantity: 1, price: 120.00, date: new Date("2024-01-17"), status: "shipped" },
  { orderId: "ORD004", customerId: "C003", product: "Monitor", quantity: 2, price: 250.00, date: new Date("2024-01-18"), status: "delivered" },
  { orderId: "ORD005", customerId: "C002", product: "Webcam", quantity: 1, price: 89.99, date: new Date("2024-01-19"), status: "pending" },
  { orderId: "ORD006", customerId: "C004", product: "Mouse", quantity: 3, price: 29.99, date: new Date("2024-01-20"), status: "delivered" },
  { orderId: "ORD007", customerId: "C001", product: "Laptop", quantity: 1, price: 1299.99, date: new Date("2024-02-01"), status: "delivered" }
]);
```

**Practice Problems** ($match, $group, $project, $sort, $limit):
1. Use $match to filter only "delivered" orders
2. Use $group to count total number of orders
3. Use $group to find total revenue (sum of price * quantity)
4. Use $project to create a new field "totalPrice" = price * quantity
5. Use $sort to order results by date descending
6. Use $limit to get top 5 orders
7. Match delivered orders, then count them
8. Group by product and count how many times each was ordered
9. Group by status and calculate total revenue per status
10. Match orders from January 2024, then sort by price
11. Project only orderId, product, and calculated total (price * quantity)
12. Group by customerId and sum their total spending
13. Match orders with quantity > 1, then project with 10% discount
14. Sort by price descending and limit to 3 most expensive orders
15. Group by product, calculate average price per product
16. Match "delivered" status, group by customer, count their orders
17. Project month from date field, group by month, sum revenue
18. Filter orders where price > $100, sort by quantity
19. Group by customer, find their maximum order value
20. Create pipeline: match delivered → group by product → sort by count descending

---

### Topic 13: Aggregation - $group and Accumulators
**Problem Statement**: Calculate totals, averages, and counts for business insights.

**Dummy Data**: Use orders collection from Topic 12

**Practice Problems** ($sum, $avg, $min, $max, $first, $last, $push):
1. Calculate total revenue across all orders (use $sum)
2. Find average order value (price * quantity)
3. Group by product and sum total quantity sold
4. Find minimum and maximum price in orders
5. Group by customer and calculate their average order value
6. Count distinct products ordered using $group
7. Group by status, find highest value order in each status
8. Calculate total quantity of items sold across all orders
9. Group by product, find min and max price for each product
10. Find the first and last order date in the dataset
11. Group by customer, use $push to create array of all their products
12. Calculate average quantity per order
13. Group by month, sum total revenue per month
14. Find product with highest total revenue (group + sort + limit)
15. Group by customer, calculate total items they bought (sum of quantity)
16. Find average price per status category
17. Group by product, count orders and sum revenue for each
18. Calculate standard deviation of prices (use $stdDevPop)
19. Group by customer, find date of their last order
20. Create array of all unique products ordered using $addToSet

---

### Topic 14: Aggregation - $lookup (Joins)
**Problem Statement**: Combine customer and order data for comprehensive reports.

**Dummy Data**:
```javascript
// Collection: customers
db.customers.insertMany([
  { customerId: "C001", name: "John Doe", email: "john@email.com", city: "New York", joinDate: new Date("2023-05-10") },
  { customerId: "C002", name: "Jane Smith", email: "jane@email.com", city: "Los Angeles", joinDate: new Date("2023-06-15") },
  { customerId: "C003", name: "Bob Johnson", email: "bob@email.com", city: "Chicago", joinDate: new Date("2023-07-20") },
  { customerId: "C004", name: "Alice Williams", email: "alice@email.com", city: "Houston", joinDate: new Date("2023-08-05") }
]);

// Use orders collection from Topic 12
```

**Practice Problems** ($lookup, $unwind):
1. Join orders with customers to get customer name with each order
2. Lookup customers and show only orders with customer details
3. Join orders with customers, unwind the results
4. Count total orders per customer using lookup and group
5. Find customers with their total spending (lookup + group + sum)
6. Get customer info along with their most recent order
7. List customers who have never placed an order (use $lookup with empty array check)
8. Join and filter: get orders with customer city = "New York"
9. Calculate average order value per city (lookup + group)
10. Find customers and count of "delivered" orders for each
11. Lookup orders for each customer, project only name and order count
12. Find customers who spent more than $500 total
13. Find customers who spent more than $500 total
14. Join customers with orders and get array of all products they bought
15. Lookup and show customers with order count and total revenue
16. Find the most valuable customer (highest total spending)
17. Get customers from "Los Angeles" with all their order details
18. Calculate average number of items per order for each city
19. Join and find customers who ordered "Laptop"
20. Create a report: customer name, email, total orders, total spent

---

### Topic 15: Aggregation - Advanced Stages
**Problem Statement**: Transform and reshape data for complex analytics.

**Dummy Data**:
```javascript
// Collection: sales
db.sales.insertMany([
  {
    month: "January",
    year: 2024,
    products: [
      { name: "Laptop", sold: 45, revenue: 58500 },
      { name: "Mouse", sold: 230, revenue: 6897 }
    ]
  },
  {
    month: "February",
    year: 2024,
    products: [
      { name: "Laptop", sold: 52, revenue: 67548 },
      { name: "Mouse", sold: 198, revenue: 5934 },
      { name: "Keyboard", sold: 87, revenue: 10440 }
    ]
  },
  {
    month: "March",
    year: 2024,
    products: [
      { name: "Laptop", sold: 48, revenue: 62400 },
      { name: "Mouse", sold: 215, revenue: 6445 },
      { name: "Keyboard", sold: 102, revenue: 12240 }
    ]
  }
]);
```

**Practice Problems** ($unwind, $addFields, $bucket, $facet, $replaceRoot):
1. Use $unwind to deconstruct the products array
2. Unwind products, then group by product name to get total sold
3. Use $addFields to add a computed field "avgPricePerUnit" = revenue/sold
4. After unwinding, calculate total revenue per product across all months
5. Use $bucket to group products by revenue ranges (0-10000, 10000-50000, 50000+)
6. Create a facet with two pipelines: one for totals, one for averages
7. Unwind, then use $replaceRoot to promote product subdocument to root
8. Add a field calculating month number from month name
9. Use $bucket to categorize sales by sold quantity ranges
10. Facet: separate pipelines for Laptop stats and Mouse stats
11. Unwind products, add field for profit margin (assume 30% margin)
12. Group by month after unwinding, sum total revenue per month
13. Use $bucketAuto to automatically create 3 buckets based on revenue
14. Add field to calculate year-month combination
15. Unwind, sort by revenue, limit to top 5 product-months
16. Use $facet to get both monthly summaries and product summaries
17. Add field calculating percentage of total monthly revenue per product
18. Unwind and filter products with sold > 100
19. Use $sortByCount after unwinding to count documents per product name
20. Complex: unwind → addFields → group → sort → limit pipeline

---

## Level 4: Expert Queries

### Topic 16: Text Search
**Problem Statement**: Implement full-text search for product descriptions.

**Dummy Data**:
```javascript
// Collection: productCatalog
// First create text index: db.productCatalog.createIndex({ name: "text", description: "text" })

db.productCatalog.insertMany([
  {
    name: "Premium Wireless Headphones",
    description: "High-quality noise cancelling headphones with superior sound quality and long battery life. Perfect for music lovers and professionals.",
    price: 199.99,
    category: "Audio"
  },
  {
    name: "Portable Bluetooth Speaker",
    description: "Compact waterproof speaker with amazing bass and 12-hour battery. Great for outdoor activities and parties.",
    price: 79.99,
    category: "Audio"
  },
  {
    name: "Gaming Headset",
    description: "Professional gaming headphones with surround sound and crystal clear microphone. Ideal for gamers and streamers.",
    price: 149.99,
    category: "Gaming"
  },
  {
    name: "Wireless Earbuds",
    description: "Compact true wireless earbuds with noise cancellation and premium sound. Perfect for workouts and commuting.",
    price: 129.99,
    category: "Audio"
  },
  {
    name: "Studio Monitor Speakers",
    description: "Professional studio quality speakers for music production and audio editing. Crystal clear sound reproduction.",
    price: 399.99,
    category: "Professional"
  }
]);
```

**Practice Problems** ($text, $search, text scores, $meta):
1. Search for products containing "wireless"
2. Search for products with "noise cancelling" or "noise cancellation"
3. Search for "gaming" and sort by text relevance score
4. Search for "speaker" and project the text score
5. Search for products mentioning "battery" in description
6. Search for "professional" and filter results with price < $200
7. Perform case-insensitive search for "HEADPHONES"
8. Search for "premium sound" phrase
9. Search for "waterproof" and sort by price
10. Use text search with negation: search "audio" but exclude "wireless"
11. Search multiple terms: "gaming professional"
12. Get top 3 most relevant results for "music quality"
13. Search and project only name, price, and relevance score
14. Search for "outdoor" and filter by category = "Audio"
15. Combine text search with regular query: search "headphones" where price > $150

---

### Topic 17: Geospatial Queries
**Problem Statement**: Find stores or delivery locations near customer addresses.

**Dummy Data**:
```javascript
// Collection: stores
// First create 2dsphere index: db.stores.createIndex({ location: "2dsphere" })

db.stores.insertMany([
  {
    name: "Downtown Store",
    location: { type: "Point", coordinates: [-73.985428, 40.748817] }, // NYC Times Square
    type: "retail",
    inventory: 500
  },
  {
    name: "Uptown Branch",
    location: { type: "Point", coordinates: [-73.968285, 40.785091] }, // NYC Upper West
    type: "retail",
    inventory: 300
  },
  {
    name: "Warehouse Center",
    location: { type: "Point", coordinates: [-74.005941, 40.712784] }, // Manhattan Downtown
    type: "warehouse",
    inventory: 5000
  },
  {
    name: "Brooklyn Store",
    location: { type: "Point", coordinates: [-73.950270, 40.650002] }, // Brooklyn
    type: "retail",
    inventory: 400
  },
  {
    name: "Queens Branch",
    location: { type: "Point", coordinates: [-73.794327, 40.722620] }, // Queens
    type: "retail",
    inventory: 350
  }
]);

// Collection: customers with locations
db.customersGeo.insertMany([
  { name: "Alice", location: { type: "Point", coordinates: [-73.985, 40.758] } }, // Near Times Square
  { name: "Bob", location: { type: "Point", coordinates: [-73.960, 40.800] } }, // Upper Manhattan
  { name: "Carol", location: { type: "Point", coordinates: [-73.945, 40.650] } }  // Brooklyn
]);
```

**Practice Problems** ($near, $geoWithin, $geoNear, $centerSphere):
1. Find stores within 5km of coordinates [-73.985428, 40.748817]
2. Find nearest 3 stores to a given location using $near
3. Find stores within 10km radius of Times Square
4. Use $geoNear aggregation to find stores with distance from a point
5. Find all retail stores within 3km of coordinates [-73.968285, 40.785091]
6. Find stores within a circular region using $centerSphere
7. Get stores sorted by distance from Brooklyn coordinates
8. Find warehouses within 15km of downtown Manhattan
9. Use $geoNear and project distance in kilometers
10. Find closest store for each customer (requires $geoNear in aggregation)
11. Find stores within a polygon area (define polygon coordinates)
12. Get stores within 2km and filter by inventory > 400
13. Find all locations within 8km and sort by inventory
14. Use $geoWithin with $center to find stores in a circular area
15. Calculate distance from customer to nearest store using aggregation
16. Find stores between 5km and 10km from a point (use $minDistance and $maxDistance)
17. Get 2 nearest retail stores excluding warehouses
18. Find stores within specific bounds (box query with $geoWithin and $box)
19. Use $geoNear in aggregation with match stage for type = "retail"
20. Calculate average distance to all stores from a central point

---

### Topic 18: Indexes and Performance
**Problem Statement**: Optimize query performance for large datasets.

**Dummy Data**:
```javascript
// Generate larger dataset for testing
// Collection: products_large
var products = [];
for (var i = 1; i <= 10000; i++) {
  products.push({
    productId: "PROD" + i,
    name: "Product " + i,
    category: ["Electronics", "Clothing", "Books", "Home", "Sports"][i % 5],
    price: Math.random() * 1000,
    stock: Math.floor(Math.random() * 500),
    brand: ["BrandA", "BrandB", "BrandC", "BrandD"][i % 4],
    rating: 1 + Math.random() * 4,
    tags: ["tag1", "tag2", "tag3", "tag4"].slice(0, Math.floor(Math.random() * 4) + 1)
  });
}
db.products_large.insertMany(products);
```

**Practice Problems**:
1. Create a single field index on "category"
2. Create a compound index on category and price
3. Analyze query performance using .explain("executionStats")
4. Create an index on price in descending order
5. Create a multikey index on tags array
6. Compare query performance before and after creating index
7. Create a compound index on brand, category, and price
8. Use .explain() to check if index is being used
9. Create a sparse index on optional field
10. Create partial index for products with price > 100
11. Create TTL index for documents with expiration date
12. Analyze index usage with db.collection.stats()
13. Create unique index on productId
14. Drop an unused index to save space
15. Create text index for full-text search on name and description
16. Use hint() to force MongoDB to use specific index
17. Create background index to avoid blocking writes
18. Check index size using db.collection.totalIndexSize()
19. Create compound index and test sort performance
20. Identify slow queries using profiler and create appropriate indexes

---

### Topic 19: Transactions
**Problem Statement**: Ensure data consistency when transferring inventory between warehouses.

**Dummy Data**:
```javascript
// Collection: inventory
db.inventory.insertMany([
  { warehouseId: "WH001", product: "Laptop", quantity: 50, location: "New York" },
  { warehouseId: "WH002", product: "Laptop", quantity: 30, location: "California" },
  { warehouseId: "WH001", product: "Mouse", quantity: 200, location: "New York" },
  { warehouseId: "WH002", product: "Mouse", quantity: 150, location: "California" },
  { warehouseId: "WH003", product: "Keyboard", quantity: 75, location: "Texas" }
]);

// Collection: transferLog
db.transferLog.insertMany([
  { transferId: "T001", from: "WH001", to: "WH002", product: "Laptop", quantity: 10, date: new Date("2024-01-15"), status: "completed" }
]);
```

**Practice Problems** (Multi-document transactions):
1. Transfer 10 Laptops from WH001 to WH002 (update both in transaction)
2. Transfer inventory and log the transaction in transferLog collection
3. Implement rollback if source warehouse has insufficient quantity
4. Transfer multiple products in single transaction
5. Update inventory and create audit log entry atomically
6. Handle transaction abort when warehouse doesn't exist
7. Transfer with validation: check quantity > 0 before transfer
8. Implement transaction with session and commit/abort
9. Create order and update inventory in same transaction
10. Transfer inventory and update last_modified timestamp atomically
11. Rollback transaction if target warehouse capacity exceeded
12. Multi-step transaction: deduct from source, add to target, log transfer
13. Transaction with read concern "snapshot"
14. Implement retry logic for transaction conflicts
15. Transfer between 3 warehouses in single transaction

---

### Topic 20: Complex Real-World Scenarios
**Problem Statement**: Build a complete e-commerce analytics system.

**Dummy Data**:
```javascript
// Collection: users
db.users.insertMany([
  { userId: "U001", name: "Emma Wilson", email: "emma@email.com", registeredDate: new Date("2023-01-15"), preferences: ["electronics", "books"], city: "New York", loyaltyPoints: 450 },
  { userId: "U002", name: "Michael Brown", email: "michael@email.com", registeredDate: new Date("2023-03-20"), preferences: ["sports", "outdoor"], city: "Los Angeles", loyaltyPoints: 230 },
  { userId: "U003", name: "Sarah Davis", email: "sarah@email.com", registeredDate: new Date("2023-06-10"), preferences: ["fashion", "beauty"], city: "Chicago", loyaltyPoints: 180 },
  { userId: "U004", name: "James Miller", email: "james@email.com", registeredDate: new Date("2023-08-22"), preferences: ["electronics", "gaming"], city: "Houston", loyaltyPoints: 520 }
]);

// Collection: products (comprehensive)
db.products.insertMany([
  {
    productId: "P001",
    name: "Laptop Pro",
    category: "electronics",
    price: 1299.99,
    cost: 900,
    reviews: [
      { userId: "U001", rating: 5, comment: "Excellent performance", date: new Date("2024-01-20"), helpful: 15 },
      { userId: "U002", rating: 4, comment: "Good value", date: new Date("2024-01-25"), helpful: 8 }
    ],
    tags: ["computer", "work", "gaming"],
    stock: 45,
    supplier: "TechCorp"
  },
  {
    productId: "P002",
    name: "Running Shoes",
    category: "sports",
    price: 89.99,
    cost: 45,
    reviews: [
      { userId: "U002", rating: 5, comment: "Very comfortable", date: new Date("2024-02-01"), helpful: 12 }
    ],
    tags: ["fitness", "running", "outdoor"],
    stock: 120,
    supplier: "SportStyle"
  },
  {
    productId: "P003",
    name: "Wireless Mouse",
    category: "electronics",
    price: 29.99,
    cost: 15,
    reviews: [
      { userId: "U001", rating: 4, comment: "Works great", date: new Date("2024-01-28"), helpful: 5 },
      { userId: "U004", rating: 5, comment: "Perfect for gaming", date: new Date("2024-02-10"), helpful: 10 }
    ],
    tags: ["computer", "wireless", "gaming"],
    stock: 200,
    supplier: "TechCorp"
  },
  {
    productId: "P004",
    name: "Yoga Mat",
    category: "sports",
    price: 34.99,
    cost: 12,
    reviews: [],
    tags: ["fitness", "yoga", "exercise"],
    stock: 85,
    supplier: "FitGear"
  }
]);

// Collection: orderHistory
db.orderHistory.insertMany([
  {
    orderId: "O001",
    userId: "U001",
    items: [
      { productId: "P001", quantity: 1, price: 1299.99 }
    ],
    total: 1299.99,
    orderDate: new Date("2024-01-21"),
    status: "delivered",
    deliveryDate: new Date("2024-01-25"),
    paymentMethod: "credit_card",
    shippingAddress: { city: "New York", state: "NY", zipCode: "10001" }
  },
  {
    orderId: "O002",
    userId: "U002",
    items: [
      { productId: "P002", quantity: 2, price: 89.99 }
    ],
    total: 179.98,
    orderDate: new Date("2024-02-02"),
    status: "delivered",
    deliveryDate: new Date("2024-02-06"),
    paymentMethod: "paypal",
    shippingAddress: { city: "Los Angeles", state: "CA", zipCode: "90001" }
  },
  {
    orderId: "O003",
    userId: "U001",
    items: [
      { productId: "P003", quantity: 1, price: 29.99 },
      { productId: "P004", quantity: 1, price: 34.99 }
    ],
    total: 64.98,
    orderDate: new Date("2024-02-15"),
    status: "shipped",
    paymentMethod: "credit_card",
    shippingAddress: { city: "New York", state: "NY", zipCode: "10001" }
  },
  {
    orderId: "O004",
    userId: "U004",
    items: [
      { productId: "P003", quantity: 2, price: 29.99 }
    ],
    total: 59.98,
    orderDate: new Date("2024-02-18"),
    status: "delivered",
    deliveryDate: new Date("2024-02-22"),
    paymentMethod: "debit_card",
    shippingAddress: { city: "Houston", state: "TX", zipCode: "77001" }
  },
  {
    orderId: "O005",
    userId: "U002",
    items: [
      { productId: "P001", quantity: 1, price: 1299.99 }
    ],
    total: 1299.99,
    orderDate: new Date("2024-03-01"),
    status: "pending",
    paymentMethod: "paypal",
    shippingAddress: { city: "Los Angeles", state: "CA", zipCode: "90001" }
  }
]);
```

**Complex Practice Problems**:

**Customer Analytics:**
1. Calculate customer lifetime value (total spent per customer)
2. Find customers who haven't ordered in last 30 days
3. Segment customers by spending tiers (<$100, $100-$500, >$500)
4. Calculate average order value per customer
5. Find top 10 customers by loyalty points and total spending

**Product Analytics:**
6. Calculate profit margin for each product (price - cost)
7. Find products with average rating > 4.5 and > 5 reviews
8. Calculate inventory turnover ratio (orders/stock)
9. Find products frequently bought together (co-occurrence analysis)
10. Identify slow-moving products (low orders, high stock)

**Sales Analytics:**
11. Calculate month-over-month revenue growth
12. Find best-selling products by quantity and revenue
13. Calculate conversion rate by category
14. Analyze sales by payment method
15. Find peak ordering hours/days using date functions

**Advanced Joins:**
16. Join users + orders + products for complete order history report
17. Calculate average review rating per product category
18. Find users who reviewed products they purchased
19. Create customer profile: name, total orders, favorite category, total spent
20. Generate supplier report: products supplied, total revenue, average rating

**Recommendation Engine:**
21. Recommend products based on user preferences and order history
22. Find similar users based on purchase patterns
23. Suggest products based on high ratings in user's favorite category
24. Identify trending products (high recent orders)
25. Build "customers also bought" recommendations

**Business Intelligence:**
26. Create daily sales dashboard (orders, revenue, average order value)
27. Calculate customer retention rate month-over-month
28. Find products with declining sales trend
29. Analyze geographical sales distribution
30. Calculate ROI per product (revenue vs cost)

---

## Practice Exercises by Level

### Beginner Exercises (Topics 1-4)
1. Find all electronics products under $100
2. Update stock for products when orders are placed
3. Delete products with zero ratings
4. Count total products by category
5. Insert 20 products with various categories
6. Find products and sort by price ascending
7. Update all products to add a createdDate field
8. Delete discontinued products (stock = 0 and no recent orders)

### Intermediate Exercises (Topics 5-9)
1. Find products with at least 2 specific tags
2. Get top 10 highest-rated products
3. Calculate average price per category
4. Find customers who ordered more than 3 times
5. Implement pagination for product listing (page size: 20)
6. Find products matching multiple criteria (price range, category, rating)
7. Project only necessary fields to optimize query performance
8. Sort products by multiple criteria (rating desc, price asc)

### Advanced Exercises (Topics 10-15)
1. Join orders with customers and products for full order details
2. Calculate month-over-month revenue growth
3. Find products frequently bought together
4. Implement geo-based store finder
5. Build recommendation engine using aggregation
6. Use $unwind and $group to analyze array data
7. Create complex aggregation pipeline with 5+ stages
8. Calculate running totals and moving averages

### Expert Exercises (Topics 16-20)
1. Optimize slow queries using indexes and explain plans
2. Implement inventory transfer with transactions
3. Build real-time analytics dashboard pipeline
4. Create text search with relevance scoring
5. Design schema for high-performance multi-tenant application
6. Implement full-text search with filters and facets
7. Build geospatial query for delivery radius calculation
8. Create comprehensive e-commerce reporting system

---

## Learning Tips

1. **Start Small**: Begin with simple CRUD operations before moving to aggregations
2. **Practice Daily**: Work through 2-3 topics each day
3. **Use MongoDB Compass**: Visualize your queries and results
4. **Read Documentation**: Official MongoDB docs are excellent resources
5. **Build Projects**: Apply learning by building a complete application
6. **Optimize**: Always consider performance and indexing strategies
7. **Test Edge Cases**: Try queries with empty results, null values, missing fields
8. **Use Explain**: Analyze query execution plans to understand performance
9. **Experiment**: Try different approaches to solve the same problem
10. **Document**: Comment your complex queries for future reference

---

## Recommended Practice Sequence

**Week 1: Foundation** (Topics 1-5)
- Day 1-2: Topics 1-2 (INSERT, READ)
- Day 3-4: Topics 3-4 (UPDATE, DELETE)
- Day 5-7: Topic 5 (Comparison Operators) + Review

**Week 2: Intermediate Queries** (Topics 6-10)
- Day 1-2: Topics 6-7 (Logical Operators, Arrays)
- Day 3-4: Topics 8-9 (Projection, Sorting/Limiting)
- Day 5-7: Topic 10 (Embedded Documents) + Review

**Week 3: Aggregation Framework** (Topics 11-15)
- Day 1-2: Topics 11-12 (Update Operators, Basic Aggregation)
- Day 3-4: Topics 13-14 ($group, $lookup)
- Day 5-7: Topic 15 (Advanced Stages) + Review

**Week 4: Advanced & Expert** (Topics 16-20)
- Day 1-2: Topics 16-17 (Text Search, Geospatial)
- Day 3-4: Topics 18-19 (Indexes, Transactions)
- Day 5-7: Topic 20 (Complex Scenarios) + Final Review

---

## Additional Resources

**Official MongoDB Documentation:**
- MongoDB Manual: https://docs.mongodb.com/manual/
- Aggregation Pipeline: https://docs.mongodb.com/manual/aggregation/
- Query Operators: https://docs.mongodb.com/manual/reference/operator/query/

**Practice Platforms:**
- MongoDB University (Free Courses)
- MongoDB Atlas (Free Cloud Database)
- MongoDB Compass (GUI Tool)

**Sample Query Templates:**

```javascript
// Basic Find
db.collection.find({ field: value })

// Aggregation Pipeline
db.collection.aggregate([
  { $match: { field: value } },
  { $group: { _id: "$field", total: { $sum: 1 } } },
  { $sort: { total: -1 } },
  { $limit: 10 }
])

// Update with Operators
db.collection.updateMany(
  { filter },
  { $set: { field: value }, $inc: { count: 1 } }
)

// Index Creation
db.collection.createIndex({ field1: 1, field2: -1 })

// Transaction Example
const session = db.getMongo().startSession();
session.startTransaction();
try {
  db.collection1.updateOne({ _id: 1 }, { $inc: { qty: -1 } }, { session });
  db.collection2.insertOne({ item: "X" }, { session });
  session.commitTransaction();
} catch (error) {
  session.abortTransaction();
}
session.endSession();
```

---

## Troubleshooting Common Issues

1. **Query returns too many documents**: Add limit() or use more specific filters
2. **Slow queries**: Create appropriate indexes and use explain()
3. **Aggregation memory errors**: Use allowDiskUse: true for large datasets
4. **Array query issues**: Remember to use proper array operators ($elemMatch, $all)
5. **Embedded document queries**: Use dot notation correctly
6. **Index not being used**: Check query shape matches index definition
7. **Transaction failures**: Ensure replica set is configured properly
8. **Text search not working**: Create text index first

---

## Final Project Ideas

1. **E-commerce Platform**: Product catalog, orders, customers, inventory management
2. **Social Media Analytics**: Posts, users, comments, likes, trending topics
3. **Food Delivery System**: Restaurants, menus, orders, delivery tracking
4. **Library Management**: Books, members, checkouts, reservations
5. **Fitness Tracking App**: Users, workouts, goals, progress tracking
6. **Real Estate Platform**: Properties, agents, inquiries, transactions
7. **Blog Platform**: Posts, authors, comments, tags, categories
8. **Task Management System**: Projects, tasks, users, deadlines, priorities

---

**Good luck with your MongoDB learning journey! 🚀**

*Remember: The key to mastering MongoDB is consistent practice. Work through these problems daily, experiment with your own variations, and don't hesitate to explore the official documentation.*
