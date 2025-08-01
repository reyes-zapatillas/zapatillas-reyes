
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zapatillas Reyes</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f4f4f4;
      color: #333;
    }

    header {
      background-color: #000;
      color: #fff;
      padding: 1rem;
      text-align: center;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      padding: 20px;
    }

    .product {
      background: white;
      padding: 10px;
      border-radius: 10px;
      text-align: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .product img {
      max-width: 100%;
      height: auto;
      border-radius: 8px;
    }

    .product button {
      background-color: #e63946;
      color: white;
      border: none;
      padding: 10px 15px;
      margin-top: 10px;
      cursor: pointer;
      border-radius: 5px;
    }

    #cart {
      position: fixed;
      top: 10px;
      right: 10px;
      background: white;
      border: 2px solid #000;
      border-radius: 10px;
      padding: 15px;
      width: 250px;
    }

    #cart h2 {
      margin-top: 0;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
    }

    .cart-item button {
      background: #000;
      color: white;
      border: none;
      cursor: pointer;
      padding: 2px 5px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Zapatillas Reyes</h1>
    <p>Tu estilo comienza por los pies</p>
  </header>

  <div class="products" id="product-list">
    <!-- Productos se insertan aquí -->
  </div>

  <div id="cart">
    <h2>🛒 Carrito</h2>
    <div id="cart-items"></div>
    <p><strong>Total: S/ <span id="total">0.00</span></strong></p>
  </div>

  <script>
    const products = [
      { id: 1, name: 'Zapatilla Nike Air', price: 299.90, image: 'https://via.placeholder.com/200x150?text=Nike+Air' },
      { id: 2, name: 'Adidas Runner Pro', price: 249.90, image: 'https://via.placeholder.com/200x150?text=Adidas+Runner' },
      { id: 3, name: 'Puma Flex', price: 199.90, image: 'https://via.placeholder.com/200x150?text=Puma+Flex' }
    ];

    const cart = [];

    const productList = document.getElementById('product-list');
    const cartItems = document.getElementById('cart-items');
    const totalEl = document.getElementById('total');

    function renderProducts() {
      products.forEach(product => {
        const div = document.createElement('div');
        div.className = 'product';
        div.innerHTML = `
          <img src="${product.image}" alt="${product.name}">
          <h3>${product.name}</h3>
          <p>S/ ${product.price.toFixed(2)}</p>
          <button onclick="addToCart(${product.id})">Añadir al carrito</button>
        `;
        productList.appendChild(div);
      });
    }

    function addToCart(productId) {
      const product = products.find(p => p.id === productId);
      cart.push(product);
      updateCart();
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      updateCart();
    }

    function updateCart() {
      cartItems.innerHTML = '';
      let total = 0;

      cart.forEach((item, index) => {
        const div = document.createElement('div');
        div.className = 'cart-item';
        div.innerHTML = `
          <span>${item.name}</span>
          <span>S/ ${item.price.toFixed(2)}</span>
          <button onclick="removeFromCart(${index})">X</button>
        `;
        cartItems.appendChild(div);
        total += item.price;
      });

      totalEl.textContent = total.toFixed(2);
    }

    renderProducts();
  </script>
</body>
</html>
