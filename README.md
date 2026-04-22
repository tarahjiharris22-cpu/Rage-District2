<style>
/* ... keep your previous styles ... */

.cart {
position: fixed;
right: 0;
top: 0;
width: 300px; /* Slightly wider to fit forms */
height: 100%;
background: #000;
padding: 20px;
overflow-y: auto;
border-left: 2px solid #ff1a1a;
box-sizing: border-box;
}

.checkout-form {
margin-top: 20px;
display: flex;
flex-direction: column;
gap: 10px;
}

.checkout-form label {
font-size: 12px;
color: #ff1a1a;
text-transform: uppercase;
font-weight: bold;
}

.checkout-form input {
background: #111;
border: 1px solid #333;
color: white;
padding: 10px;
border-radius: 5px;
font-size: 14px;
}

.checkout-form input:focus {
outline: none;
border-color: #ff1a1a;
}

.row {
display: flex;
gap: 10px;
}

.row input {
width: 50%;
}

.checkout {
margin-top: 20px;
width: 100%;
padding: 15px;
background: #ff1a1a;
color: black;
font-weight: bold;
border: none;
cursor: pointer;
text-transform: uppercase;
}

.checkout:hover {
background: #fff;
}
</style>

<div class="cart">
<h2>🛒 YOUR CART</h2>
<div id="cartItems"></div>
<hr style="border: 0.5px solid #222;">
<h3>Total: $<span id="total">0</span></h3>

<div class="checkout-form">
<label>Shipping Address</label>
<input type="text" id="fullName" placeholder="Full Name">
<input type="text" id="address" placeholder="Street Address">
<div class="row">
<input type="text" id="city" placeholder="City">
<input type="text" id="zip" placeholder="Zip Code">
</div>

<label style="margin-top:10px;">Payment Details</label>
<input type="tel" id="cardNumber" placeholder="Card Number (16 digits)" maxlength="16">
<div class="row">
<input type="tel" id="exp" placeholder="MM/YY" maxlength="5">
<input type="password" id="cvv" placeholder="CVV" maxlength="3">
</div>
</div>

<button class="checkout" onclick="processOrder()">Complete Order</button>
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
div.style.padding = "5px 0";
div.innerText = "• " + item.name + " - $" + item.price;
cartItems.appendChild(div);
});
document.getElementById("total").innerText = total;
}

function processOrder() {
// Get all input values
const fields = {
name: document.getElementById("fullName").value,
addr: document.getElementById("address").value,
card: document.getElementById("cardNumber").value,
cvv: document.getElementById("cvv").value
};

// Basic Validation
if (cart.length === 0) {
alert("Your cart is empty.");
return;
}

if (!fields.name || !fields.addr || fields.card.length < 16) {
alert("Please fill in all shipping and card details correctly.");
return;
}

// In a real scenario, you would send this to a secure server here.
// Since this is for demonstration:
alert("Order Received! Processing payment for " + fields.name);

// Redirect to your confirmation or back to the shop
window.location.reload();
}
</script>
