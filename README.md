<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rage District</title>

<style>
body {
margin: 0;
font-family: Arial, sans-serif;
background: #0a0a0a;
color: #fff;
}

header {
background: black;
padding: 20px;
text-align: center;
font-size: 30px;
color: #ff1a1a;
font-weight: bold;
letter-spacing: 2px;
}

nav {
display: flex;
justify-content: center;
gap: 20px;
background: #111;
padding: 10px;
border-bottom: 1px solid #333;
}

nav a {
color: white;
text-decoration: none;
text-transform: uppercase;
font-size: 14px;
}

.hero {
text-align: center;
padding: 100px 20px;
}

.btn {
background: #ff1a1a;
padding: 10px 20px;
color: black;
cursor: pointer;
border: none;
margin-top: 10px;
font-weight: bold;
}

.products {
padding: 40px;
text-align: center;
margin-right: 300px; /* Make room for the fixed cart */
}

.grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
gap: 20px;
}

.product {
background: #1a1a1a;
padding: 15px;
border-radius: 10px;
border: 1px solid #222;
}

/* CART STYLES */
.cart {
position: fixed;
right: 0;
top: 0;
width: 300px;
height: 100%;
background: black;
padding: 20px;
overflow-y: auto;
border-left: 2px solid #ff1a1a;
box-sizing: border-box;
}

.cart h2 { text-align: center; color: #ff1a1a; }

.cart-item {
margin: 10px 0;
font-size: 14px;
border-bottom: 1px solid #222;
padding-bottom: 5px;
}

/* FORM STYLES */
.checkout-section {
display: none; /* Hidden until items are added */
margin-top: 20px;
}

label {
display: block;
font-size: 10px;
color: #ff1a1a;
margin-top: 10px;
text-transform: uppercase;
}

input {
width: 100%;
padding: 10px;
margin-top: 5px;
background: #111;
border: 1px solid #333;
color: white;
box-sizing: border-box;
border-radius: 4px;
}

input:focus { border-color: #ff1a1a; outline: none; }

.row { display: flex; gap: 5px; }

.checkout-btn {
width: 100%;
padding: 15px;
background: #ff1a1a;
border: none;
cursor: pointer;
font-weight: bold;
margin-top: 20px;
text-transform: uppercase;
}

.checkout-btn:hover { background: white; }

@media (max-width: 768px) {
.products { margin-right: 0; margin-bottom: 400px; }
.cart { position: relative; width: 100%; height: auto; border-left: none; border-top: 2px solid #ff1a1a; }
}
</style>
</head>

<body>

<header>RAGE DISTRICT</header>

<nav>
<a href="#">Home</a>
<a href="#shop">Shop</a>
</nav>

<section class="hero">
<h1>Streetwear Built From Chaos</h1>
<p>Rage District Collection</p>
</section>

<section class="products" id="shop">
<h2>Shop</h2>
<div class="grid">
<div class="product">
<h3>Graphic Shirt</h3>
<p>$30</p>
<button class="btn" onclick="addToCart('Graphic Shirt', 30)">Add to Cart</button>
</div>
<div class="product">
<h3>Zip-Up Jacket</h3>
<p>$70</p>
<button class="btn" onclick="addToCart('Zip-Up Jacket', 70)">Add to Cart</button>
</div>
<div class="product">
<h3>Jorts</h3>
<p>$45</p>
<button class="btn" onclick="addToCart('Jorts', 45)">Add to Cart</button>
</div>
<div class="product">
<h3>Street Pants</h3>
<p>$60</p>
<button class="btn" onclick="addToCart('Street Pants', 60)">Add to Cart</button>
</div>
</div>
</section>

<div class="cart">
<h2>🛒 CART</h2>
<div id="cartItems"></div>
<h3 style="text-align: right;">Total: $<span id="total">0</span></h3>

<div id="checkoutSection" class="checkout-section">
<hr style="border: 1px solid #222;">

<label>Full Name</label>
<input type="text" id="name" placeholder="John Doe">

<label>Shipping Address</label>
<input type="text" id="address" placeholder="123 Rage St">
<div class="row">
<input type="text" id="city" placeholder="City">
<input type="text" id="zip" placeholder="Zip">
</div>

<label>Card Information</label>
<input type="tel" id="card" placeholder="0000 0000 0000 0000" maxlength="16">
<div class="row">
<input type="tel" id="exp" placeholder="MM/YY" maxlength="5">
<input type="password" id="cvv" placeholder="CVV" maxlength="3">
</div>

<button class="checkout-btn" onclick="processOrder()">Complete Purchase</button>
</div>
</div>

<script>
let cart = [];
let total = 0;

function addToCart(name, price) {
cart.push({name, price});
total += price;
displayCart();
// Show the checkout form once something is in the cart
document.getElementById("checkoutSection").style.display = "block";
}

function displayCart() {
let cartItems = document.getElementById("cartItems");
cartItems.innerHTML = "";

cart.forEach(item => {
let div = document.createElement("div");
div.classList.add("cart-item");
div.innerText = item.name + " - $" + item.price;
cartItems.appendChild(div);
});

document.getElementById("total").innerText = total;
}

function processOrder() {
const name = document.getElementById("name").value;
const address = document.getElementById("address").value;
const card = document.getElementById("card").value;

if (!name || !address || card.length < 16) {
alert("Please fill out all shipping and payment info correctly.");
return;
}

// This is where you would normally send data to a server.
// For now, we simulate success:
alert("Thank you, " + name + "! Order placed successfully.");

// Clear cart and reset
cart = [];
total = 0;
displayCart();
document.getElementById("checkoutSection").style.display = "none";

// Redirect to your Cash App or a thank you page if desired
// window.location.href = "https://cash.app/$Trxpstartarahji";
}
</script>

</body>
</html>
