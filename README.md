<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fresh Basket - Online Vegetable Store</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f5f8f4;
            color: #222;
        }

        header {
            background: #198754;
            color: white;
            padding: 15px 7%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 25px;
            font-weight: bold;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin-left: 20px;
        }

        .cart-btn {
            background: white;
            color: #198754;
            border: none;
            padding: 10px 15px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
        }

        .hero {
            min-height: 400px;
            padding: 80px 7%;
            background: linear-gradient(120deg, #dff5df, #ffffff);
            display: flex;
            align-items: center;
        }

        .hero-content {
            max-width: 600px;
        }

        .hero h1 {
            font-size: 48px;
            color: #146c43;
            margin-bottom: 15px;
        }

        .hero p {
            font-size: 19px;
            margin-bottom: 25px;
            line-height: 1.6;
        }

        .shop-btn {
            display: inline-block;
            background: #198754;
            color: white;
            text-decoration: none;
            padding: 13px 25px;
            border-radius: 6px;
        }

        .section {
            padding: 50px 7%;
        }

        .section-title {
            text-align: center;
            margin-bottom: 30px;
            font-size: 32px;
            color: #146c43;
        }

        .categories {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin-bottom: 30px;
        }

        .category {
            padding: 10px 20px;
            border: 1px solid #198754;
            border-radius: 25px;
            background: white;
            cursor: pointer;
        }

        .category:hover {
            background: #198754;
            color: white;
        }

        .products {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
            gap: 20px;
        }

        .product {
            background: white;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 3px 12px rgba(0,0,0,0.08);
        }

        .product-image {
            font-size: 70px;
            margin-bottom: 10px;
        }

        .product h3 {
            margin: 10px 0;
        }

        .price {
            color: #198754;
            font-size: 20px;
            font-weight: bold;
            margin: 10px;
        }

        .add-btn {
            border: none;
            background: #198754;
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
        }

        .offer {
            background: #fff3cd;
            text-align: center;
            padding: 25px;
            margin: 20px 7%;
            border-radius: 10px;
        }

        footer {
            background: #146c43;
            color: white;
            text-align: center;
            padding: 30px;
            margin-top: 30px;
        }

        /* Cart */

        .cart {
            position: fixed;
            right: -400px;
            top: 0;
            width: 360px;
            height: 100%;
            background: white;
            box-shadow: -5px 0 20px rgba(0,0,0,0.2);
            padding: 25px;
            transition: 0.3s;
            z-index: 200;
            overflow-y: auto;
        }

        .cart.active {
            right: 0;
        }

        .close-cart {
            float: right;
            cursor: pointer;
            font-size: 22px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid #ddd;
        }

        .checkout {
            width: 100%;
            padding: 13px;
            background: #198754;
            color: white;
            border: none;
            border-radius: 5px;
            margin-top: 20px;
            cursor: pointer;
        }

        @media(max-width: 600px) {
            nav {
                display: none;
            }

            .hero h1 {
                font-size: 35px;
            }

            .hero {
                padding: 60px 5%;
            }

            .section {
                padding: 40px 5%;
            }

            .cart {
                width: 90%;
            }
        }
    </style>
</head>

<body>

<header>
    <div class="logo">🥬 Fresh Basket</div>

    <nav>
        <a href="#home">Home</a>
        <a href="#products">Vegetables</a>
        <a href="#contact">Contact</a>
    </nav>

    <button class="cart-btn" onclick="openCart()">
        🛒 Cart (<span id="cartCount">0</span>)
    </button>
</header>


<section class="hero" id="home">
    <div class="hero-content">
        <h1>Fresh Vegetables Delivered To Your Door</h1>

        <p>
            Fresh, hygienic and quality vegetables at affordable prices.
            Order online and get same-day local delivery.
        </p>

        <a href="#products" class="shop-btn">
            Shop Now
        </a>
    </div>
</section>


<div class="offer">
    <h2>🎉 Today's Offer</h2>
    <p>Free delivery on orders above ₹299</p>
</div>


<section class="section" id="products">

    <h2 class="section-title">Fresh Vegetables</h2>

    <div class="categories">
        <button class="category">All</button>
        <button class="category">Vegetables</button>
        <button class="category">Leafy</button>
        <button class="category">Organic</button>
    </div>

    <div class="products">

        <div class="product">
            <div class="product-image">🥔</div>
            <h3>Potato</h3>
            <p>Fresh Potato</p>
            <div class="price">₹30 / kg</div>
            <button class="add-btn"
                onclick="addToCart('Potato',30)">
                Add to Cart
            </button>
        </div>

        <div class="product">
            <div class="product-image">🍅</div>
            <h3>Tomato</h3>
            <p>Fresh Tomato</p>
            <div class="price">₹40 / kg</div>
            <button class="add-btn"
                onclick="addToCart('Tomato',40)">
                Add to Cart
            </button>
        </div>

        <div class="product">
            <div class="product-image">🧅</div>
            <h3>Onion</h3>
            <p>Fresh Onion</p>
            <div class="price">₹35 / kg</div>
            <button class="add-btn"
                onclick="addToCart('Onion',35)">
                Add to Cart
            </button>
        </div>

        <div class="product">
            <div class="product-image">🥕</div>
            <h3>Carrot</h3>
            <p>Fresh Carrot</p>
            <div class="price">₹50 / kg</div>
            <button class="add-btn"
                onclick="addToCart('Carrot',50)">
                Add to Cart
            </button>
        </div>

        <div class="product">
            <div class="product-image">🥦</div>
            <h3>Broccoli</h3>
            <p>Fresh Broccoli</p>
            <div class="price">₹80 / kg</div>
            <button class="add-btn"
                onclick="addToCart('Broccoli',80)">
                Add to Cart
            </button>
        </div>

        <div class="product">
            <div class="product-image">🥬</div>
            <h3>Spinach</h3>
            <p>Fresh Green Spinach</p>
            <div class="price">₹25 / bunch</div>
            <button class="add-btn"
                onclick="addToCart('Spinach',25)">
                Add to Cart
            </button>
        </div>

    </div>
</section>


<div class="cart" id="cart">

    <span class="close-cart" onclick="closeCart()">✖</span>

    <h2>Your Cart</h2>

    <br>

    <div id="cartItems"></div>

    <h3>Total: ₹<span id="cartTotal">0</span></h3>

    <button class="checkout" onclick="checkout()">
        Order on WhatsApp
    </button>

</div>


<footer id="contact">

    <h3>🥬 Fresh Basket</h3>

    <p>Fresh Vegetables • Fast Delivery • Best Price</p>

    <p>📞 +91 98765 43210</p>

    <p>📍 Your City, Jharkhand</p>

    <br>

    <p>© 2026 Fresh Basket. All Rights Reserved.</p>

</footer>


<script>

let cart = [];

function addToCart(name, price) {

    cart.push({
        name: name,
        price: price
    });

    updateCart();

    alert(name + " added to cart!");
}


function updateCart() {

    document.getElementById("cartCount").innerText =
        cart.length;

    let items = "";

    let total = 0;

    cart.forEach(function(item, index) {

        items += `
            <div class="cart-item">
                <span>${item.name}</span>
                <span>₹${item.price}</span>
            </div>
        `;

        total += item.price;
    });

    document.getElementById("cartItems").innerHTML = items;

    document.getElementById("cartTotal").innerText = total;
}


function openCart() {

    document.getElementById("cart")
        .classList.add("active");
}


function closeCart() {

    document.getElementById("cart")
        .classList.remove("active");
}


function checkout() {

    if(cart.length === 0) {

        alert("Please add vegetables to cart.");

        return;
    }

    let message =
        "Hello Fresh Basket,%0A%0AI want to order:%0A";

    let total = 0;

    cart.forEach(function(item) {

        message +=
            item.name + " - ₹" +
            item.price + "%0A";

        total += item.price;
    });

    message +=
        "%0ATotal: ₹" +
        total +
        "%0A%0APlease confirm my order.";

    let phone = "919876543210";

    window.open(
        "https://wa.me/" +
        phone +
        "?text=" +
        message,
        "_blank"
    );
}

</script>

</body>
</html>
