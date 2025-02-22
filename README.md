# Flipkart Bye Project

This is a clone of the Flipkart website created using HTML and CSS. 

The project is still in progress and JavaScript will be added later.

## [// E-Commerce Website (Basic Flipkart Clone)
// Tech Stack: React (Frontend) + Node.js (Backend) + MongoDB (Database)

// Step 1: Setup Express Server (Backend)
const express = require("express");
const mongoose = require("mongoose");
const cors = require("cors");
const app = express();
const port = 5000;

app.use(express.json());
app.use(cors());

// Connect to MongoDB
mongoose.connect("mongodb://localhost:27017/ecommerce", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const ProductSchema = new mongoose.Schema({
  name: String,
  price: Number,
  category: String,
  image: String,
});
const Product = mongoose.model("Product", ProductSchema);

// API Endpoints
app.get("/products", async (req, res) => {
  const products = await Product.find();
  res.json(products);
});

app.post("/products", async (req, res) => {
  const newProduct = new Product(req.body);
  await newProduct.save();
  res.json(newProduct);
});

// YouTube Channel Link Endpoint
app.get("/youtube", (req, res) => {
  res.json({ link: "https://www.youtube.com/@UltimateGaming-l5u" });
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});

// Step 2: Setup React Frontend (Basic UI with Product Listing)
// Create React App and use Axios to fetch data

// Frontend (React) Code
const React = require("react");
const axios = require("axios");

const HomePage = () => {
  const [products, setProducts] = React.useState([]);

  React.useEffect(() => {
    axios.get("http://localhost:5000/products").then((response) => {
      setProducts(response.data);
    });
  }, []);

  return (
    <div>
      <h1>Welcome to Our E-Commerce Store</h1>
      <a href="https://www.youtube.com/@UltimateGaming-l5u" target="_blank" rel="noopener noreferrer">
        Subscribe to Our YouTube Channel
      </a>
      <h2>Products</h2>
      <ul>
        {products.map((product) => (
          <li key={product._id}>{product.name} - ${product.price}</li>
        ))}
      </ul>
    </div>
  );
};

module.exports = HomePage;
/)

## Note : 
If you are opening the site in mobile phone, Please open in Desktop Mode

## Preview Images:

![preview-img](https://github.com/AmanKumarSinhaGitHub/Flipkart-Clone/assets/65329366/7f7137a9-df36-45eb-a39b-8ff6efd64d7c)


## Contributing

Contributions are welcome! Please feel free to submit a pull request.
