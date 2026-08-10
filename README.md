<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>TerraCraft · Botswana Artifacts</title>
  <!-- Font Awesome 6 (free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
  <!-- Google Font Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet" />
  <!-- Tailwind CSS via CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            cream: '#F8F6F2',
            charcoal: '#222222',
            terracotta: '#D5641C',
            softborder: '#E5E0D8',
          },
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
          }
        }
      }
    }
  </script>
  <style>
    /* custom polish */
    body { background: #F8F6F2; color: #222222; }
    .card-hover { transition: all 0.2s ease; }
    .card-hover:hover { transform: translateY(-4px); box-shadow: 0 20px 30px -10px rgba(0,0,0,0.08); }
    .heart-btn { transition: transform 0.15s; }
    .heart-btn:hover { transform: scale(1.2); }
    .tab-btn { transition: background 0.15s, color 0.15s; }
    .tab-btn.active { background: #D5641C; color: white; }
    .tab-btn:not(.active):hover { background: #f0ebe3; }
    .sticky-panel { position: sticky; top: 2rem; align-self: start; }
    .category-scroll::-webkit-scrollbar { height: 6px; background: #eae5dd; border-radius: 20px; }
    .category-scroll::-webkit-scrollbar-thumb { background: #D5641C; border-radius: 20px; }
    input, select, textarea { border: 1px solid #ddd8cf; }
    input:focus, select:focus, textarea:focus { outline: 2px solid #D5641C; outline-offset: 1px; }
    .badge { transition: all 0.2s; }
  </style>
</head>
<body class="font-sans text-charcoal antialiased">

<div id="app" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pb-10">

  <!-- ========== GLOBAL HEADER ========== -->
  <header class="py-5 border-b border-softborder/60">
    <div class="flex flex-wrap items-center gap-4">
      <!-- Logo: TerraCraft -->
      <div class="text-2xl font-semibold tracking-tight flex items-center gap-1">
        <span class="text-terracotta">✦</span> TerraCraft
      </div>
      <!-- Search bar (centered) -->
      <div class="flex-1 min-w-[180px] relative">
        <i class="fas fa-search absolute left-3 top-1/2 -translate-y-1/2 text-softborder"></i>
        <input type="text" id="searchInput" placeholder="Search artifacts, pottery, baskets..." class="w-full bg-white/80 pl-9 pr-4 py-2 rounded-full border border-softborder focus:border-terracotta transition" />
      </div>
      <!-- Actions -->
      <div class="flex items-center gap-3 ml-auto">
        <button class="text-sm font-medium border border-softborder px-4 py-1.5 rounded-full hover:bg-white transition">Sign In</button>
        <button class="relative text-xl" id="favCounterWrap">
          <i class="far fa-heart"></i>
          <span id="favBadge" class="absolute -top-1 -right-2 text-[10px] bg-terracotta text-white w-4 h-4 rounded-full flex items-center justify-center">0</span>
        </button>
        <button class="relative text-xl" id="cartToggle">
          <i class="fas fa-shopping-bag"></i>
          <span id="cartBadge" class="absolute -top-1 -right-2 text-[10px] bg-terracotta text-white w-4 h-4 rounded-full flex items-center justify-center">0</span>
        </button>
      </div>
    </div>
    <!-- Category nav (Botswana-inspired) -->
    <nav class="mt-4 flex flex-wrap gap-3 text-sm font-medium text-charcoal/80">
      <a href="#" class="hover:text-terracotta">Pottery & Ceramics</a>
      <a href="#" class="hover:text-terracotta">Basketry & Weave</a>
      <a href="#" class="hover:text-terracotta">Jewelry & Beads</a>
      <a href="#" class="hover:text-terracotta">Home & Living</a>
      <a href="#" class="hover:text-terracotta">Vintage Artifacts</a>
      <a href="#" class="hover:text-terracotta">Textiles & Clothing</a>
      <a href="#" class="hover:text-terracotta ml-auto text-terracotta font-semibold" id="dashboardToggle">⭐ Seller Dashboard</a>
    </nav>
  </header>

  <!-- ========== MAIN CONTENT ========== -->
  <main id="mainContent" class="mt-8">

    <!-- ************ LANDING PAGE (default) ************ -->
    <section id="landingPage">
      <!-- Hero -->
      <div class="bg-white/70 rounded-3xl p-8 md:p-12 mb-12 text-center shadow-sm border border-softborder/40">
        <h1 class="text-4xl md:text-5xl font-bold tracking-tight">Find things you love.<br />Support Botswana's makers.</h1>
        <p class="text-lg text-charcoal/70 mt-3 max-w-2xl mx-auto">Handcrafted pottery, woven baskets, beaded jewelry — each piece tells a story.</p>
      </div>

      <!-- Shop by Category (horizontal scroll) -->
      <div class="mb-12">
        <h2 class="text-2xl font-semibold mb-4">Shop by Category</h2>
        <div class="category-scroll flex gap-6 overflow-x-auto pb-4">
          <div class="flex-shrink-0 w-24 h-24 rounded-full bg-softborder/40 flex items-center justify-center text-center text-sm font-medium border-2 border-transparent hover:border-terracotta transition">Pottery</div>
          <div class="flex-shrink-0 w-24 h-24 rounded-full bg-softborder/40 flex items-center justify-center text-center text-sm font-medium border-2 border-transparent hover:border-terracotta transition">Baskets</div>
          <div class="flex-shrink-0 w-24 h-24 rounded-full bg-softborder/40 flex items-center justify-center text-center text-sm font-medium border-2 border-transparent hover:border-terracotta transition">Jewelry</div>
          <div class="flex-shrink-0 w-24 h-24 rounded-full bg-softborder/40 flex items-center justify-center text-center text-sm font-medium border-2 border-transparent hover:border-terracotta transition">Textiles</div>
          <div class="flex-shrink-0 w-24 h-24 rounded-full bg-softborder/40 flex items-center justify-center text-center text-sm font-medium border-2 border-transparent hover:border-terracotta transition">Vintage</div>
          <div class="flex-shrink-0 w-24 h-24 rounded-full bg-softborder/40 flex items-center justify-center text-center text-sm font-medium border-2 border-transparent hover:border-terracotta transition">Home</div>
        </div>
      </div>

      <!-- Product Grid (filterable) -->
      <div class="mb-12">
        <div class="flex justify-between items-center mb-4">
          <h2 class="text-2xl font-semibold">Curated Editors' Picks</h2>
          <span class="text-sm text-charcoal/60" id="resultCount">8 items</span>
        </div>
        <div id="productGrid" class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-6"></div>
      </div>

      <!-- Trending Now -->
      <div>
        <h2 class="text-2xl font-semibold mb-4">Trending Now</h2>
        <div id="trendingGrid" class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-6"></div>
      </div>
    </section>

    <!-- ************ PRODUCT DETAIL (hidden by default) ************ -->
    <section id="productDetail" class="hidden">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
        <!-- left gallery -->
        <div>
          <div id="mainImage" class="bg-white rounded-2xl overflow-hidden border border-softborder/50 h-80 flex items-center justify-center">
            <img id="detailMainImg" src="" alt="" class="object-cover w-full h-full" />
          </div>
          <div class="flex gap-2 mt-3" id="thumbnailStrip"></div>
        </div>
        <!-- right sticky panel -->
        <div class="sticky-panel">
          <div class="bg-white p-6 rounded-2xl border border-softborder/50">
            <div class="flex items-center gap-2 text-sm">
              <i class="fas fa-store text-terracotta"></i>
              <span id="detailShop" class="font-medium">BotswanArt</span>
              <span class="text-amber-400 ml-2"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star-half-alt"></i></span>
              <span class="text-xs text-charcoal/60">(24)</span>
            </div>
            <h3 id="detailTitle" class="text-2xl font-bold mt-2">Product</h3>
            <p id="detailPrice" class="text-2xl font-semibold text-terracotta mt-1">$48.00</p>
            <!-- variations -->
            <div class="mt-4 flex flex-wrap gap-4">
              <div><label class="block text-xs uppercase tracking-wide text-charcoal/60">Size</label><select class="mt-1 py-1.5 px-3 rounded-full bg-cream border-softborder text-sm"><option>One Size</option><option>S</option><option>M</option><option>L</option></select></div>
              <div><label class="block text-xs uppercase tracking-wide text-charcoal/60">Color</label><select class="mt-1 py-1.5 px-3 rounded-full bg-cream border-softborder text-sm"><option>Natural</option><option>Terracotta</option><option>Indigo</option></select></div>
            </div>
            <button id="addToCartBtn" class="mt-6 w-full bg-terracotta text-white py-3 rounded-full font-medium hover:bg-[#bf4f14] transition">Add to Cart</button>
            <!-- tabs -->
            <div class="mt-6 border-t border-softborder/40 pt-4">
              <div class="flex gap-2 text-sm">
                <button class="tab-btn active px-4 py-1.5 rounded-full" data-tab="desc">Description</button>
                <button class="tab-btn px-4 py-1.5 rounded-full" data-tab="shipping">Shipping</button>
                <button class="tab-btn px-4 py-1.5 rounded-full" data-tab="seller">Meet the Seller</button>
              </div>
              <div id="tabContent" class="mt-3 text-sm text-charcoal/80 leading-relaxed">Hand-thrown stoneware, glazed in warm oatmeal. Each piece is unique.</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ************ SELLER DASHBOARD (hidden) ************ -->
    <section id="sellerDashboard" class="hidden">
      <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 mb-6">
        <h2 class="text-2xl font-bold">🧑‍🎨 Seller Dashboard</h2>
        <div class="bg-white px-4 py-2 rounded-full border border-softborder/50 text-sm"><span class="font-medium">Sales this month</span> <span class="text-terracotta font-bold">$1,248</span> <span class="text-green-600 text-xs ml-2"><i class="fas fa-arrow-up"></i> +12%</span></div>
      </div>
      <!-- mini chart -->
      <div class="bg-white p-4 rounded-2xl border border-softborder/50 mb-8 flex items-end h-20 gap-2">
        <div class="w-full flex items-end gap-1 h-full"><div class="bg-terracotta/40 h-[30%] w-full rounded-t"></div><div class="bg-terracotta/60 h-[55%] w-full rounded-t"></div><div class="bg-terracotta/80 h-[40%] w-full rounded-t"></div><div class="bg-terracotta h-[70%] w-full rounded-t"></div><div class="bg-terracotta/70 h-[50%] w-full rounded-t"></div><div class="bg-terracotta/30 h-[25%] w-full rounded-t"></div><div class="bg-terracotta/90 h-[80%] w-full rounded-t"></div></div>
      </div>
      <!-- Active listings -->
      <div class="mb-8">
        <h3 class="text-xl font-semibold mb-3">Active Listings</h3>
        <div id="activeListings" class="grid grid-cols-1 sm:grid-cols-2 gap-4"></div>
      </div>
      <!-- New Listing Form -->
      <div class="bg-white p-6 rounded-2xl border border-softborder/50 max-w-xl">
        <h3 class="text-xl font-semibold mb-3">New Listing</h3>
        <form id="newListingForm" class="space-y-3">
          <input id="formTitle" placeholder="Title" class="w-full px-4 py-2 rounded-full bg-cream border-softborder" required />
          <input id="formPrice" placeholder="Price (USD)" type="number" class="w-full px-4 py-2 rounded-full bg-cream border-softborder" required />
          <input id="formCategory" placeholder="Category" class="w-full px-4 py-2 rounded-full bg-cream border-softborder" required />
          <textarea id="formDesc" placeholder="Description" rows="2" class="w-full px-4 py-2 rounded-2xl bg-cream border-softborder"></textarea>
          <input id="formImage" placeholder="Image URL" class="w-full px-4 py-2 rounded-full bg-cream border-softborder" value="https://picsum.photos/seed/botswana/400/400" />
          <button type="submit" class="bg-terracotta text-white px-6 py-2 rounded-full hover:bg-[#bf4f14] transition">Add Listing</button>
        </form>
      </div>
    </section>

  </main>

  <!-- ========== CART SIDEBAR ========== -->
  <div id="cartSidebar" class="fixed inset-0 bg-black/20 backdrop-blur-sm hidden z-50">
    <div class="absolute right-0 top-0 h-full w-96 bg-white shadow-2xl p-6 overflow-y-auto">
      <div class="flex justify-between items-center border-b border-softborder/40 pb-3"><span class="text-xl font-semibold">Your Cart</span><button id="closeCart" class="text-2xl">&times;</button></div>
      <div id="cartItems" class="mt-4 space-y-4"></div>
      <div class="border-t border-softborder/40 pt-4 mt-4"><span class="font-medium">Subtotal: </span><span id="cartSubtotal" class="font-bold text-terracotta">$0.00</span></div>
      <button class="w-full bg-terracotta text-white py-3 rounded-full mt-4 hover:bg-[#bf4f14] transition">Checkout</button>
    </div>
  </div>

  <!-- ========== FOOTER ========== -->
  <footer class="mt-16 border-t border-softborder/60 pt-8 grid grid-cols-2 md:grid-cols-4 gap-6 text-sm text-charcoal/70">
    <div><h4 class="font-semibold text-charcoal">Shop</h4><p>Pottery</p><p>Baskets</p><p>Jewelry</p></div>
    <div><h4 class="font-semibold text-charcoal">Sell</h4><p>Start selling</p><p>How it works</p><p>Success stories</p></div>
    <div><h4 class="font-semibold text-charcoal">About</h4><p>Our story</p><p>Community</p><p>Press</p></div>
    <div><h4 class="font-semibold text-charcoal">Help</h4><p>FAQ</p><p>Contact</p><p>Returns</p></div>
    <div class="col-span-2 md:col-span-4 flex justify-between items-center border-t border-softborder/30 pt-4 mt-2 text-xs"><span>© 2026 TerraCraft · Botswana</span><span><i class="fas fa-globe"></i> BWP · English</span></div>
  </footer>
</div>

<script>
  (function() {
    // ---- SAMPLE DATA (Botswana-inspired) ----
    const sampleProducts = [
      { id: 1, title: "Hand-thrown Pot", price: 48, category: "Pottery", shop: "Earth & Kiln", rating: 4.8, image: "https://picsum.photos/seed/pot/400/400", freeShipping: true, description: "Terracotta clay, fired in open kiln. Perfect for plants." },
      { id: 2, title: "Woven Basket", price: 72, category: "Basketry", shop: "Weave & Co", rating: 4.9, image: "https://picsum.photos/seed/basket/400/400", freeShipping: false, description: "Elephant grass, natural dyes. 40cm diameter." },
      { id: 3, title: "Beaded Necklace", price: 34, category: "Jewelry", shop: "Aurelia Beads", rating: 4.7, image: "https://picsum.photos/seed/beads/400/400", freeShipping: true, description: "Hand-rolled glass beads, brass findings." },
      { id: 4, title: "Wooden Carving", price: 28, category: "Vintage", shop: "Heritage Wood", rating: 4.6, image: "https://picsum.photos/seed/carving/400/400", freeShipping: false, description: "African mahogany, abstract form." },
      { id: 5, title: "Indigo Shirt", price: 65, category: "Textiles", shop: "BotswanWeave", rating: 4.9, image: "https://picsum.photos/seed/shirt/400/400", freeShipping: true, description: "Hand-loomed cotton, indigo dye." },
      { id: 6, title: "Ceramic Vase", price: 52, category: "Pottery", shop: "Earth & Kiln", rating: 4.5, image: "https://picsum.photos/seed/vase2/400/400", freeShipping: false, description: "Sgraffito pattern, matte glaze." },
      { id: 7, title: "Beaded Bracelet", price: 39, category: "Jewelry", shop: "Aurelia Beads", rating: 4.3, image: "https://picsum.photos/seed/bracelet/400/400", freeShipping: true, description: "Recycled glass beads, adjustable." },
      { id: 8, title: "Leather Sandals", price: 58, category: "Clothing", shop: "Footprint", rating: 4.8, image: "https://picsum.photos/seed/sandals/400/400", freeShipping: false, description: "Hand-stitched, vegetable-tanned leather." },
    ];
    const trending = sampleProducts.slice(2,6);

    // ---- STATE ----
    let products = [...sampleProducts];
    let cart = [];
    let favorites = new Set();
    let currentProductId = null;

    // DOM refs
    const grid = document.getElementById('productGrid');
    const trendingGrid = document.getElementById('trendingGrid');
    const searchInput = document.getElementById('searchInput');
    const cartBadge = document.getElementById('cartBadge');
    const cartSidebar = document.getElementById('cartSidebar');
    const cartItems = document.getElementById('cartItems');
    const cartSubtotal = document.getElementById('cartSubtotal');
    const resultCount = document.getElementById('resultCount');
    const dashboardToggle = document.getElementById('dashboardToggle');
    const landingPage = document.getElementById('landingPage');
    const productDetail = document.getElementById('productDetail');
    const sellerDashboard = document.getElementById('sellerDashboard');
    const detailMainImg = document.getElementById('detailMainImg');
    const detailTitle = document.getElementById('detailTitle');
    const detailPrice = document.getElementById('detailPrice');
    const detailShop = document.getElementById('detailShop');
    const thumbnailStrip = document.getElementById('thumbnailStrip');
    const tabContent = document.getElementById('tabContent');
    const addToCartBtn = document.getElementById('addToCartBtn');
    const activeListings = document.getElementById('activeListings');
    const newListingForm = document.getElementById('newListingForm');
    const favBadge = document.getElementById('favBadge');

    // ---- RENDER PRODUCT CARDS ----
    function renderProducts(list, container, isTrending = false) {
      if (!container) return;
      container.innerHTML = list.map(p => {
        const fav = favorites.has(p.id) ? 'fas' : 'far';
        const shippingBadge = p.freeShipping ? `<span class="text-[10px] bg-green-100 text-green-700 px-2 py-0.5 rounded-full">Free shipping</span>` : '';
        return `<div class="bg-white rounded-2xl border border-softborder/40 overflow-hidden card-hover relative group">
          <div class="relative h-48 bg-cream"><img src="${p.image}" alt="${p.title}" class="w-full h-full object-cover" loading="lazy" /></div>
          <button class="heart-btn absolute top-2 right-2 text-xl text-charcoal/60 hover:text-red-500 transition" data-id="${p.id}"><i class="${fav} fa-heart text-white drop-shadow-md" style="text-shadow: 0 0 4px rgba(0,0,0,0.3)"></i></button>
          <div class="p-3">
            <div class="font-semibold text-sm leading-tight">${p.title}</div>
            <div class="flex items-center text-xs mt-1"><span class="text-amber-400">★★★★</span><span class="text-amber-400">${p.rating >= 4.8 ? '★' : '☆'}</span><span class="ml-1 text-charcoal/50">(${Math.floor(p.rating * 5)})</span></div>
            <div class="flex justify-between items-center mt-1"><span class="font-bold text-terracotta">$${p.price}</span>${shippingBadge}</div>
            ${isTrending ? '' : `<button class="view-detail text-xs text-terracotta underline mt-1" data-id="${p.id}">View</button>`}
          </div>
        </div>`;
      }).join('');

      // heart toggles
      container.querySelectorAll('.heart-btn').forEach(btn => {
        btn.addEventListener('click', (e) => {
          e.stopPropagation();
          const id = Number(btn.dataset.id);
          if (favorites.has(id)) favorites.delete(id); else favorites.add(id);
          renderProducts(products, grid, false);
          renderProducts(trending, trendingGrid, true);
          favBadge.textContent = favorites.size || '0';
        });
      });

      if (!isTrending) {
        container.querySelectorAll('.view-detail').forEach(btn => {
          btn.addEventListener('click', (e) => {
            const id = Number(btn.dataset.id);
            openProductDetail(id);
          });
        });
      }
    }

    // ---- OPEN PRODUCT DETAIL ----
    function openProductDetail(id) {
      const product = products.find(p => p.id === id);
      if (!product) return;
      currentProductId = id;
      landingPage.classList.add('hidden');
      productDetail.classList.remove('hidden');
      sellerDashboard.classList.add('hidden');
      // fill detail
      detailMainImg.src = product.image;
      detailTitle.textContent = product.title;
      detailPrice.textContent = `$${product.price}`;
      detailShop.textContent = product.shop;
      // thumbnails (mock)
      thumbnailStrip.innerHTML = `<img src="${product.image}" class="w-16 h-16 rounded-lg border-2 border-terracotta object-cover cursor-pointer" />`;
      // tab content
      tabContent.textContent = product.description || 'Handcrafted in Botswana.';
      // set add to cart
      addToCartBtn.onclick = () => addToCart(product);
    }

    // ---- ADD TO CART ----
    function addToCart(product) {
      const existing = cart.find(item => item.id === product.id);
      if (existing) existing.quantity += 1;
      else cart.push({ ...product, quantity: 1 });
      updateCartUI();
      // open sidebar
      cartSidebar.classList.remove('hidden');
    }

    function updateCartUI() {
      cartBadge.textContent = cart.reduce((acc, i) => acc + i.quantity, 0);
      renderCartItems();
    }

    function renderCartItems() {
      if (!cartItems) return;
      if (cart.length === 0) {
        cartItems.innerHTML = '<p class="text-charcoal/60 text-sm">Your cart is empty.</p>';
        cartSubtotal.textContent = '$0.00';
        return;
      }
      cartItems.innerHTML = cart.map(item => `
        <div class="flex justify-between items-center border-b border-softborder/30 pb-2">
          <div><span class="font-medium">${item.title}</span> <span class="text-xs text-charcoal/50">×${item.quantity}</span></div>
          <div class="flex items-center gap-2"><span class="text-terracotta font-semibold">$${(item.price * item.quantity).toFixed(2)}</span><button class="remove-item text-xs text-red-400 hover:text-red-600" data-id="${item.id}"><i class="fas fa-trash-alt"></i></button></div>
        </div>
      `).join('');
      const total = cart.reduce((sum, i) => sum + i.price * i.quantity, 0);
      cartSubtotal.textContent = `$${total.toFixed(2)}`;
      // remove handlers
      document.querySelectorAll('.remove-item').forEach(btn => {
        btn.addEventListener('click', () => {
          const id = Number(btn.dataset.id);
          cart = cart.filter(item => item.id !== id);
          updateCartUI();
        });
      });
    }

    // ---- SEARCH ----
    searchInput.addEventListener('input', function() {
      const q = this.value.toLowerCase().trim();
      const filtered = q ? products.filter(p => p.title.toLowerCase().includes(q) || p.category.toLowerCase().includes(q)) : products;
      renderProducts(filtered, grid, false);
      resultCount.textContent = filtered.length + ' items';
    });

    // ---- DASHBOARD TOGGLE ----
    dashboardToggle.addEventListener('click', (e) => {
      e.preventDefault();
      landingPage.classList.add('hidden');
      productDetail.classList.add('hidden');
      sellerDashboard.classList.toggle('hidden');
      if (!sellerDashboard.classList.contains('hidden')) renderActiveListings();
    });

    // ---- RENDER ACTIVE LISTINGS (dashboard) ----
    function renderActiveListings() {
      activeListings.innerHTML = products.map(p => `
        <div class="bg-white p-3 rounded-xl border border-softborder/50 flex items-center gap-3">
          <img src="${p.image}" class="w-12 h-12 rounded-lg object-cover" />
          <div class="flex-1"><div class="font-semibold text-sm">${p.title}</div><div class="text-xs text-charcoal/60">$${p.price}</div></div>
          <div><button class="text-xs text-terracotta border border-terracotta/40 px-2 py-0.5 rounded-full hover:bg-terracotta/10">Edit</button><button class="text-xs text-red-400 ml-1 hover:text-red-600 delete-listing" data-id="${p.id}"><i class="fas fa-trash-alt"></i></button></div>
        </div>
      `).join('');
      document.querySelectorAll('.delete-listing').forEach(btn => {
        btn.addEventListener('click', function() {
          const id = Number(this.dataset.id);
          products = products.filter(p => p.id !== id);
          renderActiveListings();
          renderProducts(products, grid, false);
          renderProducts(trending, trendingGrid, true);
          resultCount.textContent = products.length + ' items';
        });
      });
    }

    // ---- NEW LISTING FORM ----
    newListingForm.addEventListener('submit', function(e) {
      e.preventDefault();
      const title = document.getElementById('formTitle').value.trim();
      const price = parseFloat(document.getElementById('formPrice').value);
      const category = document.getElementById('formCategory').value.trim();
      const description = document.getElementById('formDesc').value.trim();
      const image = document.getElementById('formImage').value.trim() || 'https://picsum.photos/seed/new/400/400';
      if (!title || !price || !category) return;
      const newId = Date.now();
      const newProduct = { id: newId, title, price, category, shop: 'Your Studio', rating: 4.5, image, freeShipping: false, description };
      products.push(newProduct);
      renderProducts(products, grid, false);
      renderActiveListings();
      resultCount.textContent = products.length + ' items';
      this.reset();
      document.getElementById('formImage').value = 'https://picsum.photos/seed/botswana/400/400';
      alert('Listing added! 🎉');
    });

    // ---- CART SIDEBAR TOGGLE ----
    document.getElementById('cartToggle').addEventListener('click', () => cartSidebar.classList.toggle('hidden'));
    document.getElementById('closeCart').addEventListener('click', () => cartSidebar.classList.add('hidden'));
    cartSidebar.addEventListener('click', (e) => { if (e.target === cartSidebar) cartSidebar.classList.add('hidden'); });

    // ---- TAB SWITCH (product detail) ----
    document.querySelectorAll('.tab-btn').forEach(btn => {
      btn.addEventListener('click', function() {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        const tab = this.dataset.tab;
        const contents = {
          desc: 'Handcrafted in Botswana with traditional techniques. Each piece is unique.',
          shipping: 'Ships within 3-5 business days. Free returns within 14 days.',
          seller: 'Meet the maker: a local artisan with 10+ years of experience.'
        };
        tabContent.textContent = contents[tab] || contents.desc;
      });
    });

    // ---- INIT ----
    renderProducts(products, grid, false);
    renderProducts(trending, trendingGrid, true);
    resultCount.textContent = products.length + ' items';
    favBadge.textContent = favorites.size || '0';
    renderActiveListings();

    // ---- extra: close detail via back? we add a simple "go back" link on detail (hidden) but we can use dashboard toggle to go back.
    // we also add a small "back to shop" on detail via double click on header logo? but we'll just use dashboard toggle as fallback.
    // For UX, we can add a hidden back button but we keep it minimal.
    // we also allow clicking logo to go home
    document.querySelector('.text-2xl.font-semibold')?.addEventListener('click', function() {
      landingPage.classList.remove('hidden');
      productDetail.classList.add('hidden');
      sellerDashboard.classList.add('hidden');
    });

  })();
</script>
</body>
</html>
