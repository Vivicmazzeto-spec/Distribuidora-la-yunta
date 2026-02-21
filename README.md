<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Distribuidora La Yunta | Catálogo de Productos</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --color-fondo: #f5f5f5;
            --color-texto: #111;
            --color-acento: #6c5ce7;
            --color-secundario: #e0e0e0;
            --fuente-principal: 'Poppins', sans-serif;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: var(--fuente-principal); background: var(--color-fondo); color: var(--color-texto); line-height: 1.6; }

        h1,h2,h3 { color: var(--color-acento); }

        /* NAV */
        nav { padding: 20px 5%; display:flex; justify-content:space-between; align-items:center; background:#fff; box-shadow:0 2px 5px rgba(0,0,0,0.1); position:sticky; top:0; z-index:1000; }
        .logo { font-weight:700; font-size:1.5rem; color: var(--color-acento); }
        .nav-links { display:flex; gap:20px; }
        .nav-links a { text-decoration:none; color: var(--color-texto); font-weight:500; }
        .nav-links a:hover { color: var(--color-acento); }
        .menu-toggle { display:none; cursor:pointer; }

        /* HERO */
        .hero { text-align:center; padding:100px 20px 50px; background: linear-gradient(135deg,#6c5ce7,#a29bfe); color:#fff; }
        .hero h1 { font-size:2.5rem; margin-bottom:20px; }
        .hero p { max-width:600px; margin:0 auto 20px; }

        /* CATÁLOGO */
        .catalogo { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:20px; padding:40px 10%; }
        .producto { background:#fff; border-radius:10px; box-shadow:0 5px 15px rgba(0,0,0,0.1); padding:20px; text-align:center; }
        .producto img { width:100%; height:200px; object-fit:cover; border-radius:10px; margin-bottom:15px; }
        .producto h3 { margin-bottom:10px; }
        .producto p { font-size:0.9rem; margin-bottom:15px; color:#555; }
        .producto span { font-weight:600; font-size:1.1rem; display:block; margin-bottom:10px; }
        .btn { padding:10px 20px; background: var(--color-acento); color:#fff; border:none; border-radius:30px; cursor:pointer; font-weight:600; transition:0.3s; }
        .btn:hover { background:transparent; border:2px solid var(--color-acento); color: var(--color-acento); }

        /* CARRITO */
        .carrito-box { position:fixed; top:80px; right:20px; width:300px; background:#fff; border-radius:10px; box-shadow:0 5px 15px rgba(0,0,0,0.2); padding:20px; max-height:80vh; overflow-y:auto; }
        .carrito-box h3 { margin-bottom:15px; text-align:center; }
        .carrito-item { display:flex; justify-content:space-between; margin-bottom:10px; }
        .carrito-item span { font-weight:500; }
        .carrito-total { font-weight:700; margin-top:15px; text-align:right; }
        .carrito-box form { margin-top:15px; display:flex; flex-direction:column; gap:10px; }
        .carrito-box input, .carrito-box textarea { padding:8px; border-radius:5px; border:1px solid #ccc; }
        .carrito-box button { margin-top:10px; }

        /* RESPONSIVE */
        @media(max-width:768px){.carrito-box{position:static;width:90%;margin:20px auto;} .catalogo{padding:20px;} .hero h1{font-size:2rem;} .hero p{font-size:1rem;} }
    </style>
</head>
<body>

    <nav>
        <div class="logo">Distribuidora La Yunta</div>
        <div class="menu-toggle">☰</div>
        <div class="nav-links">
            <a href="#catalogo">Catálogo</a>
            <a href="#carrito">Pedido</a>
        </div>
    </nav>

    <section class="hero">
        <h1>Bienvenido a Distribuidora La Yunta</h1>
        <p>Elige los productos que necesitas, agrégalos al carrito y envíanos tu pedido. Nosotros nos encargamos del resto.</p>
    </section>

    <section id="catalogo" class="catalogo">
        <!-- PRODUCTOS -->
        <div class="producto">
            <img src="https://via.placeholder.com/300x200?text=Producto+1" alt="Producto 1">
            <h3>Producto 1</h3>
            <p>Descripción breve del producto 1.</p>
            <span>$100</span>
            <button class="btn" onclick="agregarCarrito('Producto 1',100)">Agregar al pedido</button>
        </div>
        <div class="producto">
            <img src="https://via.placeholder.com/300x200?text=Producto+2" alt="Producto 2">
            <h3>Producto 2</h3>
            <p>Descripción breve del producto 2.</p>
            <span>$150</span>
            <button class="btn" onclick="agregarCarrito('Producto 2',150)">Agregar al pedido</button>
        </div>
        <div class="producto">
            <img src="https://via.placeholder.com/300x200?text=Producto+3" alt="Producto 3">
            <h3>Producto 3</h3>
            <p>Descripción breve del producto 3.</p>
            <span>$200</span>
            <button class="btn" onclick="agregarCarrito('Producto 3',200)">Agregar al pedido</button>
        </div>
    </section>

    <!-- CARRITO DE PEDIDOS -->
    <div class="carrito-box" id="carrito">
        <h3>Tu Pedido</h3>
        <div id="items-carrito"></div>
        <div class="carrito-total" id="total-carrito">Total: $0</div>
        <form action="https://formspree.io/f/tu-email-aqui" method="POST">
            <input type="text" name="nombre" placeholder="Tu nombre" required>
            <input type="email" name="email" placeholder="Correo" required>
            <input type="text" name="telefono" placeholder="Teléfono" required>
            <textarea name="mensaje" placeholder="Comentarios adicionales" rows="3"></textarea>
            <input type="hidden" name="pedido" id="pedido-form">
            <button type="submit" class="btn">Enviar Pedido</button>
        </form>
    </div>

    <script>
        let carrito = [];
        const itemsCarrito = document.getElementById('items-carrito');
        const totalCarrito = document.getElementById('total-carrito');
        const pedidoForm = document.getElementById('pedido-form');

        function agregarCarrito(nombre, precio) {
            carrito.push({nombre, precio});
            actualizarCarrito();
        }

        function actualizarCarrito() {
            itemsCarrito.innerHTML = '';
            let total = 0;
            carrito.forEach((item, index) => {
                total += item.precio;
                const div = document.createElement('div');
                div.className = 'carrito-item';
                div.innerHTML = `<span>${item.nombre} - $${item.precio}</span> <button onclick="eliminarItem(${index})">X</button>`;
                itemsCarrito.appendChild(div);
            });
            totalCarrito.textContent = `Total: $${total}`;
            pedidoForm.value = carrito.map(i=>i.nombre + ' $'+i.precio).join(', ');
        }

        function eliminarItem(index) {
            carrito.splice(index,1);
            actualizarCarrito();
        }
    </script>

</body>
</html>
