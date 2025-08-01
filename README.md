
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zapatillas Reyes</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Arial Black', sans-serif;
      background-color: #000;
      color: #fff;
      scroll-behavior: smooth;
    }

    header {
      background-color: #111;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      font-size: 2.5rem;
      color: #fff;
    }

    nav {
      display: flex;
      justify-content: center;
      gap: 25px;
      background-color: #222;
      padding: 15px 0;
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: bold;
      text-transform: uppercase;
    }

    nav a:hover {
      color: #e63946;
    }

    .hero {
      background: url('https://wallpaperaccess.com/full/1355617.jpg') center/cover no-repeat;
      height: 70vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    .hero h2 {
      background-color: rgba(0, 0, 0, 0.6);
      padding: 20px;
      font-size: 3rem;
      color: #fff;
    }

    section {
      padding: 40px 20px;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
    }

    .product {
      background: #1a1a1a;
      padding: 15px;
      border-radius: 10px;
      text-align: center;
      transition: transform 0.3s;
    }

    .product:hover {
      transform: scale(1.05);
    }

    .product img {
      width: 100%;
      border-radius: 8px;
    }

    .product h3 {
      margin-top: 10px;
      font-size: 1.1rem;
    }

    .product p {
      color: #e63946;
      font-weight: bold;
    }

    .product button {
      margin-top: 10px;
      padding: 10px 15px;
      background: #e63946;
      border: none;
      color: white;
      cursor: pointer;
      border-radius: 5px;
    }

    #cart {
      background: #111;
      border: 1px solid #333;
      padding: 20px;
      border-radius: 10px;
      max-width: 400px;
      margin: 0 auto;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
    }

    .cart-item button {
      background: #444;
      color: #fff;
      border: none;
      padding: 3px 6px;
      cursor: pointer;
    }

    footer {
      background: #111;
      color: #aaa;
      text-align: center;
      padding: 20px;
      margin-top: 40px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Zapatillas Reyes</h1>
  </header>

  <nav>
    <a href="#inicio">Inicio</a>
    <a href="#hombres">Hombres</a>
    <a href="#mujeres">Mujeres</a>
    <a href="#ofertas">Ofertas</a>
    <a href="#contacto">Contacto</a>
    <a href="#carrito">Carrito</a>
  </nav>

  <section class="hero" id="inicio">
    <h2>Lleva tu juego al siguiente nivel</h2>
  </section>

  <section id="hombres">
    <h2 style="text-align:center; margin-bottom: 20px;">Zapatillas para Hombres</h2>
    <div class="products" id="product-list">
      <!-- Productos se cargan aquí -->
    </div>
  </section>

  <section id="carrito">
    <h2 style="text-align:center;">🛒 Tu carrito</h2>
    <div id="cart"></div>
  </section>

  <section id="contacto">
    <h2 style="text-align:center;">Contáctanos</h2>
    <p style="text-align:center;">📱 WhatsApp: +51 999 999 999</p>
    <p style="text-align:center;">📧 Email: contacto@zapatillasreyes.pe</p>
    <p style="text-align:center;">📍 Dirección: Lima, Perú</p>
  </section>

  <footer>
    © 2025 Zapatillas Reyes. Inspirado en Nike.
  </footer>

  <script>
    const products = [
      { id: 1, name: 'Air Max 270', price: 399.90, image: 'https://static.nike.com/a/images/c_limit,w_592,f_auto/t_product_v1/e46e2720-2e2e-4da2-b198-e17d11d5aeda/air-max-270-zapatillas.png' },
      { id: 2, name: 'Nike ZoomX', price: 459.90, image: 'https://static.nike.com/a/images/c_limit,w_592,f_auto/t_product_v1/f6d38191-dc2e-4d10-8885-1e6b2162f8f9/zoomx-vaporfly-next-3-zapatillas.png' },
      { id: 3, name: 'Nike Pegasus', price: 359.90, image: 'https://static.nike.com/a/images/c_limit,w_592,f_auto/t_product_v1/71d905cf-41fd-4f83-9e91-87f4a3152a49/pegasus-40-zapatillas.png' }
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
          <button onclick="addToCart(${product.id})">Añadir</button>
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
      const cartEl = document.getElementById('cart');
      cartEl.innerHTML = '';
      let total = 0;

      if (cart.length === 0) {
        cartEl.innerHTML = '<p style="text-align:center;">Tu carrito está vacío.</p>';
        return;
      }

      cart.forEach((item, index) => {
        const div = document.createElement('div');
        div.className = 'cart-item';
        div.innerHTML = `
          <span>${item.name}</span>
          <span>S/ ${item.price.toFixed(2)}</span>
          <button onclick="removeFromCart(${index})">X</button>
        `;
        cartEl.appendChild(div);
        total += item.price;
      });

      const totalText = document.createElement('p');
      totalText.innerHTML = `<strong>Total: S/ ${total.toFixed(2)}</strong>`;
      cartEl.appendChild(totalText);
    }

    renderProducts();
  </script>



