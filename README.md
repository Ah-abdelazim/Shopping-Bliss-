# Shopping-Bliss-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Bliss | Premium Online Store</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .product-card:hover .add-btn { opacity: 1; transform: translateY(0); }
        .view-transition { animation: fadeIn 0.3s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    </style>
</head>
<body class="bg-gray-50 text-gray-900">

    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-white/80 backdrop-blur-md z-50 border-b border-gray-100">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center gap-2 cursor-pointer" onclick="navigate('home')">
                    <div class="w-10 h-10 bg-indigo-600 rounded-xl flex items-center justify-center shadow-lg shadow-indigo-200">
                        <i data-lucide="shopping-bag" class="text-white w-6 h-6"></i>
                    </div>
                    <span class="text-xl font-bold tracking-tight text-gray-900">Shopping <span class="text-indigo-600">Bliss</span></span>
                </div>

                <div class="hidden md:flex items-center space-x-8 text-sm font-medium text-gray-600">
                    <button onclick="navigate('home')" class="hover:text-indigo-600 transition-colors">Home</button>
                    <button onclick="navigate('products')" class="hover:text-indigo-600 transition-colors">Shop</button>
                    <button onclick="navigate('contact')" class="hover:text-indigo-600 transition-colors">Contact</button>
                </div>

                <div class="flex items-center gap-4">
                    <button onclick="navigate('cart')" class="relative p-2 hover:bg-gray-100 rounded-full transition-colors">
                        <i data-lucide="shopping-cart" class="w-6 h-6 text-gray-700"></i>
                        <span id="cart-count" class="absolute -top-1 -right-1 bg-indigo-600 text-white text-[10px] font-bold w-5 h-5 flex items-center justify-center rounded-full border-2 border-white">0</span>
                    </button>
                    <button class="md:hidden" onclick="toggleMobileMenu()">
                        <i data-lucide="menu" class="w-6 h-6"></i>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content Area -->
    <main id="app-container" class="pt-20 min-h-screen">
        <!-- Content injected by JS -->
    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-gray-100 pt-16 pb-8">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-4 gap-12">
            <div class="col-span-1 md:col-span-2">
                <div class="flex items-center gap-2 mb-6">
                    <div class="w-8 h-8 bg-indigo-600 rounded-lg flex items-center justify-center">
                        <i data-lucide="shopping-bag" class="text-white w-5 h-5"></i>
                    </div>
                    <span class="text-lg font-bold tracking-tight">Shopping Bliss</span>
                </div>
                <p class="text-gray-500 max-w-sm mb-6 leading-relaxed">Your destination for premium quality products delivered with love. We focus on quality and customer satisfaction above all.</p>
                <div class="flex gap-4">
                <a href="#" class="p-2 bg-gray-50 rounded-lg hover:text-indigo-600 transition-colors"><i data-lucide="instagram" class="w-5 h-5"></i></a>
                    <a href="#" class="p-2 bg-gray-50 rounded-lg hover:text-indigo-600 transition-colors"><i data-lucide="facebook" class="w-5 h-5"></i></a>
                    <a href="#" class="p-2 bg-gray-50 rounded-lg hover:text-indigo-600 transition-colors"><i data-lucide="twitter" class="w-5 h-5"></i></a>
                </div>
            </div>
            <div>
                <h4 class="font-bold mb-6">Quick Links</h4>
                <ul class="space-y-4 text-sm text-gray-500">
                    <li><button onclick="navigate('home')" class="hover:text-indigo-600">Home</button></li>
                    <li><button onclick="navigate('products')" class="hover:text-indigo-600">All Products</button></li>
                    <li><button onclick="navigate('contact')" class="hover:text-indigo-600">Support</button></li>
                    <li><button onclick="navigate('admin')" class="text-gray-400 hover:text-indigo-600">Admin Dashboard</button></li>
                </ul>
            </div>
            <div>
                <h4 class="font-bold mb-6">Newsletter</h4>
                <p class="text-sm text-gray-500 mb-4">Subscribe to get special offers and once-in-a-lifetime deals.</p>
                <div class="flex gap-2">
                    <input type="email" placeholder="Your email" class="bg-gray-50 border border-gray-200 rounded-xl px-4 py-2 text-sm w-full focus:ring-2 focus:ring-indigo-500/20 focus:outline-none">
                    <button class="bg-indigo-600 text-white px-4 rounded-xl font-bold text-sm">Join</button>
                </div>
            </div>
        </div>
        <div class="max-w-7xl mx-auto px-4 mt-16 pt-8 border-t border-gray-100 text-center text-gray-400 text-xs">
            © 2024 Shopping Bliss Store. Built for Excellence.
        </div>
    </footer>

    <!-- Templates & Logic -->
    <script>
        // --- Store State ---
        const DEFAULT_PRODUCTS = [
            { id: 1, name: "Wireless Aura Headphones", price: 249, category: "Electronics", description: "Experience crystal clear sound with active noise cancellation and 40-hour battery life.", image: "🎧", featured: true },
            { id: 2, name: "Lunar Smart Watch", price: 199, category: "Wearables", description: "Track your health, sleep, and fitness with the most advanced sensors on your wrist.", image: "⌚", featured: true },
            { id: 3, name: "Minimalist Desk Lamp", price: 85, category: "Home", description: "Eye-friendly LED lighting with adjustable brightness and wireless charging base.", image: "💡", featured: true },
            { id: 4, name: "Cloud Cushion Sneakers", price: 120, category: "Fashion", description: "The most comfortable walking shoes you will ever own. Light as a feather.", image: "👟", featured: false },
            { id: 5, name: "Titanium Water Bottle", price: 45, category: "Lifestyle", description: "Double-walled vacuum insulation keeps your drinks cold for 24 hours.", image: "🍶", featured: false },
            { id: 6, name: "Zen Mechanical Keyboard", price: 160, category: "Electronics", description: "Tactile typing experience with custom RGB lighting and hot-swappable switches.", image: "⌨️", featured: true },
            { id: 7, name: "Vegan Leather Wallet", price: 55, category: "Accessories", description: "Slim, RFID-blocking wallet made from sustainable materials.", image: "👛", featured: false },
            { id: 8, name: "Pro Studio Microphone", price: 310, category: "Electronics", description: "Professional grade cardioid microphone for streaming and podcasting.", image: "🎙️", featured: false },
            { id: 9, name: "Ergo Office Chair", price: 499, category: "Home", description: "Premium ergonomic support for long working hours with mesh breathable back.", image: "💺", featured: false },
            { id: 10, name: "Compact Coffee Maker", price: 140, category: "Home", description: "Brews the perfect cup of artisan coffee in under 2 minutes.", image: "☕", featured: true }
        ];

        let products = JSON.parse(localStorage.getItem('sb_products')) || DEFAULT_PRODUCTS;
        let cart = JSON.parse(localStorage.getItem('sb_cart')) || [];
        let currentView = 'home';
        let filterCategory = 'All';
        let searchQuery = '';

        // --- Core Functions ---
        function saveToStorage() {
            localStorage.setItem('sb_products', JSON.stringify(products));
            localStorage.setItem('sb_cart', JSON.stringify(cart));
            updateCartUI();
        }

        function navigate(view, id = null) {
            currentView = view;
            window.scrollTo(0, 0);
            render();
        }

        function updateCartUI() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cart-count').innerText = count;
        }

        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existing = cart.find(item => item.id === productId);
            if (existing) {
                existing.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            saveToStorage();
            showToast(Added ${product.name} to cart!);
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            saveToStorage();
            render();
        }

        function updateCartQty(productId, delta) {
            const item = cart.find(i => i.id === productId);
            if (item) {
                item.quantity += delta;
                if (item.quantity < 1) removeFromCart(productId);
                else {
                    saveToStorage();
                    render();
                }
            }
        }

        function showToast(message) {
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-8 right-8 bg-gray-900 text-white px-6 py-3 rounded-2xl shadow-2xl z-[100] animate-bounce';
            toast.innerText = message;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 3000);
        }

        // --- Views ---
        const Views = {
            home: () => `
                <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 view-transition">
                    <div class="relative bg-indigo-600 rounded-[3rem] overflow-hidden p-12 md:p-24 flex items-center min-h-[500px]">
                        <div class="relative z-10 max-w-xl text-white">
                            <span class="inline-block py-1 px-3 bg-indigo-500 rounded-full text-xs font-bold mb-6 tracking-widest uppercase">Premium Collection</span>
                            <h2 class="text-5xl md:text-7xl font-extrabold mb-8 leading-tight">Elevate Your Lifestyle.</h2>
                            <p class="text-indigo-100 text-lg mb-10 opacity-90">Discover our curated selection of high-end tech, minimalist home goods, and fashion essentials at Shopping Bliss.</p>
                            <button onclick="navigate('products')" class="bg-white text-indigo-600 font-bold px-8 py-4 rounded-2xl hover:bg-indigo-50 transition-all flex items-center gap-2 group">
                                Start Shopping <i data-lucide="arrow-right" class="w-5 h-5 group-hover:translate-x-1 transition-transform"></i>
                            </button>
                        </div>
                        <div class="absolute right-0 bottom-0 opacity-20 md:opacity-100 transform translate-y-10 translate-x-10 pointer-events-none">
                            <span class="text-[300px]">🛍️</span>
                        </div>
                    </div>
<div class="mt-24">
                        <div class="flex justify-between items-end mb-12">
                            <div>
                                <h3 class="text-3xl font-bold mb-2">Featured Products</h3>
                                <p class="text-gray-500">Handpicked items our customers love the most.</p>
                            </div>
                            <button onclick="navigate('products')" class="text-indigo-600 font-bold flex items-center gap-1 hover:underline">View All <i data-lucide="chevron-right" class="w-4 h-4"></i></button>
                        </div>
                        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                            ${products.filter(p => p.featured).map(p => ProductCard(p)).join('')}
                        </div>
                    </div>
                </section>
            ,

            products: () => {
                const categories = ['All', ...new Set(products.map(p => p.category))];
                const filtered = products.filter(p => {
                    const matchCat = filterCategory === 'All' || p.category === filterCategory;
                    const matchSearch = p.name.toLowerCase().includes(searchQuery.toLowerCase());
                    return matchCat && matchSearch;
                });

                return 
                <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 view-transition">
                    <div class="flex flex-col md:flex-row md:items-center justify-between gap-6 mb-12">
                        <h2 class="text-4xl font-bold">Our Collection</h2>
                        <div class="flex flex-wrap gap-4 items-center">
                            <div class="relative">
                                <i data-lucide="search" class="absolute left-3 top-1/2 -translate-y-1/2 w-4 h-4 text-gray-400"></i>
                                <input type="text" placeholder="Search products..." 
                                    oninput="searchQuery = this.value; render()" 
                                    value="${searchQuery}"
                                    class="bg-white border border-gray-200 rounded-xl py-2.5 pl-10 pr-4 text-sm w-full md:w-64 focus:ring-2 focus:ring-indigo-500/20 focus:outline-none transition-all">
                            </div>
                            <select onchange="filterCategory = this.value; render()" class="bg-white border border-gray-200 rounded-xl py-2.5 px-4 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500/20">
                                ${categories.map(c => <option value="${c}" ${filterCategory === c ? 'selected' : ''}>${c}</option>).join('')}
                            </select>
                        </div>
                    </div>

                    ${filtered.length === 0 ? 
                        <div class="py-20 text-center">
                            <i data-lucide="package-search" class="w-16 h-16 text-gray-300 mx-auto mb-4"></i>
                            <h3 class="text-xl font-bold text-gray-900">No products found</h3>
                            <p class="text-gray-500 mt-2">Try adjusting your filters or search terms.</p>
                        </div>
                     : 
                        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                            ${filtered.map(p => ProductCard(p)).join('')}
                        </div>
                    }
                </section>
            ;
            },

            cart: () => {
                const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                return 
                <section class="max-w-5xl mx-auto px-4 py-12 view-transition">
                <h2 class="text-3xl font-bold mb-8">Your Cart</h2>
                    ${cart.length === 0 ? 
                        <div class="bg-white rounded-3xl p-12 text-center border border-gray-100">
                            <div class="w-24 h-24 bg-gray-50 rounded-full flex items-center justify-center mx-auto mb-6 text-4xl">🛒</div>
                            <h3 class="text-2xl font-bold text-gray-900">Your cart is empty</h3>
                            <p class="text-gray-500 mt-2 mb-8">Looks like you haven't added anything to your cart yet.</p>
                            <button onclick="navigate('products')" class="bg-indigo-600 text-white font-bold px-8 py-3 rounded-xl hover:bg-indigo-700 transition-colors">Start Shopping</button>
                        </div>
                     : 
                        <div class="grid grid-cols-1 lg:grid-cols-3 gap-12">
                            <div class="lg:col-span-2 space-y-4">
                                ${cart.map(item => 
                                    <div class="bg-white p-4 rounded-2xl border border-gray-100 flex gap-4 items-center">
                                        <div class="w-20 h-20 bg-gray-50 rounded-xl flex items-center justify-center text-3xl shrink-0">${item.image}</div>
                                        <div class="flex-1">
                                            <h4 class="font-bold text-gray-900">${item.name}</h4>
                                            <p class="text-indigo-600 font-bold">$${item.price}</p>
                                        </div>
                                        <div class="flex items-center gap-3 bg-gray-50 rounded-lg px-2 py-1">
                                            <button onclick="updateCartQty(${item.id}, -1)" class="p-1 hover:text-indigo-600"><i data-lucide="minus" class="w-4 h-4"></i></button>
                                            <span class="font-bold w-4 text-center text-sm">${item.quantity}</span>
                                            <button onclick="updateCartQty(${item.id}, 1)" class="p-1 hover:text-indigo-600"><i data-lucide="plus" class="w-4 h-4"></i></button>
                                        </div>
                                        <button onclick="removeFromCart(${item.id})" class="text-gray-300 hover:text-red-500 transition-colors">
                                            <i data-lucide="trash-2" class="w-5 h-5"></i>
                                        </button>
                                    </div>
                                `).join('')}
                            </div>
                            <div class="bg-white p-8 rounded-3xl border border-gray-100 h-fit">
                                <h3 class="text-xl font-bold mb-6">Order Summary</h3>
                                <div class="space-y-4 mb-6">
                                    <div class="flex justify-between text-gray-500"><span>Subtotal</span><span>$${subtotal.toLocaleString()}</span></div>
                                    <div class="flex justify-between text-gray-500"><span>Shipping</span><span class="text-green-600 font-bold">Free</span></div>
                                    <div class="border-t border-gray-100 pt-4 flex justify-between font-bold text-xl"><span>Total</span><span>$${subtotal.toLocaleString()}</span></div>
                                </div>
                                <button onclick="checkoutViaWhatsApp()" class="w-full bg-green-600 text-white font-bold py-4 rounded-xl flex items-center justify-center gap-2 hover:bg-green-700 transition-all shadow-lg shadow-green-100">
                                    <i data-lucide="message-circle" class="w-5 h-5"></i>
                                    Checkout via WhatsApp
                                    </button>
                                <p class="text-[10px] text-gray-400 mt-4 text-center">Fast delivery within 3-5 business days.</p>
                            </div>
                        </div>
                    }
                </section>
            ;
            },

            admin: () => `
                <section class="max-w-7xl mx-auto px-4 py-12 view-transition">
                    <div class="flex justify-between items-center mb-10">
                        <h2 class="text-3xl font-bold">Admin Dashboard</h2>
                        <button onclick="showAdminModal()" c
