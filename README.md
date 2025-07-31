
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zapatillas Reyes</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Montserrat', sans-serif;
    }
  </style>
</head>
<body class="bg-gray-100">
  <!-- Navbar -->
  <nav class="bg-white shadow p-4 flex justify-between items-center">
    <h1 class="text-2xl font-bold text-blue-800">Zapatillas Reyes</h1>
    <div class="space-x-4">
      <a href="#productos" class="text-gray-700 hover:text-blue-800">Productos</a>
      <a href="#nosotros" class="text-gray-700 hover:text-blue-800">Nosotros</a>
      <a href="#contacto" class="text-gray-700 hover:text-blue-800">Contacto</a>
      <button id="carritoBtn" class="bg-blue-800 text-white px-4 py-2 rounded">Carrito (<span id="carritoContador">0</span>)</button>
    </div>
  </nav>

  <!-- Productos -->
  <section id="productos" class="p-8">
    <h2 class="text-3xl font-bold mb-6 text-center text-blue-800">Nuestros Productos</h2>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
      <div class="bg-white rounded shadow p-4 text-center">
        <img src="https://via.placeholder.com/200" alt="Zapatilla 1" class="mx-auto mb-2"/>
        <h3 class="font-semibold">Zapatilla Urbana</h3>
        <p class="text-gray-500">S/ 199.00</p>
        <button onclick="agregarAlCarrito('Zapatilla Urbana', 199)" class="mt-2 bg-blue-800 text-white px-4 py-1 rounded">Agregar al carrito</button>
      </div>
      <div class="bg-white rounded shadow p-4 text-center">
        <img src="https://via.placeholder.com/200" alt="Zapatilla 2" class="mx-auto mb-2"/>
        <h3 class="font-semibold">Zapatilla Running</h3>
        <p class="text-gray-500">S/ 249.00</p>
        <button onclick="agregarAlCarrito('Zapatilla Running', 249)" class="mt-2 bg-blue-800 text-white px-4 py-1 rounded">Agregar al carrito</button>
      </div>
      <div class="bg-white rounded shadow p-4 text-center">
        <img src="https://via.placeholder.com/200" alt="Zapatilla 3" class="mx-auto mb-2"/>
        <h3 class="font-semibold">Zapatilla Clásica</h3>
        <p class="text-gray-500">S/ 179.00</p>
        <button onclick="agregarAlCarrito('Zapatilla Clásica', 179)" class="mt-2 bg-blue-800 text-white px-4 py-1 rounded">Agregar al carrito</button>
      </div>
    </div>
  </section>

  <!-- Nosotros -->
  <section id="nosotros" class="p-8 bg-white">
    <h2 class="text-3xl font-bold mb-4 text-blue-800">Sobre Nosotros</h2>
    <p class="text-gray-700 max-w-2xl">En Zapatillas Reyes nos dedicamos a ofrecer calzado de alta calidad, combinando diseño, comodidad y estilo. Nuestro objetivo es que encuentres la zapatilla perfecta para cada ocasión.</p>
  </section>

  <!-- Contacto -->
  <section id="contacto" class="p-8">
    <h2 class="text-3xl font-bold mb-4 text-blue-800">Contáctanos</h2>
    <form class="max-w-md space-y-4">
      <input type="text" placeholder="Nombre" class="w-full p-2 border rounded" required />
      <input type="email" placeholder="Correo electrónico" class="w-full p-2 border rounded" required />
      <textarea placeholder="Mensaje" class="w-full p-2 border rounded" required></textarea>
      <button class="bg-blue-800 text-white px-4 py-2 rounded">Enviar</button>
    </form>
  </section>

  <!-- Carrito (modal básico) -->
  <div id="carritoModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
    <div class="bg-white rounded p-6 w-80">
      <h3 class="text-xl font-bold mb-4">Tu Carrito</h3>
      <ul id="listaCarrito" class="mb-4 space-y-2"></ul>
      <p class="font-bold">Total: S/ <span id="totalCarrito">0</span></p>
      <button onclick="cerrarCarrito()" class="mt-4 bg-red-600 text-white px-4 py-2 rounded">Cerrar</button>
    </div>
  </div>

  <script>
    let carrito = [];

    function agregarAlCarrito(nombre, precio) {
      carrito.push({ nombre, precio });
      actualizarCarrito();
    }

    function actualizarCarrito() {
      document.getElementById('carritoContador').innerText = carrito.length;
      const lista = document.getElementById('listaCarrito');
      lista.innerHTML = '';
      let total = 0;
      carrito.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.nombre} - S/ ${item.precio}`;
        lista.appendChild(li);
        total += item.precio;
      });
      document.getElementById('totalCarrito').innerText = total.toFixed(2);
    }

    document.getElementById('carritoBtn').addEventListener('click', () => {
      document.getElementById('carritoModal').classList.remove('hidden');
      document.getElementById('carritoModal').classList.add('flex');
    });

    function cerrarCarrito() {
      document.getElementById('carritoModal').classList.add('hidden');
    }
  </script>
</body>
</html>
