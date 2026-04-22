<style>
/* ... existing styles ... */

.address-fields {
margin-top: 20px;
border-top: 1px solid #333;
padding-top: 15px;
}

.address-fields input {
width: 100%;
padding: 8px;
margin: 5px 0;
background: #222;
border: 1px solid #444;
color: white;
box-sizing: border-box; /* Ensures padding doesn't break width */
}

.address-fields h4 {
margin: 5px 0;
font-size: 14px;
color: #ff1a1a;
}
</style>

<div class="cart">
<h2>🛒 Cart</h2>
<div id="cartItems"></div>
<h3>Total: $<span id="total">0</span></h3>

<div class="address-fields">
<h4>Shipping Details</h4>
<input type="text" id="custName" placeholder="Full Name">
<input type="text" id="custAddr" placeholder="Street Address">
<input type="text" id="custCity" placeholder="City, State, Zip">
</div>

<button class="checkout" onclick="checkout()" style="margin-top: 15px;">Checkout</button>
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
const name = document.getElementById("custName").value;
const addr = document.getElementById("custAddr").value;
const city = document.getElementById("custCity").value;

if (cart.length === 0) {
alert("Your cart is empty!");
return;
}

if (!name || !addr || !city) {
alert("Please fill out your shipping address before checking out.");
return;
}

// Optional: Alert the user to include their name in the Cash App note
alert("Please include your name ('" + name + "') in the Cash App note so we can match your payment to your address!");

// Redirect to Cash App
window.location.href = "https://cash.app/$Trxpstartarahji/" + total;
}
</script>
