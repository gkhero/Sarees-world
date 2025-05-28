<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Saree Business</title>
  <style>
    /* Basic styling for layout and components */
    body { 
      font-family: Arial, sans-serif; 
      margin: 0; 
      padding: 0; 
      background-color: #fafafa;
    }
    header, footer, .container { 
      padding: 20px; 
      text-align: center; 
    }
    header { 
      background-color: #f8f8f8; 
    }
    .products { 
      display: flex; 
      flex-wrap: wrap; 
      justify-content: center; 
      margin: 20px;
    }
    .product { 
      border: 1px solid #ddd; 
      margin: 10px; 
      padding: 10px; 
      width: 300px; 
      text-align: center;
      background-color: #fff;
    }
    .product img { 
      max-width: 100%; 
      height: auto;
    }
    .product button { 
      background-color: #4CAF50; 
      color: white; 
      padding: 10px 15px; 
      border: none; 
      cursor: pointer; 
      margin-top: 10px;
    }
    .product button:hover { 
      background-color: #45a049; 
    }
    .cart { 
      background-color: #f0f0f0; 
      padding: 10px 20px; 
      width: 80%; 
      margin: 20px auto;
      text-align: left;
    }
    .cart-header { 
      font-size: 20px; 
      margin-bottom: 10px; 
    }
    .cart button { 
      background-color: #ff9800; 
      color: white; 
      padding: 10px 15px; 
      border: none; 
      cursor: pointer;
      margin-top: 10px;
    }
    .cart button:hover { 
      background-color: #e68900; 
    }
    .contact { 
      margin-top: 40px; 
      padding: 20px; 
      background: #eef;
    }
  </style>
</head>
<body>
  <header>
    <h1>Welcome to Our Saree Business</h1>
  </header>
  
  <div class="products">
    <!-- Example product cards -->
    <div class="product" data-id="1">
      <img src="https://via.placeholder.com/300x200?text=Saree+1" alt="Saree 1">
      <h2>silk Saree 1</h2>
      <p>Price: ₹1999</p>
      <button onclick="addToCart(1, 'silk Saree 1', 1999)">Add to Cart</button>
    </div>
    <div class="product" data-id="2">
      <img src="https://via.placeholder.com/300x200?text=Saree+2" alt="Saree 2">
      <h2>Beautiful Saree 2</h2>
      <p>Price: ₹2499</p>
      <button onclick="addToCart(2, 'Beautiful Saree 2', 2499)">Add to Cart</button>
    </div>
    <div class="product" data-id="3">
      <img src00?text=Saree+3" alt="Saree 3">
      <h2>Stylish Saree 3</h2>
      <p>Price: ₹2999</p>
      <button onclick="addToCart(3, 'Stylish Saree 3', 2999)">Add to Cart</button>
    </div>
  </div>
  
  <div class="cart">
    <div class="cart-header">Shopping Cart</div>
    <ul id="cartItems">
      <!-- Dynamically added cart items will appear here -->
    </ul>
    <div id="total"></div>
    <button onclick="buyItems()">Buy Now</button>
  </div>
  
  <div class="contact">
    <h2>Contact Us</h2>
    <p>Phone: +91-7358547471</p>
    <p>Email.dhanasathiyak@gmail.com</p>
  </div>
  
  <footer>
    <p>&copy; 2025 Saree Business. All rights reserved.</p>
  </footer>
  
  <script>
    // Array to hold cart items
    let cart = [];
    
    // Function to add an item to the cart
    function addToCart(id, name, price) {
      cart.push({ id, name, price });
      updateCartDisplay();
    }
    
    // Function to update the cart display in the webpage
    function updateCartDisplay() {
      const cartItems = document.getElementById('cartItems');
      cartItems.innerHTML = '';
      let total = 0;
      cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.name} - ₹${item.price}`;
        cartItems.appendChild(li);
        total += item.price;
      });
      document.getElementById('total').textContent = `Total: ₹${total}`;
    }
    
    // Function to simulate the purchase process
    function buyItems() {
      if (cart.length === 0) {
        alert('Your cart is empty! Please add at least one saree.');
        return;
      }
      
      let total = cart.reduce((sum, item) => sum + item.price, 0);
      let confirmation = confirm(`Your total is ₹${total}. Do you want to proceed to checkout?`);
      if (confirmation) {
        // Here you could integrate real payment processing or order confirmation
        alert('Thank you for your purchase!');
        cart = []; // Reset the cart after purchase
        updateCartDisplay();
      }
    }
  </script>
</body>
</html>



