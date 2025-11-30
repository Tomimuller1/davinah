<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> DAVINAH - Velas de Lujo</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            background: #000;
            color: #fff;
            overflow-x: hidden;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            background: linear-gradient(135deg, #1a1a1a 0%, #000 100%);
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 150%;
            height: 150%;
            background: radial-gradient(circle, rgba(255,215,0,0.1) 0%, transparent 70%);
            animation: pulse 8s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.3; }
            50% { transform: scale(1.1); opacity: 0.5; }
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            padding: 0 20px;
        }

        .hero h1 {
            font-size: clamp(3rem, 8vw, 7rem);
            font-weight: 700;
            letter-spacing: -0.02em;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #fff 0%, #d4af37 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: fadeInUp 1s ease-out;
        }

        .hero p {
            font-size: clamp(1.2rem, 2vw, 1.8rem);
            font-weight: 300;
            color: #ccc;
            margin-bottom: 40px;
            animation: fadeInUp 1s ease-out 0.2s backwards;
        }

        .cta-button {
            display: inline-block;
            padding: 18px 50px;
            background: #fff;
            color: #000;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            animation: fadeInUp 1s ease-out 0.4s backwards;
            box-shadow: 0 10px 40px rgba(255,255,255,0.2);
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 50px rgba(255,255,255,0.3);
            background: #d4af37;
            color: #fff;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 25px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(10px);
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: 0.1em;
            color: #d4af37;
        }

        /* Cart Icon */
        .cart-icon {
            position: relative;
            cursor: pointer;
            font-size: 1.5rem;
            transition: transform 0.3s ease;
        }

        .cart-icon:hover {
            transform: scale(1.1);
        }

        .cart-badge {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #d4af37;
            color: #000;
            border-radius: 50%;
            width: 22px;
            height: 22px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            font-weight: 700;
        }

        /* Cart Panel */
        .cart-panel {
            position: fixed;
            top: 0;
            right: -450px;
            width: 450px;
            height: 100vh;
            background: #0a0a0a;
            box-shadow: -5px 0 30px rgba(0,0,0,0.5);
            z-index: 2000;
            transition: right 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            display: flex;
            flex-direction: column;
        }

        .cart-panel.open {
            right: 0;
        }

        .cart-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            backdrop-filter: blur(5px);
            z-index: 1999;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.4s ease;
        }

        .cart-overlay.active {
            opacity: 1;
            pointer-events: all;
        }

        .cart-header {
            padding: 30px;
            border-bottom: 1px solid #222;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cart-title {
            font-size: 1.8rem;
            font-weight: 700;
        }

        .close-cart {
            background: none;
            border: none;
            color: #fff;
            font-size: 1.8rem;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .close-cart:hover {
            transform: rotate(90deg);
        }

        .cart-items {
            flex: 1;
            overflow-y: auto;
            padding: 20px 30px;
        }

        .cart-item {
            display: flex;
            gap: 20px;
            padding: 20px 0;
            border-bottom: 1px solid #1a1a1a;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .cart-item-image {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #1a1a1a 0%, #2a2a2a 100%);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-name {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .cart-item-price {
            color: #d4af37;
            font-weight: 600;
            margin-bottom: 12px;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .qty-btn {
            width: 30px;
            height: 30px;
            border: 1px solid #333;
            background: transparent;
            color: #fff;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1rem;
        }

        .qty-btn:hover {
            background: #d4af37;
            border-color: #d4af37;
            color: #000;
        }

        .quantity {
            font-weight: 600;
            min-width: 30px;
            text-align: center;
        }

        .remove-item {
            background: none;
            border: none;
            color: #666;
            cursor: pointer;
            font-size: 1.2rem;
            transition: color 0.3s ease;
            margin-left: 10px;
        }

        .remove-item:hover {
            color: #ff4444;
        }

        .empty-cart {
            text-align: center;
            padding: 60px 20px;
            color: #666;
        }

        .empty-cart-icon {
            font-size: 4rem;
            margin-bottom: 20px;
            opacity: 0.3;
        }

        .cart-footer {
            padding: 30px;
            border-top: 1px solid #222;
            background: #000;
        }

        .cart-subtotal {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            font-size: 1rem;
            color: #999;
        }

        .cart-total {
            display: flex;
            justify-content: space-between;
            margin-bottom: 25px;
            font-size: 1.5rem;
            font-weight: 700;
        }

        .cart-total-amount {
            color: #d4af37;
        }

        .checkout-button {
            width: 100%;
            padding: 18px;
            background: #d4af37;
            color: #000;
            border: none;
            border-radius: 50px;
            font-weight: 700;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .checkout-button:hover {
            background: #fff;
            transform: scale(1.02);
        }

        .checkout-button:disabled {
            background: #333;
            color: #666;
            cursor: not-allowed;
            transform: none;
        }

        .nav-links {
            display: flex;
            gap: 40px;
            list-style: none;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #d4af37;
        }

        /* Mobile Cart */
        @media (max-width: 768px) {
            .cart-panel {
                width: 100%;
                right: -100%;
          }
        }

        /* Collection Section */
        .collection {
            padding: 120px 50px;
            background: #0a0a0a;
        }

        .section-title {
            text-align: center;
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 700;
            margin-bottom: 80px;
            letter-spacing: -0.02em;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 60px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .product-card {
            background: #111;
            border-radius: 20px;
            overflow: hidden;
            transition: transform 0.5s ease, box-shadow 0.5s ease, background 0.5s ease;
            cursor: pointer;
            position: relative;
        }

        .product-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(212,175,55,0.15) 0%, rgba(255,215,0,0.1) 100%);
            opacity: 0;
            transition: opacity 0.5s ease;
            z-index: 1;
            pointer-events: none;
        }

        .product-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 30px 60px rgba(212,175,55,0.3);
            background: linear-gradient(135deg, #1a1a1a 0%, #2a2020 100%);
        }

        .product-card:hover::before {
            opacity: 1;
        }

        .product-image {
            width: 100%;
            height: 400px;
            background: linear-gradient(135deg, #1a1a1a 0%, #2a2a2a 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            transition: background 0.5s ease;
            z-index: 2;
        }

        .product-card:hover .product-image {
            background: linear-gradient(135deg, #2a2520 0%, #3a3020 100%);
        }

        .product-image::before {
            content: '';
            position: absolute;
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, rgba(212,175,55,0.3) 0%, transparent 70%);
            border-radius: 50%;
            animation: glow 3s ease-in-out infinite;
            transition: all 0.5s ease;
        }

        .product-card:hover .product-image::before {
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(212,175,55,0.5) 0%, rgba(255,215,0,0.3) 50%, transparent 70%);
        }

        .candle-icon {
            font-size: 120px;
            z-index: 2;
            filter: drop-shadow(0 0 20px rgba(212,175,55,0.5));
        }

        .product-info {
            padding: 35px;
            position: relative;
            z-index: 2;
        }

        .product-name {
            font-size: 1.8rem;
            font-weight: 600;
            margin-bottom: 12px;
            color: #fff;
        }

        .product-description {
            font-size: 1rem;
            color: #999;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .product-price {
            font-size: 2rem;
            font-weight: 700;
            color: #d4af37;
            margin-bottom: 25px;
        }

        .buy-button {
            width: 100%;
            padding: 15px;
            background: #fff;
            color: #000;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .buy-button:hover {
            background: #d4af37;
            color: #fff;
            transform: scale(1.02);
        }

        /* Features Section */
        .features {
            padding: 120px 50px;
            background: #000;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 50px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .feature-item {
            text-align: center;
            padding: 40px 30px;
            background: rgba(255,255,255,0.03);
            border-radius: 20px;
            transition: all 0.3s ease;
        }

        .feature-item:hover {
            background: rgba(212,175,55,0.1);
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 20px;
        }

        .feature-title {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 15px;
        }

        .feature-text {
            color: #999;
            line-height: 1.6;
        }

        /* Footer */
        footer {
            padding: 60px 50px;
            background: #0a0a0a;
            text-align: center;
            border-top: 1px solid #222;
        }

        footer p {
            color: #666;
            font-size: 0.9rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            nav {
                padding: 20px 25px;
            }

            .nav-links {
                gap: 20px;
                font-size: 0.9rem;
            }

            .collection, .features {
                padding: 80px 25px;
            }

            .products-grid {
                grid-template-columns: 1fr;
                gap: 40px;
            }
        }

        /* Scroll Animation */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="logo">DAVINAH</div>
        <ul class="nav-links">
            <li><a href="#coleccion">Colección</a></li>
            <li><a href="#caracteristicas">Características</a></li>
            <li><a href="#contacto">Contacto</a></li>
        </ul>
        <div class="cart-icon" onclick="toggleCart()">
            🛒
            <span class="cart-badge" id="cartBadge">0</span>
        </div>
    </nav>

    <!-- Cart Overlay -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>

    <!-- Cart Panel -->
    <div class="cart-panel" id="cartPanel">
        <div class="cart-header">
            <h2 class="cart-title">Tu Carrito</h2>
            <button class="close-cart" onclick="toggleCart()">✕</button>
        </div>
        <div class="cart-items" id="cartItems">
            <div class="empty-cart">
                <div class="empty-cart-icon">🛒</div>
                <p>Tu carrito está vacío</p>
            </div>
        </div>
        <div class="cart-footer">
            <div class="cart-subtotal">
                <span>Subtotal:</span>
                <span id="cartSubtotal">$0</span>
            </div>
            <div class="cart-total">
                <span>Total:</span>
                <span class="cart-total-amount" id="cartTotal">$0</span>
            </div>
            <button class="checkout-button" id="checkoutBtn" disabled onclick="checkout()">
                Enviar Pedido por WhatsApp 💬
            </button>
        </div>
    </div>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1> DAVINAH</h1>
            <p>Ilumina tu mundo con elegancia</p>
            <a href="#coleccion" class="cta-button">Descubre la Colección</a>
        </div>
    </section>

    <!-- Collection Section -->
<section id="coleccion" class="collection">
    <h2 class="section-title fade-in">Nuestra Colección</h2>
    <div class="products-grid">

        <!-- Product 1 -->
        <div class="product-card fade-in">
            <div class="product-image">
                <img src="https://i.postimg.cc/nrJSgyj1/Whats-App-Image-2025-11-30-at-5-23-28-PM.jpg" alt="Essence Noir Candle">
            </div>
            <div class="product-info">
                <h3 class="product-name">Essence Noir</h3>
                <p class="product-description">Fragancia de vainilla bourbon y ámbar negro. Una experiencia sensorial única.</p>
                <div class="product-price">$89</div>
                <button class="buy-button">Añadir al Carrito</button>
            </div>
        </div>


            <!-- Product 2 -->
        <div class="product-card fade-in">
            <div class="product-image">
                <img src="https://i.postimg.cc/v8hvGgpF/Whats-App-Image-2025-11-30-at-5-23-27-PM.jpg">
            </div>
            <div class="product-info">
                <h3 class="product-name">Golden Hour</h3>
                <p class="product-description">Notas de bergamota, jazmín y madera de cedro. Elegancia en cada momento.</p>
                <div class="product-price">$95</div>
                <button class="buy-button">Añadir al Carrito</button>
            </div>
        </div>

        <!-- Product 3 -->
        <div class="product-card fade-in">
            <div class="product-image">
                <img src="https://i.postimg.cc/3J6mwg9J/Whats-App-Image-2025-11-30-at-5-23-28-PM-(1).jpg" alt="Midnight Rose Candle">
            </div>
            <div class="product-info">
                <h3 class="product-name">Midnight Rose</h3>
                <p class="product-description">Rosa damascena y pachulí. Sofisticación que perdura en el tiempo.</p>
                <div class="product-price">$92</div>
                <button class="buy-button">Añadir al Carrito</button>
            </div>
        </div>

    </div>
</section>

    <!-- Features Section -->
    <section id="caracteristicas" class="features">
        <h2 class="section-title fade-in">Excelencia en Cada Detalle</h2>
        <div class="features-grid">
            <div class="feature-item fade-in">
                <div class="feature-icon">🌿</div>
                <h3 class="feature-title">100% Natural</h3>
                <p class="feature-text">Cera de soja orgánica y aceites esenciales puros. Sin parabenos ni químicos.</p>
            </div>
            <div class="feature-item fade-in">
                <div class="feature-icon">⏱️</div>
                <h3 class="feature-title">60+ Horas</h3>
                <p class="feature-text">Duración excepcional con combustión limpia y uniforme.</p>
            </div>
            <div class="feature-item fade-in">
                <div class="feature-icon">🎨</div>
                <h3 class="feature-title">Diseño Premium</h3>
                <p class="feature-text">Envases de vidrio soplado a mano. Arte funcional para tu hogar.</p>
            </div>
            <div class="feature-item fade-in">
                <div class="feature-icon">🌍</div>
                <h3 class="feature-title">Sostenible</h3>
                <p class="feature-text">Producción ética y empaques reciclables. Lujo consciente.</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contacto">
        <p>&copy; 2025 DAVINAH. Todos los derechos reservados. | Diseñado con pasión</p>
    </footer>

    <script>
        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                target.scrollIntoView({ behavior: 'smooth', block: 'start' });
            });
        });

        // Scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

        // Shopping Cart System
        let cart = [];

        // Toggle cart panel
        function toggleCart() {
            const cartPanel = document.getElementById('cartPanel');
            const cartOverlay = document.getElementById('cartOverlay');
            cartPanel.classList.toggle('open');
            cartOverlay.classList.toggle('active');
        }

        // Add to cart
        function addToCart(name, price) {
            const existingItem = cart.find(item => item.name === name);
            
            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({
                    name: name,
                    price: price,
                    quantity: 1
                });
            }
            
            updateCart();
            updateCartBadge();
        }

        // Remove from cart
        function removeFromCart(name) {
            cart = cart.filter(item => item.name !== name);
            updateCart();
            updateCartBadge();
        }

        // Update quantity
        function updateQuantity(name, change) {
            const item = cart.find(item => item.name === name);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(name);
                } else {
                    updateCart();
                    updateCartBadge();
                }
            }
        }

        // Update cart display
        function updateCart() {
            const cartItemsContainer = document.getElementById('cartItems');
            
            if (cart.length === 0) {
                cartItemsContainer.innerHTML = `
                    <div class="empty-cart">
                        <div class="empty-cart-icon">🛒</div>
                        <p>Tu carrito está vacío</p>
                    </div>
                `;
                document.getElementById('checkoutBtn').disabled = true;
            } else {
                cartItemsContainer.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <div class="cart-item-image">🕯️</div>
                        <div class="cart-item-details">
                            <div class="cart-item-name">${item.name}</div>
                            <div class="cart-item-price">$${item.price}</div>
                            <div class="quantity-controls">
                                <button class="qty-btn" onclick="updateQuantity('${item.name}', -1)">−</button>
                                <span class="quantity">${item.quantity}</span>
                                <button class="qty-btn" onclick="updateQuantity('${item.name}', 1)">+</button>
                                <button class="remove-item" onclick="removeFromCart('${item.name}')">🗑️</button>
                            </div>
                        </div>
                    </div>
                `).join('');
                document.getElementById('checkoutBtn').disabled = false;
            }
            
            updateCartTotal();
        }

        // Update cart badge
        function updateCartBadge() {
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cartBadge').textContent = totalItems;
        }

        // Update cart total
        function updateCartTotal() {
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            document.getElementById('cartSubtotal').textContent = `$${subtotal}`;
            document.getElementById('cartTotal').textContent = `$${subtotal}`;
        }

        // Checkout function
        function checkout() {
            if (cart.length === 0) return;
            
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const itemCount = cart.reduce((sum, item) => sum + item.quantity, 0);
            
            // Build WhatsApp message
            let message = '🕯️ *PEDIDO LUMIÈRE* 🕯️\n\n';
            message += '📦 *Productos:*\n';
            
            cart.forEach(item => {
                message += `• ${item.quantity}x ${item.name} - $${item.price * item.quantity}\n`;
            });
            
            message += '\n━━━━━━━━━━━━━━━━━━━━\n';
            message += `📊 *Total de artículos:* ${itemCount}\n`;
            message += `💰 *TOTAL A PAGAR:* $${total}\n`;
            message += '━━━━━━━━━━━━━━━━━━━━\n\n';
            message += '📝 *Mensaje adicional:* (Escribe aquí cualquier comentario o instrucción especial)\n\n';
            message += '¡Gracias por tu compra! 🌟';
            
            // Encode message for URL
            const encodedMessage = encodeURIComponent(message);
            
            // WhatsApp link (remove + and spaces from phone number)
            const whatsappNumber = '543446627368';
            const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;
            
            // Redirect to WhatsApp
            window.open(whatsappURL, '_blank');
        }

        // Add to cart functionality
        document.querySelectorAll('.buy-button').forEach(button => {
            button.addEventListener('click', function() {
                const productCard = this.closest('.product-card');
                const productName = productCard.querySelector('.product-name').textContent;
                const productPrice = parseInt(productCard.querySelector('.product-price').textContent.replace('$', ''));
                
                // Add to cart
                addToCart(productName, productPrice);
                
                // Visual feedback
                this.textContent = '✓ Añadido';
                this.style.background = '#d4af37';
                this.style.color = '#fff';
                
                setTimeout(() => {
                    this.textContent = 'Añadir al Carrito';
                    this.style.background = '#fff';
                    this.style.color = '#000';
                }, 1000);
            });
        });
    </script>
</body>
</html>
