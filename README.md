/workeinstyle
│── index.html (Homepage)
│── products.html (Product Page)
│── cart.html (Shopping Cart)
│── styles.css (Styling)
│── script.js (JavaScript for cart functionality)
└── images/ (Folder for product images)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>workeinstyle - Home</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to workeinstyle</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="products.html">Shop</a>
            <a href="cart.html">Cart</a>
        </nav>
    </header>
    
    <section class="hero">
        <h2>Discover Elegant Indian Footwear</h2>
        <a href="products.html" class="btn">Shop Now</a>
    </section>
    
    <footer>
        <p>&copy; 2025 workeinstyle</p>
    </footer>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Products - workeinstyle</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Our Collection</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="products.html">Shop</a>
            <a href="cart.html">Cart</a>
        </nav>
    </header>

    <section class="products">
        <div class="product">
            <img src="images/shoe1.jpg" alt="Classic Jutti">
            <h3>Classic Jutti</h3>
            <p>₹1200</p>
            <button onclick="addToCart('Classic Jutti', 1200)">Add to Cart</button>
        </div>
        <div class="product">
            <img src="images/shoe2.jpg" alt="Embroidered Mojari">
            <h3>Embroidered Mojari</h3>
            <p>₹1500</p>
            <button onclick="addToCart('Embroidered Mojari', 1500)">Add to Cart</button>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 workeinstyle</p>
    </footer>
    
    <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cart - workeinstyle</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Your Cart</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="products.html">Shop</a>
            <a href="cart.html">Cart</a>
        </nav>
    </header>

    <section id="cart-items">
        <p>Your cart is empty.</p>
    </section>
    
    <button onclick="checkout()">Proceed to Payment</button>

    <footer>
        <p>&copy; 2025 workeinstyle</p>
    </footer>
    
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    text-align: center;
}

header {
    background: #ff6600;
    padding: 15px;
    color: white;
}

nav a {
    color: white;
    margin: 0 10px;
    text-decoration: none;
    font-weight: bold;
}

.hero {
    padding: 50px;
    background: url('images/banner.jpg') no-repeat center center/cover;
    color: white;
}

.products {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.product {
    border: 1px solid #ddd;
    margin: 10px;
    padding: 10px;
    width: 200px;
    background: white;
}

.product img {
    width: 100%;
}

button {
    background: #ff6600;
    color: white;
    padding: 10px;
    border: none;
    cursor: pointer;
}
let cart = [];

function addToCart(productName, price) {
    cart.push({ name: productName, price: price });
    alert(productName + " added to cart!");
    localStorage.setItem("cart", JSON.stringify(cart));
}

function loadCart() {
    let cartItems = document.getElementById("cart-items");
    let storedCart = JSON.parse(localStorage.getItem("cart"));

    if (storedCart && storedCart.length > 0) {
        cart = storedCart;
        cartItems.innerHTML = "";
        cart.forEach(item => {
            let itemElement = document.createElement("p");
            itemElement.textContent = `${item.name} - ₹${item.price}`;
            cartItems.appendChild(itemElement);
        });
    }
}

function checkout() {
    alert("Proceeding to payment...");
    localStorage.removeItem("cart");
    window.location.href = "payment.html";
}

if (window.location.pathname.includes("cart.html")) {
    loadCart();
}
