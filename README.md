
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zapatillas Reyes</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #d0f0c0; /* Verde claro */
      color: #333;
      scroll-behavior: smooth;
    }

    header {
      background-color: #000;
      color: #fff;
      padding: 1rem;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    nav {
      background-color: #222;
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 10px 0;
    }

    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: bold;
    }

    nav a:hover {
      text-decoration: underline;
    }

    section {
      padding: 40px 20px;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
    }

    .product {
      background: white;
      padding: 15px;
      border-radius: 10px;
      text-align: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .product img {
      width: 100%;
      height: auto;
      border-radius: 8px;
    }

    .product button {
      background-color: #e63946;
      color: white;
      border: none;
      padding: 10px;
      margin-top: 10px;
      cursor: pointer;
      border-radius: 5px;
    }

    #cart {
      background: white;
      border: 2px solid #000;
      border-radius: 10px;
      padding: 15px;
      width: 300px;
      margin-top: 20px;
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

    footer {
      background: #111;
      color: white;
      text-align: center;
      padding: 20px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Zapatillas Reyes</h1>
    <p>Tu estilo comienza por los pies</p>
  </header>

  <nav>
    <a href="#inicio">Inicio</a>
    <a href="#nosotros">Nosotros</a>
    <a href="#productos">Productos</a>
    <a href="#contacto">Contacto</a>
    <a href="#carrito">Carrito</a>
  </nav>

  <section id="inicio">
    <h2>Bienvenido</h2>
    <p>Explora las mejores zapatillas para tu estilo de vida activo y urbano.</p>
  </section>

  <section id="nosotros">
    <h2>Nosotros</h2>
    <p>Somos Zapatillas Reyes, una tienda peruana dedicada a ofrecer calzado de calidad, diseño moderno y comodidad. Nuestra misión es llevar estilo y rendimiento a tus pasos.</p>
  </section>

  <section id="productos">
    <h2>Productos</h2>
    <div class="products" id="product-list">
      <!-- Productos aquí -->
    </div>
  </section>

  <section id="contacto">
    <h2>Contacto</h2>
    <p>📞 Teléfono: +51 999 999 999</p>
    <p>📧 Email: contacto@zapatillasreyes.pe</p>
    <p>📍 Dirección: Lima, Perú</p>
  </section>

  <section id="carrito">
    <h2>🛒 Carrito de compras</h2>
    <div id="cart">
      <div id="cart-items"></div>
      <p><strong>Total: S/ <span id="total">0.00</span></strong></p>
    </div>
  </section>

  <footer>
    <p>© 2025 Zapatillas Reyes. Todos los derechos reservados.</p>
  </footer>

  <script>
    const products = [
      { id: 1, name: 'Zapatilla Nike Air', price: 299.90, image: 'https://via.placeholder.com/200x150?text=Nike+Air' },
      { id: 2, name: 'Adidas Runner Pro', price: 249.90, image: 'https://via.placeholder.com/200x150?text=Adidas+Runner' },
      { id: 3, name: 'Puma Flex', price: 199.90, image: 'https://via.placeholder.com/200x150?text=Puma+Flex' }
    ];

    const cart = [];

    function renderProducts() {
      const productList = document.getElementById('product-list');
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
      const cartItems = document.getElementById('cart-items');
      const totalEl = document.getElementById('total');
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

