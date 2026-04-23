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

.products {
padding: 40px;
text-align: center;
}

.grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
gap: 20px;
}

.product {
background: #1a1a1a;
padding: 15px;
border-radius: 10px;
}

select, input {
margin-top: 5px;
padding: 5px;
width: 90%;
}

button {
margin-top: 10px;
padding: 10px;
background: #ff1a1a;
border: none;
cursor: pointer;
}

.cart {
position: fixed;
right: 0;
top: 0;
width: 300px;
height: 100%;
background: black;
padding: 15px;
overflow-y: auto;
}

.cart h2 {
text-align: center;
}

.checkout-form {
margin-top: 20px;
}

</style>
</head>

<body>

<header>RAGE DISTRICT</header>

<section class="products">
<h2>Shop</h2>

<div class="grid">

<div class="product">
<h3>Graphic Shirt</h3>
<p>$30</p>
<select id="size1">
<option>S</option>
<option>M</option>
<option>L</option>
<option>XL</option>
</select>
<button onclick="addToCart('Graphic Shirt', 30, 'size1')">Add</button>
</div>

<div class="product">
<h3>Zip-Up Jacket</h3>
<p>$70</p>
<select id="size2">
<option>S</option>
<option>M</option>
<option>L</option>
<option>XL</option>
</select>
<button onclick="addToCart('Zip-Up Jacket', 70, 'size2')">Add</button>
</div>

<div class="product">
<h3>Jorts</h3>
<p>$45</p>
<select id="size3">
<option>S</option>
<option>M</option>
<option>L</option>
<option>XL</option>
</select>
<button onclick="addToCart('Jorts', 45, 'size3')">Add</button>
</div>

<div class="product">
<h3>Street Pants</h3>
<p>$60</p>
<select id="size4">
<option>S</option>
<option>M</option>
<option>L</option>
<option>XL</option>
</select>
<button onclick="addToCart('Street Pants', 60, 'size4')">Add</button>
</div>

</div>
</section>

<div class="cart">
<h2>🛒 Cart</h2>
<div id="cartItems"></div>
<h3>Total: $<span id="total">0</span></h3>

<div class="checkout-form">
<h3>Shipping Info</h3>

<input id="name" placeholder="Full Name">
<input id="address" placeholder="Address">
<input id="city" placeholder="City">
<input id="zip" placeholder="ZIP Code">

<button onclick="checkout()">Checkout</button>
</div>

</div>

<script>
let cart = [];
let total = 0;

function addToCart(name, price, sizeId) {
let size = document.getElementById(sizeId).value;
cart.push({name, price, size});
total += price;
displayCart();
}

function displayCart() {
let cartItems = document.getElementById("cartItems");
cartItems.innerHTML = "";

cart.forEach(item => {
let div = document.createElement("div");
div.innerText = item.name + " (" + item.size + ") - $" + item.price;
cartItems.appendChild(div);
});

document.getElementById("total").innerText = total;
}

function checkout() {
let name = document.getElementById("name").value;
let address = document.getElementById("address").value;

if (!name || !address) {
alert("Fill out shipping info");
return;
}

let order = "Order:\n";
cart.forEach(item => {
order += item.name + " (" + item.size + ")\n";
});

order += "Total: $" + total;

alert("Send this in Cash App notes:\n\n" + order);

window.location.href = "https://cash.app/$Trxpstartarahji";
}
</script>

</body>
</html>
