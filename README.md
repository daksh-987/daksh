<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Gift Haven - Premium Gift Shop</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
        }
        
        .heading-font {
            font-family: 'Playfair Display', serif;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4e8f0 100%);
        }
        
        .hero-gradient {
            background: linear-gradient(to right, rgba(0,0,0,0.7), rgba(0,0,0,0.2)), url('https://placehold.co/1600x900') center/cover;
        }
        
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
        }
        
        .cart-preview {
            transition: all 0.3s ease;
        }
        
        #cartDrawer {
            transition: transform 0.3s ease-out;
        }
        
        .fade-in {
            animation: fadeIn 0.5s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .category-filter {
            transition: all 0.2s ease;
        }
        
        .category-filter:hover {
            transform: scale(1.05);
            background-color: #f8f9fa;
        }
    </style>
</head>
<body class="bg-white">
    <!-- Header/Navbar -->
    <header class="bg-white shadow-sm sticky top-0 z-50">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center">
                <a href="index.html" class="text-2xl font-bold heading-font text-indigo-700">The Gift Haven</a>
            </div>
            
            <nav class="hidden md:flex space-x-8">
                <a href="#home" class="text-gray-700 hover:text-indigo-600">Home</a>
                <a href="#shop" class="text-gray-700 hover:text-indigo-600">Shop</a>
                <a href="#categories" class="text-gray-700 hover:text-indigo-600">Categories</a>
                <a href="#about" class="text-gray-700 hover:text-indigo-600">About</a>
                <a href="#contact" class="text-gray-700 hover:text-indigo-600">Contact</a>
            </nav>
            
            <div class="flex items-center space-x-4">
                <button id="searchBtn" class="p-2 rounded-full hover:bg-gray-100">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                    </svg>
                </button>
                
                <button id="cartBtn" class="p-2 rounded-full hover:bg-gray-100 relative">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
                    </svg>
                    <span id="cartCount" class="absolute -top-1 -right-1 bg-indigo-600 text-white text-xs rounded-full h-5 w-5 flex items-center justify-center hidden">0</span>
                </button>
                
                <button class="md:hidden p-2 rounded-full hover:bg-gray-100" id="mobileMenuBtn">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>
        
        <!-- Mobile Menu -->
        <div id="mobileMenu" class="hidden md:hidden bg-white border-t">
            <div class="container mx-auto px-4 py-2">
                <a href="#home" class="block py-2 text-gray-700 hover:text-indigo-600">Home</a>
                <a href="#shop" class="block py-2 text-gray-700 hover:text-indigo-600">Shop</a>
                <a href="#categories" class="block py-2 text-gray-700 hover:text-indigo-600">Categories</a>
                <a href="#about" class="block py-2 text-gray-700 hover:text-indigo-600">About</a>
                <a href="#contact" class="block py-2 text-gray-700 hover:text-indigo-600">Contact</a>
            </div>
        </div>
        
        <!-- Search Overlay -->
        <div id="searchOverlay" class="hidden absolute top-0 left-0 w-full bg-white shadow-md z-50">
            <div class="container mx-auto px-4 py-3 flex">
                <input type="text" placeholder="Search for gifts..." class="flex-grow px-4 py-2 border rounded-l-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                <button class="bg-indigo-600 text-white px-6 py-2 rounded-r-lg hover:bg-indigo-700">Search</button>
                <button id="closeSearchBtn" class="ml-4 text-gray-500 hover:text-gray-700">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </div>
    </header>

    <!-- Hero Section (Shop Now Page) -->
    <section id="home" class="hero-gradient text-white py-20 md:py-32">
        <div class="container mx-auto px-4">
            <div class="max-w-2xl">
                <h1 class="text-4xl md:text-6xl font-bold heading-font mb-4">Thoughtful Gifts for Every Occasion</h1>
                <p class="text-xl mb-8">Discover handpicked treasures that say "I care" in the most special way</p>
                <div class="flex flex-wrap gap-4">
                    <a href="#shop" class="bg-white text-indigo-700 px-8 py-3 rounded-lg font-medium hover:bg-indigo-50 transition duration-300">Shop Now</a>
                    <a href="#categories" class="border-2 border-white text-white px-8 py-3 rounded-lg font-medium hover:bg-white hover:text-indigo-700 transition duration-300">Browse Categories</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Featured Categories -->
    <section id="categories" class="py-12 bg-white">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl font-bold heading-font text-center mb-12">Popular Gift Categories</h2>
            
            <div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-4">
                <div class="category-filter bg-indigo-50 p-4 rounded-lg text-center cursor-pointer hover:shadow-md transition">
                    <div class="w-16 h-16 mx-auto mb-3 bg-white rounded-full flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                    </div>
                    <h3 class="font-semibold">Birthdays</h3>
                </div>
                
                <div class="category-filter bg-indigo-50 p-4 rounded-lg text-center cursor-pointer hover:shadow-md transition">
                    <div class="w-16 h-16 mx-auto mb-3 bg-white rounded-full flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M5 17v4M3 19h4m10-16v4m-2-2h4m-4 12v4m-2-2h4M12 8a4 4 0 100-8 4 4 0 000 8z" />
                        </svg>
                    </div>
                    <h3 class="font-semibold">Anniversaries</h3>
                </div>
                
                <div class="category-filter bg-indigo-50 p-4 rounded-lg text-center cursor-pointer hover:shadow-md transition">
                    <div class="w-16 h-16 mx-auto mb-3 bg-white rounded-full flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                        </svg>
                    </div>
                    <h3 class="font-semibold">Holidays</h3>
                </div>
                
                <div class="category-filter bg-indigo-50 p-4 rounded-lg text-center cursor-pointer hover:shadow-md transition">
                    <div class="w-16 h-16 mx-auto mb-3 bg-white rounded-full flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 4v16M17 4v16M3 8h4m10 0h4M3 12h18M3 16h4m10 0h4M4 20h16a1 1 0 001-1V5a1 1 0 00-1-1H4a1 1 0 00-1 1v14a1 1 0 001 1z" />
                        </svg>
                    </div>
                    <h3 class="font-semibold">Weddings</h3>
                </div>
                
                <div class="category-filter bg-indigo-50 p-4 rounded-lg text-center cursor-pointer hover:shadow-md transition">
                    <div class="w-16 h-16 mx-auto mb-3 bg-white rounded-full flex items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                    </div>
                    <h3 class="font-semibold">Just Because</h3>
                </div>
            </div>
        </div>
    </section>

    <!-- Product Listing Section -->
    <section id="shop" class="py-12 gradient-bg">
        <div class="container mx-auto px-4">
            <div class="flex justify-between items-center mb-8">
                <h2 class="text-3xl font-bold heading-font">Our Gift Selection</h2>
                <div class="flex items-center">
                    <label for="sort" class="mr-2">Sort by:</label>
                    <select id="sort" class="border rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        <option value="popular">Most Popular</option>
                        <option value="price-low">Price: Low to High</option>
                        <option value="price-high">Price: High to Low</option>
                        <option value="newest">Newest Arrivals</option>
                        <option value="rating">Highest Rated</option>
                    </select>
                </div>
            </div>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
                <!-- Product 1 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <div class="relative">
                        <img src="https://placehold.co/500x500" alt="Personalized Engraved Crystal Photo Frame with elegant floral engraving on silver frame" class="w-full h-64 object-cover"/>
                        <div class="absolute top-2 right-2 bg-indigo-600 text-white px-2 py-1 rounded-full text-xs font-medium">Bestseller</div>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Personalized Photo Frame</h3>
                            <span class="text-indigo-600 font-bold">$39.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Elegant engraved crystal</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★☆
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(127)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="1" data-name="Personalized Photo Frame" data-price="39.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 2 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <div class="relative">
                        <img src="https://placehold.co/500x500" alt="Handcrafted Leather Journal with handmade paper and brass clasp details" class="w-full h-64 object-cover"/>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Handmade Leather Journal</h3>
                            <span class="text-indigo-600 font-bold">$49.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Premium quality leather</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★★
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(89)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="2" data-name="Handmade Leather Journal" data-price="49.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 3 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <div class="relative">
                        <img src="https://placehold.co/500x500" alt="Customizable Gift Box Set with assorted premium chocolates and artisan tea selection" class="w-full h-64 object-cover"/>
                        <div class="absolute top-2 right-2 bg-red-500 text-white px-2 py-1 rounded-full text-xs font-medium">Sale</div>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Luxury Gift Box Set</h3>
                            <div>
                                <span class="text-red-500 font-bold">$59.99</span>
                                <span class="text-gray-400 text-sm line-through ml-2">$79.99</span>
                            </div>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Chocolates & premium tea</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★☆
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(214)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="3" data-name="Luxury Gift Box Set" data-price="59.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 4 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <div class="relative">
                        <img src="https://placehold.co/500x500" alt="Sterling Silver Infinity Necklace with elegant chain and minimalist design" class="w-full h-64 object-cover"/>
                        <div class="absolute top-2 right-2 bg-green-500 text-white px-2 py-1 rounded-full text-xs font-medium">New</div>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Infinity Silver Necklace</h3>
                            <span class="text-indigo-600 font-bold">$129.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">925 Sterling Silver</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★★
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(45)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="4" data-name="Infinity Silver Necklace" data-price="129.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 5 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <img src="https://placehold.co/500x500" alt="Scented Candle Gift Set with bamboo wicks and premium soy wax in three fragrances" class="w-full h-64 object-cover"/>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Aromatic Candle Set</h3>
                            <span class="text-indigo-600 font-bold">$34.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">3 Premium fragrances</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★☆
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(72)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="5" data-name="Aromatic Candle Set" data-price="34.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 6 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <div class="relative">
                        <img src="https://placehold.co/500x500" alt="Personalized Map Coordinates Art Print with custom location in minimalist black frame" class="w-full h-64 object-cover"/>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Custom Map Art Print</h3>
                            <span class="text-indigo-600 font-bold">$29.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Personalized location art</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★☆
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(156)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="6" data-name="Custom Map Art Print" data-price="29.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 7 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <div class="relative">
                        <img src="https://placehold.co/500x500" alt="Gourmet Coffee Sampler Box with 12 single-origin beans from around the world" class="w-full h-64 object-cover"/>
                        <div class="absolute top-2 right-2 bg-indigo-600 text-white px-2 py-1 rounded-full text-xs font-medium">Bestseller</div>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Gourmet Coffee Sampler</h3>
                            <span class="text-indigo-600 font-bold">$44.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">12 world regions</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★★
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(183)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="7" data-name="Gourmet Coffee Sampler" data-price="44.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
                
                <!-- Product 8 -->
                <div class="product-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300 cursor-pointer">
                    <img src="https://placehold.co/500x500" alt="Hand-knit Cashmere Scarf in soft gray with tassel details, made in Nepal" class="w-full h-64 object-cover"/>
                    <div class="p-4">
                        <div class="flex justify-between items-start">
                            <h3 class="font-semibold text-lg mb-1">Cashmere Scarf</h3>
                            <span class="text-indigo-600 font-bold">$89.99</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">100% Grade A Cashmere</p>
                        <div class="flex items-center mb-2">
                            <div class="flex text-yellow-400">
                                ★★★★☆
                            </div>
                            <span class="text-gray-500 text-sm ml-1">(62)</span>
                        </div>
                        <button class="w-full bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-300 add-to-cart" data-id="8" data-name="Cashmere Scarf" data-price="89.99" data-image="https://placehold.co/500x500">Add to Cart</button>
                    </div>
                </div>
            </div>
            
            <div class="mt-10 flex justify-center">
                <button class="bg-white text-indigo-600 px-6 py-3 rounded-lg border-2 border-indigo-600 hover:bg-indigo-50 transition duration-300">Load More</button>
            </div>
        </div>
    </section>

    <!-- Cart Drawer -->
    <div id="cartDrawer" class="fixed top-0 right-0 w-full md:w-96 h-full bg-white shadow-lg transform translate-x-full z-50 overflow-y-auto">
        <div class="p-6">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold heading-font">Your Cart</h2>
                <button id="closeCartBtn" class="text-gray-500 hover:text-gray-700">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
            
            <div id="cartItems" class="mb-6">
                <!-- Cart items will be dynamically added here -->
                <div id="emptyCartMessage" class="text-center py-10">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 mx-auto text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
                    </svg>
                    <h3 class="text-lg font-medium text-gray-500 mt-2">Your cart is empty</h3>
                    <p class="text-gray-400 mt-1">Start shopping to add items to your cart</p>
                </div>
            </div>
            
            <div id="cartSummary" class="border-t pt-4 hidden">
                <div class="flex justify-between mb-2">
                    <span class="text-gray-600">Subtotal:</span>
                    <span id="cartSubtotal" class="font-semibold">$0.00</span>
                </div>
                <div class="flex justify-between mb-4">
                    <span class="text-gray-600">Shipping:</span>
                    <span class="font-semibold text-green-600">Free</span>
                </div>
                <div class="flex justify-between text-lg font-bold mb-4">
                    <span>Total:</span>
                    <span id="cartTotal">$0.00</span>
                </div>
                <button id="checkoutBtn" class="w-full bg-indigo-600 text-white py-3 rounded-lg hover:bg-indigo-700 transition duration-300">Proceed to Checkout</button>
                <button class="w-full mt-2 border-2 border-indigo-600 text-indigo-600 py-3 rounded-lg hover:bg-indigo-50 transition duration-300">Continue Shopping</button>
            </div>
        </div>
    </div>

    <!-- Newsletter Section -->
    <section class="py-12 bg-indigo-50">
        <div class="container mx-auto px-4 text-center">
            <h2 class="text-3xl font-bold heading-font mb-4">Stay Updated</h2>
            <p class="text-gray-600 max-w-2xl mx-auto mb-6">Sign up for our newsletter to receive exclusive offers, gift ideas, and updates on new arrivals</p>
            <form class="max-w-md mx-auto flex">
                <input type="email" placeholder="Your email address" class="flex-grow px-4 py-3 rounded-l-lg border border-r-0 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                <button class="bg-indigo-600 text-white px-6 py-3 rounded-r-lg hover:bg-indigo-700 transition duration-300">Subscribe</button>
            </form>
            <p class="text-gray-400 text-xs mt-3">We respect your privacy. Unsubscribe at any time.</p>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white pt-12 pb-6">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
                <div>
                    <h3 class="text-lg font-bold heading-font mb-4">The Gift Haven</h3>
                    <p class="text-gray-400">Thoughtful gifts for every occasion. Carefully curated to delight.</p>
                </div>
                <div>
                    <h4 class="font-bold mb-4">Shop</h4>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white">All Gifts</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">New Arrivals</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Best Sellers</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Gift Cards</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold mb-4">Help</h4>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white">FAQ</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Shipping & Returns</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Privacy Policy</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Terms of Service</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold mb-4">Connect</h4>
                    <div class="flex space-x-4 mb-4">
                        <a href="#" class="text-gray-400 hover:text-white">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M22.675 0h-21.35c-.732 0-1.325.593-1.325 1.325v21.351c0 .731.593 1.324 1.325 1.324h11.495v-9.294h-3.128v-3.622h3.128v-2.671c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12v9.293h6.116c.73 0 1.323-.593 1.323-1.325v-21.35c0-.732-.593-1.325-1.325-1.325z"/>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                            </svg>
                        </a>
                    </div>
                    <p class="text-gray-400">support@gifthaven.com</p>
                    <p class="text-gray-400">(555) 123-4567</p>
                </div>
            </div>
            <div class="border-t border-gray-800 pt-6 text-center text-gray-400 text-sm">
                <p>© 2023 The Gift Haven. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Mobile Menu Toggle
        document.getElementById('mobileMenuBtn').addEventListener('click', function() {
            document.getElementById('mobileMenu').classList.toggle('hidden');
        });
        
        // Search Overlay Toggle
        document.getElementById('searchBtn').addEventListener('click', function() {
            document.getElementById('searchOverlay').classList.remove('hidden');
        });
        
        document.getElementById('closeSearchBtn').addEventListener('click', function() {
            document.getElementById('searchOverlay').classList.add('hidden');
        });
        
        // Cart Functionality
        let cart = [];
        
        // Open/Close Cart Drawer
        document.getElementById('cartBtn').addEventListener('click', function() {
            document.getElementById('cartDrawer').classList.remove('translate-x-full');
            updateCartUI();
        });
        
        document.getElementById('closeCartBtn').addEventListener('click', function() {
            document.getElementById('cartDrawer').classList.add('translate-x-full');
        });
        
        // Add to Cart
        document.querySelectorAll('.add-to-cart').forEach(button => {
            button.addEventListener('click', function() {
                const productId = this.getAttribute('data-id');
                const productName = this.getAttribute('data-name');
                const productPrice = parseFloat(this.getAttribute('data-price'));
                const productImage = this.getAttribute('data-image');
                
                // Check if product already in cart
                const existingItem = cart.find(item => item.id === productId);
                
                if (existingItem) {
                    existingItem.quantity += 1;
                } else {
                    cart.push({
                        id: productId,
                        name: productName,
                        price: productPrice,
                        image: productImage,
                        quantity: 1
                    });
                }
                
                // Update cart count badge
                updateCartCount();
                updateCartUI();
                
                // Show cart drawer
                document.getElementById('cartDrawer').classList.remove('translate-x-full');
                
                // Add to cart animation
                this.textContent = 'Added to Cart';
                setTimeout(() => {
                    this.textContent = 'Add to Cart';
                }, 1500);
            });
        });
        
        // Update cart count badge
        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            const cartCount = document.getElementById('cartCount');
            
            if (count > 0) {
                cartCount.textContent = count;
                cartCount.classList.remove('hidden');
            } else {
                cartCount.classList.add('hidden');
            }
        }
        
        // Update cart UI
        function updateCartUI() {
            const cartItemsContainer = document.getElementById('cartItems');
            const emptyCartMessage = document.getElementById('emptyCartMessage');
            const cartSummary = document.getElementById('cartSummary');
            
            if (cart.length === 0) {
                emptyCartMessage.classList.remove('hidden');
                cartSummary.classList.add('hidden');
                cartItemsContainer.innerHTML = '';
            } else {
                emptyCartMessage.classList.add('hidden');
                cartSummary.classList.remove('hidden');
                
                // Calculate subtotal
                const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                document.getElementById('cartSubtotal').textContent = '$' + subtotal.toFixed(2);
                document.getElementById('cartTotal').textContent = '$' + subtotal.toFixed(2);
                
                // Render cart items
                let cartHTML = '';
                cart.forEach(item => {
                    cartHTML += `
                        <div class="flex items-center py-4 border-b" data-id="${item.id}">
                            <div class="w-16 h-16 flex-shrink-0">
                                <img src="${item.image}" alt="${item.name}" class="w-full h-full object-cover rounded">
                            </div>
                            <div class="ml-4 flex-grow">
                                <h3 class="font-medium">${item.name}</h3>
                                <p class="text-gray-600">$${item.price.toFixed(2)}</p>
                            </div>
                            <div class="flex items-center">
                                <button class="quantity-btn px-2 py-1 border rounded-l-lg hover:bg-gray-100" data-action="decrease">-</button>
                                <span class="px-3 py-1 border-t border-b">${item.quantity}</span>
                                <button class="quantity-btn px-2 py-1 border rounded-r-lg hover:bg-gray-100" data-action="increase">+</button>
                                <button class="ml-2 text-red-500 hover:text-red-700 remove-btn">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
                                    </svg>
                                </button>
                            </div>
                        </div>
                    `;
                });
                
                cartItemsContainer.innerHTML = cartHTML;
                
                // Add event listeners to quantity buttons
                document.querySelectorAll('.quantity-btn').forEach(button => {
                    button.addEventListener('click', function() {
                        const action = this.getAttribute('data-action');
                        const itemId = this.closest('[data-id]').getAttribute('data-id');
                        const item = cart.find(item => item.id === itemId);
                        
                        if (action === 'increase') {
                            item.quantity += 1;
                        } else if (action === 'decrease' && item.quantity > 1) {
                            item.quantity -= 1;
                        }
                        
                        updateCartCount();
                        updateCartUI();
                    });
                });
                
                // Add event listeners to remove buttons
                document.querySelectorAll('.remove-btn').forEach(button => {
                    button.addEventListener('click', function() {
                        const itemId = this.closest('[data-id]').getAttribute('data-id');
                        cart = cart.filter(item => item.id !== itemId);
                        
                        updateCartCount();
                        updateCartUI();
                    });
                });
            }
        }
        
        // Checkout button
        document.getElementById('checkoutBtn').addEventListener('click', function() {
            alert('Proceeding to checkout with ' + cart.reduce((sum, item) => sum + item.quantity, 0) + ' items');
            cart = [];
            updateCartCount();
            updateCartUI();
            document.getElementById('cartDrawer').classList.add('translate-x-full');
        });
        
        // Category filter animation
        document.querySelectorAll('.category-filter').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.querySelector('svg').classList.add('animate-bounce');
            });
            
            card.addEventListener('mouseleave', function() {
                this.querySelector('svg').classList.remove('animate-bounce');
            });
        });
        
        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    targetElement.scrollIntoView({
                        behavior: 'smooth'
                    });
                }
                
                // Close mobile menu if open
                if (this.closest('#mobileMenu')) {
                    document.getElementById('mobileMenu').classList.add('hidden');
                }
            });
        });
    </script>
</body>
</html>
