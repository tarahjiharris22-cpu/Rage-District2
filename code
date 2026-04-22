<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rage District</title>

<style>
body {
margin: 0;
font-family: Arial;
background: #0a0a0a;
color: #fff;
}

header {
background: black;
padding: 20px;
text-align: center;
font-size: 30px;
color: #ff1a1a;
}

nav {
display: flex;
justify-content: center;
gap: 20px;
background: #111;
padding: 10px;
}

nav a {
color: white;
text-decoration: none;
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
}

.products {
padding: 40px;
text-align: center;
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
}

.cart {
position: fixed;
right: 0;
top: 0;
width: 250px;
height: 100%;
background: black;
padding: 15px;
overflow-y: auto;
}

.cart h2 {
text-align: center;
}

.cart-item {
margin: 10px 0;
}

.checkout {
width: 100%;
padding: 10px;
background: #ff1a1a;
border: none;
cursor: pointer;
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
<h2>🛒 Cart</h2>
<div id="cartItems"></div>
<h3>Total: $<span id="total">0</span></h3>

<button class="checkout" onclick="checkout()">Checkout</button>
</div>

<script>
let cart = [];
let total = 0;

function addToCart(name, price) {
cart.push({name, price});
total += price;
displayCart();
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

function checkout() {
window.location.href = "https://cash.app/$Trxpstartarahji";
}
</script>

</body>
</html>
