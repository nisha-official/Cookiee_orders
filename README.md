<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CrumbleCraft – Artisan Cookies</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #FDF6EC;
    --warm-brown: #5C3A1E;
    --caramel: #C8813A;
    --gold: #E8A94B;
    --dark: #1A0F06;
    --soft-brown: #8B5E3C;
    --light-tan: #F5E6CE;
    --accent: #D4562B;
    --white: #FFFFFF;
    --shadow: rgba(92,58,30,0.18);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--dark);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── HERO BACKGROUND ─────────────────────────── */
  .hero-bg {
    position: fixed;
    inset: 0;
    z-index: -1;
    background:
      radial-gradient(ellipse 80% 60% at 20% 10%, rgba(200,129,58,0.22) 0%, transparent 60%),
      radial-gradient(ellipse 60% 50% at 80% 80%, rgba(212,86,43,0.15) 0%, transparent 60%),
      url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='40' cy='40' r='2' fill='%23C8813A' fill-opacity='0.07'/%3E%3Ccircle cx='10' cy='10' r='1.2' fill='%23C8813A' fill-opacity='0.05'/%3E%3Ccircle cx='70' cy='20' r='1.5' fill='%235C3A1E' fill-opacity='0.06'/%3E%3Ccircle cx='20' cy='70' r='1' fill='%235C3A1E' fill-opacity='0.05'/%3E%3C/svg%3E"),
      #FDF6EC;
  }

  /* ── NAV ─────────────────────────────────────── */
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 48px;
    background: rgba(253,246,236,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1.5px solid rgba(200,129,58,0.2);
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 24px var(--shadow);
  }
  .logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.7rem;
    font-weight: 900;
    color: var(--warm-brown);
    letter-spacing: -0.5px;
  }
  .logo span { color: var(--caramel); }
  .nav-links { display: flex; gap: 28px; align-items: center; }
  .nav-links a {
    text-decoration: none;
    color: var(--soft-brown);
    font-weight: 500;
    font-size: 0.95rem;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--caramel); }
  .nav-btn {
    background: var(--warm-brown);
    color: #fff !important;
    padding: 9px 22px;
    border-radius: 40px;
    font-weight: 600 !important;
    transition: background 0.2s, transform 0.15s !important;
  }
  .nav-btn:hover { background: var(--caramel) !important; transform: scale(1.04); }

  /* ── PAGE SECTIONS ───────────────────────────── */
  .page { display: none; animation: fadeIn 0.4s ease; }
  .page.active { display: block; }
  @keyframes fadeIn { from { opacity:0; transform:translateY(14px);} to { opacity:1; transform:none;} }

  /* ── HERO ────────────────────────────────────── */
  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 90px 24px 60px;
  }
  .hero-badge {
    background: var(--light-tan);
    border: 1.5px solid var(--gold);
    color: var(--caramel);
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 6px 18px;
    border-radius: 40px;
    margin-bottom: 22px;
    display: inline-block;
  }
  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.8rem, 6vw, 5.2rem);
    font-weight: 900;
    color: var(--warm-brown);
    line-height: 1.08;
    max-width: 780px;
    margin-bottom: 20px;
  }
  .hero h1 em { color: var(--caramel); font-style: italic; }
  .hero p {
    font-size: 1.1rem;
    color: var(--soft-brown);
    max-width: 520px;
    line-height: 1.7;
    margin-bottom: 36px;
  }
  .hero-btns { display: flex; gap: 14px; flex-wrap: wrap; justify-content: center; }
  .btn-primary {
    background: var(--warm-brown);
    color: #fff;
    border: none;
    padding: 14px 34px;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s, transform 0.15s, box-shadow 0.2s;
    box-shadow: 0 4px 20px rgba(92,58,30,0.25);
    font-family: 'DM Sans', sans-serif;
  }
  .btn-primary:hover { background: var(--caramel); transform: translateY(-2px); box-shadow: 0 8px 28px rgba(200,129,58,0.35); }
  .btn-outline {
    background: transparent;
    color: var(--warm-brown);
    border: 2px solid var(--warm-brown);
    padding: 13px 32px;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
    font-family: 'DM Sans', sans-serif;
  }
  .btn-outline:hover { background: var(--warm-brown); color: #fff; }

  /* ── COOKIE CARDS ────────────────────────────── */
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: 2.2rem;
    font-weight: 700;
    color: var(--warm-brown);
    text-align: center;
    margin-bottom: 8px;
  }
  .section-sub {
    text-align: center;
    color: var(--soft-brown);
    margin-bottom: 42px;
    font-size: 1rem;
  }
  .cookies-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 28px;
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 24px 80px;
  }
  .cookie-card {
    background: #fff;
    border-radius: 24px;
    overflow: hidden;
    box-shadow: 0 4px 24px var(--shadow);
    transition: transform 0.22s, box-shadow 0.22s;
    cursor: pointer;
    border: 1.5px solid rgba(200,129,58,0.12);
  }
  .cookie-card:hover { transform: translateY(-6px); box-shadow: 0 14px 40px rgba(92,58,30,0.2); }
  .cookie-emoji {
    font-size: 4.5rem;
    background: var(--light-tan);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 32px 0;
    position: relative;
  }
  .cookie-badge-new {
    position: absolute;
    top: 14px; right: 14px;
    background: var(--accent);
    color: #fff;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 1.2px;
    text-transform: uppercase;
    padding: 4px 10px;
    border-radius: 20px;
  }
  .cookie-info { padding: 18px 20px 20px; }
  .cookie-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.18rem;
    font-weight: 700;
    color: var(--warm-brown);
    margin-bottom: 5px;
  }
  .cookie-desc { font-size: 0.85rem; color: var(--soft-brown); line-height: 1.5; margin-bottom: 14px; }
  .cookie-footer { display: flex; align-items: center; justify-content: space-between; }
  .cookie-price { font-size: 1.15rem; font-weight: 700; color: var(--caramel); }
  .add-btn {
    background: var(--warm-brown);
    color: #fff;
    border: none;
    border-radius: 50px;
    padding: 8px 18px;
    font-size: 0.85rem;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s;
    font-family: 'DM Sans', sans-serif;
  }
  .add-btn:hover { background: var(--caramel); }

  /* ── LOGIN FORM ──────────────────────────────── */
  .form-wrap {
    max-width: 480px;
    margin: 60px auto;
    padding: 0 24px 80px;
  }
  .form-card {
    background: #fff;
    border-radius: 28px;
    padding: 44px 40px;
    box-shadow: 0 8px 48px var(--shadow);
    border: 1.5px solid rgba(200,129,58,0.13);
  }
  .form-card h2 {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    font-weight: 800;
    color: var(--warm-brown);
    margin-bottom: 6px;
  }
  .form-card .sub { color: var(--soft-brown); font-size: 0.95rem; margin-bottom: 28px; }
  .field { margin-bottom: 18px; }
  .field label { display: block; font-weight: 600; font-size: 0.88rem; color: var(--warm-brown); margin-bottom: 7px; letter-spacing: 0.3px; }
  .field input, .field select, .field textarea {
    width: 100%;
    padding: 12px 16px;
    border: 1.5px solid rgba(200,129,58,0.3);
    border-radius: 12px;
    font-size: 0.97rem;
    font-family: 'DM Sans', sans-serif;
    color: var(--dark);
    background: var(--cream);
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .field input:focus, .field select:focus, .field textarea:focus {
    border-color: var(--caramel);
    box-shadow: 0 0 0 3px rgba(200,129,58,0.14);
  }
  .field textarea { resize: vertical; min-height: 80px; }
  .form-divider { text-align: center; color: var(--soft-brown); font-size: 0.85rem; margin: 14px 0; }
  .switch-link { color: var(--caramel); font-weight: 600; cursor: pointer; text-decoration: underline; }
  .alert {
    padding: 12px 16px;
    border-radius: 10px;
    font-size: 0.9rem;
    font-weight: 500;
    margin-bottom: 18px;
    display: none;
  }
  .alert.success { background: #eafaf1; color: #217a4b; border: 1px solid #a8dfc4; display: block; }
  .alert.error { background: #fdf0ee; color: #c0392b; border: 1px solid #f4c6be; display: block; }

  /* ── ORDER SECTION ───────────────────────────── */
  .order-wrap {
    max-width: 700px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }
  .order-summary {
    background: #fff;
    border-radius: 24px;
    padding: 28px 30px;
    box-shadow: 0 4px 24px var(--shadow);
    margin-bottom: 28px;
    border: 1.5px solid rgba(200,129,58,0.13);
  }
  .order-summary h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    color: var(--warm-brown);
    margin-bottom: 16px;
  }
  .cart-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 0;
    border-bottom: 1px dashed rgba(200,129,58,0.2);
    font-size: 0.95rem;
  }
  .cart-item:last-child { border-bottom: none; }
  .cart-item-name { font-weight: 500; color: var(--warm-brown); }
  .cart-item-qty { color: var(--soft-brown); font-size: 0.85rem; margin-left: 8px; }
  .cart-item-price { font-weight: 700; color: var(--caramel); }
  .qty-controls { display: flex; align-items: center; gap: 8px; }
  .qty-btn {
    width: 26px; height: 26px;
    border-radius: 50%;
    border: 1.5px solid var(--caramel);
    background: transparent;
    color: var(--caramel);
    font-size: 1rem;
    cursor: pointer;
    font-weight: 700;
    transition: all 0.15s;
    display: flex; align-items: center; justify-content: center;
  }
  .qty-btn:hover { background: var(--caramel); color: #fff; }
  .cart-total {
    display: flex;
    justify-content: space-between;
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--warm-brown);
    margin-top: 14px;
    padding-top: 14px;
    border-top: 2px solid var(--light-tan);
  }
  .empty-cart { text-align: center; color: var(--soft-brown); padding: 20px 0; font-size: 0.95rem; }

  /* ── WHATSAPP LINK ───────────────────────────── */
  .wa-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: #25D366;
    color: #fff;
    border: none;
    padding: 14px 28px;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    text-decoration: none;
    transition: background 0.2s, transform 0.15s, box-shadow 0.2s;
    box-shadow: 0 4px 20px rgba(37,211,102,0.3);
    font-family: 'DM Sans', sans-serif;
  }
  .wa-btn:hover { background: #1da851; transform: translateY(-2px); box-shadow: 0 8px 28px rgba(37,211,102,0.35); }
  .wa-btn svg { width: 22px; height: 22px; }

  /* ── FOOTER ──────────────────────────────────── */
  footer {
    background: var(--warm-brown);
    color: rgba(255,255,255,0.75);
    text-align: center;
    padding: 28px 24px;
    font-size: 0.88rem;
  }
  footer a { color: var(--gold); text-decoration: none; }
  footer strong { color: #fff; }

  /* ── TOAST ───────────────────────────────────── */
  #toast {
    position: fixed;
    bottom: 28px; right: 28px;
    background: var(--warm-brown);
    color: #fff;
    padding: 13px 22px;
    border-radius: 14px;
    font-size: 0.92rem;
    font-weight: 500;
    box-shadow: 0 6px 28px var(--shadow);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s;
    z-index: 9999;
  }
  #toast.show { opacity: 1; }

  .cart-count {
    background: var(--accent);
    color: #fff;
    font-size: 0.7rem;
    font-weight: 700;
    border-radius: 50%;
    width: 18px; height: 18px;
    display: inline-flex; align-items: center; justify-content: center;
    vertical-align: top;
    margin-left: -4px;
    margin-top: -6px;
  }

  @media(max-width:600px) {
    nav { padding: 14px 18px; }
    .form-card { padding: 28px 20px; }
    .hero { padding: 60px 16px 40px; }
  }
</style>
</head>
<body>

<div class="hero-bg"></div>

<!-- ── NAV ─────────────────────────────────────── -->
<nav>
  <div class="logo">Crumble<span>Craft</span></div>
  <div class="nav-links">
    <a href="#" onclick="showPage('home')">Home</a>
    <a href="#" onclick="showPage('menu')">Menu</a>
    <a href="#" onclick="showPage('order')">Order <span class="cart-count" id="cartCount">0</span></a>
    <a href="#" onclick="showPage('login')" class="nav-btn" id="authNavBtn">Login</a>
  </div>
</nav>

<!-- ── HOME ────────────────────────────────────── -->
<div id="page-home" class="page active">
  <div class="hero">
    <span class="hero-badge">✦ Freshly Baked Daily ✦</span>
    <h1>Cookies Made With <em>Love</em> & Real Butter</h1>
    <p>Handcrafted artisan cookies delivered warm to your door. Every bite tells a story of tradition, quality ingredients, and pure joy.</p>
    <div class="hero-btns">
      <button class="btn-primary" onclick="showPage('menu')">🍪 Browse Menu</button>
      <button class="btn-outline" onclick="showPage('order')">View My Order</button>
    </div>
  </div>

  <div style="text-align:center; margin-bottom:12px;">
    <div class="section-title">Why Choose Us?</div>
    <div class="section-sub">Every cookie is a masterpiece</div>
  </div>
  <div style="display:flex; gap:24px; justify-content:center; flex-wrap:wrap; padding:0 24px 80px; max-width:1000px; margin:0 auto;">
    <div style="background:#fff;border-radius:20px;padding:28px 24px;flex:1;min-width:200px;box-shadow:0 4px 20px var(--shadow);text-align:center;">
      <div style="font-size:2.5rem;margin-bottom:10px;">🧈</div>
      <div style="font-family:'Playfair Display',serif;font-weight:700;color:var(--warm-brown);margin-bottom:8px;">Real Ingredients</div>
      <div style="font-size:0.88rem;color:var(--soft-brown);">No artificial flavors. Pure butter, fresh eggs, premium chocolate.</div>
    </div>
    <div style="background:#fff;border-radius:20px;padding:28px 24px;flex:1;min-width:200px;box-shadow:0 4px 20px var(--shadow);text-align:center;">
      <div style="font-size:2.5rem;margin-bottom:10px;">⚡</div>
      <div style="font-family:'Playfair Display',serif;font-weight:700;color:var(--warm-brown);margin-bottom:8px;">Fast Delivery</div>
      <div style="font-size:0.88rem;color:var(--soft-brown);">Order before 2 PM and get same-day delivery, still warm.</div>
    </div>
    <div style="background:#fff;border-radius:20px;padding:28px 24px;flex:1;min-width:200px;box-shadow:0 4px 20px var(--shadow);text-align:center;">
      <div style="font-size:2.5rem;margin-bottom:10px;">💚</div>
      <div style="font-family:'Playfair Display',serif;font-weight:700;color:var(--warm-brown);margin-bottom:8px;">WhatsApp Orders</div>
      <div style="font-size:0.88rem;color:var(--soft-brown);">Place orders directly via WhatsApp for quick, personal service.</div>
    </div>
    <div style="background:#fff;border-radius:20px;padding:28px 24px;flex:1;min-width:200px;box-shadow:0 4px 20px var(--shadow);text-align:center;">
      <div style="font-size:2.5rem;margin-bottom:10px;">🎁</div>
      <div style="font-family:'Playfair Display',serif;font-weight:700;color:var(--warm-brown);margin-bottom:8px;">Gift Boxes</div>
      <div style="font-size:0.88rem;color:var(--soft-brown);">Beautiful packaging for gifting. Custom messages available.</div>
    </div>
  </div>
</div>

<!-- ── MENU ─────────────────────────────────────── -->
<div id="page-menu" class="page">
  <div style="padding: 60px 0 20px;">
    <div class="section-title">Our Cookie Menu</div>
    <div class="section-sub">Pick your favourites — we bake fresh every morning 🍪</div>
  </div>
  <div class="cookies-grid" id="cookiesGrid"></div>
</div>

<!-- ── LOGIN / REGISTER ─────────────────────────── -->
<div id="page-login" class="page">
  <div class="form-wrap">
    <!-- LOGIN -->
    <div id="loginForm">
      <div class="form-card">
        <h2>Welcome Back 🍪</h2>
        <p class="sub">Sign in to track your orders and save favourites.</p>
        <div id="loginAlert"></div>
        <div class="field"><label>Email Address</label><input type="email" id="loginEmail" placeholder="you@email.com"></div>
        <div class="field"><label>Password</label><input type="password" id="loginPass" placeholder="••••••••"></div>
        <button class="btn-primary" style="width:100%;margin-top:6px;" onclick="doLogin()">Sign In</button>
        <div class="form-divider">Don't have an account? <span class="switch-link" onclick="toggleAuthForm('register')">Create one</span></div>
      </div>
    </div>
    <!-- REGISTER -->
    <div id="registerForm" style="display:none;">
      <div class="form-card">
        <h2>Join CrumbleCraft ✨</h2>
        <p class="sub">Create an account to start ordering delicious cookies.</p>
        <div id="registerAlert"></div>
        <div class="field"><label>Full Name</label><input type="text" id="regName" placeholder="Jane Smith"></div>
        <div class="field"><label>Email Address</label><input type="email" id="regEmail" placeholder="you@email.com"></div>
        <div class="field"><label>Phone (for WhatsApp updates)</label><input type="tel" id="regPhone" placeholder="+91 98765 43210"></div>
        <div class="field"><label>Password</label><input type="password" id="regPass" placeholder="Choose a strong password"></div>
        <button class="btn-primary" style="width:100%;margin-top:6px;" onclick="doRegister()">Create Account</button>
        <div class="form-divider">Already have an account? <span class="switch-link" onclick="toggleAuthForm('login')">Sign in</span></div>
      </div>
    </div>
  </div>
</div>

<!-- ── ORDER ─────────────────────────────────────── -->
<div id="page-order" class="page">
  <div class="order-wrap">
    <div class="section-title" style="margin-bottom:6px;">Your Order 🛒</div>
    <div class="section-sub">Review and customise before sending</div>

    <div class="order-summary">
      <h3>Order Summary</h3>
      <div id="cartItems"></div>
      <div class="cart-total">
        <span>Total</span>
        <span id="cartTotal">₹0.00</span>
      </div>
    </div>

    <!-- Order Details Form -->
    <div id="orderDetailsForm" style="display:none;">
      <div class="form-card" style="margin-bottom:24px;">
        <h2 style="font-size:1.5rem;margin-bottom:4px;">Delivery Details</h2>
        <p class="sub">Tell us where to bring your cookies!</p>
        <div id="orderAlert"></div>
        <div class="field"><label>Full Name</label><input type="text" id="orderName" placeholder="Jane Smith"></div>
        <div class="field"><label>Phone Number</label><input type="tel" id="orderPhone" placeholder="+91 98765 43210"></div>
        <div class="field"><label>Delivery Address</label><textarea id="orderAddress" placeholder="House/Flat No., Street, Area, City, PIN"></textarea></div>
        <div class="field">
          <label>Delivery Time</label>
          <select id="orderTime">
            <option value="">Select delivery slot</option>
            <option>ASAP (within 2 hours)</option>
            <option>Morning (9 AM – 12 PM)</option>
            <option>Afternoon (12 PM – 4 PM)</option>
            <option>Evening (4 PM – 8 PM)</option>
          </select>
        </div>
        <div class="field"><label>Special Instructions (optional)</label><textarea id="orderNotes" placeholder="Nut allergy? Gift wrapping? Write here..."></textarea></div>
        <div style="display:flex;gap:12px;flex-wrap:wrap;margin-top:10px;">
          <button class="btn-primary" onclick="placeOrder()">Place Order</button>
          <a id="waLink" class="wa-btn" href="#" target="_blank">
            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            Order via WhatsApp
          </a>
        </div>
      </div>
    </div>

    <div id="loginPrompt" style="text-align:center;padding:20px 0;display:none;">
      <p style="color:var(--soft-brown);margin-bottom:16px;">Please login to place your order.</p>
      <button class="btn-primary" onclick="showPage('login')">Login / Register</button>
    </div>

    <div id="emptyCartMsg" style="text-align:center;padding:30px 0;">
      <div style="font-size:3rem;margin-bottom:12px;">🍪</div>
      <p style="color:var(--soft-brown);font-size:1rem;">Your cart is empty. <span class="switch-link" onclick="showPage('menu')">Browse our menu</span></p>
    </div>

    <!-- WhatsApp Quick Link -->
    <div style="background:#fff;border-radius:20px;padding:28px;box-shadow:0 4px 20px var(--shadow);text-align:center;border:1.5px solid rgba(37,211,102,0.2);">
      <div style="font-size:2rem;margin-bottom:10px;">💬</div>
      <div style="font-family:'Playfair Display',serif;font-size:1.2rem;font-weight:700;color:var(--warm-brown);margin-bottom:8px;">Prefer WhatsApp?</div>
      <p style="color:var(--soft-brown);font-size:0.9rem;margin-bottom:18px;">Chat directly with us for custom orders, bulk quantities, or gift boxes.</p>
      <a class="wa-btn" href="https://wa.me/919876543210?text=Hi%20CrumbleCraft!%20I'd%20like%20to%20place%20a%20cookie%20order%20🍪" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor" style="width:20px;height:20px;"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        Chat on WhatsApp
      </a>
    </div>
  </div>
</div>

<!-- ── FOOTER ────────────────────────────────────── -->
<footer>
  <strong>CrumbleCraft</strong> — Artisan Cookies &nbsp;|&nbsp;
  📍 Chennai, India &nbsp;|&nbsp;
  <a href="https://wa.me/919876543210" target="_blank">💬 WhatsApp Us</a> &nbsp;|&nbsp;
  © 2026 CrumbleCraft. All rights reserved.
</footer>

<div id="toast"></div>

<script>
// ── DATA ──────────────────────────────────────────
const COOKIES = [
  { id:1, name:"Classic Choco Chip", emoji:"🍪", desc:"Buttery dough, Callebaut dark chocolate chips, a touch of sea salt.", price:120, badge:null },
  { id:2, name:"Red Velvet Dream", emoji:"❤️", desc:"Velvety cocoa cookie, cream cheese drizzle, crushed Oreo crumbs.", price:140, badge:"New" },
  { id:3, name:"Salted Caramel Bliss", emoji:"🍯", desc:"Brown butter, gooey caramel pockets, flaked Maldon salt.", price:130, badge:null },
  { id:4, name:"Double Fudge Brownie", emoji:"🍫", desc:"Rich fudge cookie, double chocolate ganache centre, cocoa dust.", price:150, badge:"Hot" },
  { id:5, name:"Lemon Lavender", emoji:"🍋", desc:"Zesty lemon, floral lavender, vanilla glaze on a soft sugar base.", price:125, badge:null },
  { id:6, name:"Peanut Butter Crunch", emoji:"🥜", desc:"Chunky peanut butter, roasted peanut pieces, honey drizzle.", price:135, badge:null },
  { id:7, name:"Matcha White Choc", emoji:"🍵", desc:"Premium Japanese matcha, creamy white chocolate swirls.", price:145, badge:"New" },
  { id:8, name:"Birthday Funfetti", emoji:"🎉", desc:"Vanilla bean dough, rainbow sprinkles, cotton candy glaze.", price:130, badge:null },
];

let cart = {};
let currentUser = null;

// ── PAGES ─────────────────────────────────────────
function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  if (id === 'menu') renderMenu();
  if (id === 'order') renderOrder();
  window.scrollTo({top:0, behavior:'smooth'});
}

// ── MENU ──────────────────────────────────────────
function renderMenu() {
  const g = document.getElementById('cookiesGrid');
  g.innerHTML = COOKIES.map(c => `
    <div class="cookie-card">
      <div class="cookie-emoji">
        ${c.emoji}
        ${c.badge ? `<span class="cookie-badge-new">${c.badge}</span>` : ''}
      </div>
      <div class="cookie-info">
        <div class="cookie-name">${c.name}</div>
        <div class="cookie-desc">${c.desc}</div>
        <div class="cookie-footer">
          <span class="cookie-price">₹${c.price}</span>
          <button class="add-btn" onclick="addToCart(${c.id})">+ Add</button>
        </div>
      </div>
    </div>
  `).join('');
}

// ── CART ──────────────────────────────────────────
function addToCart(id) {
  cart[id] = (cart[id] || 0) + 1;
  updateCartCount();
  const c = COOKIES.find(x => x.id === id);
  showToast(`${c.emoji} ${c.name} added!`);
}

function updateCartCount() {
  const total = Object.values(cart).reduce((a,b)=>a+b,0);
  document.getElementById('cartCount').textContent = total;
}

function renderOrder() {
  const items = document.getElementById('cartItems');
  const totalEl = document.getElementById('cartTotal');
  const emptyMsg = document.getElementById('emptyCartMsg');
  const detailsForm = document.getElementById('orderDetailsForm');
  const loginPrompt = document.getElementById('loginPrompt');

  const keys = Object.keys(cart).filter(k => cart[k] > 0);

  if (!keys.length) {
    items.innerHTML = '';
    totalEl.textContent = '₹0.00';
    emptyMsg.style.display = 'block';
    detailsForm.style.display = 'none';
    loginPrompt.style.display = 'none';
    return;
  }

  emptyMsg.style.display = 'none';
  let total = 0;
  items.innerHTML = keys.map(k => {
    const c = COOKIES.find(x => x.id === +k);
    const sub = c.price * cart[k];
    total += sub;
    return `
      <div class="cart-item">
        <span>${c.emoji} <span class="cart-item-name">${c.name}</span></span>
        <div style="display:flex;align-items:center;gap:14px;">
          <div class="qty-controls">
            <button class="qty-btn" onclick="changeQty(${k},-1)">−</button>
            <span>${cart[k]}</span>
            <button class="qty-btn" onclick="changeQty(${k},1)">+</button>
          </div>
          <span class="cart-item-price">₹${sub}</span>
        </div>
      </div>`;
  }).join('');
  totalEl.textContent = `₹${total}.00`;

  if (currentUser) {
    detailsForm.style.display = 'block';
    loginPrompt.style.display = 'none';
    document.getElementById('orderName').value = currentUser.name || '';
    document.getElementById('orderPhone').value = currentUser.phone || '';
  } else {
    detailsForm.style.display = 'none';
    loginPrompt.style.display = 'block';
  }
}

function changeQty(id, delta) {
  cart[id] = Math.max(0, (cart[id]||0) + delta);
  updateCartCount();
  renderOrder();
}

// ── AUTH ──────────────────────────────────────────
function toggleAuthForm(type) {
  document.getElementById('loginForm').style.display = type === 'login' ? 'block' : 'none';
  document.getElementById('registerForm').style.display = type === 'register' ? 'block' : 'none';
}

function doLogin() {
  const email = document.getElementById('loginEmail').value.trim();
  const pass  = document.getElementById('loginPass').value;
  const al    = document.getElementById('loginAlert');
  al.className = '';

  if (!email || !pass) { showAlert(al, 'error', 'Please fill in all fields.'); return; }

  const users = JSON.parse(localStorage.getItem('cc_users') || '[]');
  const user  = users.find(u => u.email === email && u.pass === pass);
  if (!user) { showAlert(al, 'error', 'Invalid email or password.'); return; }

  currentUser = user;
  showAlert(al, 'success', `Welcome back, ${user.name}! 🍪`);
  document.getElementById('authNavBtn').textContent = user.name.split(' ')[0];
  setTimeout(() => showPage('menu'), 1200);
}

function doRegister() {
  const name  = document.getElementById('regName').value.trim();
  const email = document.getElementById('regEmail').value.trim();
  const phone = document.getElementById('regPhone').value.trim();
  const pass  = document.getElementById('regPass').value;
  const al    = document.getElementById('registerAlert');
  al.className = '';

  if (!name || !email || !pass) { showAlert(al, 'error', 'Please fill in all required fields.'); return; }

  const users = JSON.parse(localStorage.getItem('cc_users') || '[]');
  if (users.find(u => u.email === email)) { showAlert(al, 'error', 'An account with this email already exists.'); return; }

  const user = { name, email, phone, pass };
  users.push(user);
  localStorage.setItem('cc_users', JSON.stringify(users));
  currentUser = user;
  showAlert(al, 'success', `Account created! Welcome, ${name} 🎉`);
  document.getElementById('authNavBtn').textContent = name.split(' ')[0];
  setTimeout(() => showPage('menu'), 1200);
}

function showAlert(el, type, msg) {
  el.className = 'alert ' + type;
  el.textContent = msg;
}

// ── PLACE ORDER ───────────────────────────────────
function placeOrder() {
  const name    = document.getElementById('orderName').value.trim();
  const phone   = document.getElementById('orderPhone').value.trim();
  const address = document.getElementById('orderAddress').value.trim();
  const time    = document.getElementById('orderTime').value;
  const notes   = document.getElementById('orderNotes').value.trim();
  const al      = document.getElementById('orderAlert');
  al.className = '';

  if (!name || !phone || !address || !time) { showAlert(al, 'error', 'Please fill in all delivery details.'); return; }

  // Build WhatsApp message
  const keys = Object.keys(cart).filter(k => cart[k] > 0);
  let orderText = `🍪 *CrumbleCraft Order*\n\n`;
  orderText += `*Name:* ${name}\n*Phone:* ${phone}\n*Address:* ${address}\n*Slot:* ${time}\n\n`;
  orderText += `*Items:*\n`;
  let total = 0;
  keys.forEach(k => {
    const c = COOKIES.find(x => x.id === +k);
    const sub = c.price * cart[k];
    total += sub;
    orderText += `  • ${c.name} x${cart[k]} = ₹${sub}\n`;
  });
  orderText += `\n*Total:* ₹${total}\n`;
  if (notes) orderText += `\n*Notes:* ${notes}`;

  const waUrl = `https://wa.me/918825831137?text=${encodeURIComponent(orderText)}`;
  document.getElementById('waLink').href = waUrl;
  document.getElementById('waLink').click();

  showAlert(al, 'success', '🎉 Order sent via WhatsApp! We\'ll confirm shortly.');
  showToast('Order placed via WhatsApp!');
}

// ── TOAST ─────────────────────────────────────────
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2200);
}

// ── INIT ──────────────────────────────────────────
renderMenu();
</script>
</body>
</html>
