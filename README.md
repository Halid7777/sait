<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NeoTech — Магазин электроники</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@400;700;900&family=Manrope:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --orange: #ff6b00;
  --pink:   #ff2d78;
  --purple: #7c3aed;
  --cyan:   #00c8e0;
  --green:  #00c47a;
  --yellow: #ffd000;
  --bg:     #fff8f2;
  --text:   #1a1a2e;
  --muted:  #8888a0;
  --card:   #ffffff;
  --r:      16px;
  --rlg:    24px;
}

html { scroll-behavior: smooth; }
body { font-family: 'Manrope', sans-serif; background: var(--bg); color: var(--text); overflow-x: hidden; }

/* ===== HEADER ===== */
header {
  position: sticky; top: 0; z-index: 200;
  background: rgba(255,255,255,0.92);
  backdrop-filter: blur(18px);
  border-bottom: 3px solid;
  border-image: linear-gradient(90deg,#ff6b00,#ff2d78,#7c3aed,#00c8e0) 1;
  padding: 0 5%;
}
.nav { display:flex; align-items:center; justify-content:space-between; height:64px; gap:16px; }
.logo {
  font-family:'Unbounded',sans-serif; font-weight:900; font-size:clamp(17px,3vw,23px);
  background:linear-gradient(90deg,#ff6b00,#ff2d78,#7c3aed);
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  white-space:nowrap; letter-spacing:-1px;
}
.nav-links { display:flex; gap:24px; list-style:none; }
.nav-links a { color:var(--muted); text-decoration:none; font-size:14px; font-weight:600; transition:color .2s; }
.nav-links a:hover { color:var(--orange); }
.nav-actions { display:flex; gap:10px; align-items:center; flex-shrink:0; }
.btn-cart {
  background:linear-gradient(135deg,#ff6b00,#ff2d78);
  border:none; border-radius:12px; padding:9px 20px;
  color:#fff; font-family:'Manrope',sans-serif; font-weight:700; font-size:14px;
  cursor:pointer; transition:transform .15s, box-shadow .15s; white-space:nowrap;
}
.btn-cart:hover { transform:translateY(-2px); box-shadow:0 6px 24px rgba(255,107,0,0.35); }
.cart-badge {
  background:#fff; color:#ff2d78;
  font-size:10px; font-weight:800;
  min-width:18px; height:18px; border-radius:9px;
  display:inline-flex; align-items:center; justify-content:center;
  padding:0 4px; margin-left:5px;
}
.hamburger { display:none; background:none; border:none; cursor:pointer; flex-direction:column; gap:5px; padding:4px; }
.hamburger span { display:block; width:24px; height:2.5px; background:var(--text); border-radius:2px; }
@media(max-width:768px){ .nav-links{display:none;} .hamburger{display:flex;} }

/* ===== HERO ===== */
.hero {
  position:relative; overflow:hidden;
  min-height:clamp(480px,80vh,680px);
  display:flex; align-items:center;
  padding:60px 5%;
  background: linear-gradient(135deg,#fff8f2 0%,#fff0fa 40%,#f0f4ff 100%);
}
.blob { position:absolute; border-radius:50%; filter:blur(80px); opacity:.5; animation:float 8s ease-in-out infinite; }
.b1 { width:480px; height:480px; background:#ffb347; top:-160px; right:-80px; }
.b2 { width:380px; height:380px; background:#ff69b4; bottom:-100px; left:-80px; animation-delay:2s; }
.b3 { width:280px; height:280px; background:#a78bfa; top:40%; right:22%; animation-delay:4s; }
.b4 { width:250px; height:250px; background:#67e8f9; top:15%; left:28%; animation-delay:1.5s; }
.b5 { width:200px; height:200px; background:#86efac; bottom:10%; right:10%; animation-delay:3s; }
@keyframes float{0%,100%{transform:translateY(0) scale(1)}50%{transform:translateY(-28px) scale(1.04)}}

.hero-content { position:relative; z-index:1; max-width:580px; }
.hero-pill {
  display:inline-flex; align-items:center; gap:8px;
  background:#fff; border-radius:100px; padding:7px 16px;
  font-size:12px; font-weight:700; color:var(--orange); letter-spacing:.5px;
  box-shadow:0 4px 20px rgba(255,107,0,0.2); margin-bottom:28px;
  animation:fadeUp .5s ease both .1s;
}
.pill-dot { width:8px; height:8px; background:var(--orange); border-radius:50%; animation:blink 1.4s ease-in-out infinite; flex-shrink:0; }
@keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}

.hero h1 {
  font-family:'Unbounded',sans-serif; font-weight:900;
  font-size:clamp(28px,6vw,64px); line-height:1.05; letter-spacing:-2px;
  color:var(--text); margin-bottom:20px;
  animation:fadeUp .5s ease both .2s;
}
.g1 { background:linear-gradient(90deg,#ff6b00,#ff2d78); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
.g2 { background:linear-gradient(90deg,#7c3aed,#00c8e0); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
.g3 { background:linear-gradient(90deg,#00c8e0,#00c47a); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }

.hero-desc { font-size:clamp(14px,2vw,17px); color:var(--muted); line-height:1.7; max-width:440px; margin-bottom:36px; animation:fadeUp .5s ease both .3s; }

.hero-btns { display:flex; gap:14px; flex-wrap:wrap; animation:fadeUp .5s ease both .4s; }
.btn-main {
  background:linear-gradient(135deg,#ff6b00,#ff2d78);
  border:none; border-radius:var(--r); padding:14px 28px;
  color:#fff; font-family:'Manrope',sans-serif; font-weight:700; font-size:15px;
  cursor:pointer; transition:transform .2s, box-shadow .2s;
  box-shadow:0 6px 24px rgba(255,107,0,0.3);
}
.btn-main:hover { transform:translateY(-2px); box-shadow:0 10px 36px rgba(255,107,0,0.4); }
.btn-ghost {
  background:#fff; border:2px solid #e8e0ff;
  border-radius:var(--r); padding:14px 28px;
  color:var(--purple); font-family:'Manrope',sans-serif; font-weight:700; font-size:15px;
  cursor:pointer; transition:border-color .2s, background .2s;
}
.btn-ghost:hover { border-color:var(--purple); background:#f5f0ff; }

.hero-stats { display:flex; gap:32px; margin-top:48px; flex-wrap:wrap; animation:fadeUp .5s ease both .5s; }
.hstat .num {
  font-family:'Unbounded',sans-serif; font-weight:900; font-size:clamp(22px,3vw,30px);
  background:linear-gradient(90deg,var(--orange),var(--pink)); -webkit-background-clip:text; -webkit-text-fill-color:transparent;
}
.hstat .lbl { font-size:12px; color:var(--muted); margin-top:2px; }

.hero-img-wrap {
  position:absolute; right:5%; top:50%; transform:translateY(-50%);
  z-index:1; animation:float 5s ease-in-out infinite;
}
.hero-emoji { font-size:clamp(100px,14vw,180px); filter:drop-shadow(0 24px 60px rgba(255,45,120,.35)) drop-shadow(0 8px 20px rgba(255,107,0,.3)); }
@media(max-width:900px){ .hero-img-wrap{display:none;} }

@keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}

/* ===== SECTIONS ===== */
section { padding:64px 5%; }
.sec-head { margin-bottom:32px; }
.sec-title { font-family:'Unbounded',sans-serif; font-weight:700; font-size:clamp(20px,3vw,28px); margin-bottom:6px; }
.sec-sub { color:var(--muted); font-size:14px; }

/* ===== BRANDS ===== */
.brands-row { display:flex; gap:14px; overflow-x:auto; padding-bottom:6px; scrollbar-width:none; }
.brands-row::-webkit-scrollbar{display:none;}
.bc {
  flex-shrink:0; background:#fff; border-radius:14px; padding:13px 22px;
  font-weight:700; font-size:14px; color:var(--text);
  box-shadow:0 2px 12px rgba(0,0,0,0.07); border:2px solid transparent;
  cursor:pointer; transition:border-color .2s, transform .2s, color .2s;
  white-space:nowrap;
}
.bc:hover { transform:translateY(-3px); }
.bc:nth-child(1):hover{border-color:#ff6b00;color:#ff6b00;}
.bc:nth-child(2):hover{border-color:#555;color:#333;}
.bc:nth-child(3):hover{border-color:#ff2d78;color:#ff2d78;}
.bc:nth-child(4):hover{border-color:#ff6a00;color:#ff6a00;}
.bc:nth-child(5):hover{border-color:#ffd000;color:#b38600;}
.bc:nth-child(6):hover{border-color:#7c3aed;color:#7c3aed;}
.bc:nth-child(7):hover{border-color:#00c47a;color:#00c47a;}

/* ===== CATEGORIES ===== */
.cats { display:grid; grid-template-columns:repeat(auto-fill,minmax(130px,1fr)); gap:12px; }
.cat {
  background:#fff; border-radius:var(--r); padding:20px 14px;
  display:flex; flex-direction:column; align-items:center; gap:10px;
  text-align:center; cursor:pointer; border:2px solid transparent;
  box-shadow:0 2px 12px rgba(0,0,0,0.06);
  transition:transform .25s, box-shadow .25s, border-color .25s;
}
.cat:hover{transform:translateY(-5px);box-shadow:0 12px 32px rgba(0,0,0,0.12);}
.cat:nth-child(1):hover{border-color:#ff6b00;}
.cat:nth-child(2):hover{border-color:#ff2d78;}
.cat:nth-child(3):hover{border-color:#7c3aed;}
.cat:nth-child(4):hover{border-color:#00c8e0;}
.cat:nth-child(5):hover{border-color:#00c47a;}
.cat:nth-child(6):hover{border-color:#ffd000;}
.cat-ico{width:52px;height:52px;border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:26px;}
.cat-nm{font-size:13px;font-weight:700;color:var(--text);}
.cat-cnt{font-size:11px;color:var(--muted);}

/* ===== PRODUCTS ===== */
.products { display:grid; grid-template-columns:repeat(auto-fill,minmax(255px,1fr)); gap:20px; }
.pcard {
  background:#fff; border-radius:var(--rlg); overflow:hidden;
  box-shadow:0 4px 20px rgba(0,0,0,0.07); border:2px solid transparent;
  cursor:pointer; transition:transform .3s, box-shadow .3s, border-color .3s;
}
.pcard:hover{transform:translateY(-6px);}
.po:hover{border-color:#ff6b00;box-shadow:0 16px 48px rgba(255,107,0,0.18);}
.pp:hover{border-color:#ff2d78;box-shadow:0 16px 48px rgba(255,45,120,0.18);}
.pv:hover{border-color:#7c3aed;box-shadow:0 16px 48px rgba(124,58,237,0.18);}
.pc:hover{border-color:#00c8e0;box-shadow:0 16px 48px rgba(0,200,224,0.18);}
.pg:hover{border-color:#00c47a;box-shadow:0 16px 48px rgba(0,196,122,0.18);}
.py:hover{border-color:#ffd000;box-shadow:0 16px 48px rgba(255,208,0,0.22);}

.pimg{height:190px;display:flex;align-items:center;justify-content:center;font-size:70px;position:relative;}
.pbadge{position:absolute;top:12px;left:12px;border-radius:10px;padding:4px 10px;font-size:11px;font-weight:800;letter-spacing:.5px;}
.hot{background:linear-gradient(135deg,#ff6b00,#ff2d78);color:#fff;}
.newb{background:linear-gradient(135deg,#7c3aed,#00c8e0);color:#fff;}
.sale{background:linear-gradient(135deg,#ffd000,#ff6b00);color:#fff;}
.pfav{position:absolute;top:12px;right:12px;background:rgba(255,255,255,0.9);border:none;border-radius:10px;width:34px;height:34px;display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:16px;transition:background .2s;}
.pfav:hover{background:#ffe0ee;}

.pinfo{padding:16px;}
.pbrand{font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px;}
.pname{font-weight:700;font-size:15px;margin-bottom:8px;line-height:1.35;color:var(--text);}
.prating{display:flex;align-items:center;gap:6px;margin-bottom:14px;}
.stars{color:#ffd000;font-size:13px;}
.rnum{font-size:12px;color:var(--muted);}
.pfoot{display:flex;align-items:center;justify-content:space-between;gap:8px;}
.pprice{font-family:'Unbounded',sans-serif;font-weight:700;font-size:clamp(15px,2vw,17px);color:var(--orange);}
.pprice .old{font-family:'Manrope',sans-serif;font-weight:400;font-size:12px;color:var(--muted);text-decoration:line-through;display:block;margin-bottom:2px;}
.btn-add{background:linear-gradient(135deg,#7c3aed,#ff2d78);border:none;border-radius:10px;padding:9px 16px;color:#fff;font-family:'Manrope',sans-serif;font-weight:700;font-size:13px;cursor:pointer;transition:opacity .2s, transform .15s;white-space:nowrap;}
.btn-add:hover{opacity:.85;transform:scale(1.04);}
.btn-add.added{background:linear-gradient(135deg,#00c47a,#00c8e0);}

/* ===== PROMO BANNERS ===== */
.promos{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:20px;padding:0 5% 60px;}
.promo{border-radius:var(--rlg);padding:32px 28px;position:relative;overflow:hidden;cursor:pointer;transition:transform .2s,box-shadow .2s;}
.promo:hover{transform:translateY(-4px);box-shadow:0 16px 48px rgba(0,0,0,0.15);}
.promo::before{content:'';position:absolute;right:-20px;bottom:-20px;width:130px;height:130px;border-radius:50%;background:rgba(255,255,255,0.15);}
.promo::after{content:'';position:absolute;right:36px;bottom:36px;width:70px;height:70px;border-radius:50%;background:rgba(255,255,255,0.1);}
.pr1{background:linear-gradient(135deg,#ff6b00,#ff2d78);}
.pr2{background:linear-gradient(135deg,#7c3aed,#00c8e0);}
.pr3{background:linear-gradient(135deg,#ffd000,#00c47a);}
.ptag{font-size:11px;font-weight:800;letter-spacing:2px;color:rgba(255,255,255,0.85);text-transform:uppercase;margin-bottom:8px;}
.ptitle{font-family:'Unbounded',sans-serif;font-weight:900;font-size:clamp(18px,2.5vw,24px);color:#fff;line-height:1.15;margin-bottom:8px;}
.pdesc{font-size:13px;color:rgba(255,255,255,0.85);margin-bottom:20px;}
.pcta{display:inline-block;background:rgba(255,255,255,0.25);backdrop-filter:blur(4px);border:1px solid rgba(255,255,255,0.4);border-radius:10px;padding:8px 18px;color:#fff;font-weight:700;font-size:13px;}

/* ===== FEATURES ===== */
.feats{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;}
.feat{background:#fff;border-radius:var(--r);padding:24px 20px;box-shadow:0 2px 12px rgba(0,0,0,0.06);display:flex;gap:16px;align-items:flex-start;border-left:4px solid;transition:transform .2s,box-shadow .2s;}
.feat:hover{transform:translateY(-3px);box-shadow:0 8px 28px rgba(0,0,0,0.1);}
.feat:nth-child(1){border-color:#ff6b00;}
.feat:nth-child(2){border-color:#ff2d78;}
.feat:nth-child(3){border-color:#7c3aed;}
.feat:nth-child(4){border-color:#00c47a;}
.feat-ico{font-size:28px;flex-shrink:0;}
.ftitle{font-weight:700;font-size:14px;margin-bottom:4px;}
.fdesc{font-size:12px;color:var(--muted);line-height:1.55;}

/* ===== NEWSLETTER ===== */
.newsletter{margin:0 5% 60px;background:linear-gradient(135deg,#fff0fa,#f0f4ff,#fff8f2);border:2px solid #ffd0e8;border-radius:var(--rlg);padding:48px 40px;display:flex;align-items:center;justify-content:space-between;gap:32px;flex-wrap:wrap;}
.nl-title{font-family:'Unbounded',sans-serif;font-weight:900;font-size:clamp(17px,2.5vw,24px);margin-bottom:6px;}
.nl-title span{background:linear-gradient(90deg,#ff6b00,#7c3aed);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.nl-desc{font-size:14px;color:var(--muted);}
.nl-form{display:flex;gap:10px;flex-wrap:wrap;}
.nl-input{border:2px solid #e8e0ff;border-radius:12px;padding:12px 18px;font-family:'Manrope',sans-serif;font-size:14px;color:var(--text);background:#fff;width:240px;max-width:100%;outline:none;transition:border-color .2s;}
.nl-input:focus{border-color:var(--purple);}
.nl-btn{background:linear-gradient(135deg,#ff6b00,#ff2d78);border:none;border-radius:12px;padding:12px 24px;color:#fff;font-family:'Manrope',sans-serif;font-weight:700;font-size:14px;cursor:pointer;transition:transform .2s,box-shadow .2s;white-space:nowrap;}
.nl-btn:hover{transform:translateY(-2px);box-shadow:0 6px 24px rgba(255,107,0,.3);}

/* ===== FOOTER ===== */
footer{background:#fff;border-top:3px solid;border-image:linear-gradient(90deg,#ff6b00,#ff2d78,#7c3aed,#00c8e0) 1;padding:40px 5%;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:20px;}
.fl{font-family:'Unbounded',sans-serif;font-weight:900;font-size:20px;background:linear-gradient(90deg,#ff6b00,#ff2d78,#7c3aed);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.flinks{display:flex;gap:20px;flex-wrap:wrap;}
.flinks a{color:var(--muted);font-size:13px;text-decoration:none;font-weight:600;transition:color .2s;}
.flinks a:hover{color:var(--orange);}
.fcopy{font-size:12px;color:var(--muted);}

/* ===== TOAST ===== */
#toast{position:fixed;bottom:24px;right:24px;z-index:999;background:#fff;border-radius:14px;padding:14px 20px;font-size:14px;font-weight:700;color:var(--text);box-shadow:0 8px 32px rgba(0,0,0,0.15);border-left:4px solid var(--orange);opacity:0;transform:translateY(14px);transition:opacity .3s,transform .3s;pointer-events:none;max-width:280px;}
#toast.show{opacity:1;transform:translateY(0);}

@media(max-width:640px){
  .products{grid-template-columns:repeat(auto-fill,minmax(155px,1fr));gap:12px;}
  .pimg{height:140px;font-size:54px;}
  .hero{min-height:420px;padding:44px 5%;}
  footer{flex-direction:column;align-items:flex-start;}
  .newsletter{padding:28px 20px;}
}
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <nav class="nav">
    <div class="logo">Neo⚡Tech</div>
    <ul class="nav-links">
      <li><a href="#">Каталог</a></li>
      <li><a href="#">Акции</a></li>
      <li><a href="#">Бренды</a></li>
      <li><a href="#">Контакты</a></li>
    </ul>
    <div class="nav-actions">
      <button class="btn-cart" onclick="openCart()">
        🛒 Корзина <span class="cart-badge" id="cnt">0</span>
      </button>
      <button class="hamburger" onclick="showToast('📋 Каталог · Акции · Бренды · Контакты')">
        <span></span><span></span><span></span>
      </button>
    </div>
  </nav>
</header>

<!-- HERO -->
<div class="hero">
  <div class="blob b1"></div><div class="blob b2"></div>
  <div class="blob b3"></div><div class="blob b4"></div><div class="blob b5"></div>
  <div class="hero-content">
    <div class="hero-pill"><span class="pill-dot"></span>🔥 Распродажа — до −50%</div>
    <h1>Лучшая<br><span class="g1">электроника</span><br><span class="g2">вашей жизни</span></h1>
    <p class="hero-desc">Смартфоны, ноутбуки, гаджеты. Оригинальная техника с доставкой по всему Казахстану.</p>
    <div class="hero-btns">
      <button class="btn-main" onclick="document.getElementById('catalog').scrollIntoView({behavior:'smooth'})">Смотреть каталог</button>
      <button class="btn-ghost" onclick="showToast('📦 Акции обновляются каждую пятницу!')">Все акции →</button>
    </div>
    <div class="hero-stats">
      <div class="hstat"><div class="num">12K+</div><div class="lbl">товаров</div></div>
      <div class="hstat"><div class="num">98%</div><div class="lbl">довольных</div></div>
      <div class="hstat"><div class="num">1–2</div><div class="lbl">дня доставки</div></div>
    </div>
  </div>
  <div class="hero-img-wrap">
    <div class="hero-emoji">📱</div>
  </div>
</div>

<!-- BRANDS -->
<section>
  <div class="sec-head"><h2 class="sec-title">Популярные бренды</h2></div>
  <div class="brands-row">
    <div class="bc" onclick="showToast('Samsung — 284 товара')">📱 Samsung</div>
    <div class="bc" onclick="showToast('Apple — 196 товаров')"> Apple</div>
    <div class="bc" onclick="showToast('Sony — 142 товара')">🎧 Sony</div>
    <div class="bc" onclick="showToast('Xiaomi — 310 товаров')">📡 Xiaomi</div>
    <div class="bc" onclick="showToast('JBL — 88 товаров')">🔊 JBL</div>
    <div class="bc" onclick="showToast('ASUS — 76 товаров')">💻 ASUS</div>
    <div class="bc" onclick="showToast('Huawei — 95 товаров')">🌐 Huawei</div>
  </div>
</section>

<!-- CATEGORIES -->
<section>
  <div class="sec-head"><h2 class="sec-title">Категории</h2><p class="sec-sub">Найдите нужное быстро</p></div>
  <div class="cats">
    <div class="cat" onclick="showToast('📱 Смартфоны — 284 товара')">
      <div class="cat-ico" style="background:#fff5ee">📱</div>
      <div class="cat-nm">Смартфоны</div><div class="cat-cnt">284 товара</div>
    </div>
    <div class="cat" onclick="showToast('💻 Ноутбуки — 156 товаров')">
      <div class="cat-ico" style="background:#fdf0f8">💻</div>
      <div class="cat-nm">Ноутбуки</div><div class="cat-cnt">156 товаров</div>
    </div>
    <div class="cat" onclick="showToast('🎧 Наушники — 320 товаров')">
      <div class="cat-ico" style="background:#f5f0ff">🎧</div>
      <div class="cat-nm">Наушники</div><div class="cat-cnt">320 товаров</div>
    </div>
    <div class="cat" onclick="showToast('📟 Планшеты — 98 товаров')">
      <div class="cat-ico" style="background:#f0fcff">📟</div>
      <div class="cat-nm">Планшеты</div><div class="cat-cnt">98 товаров</div>
    </div>
    <div class="cat" onclick="showToast('⌚ Умные часы — 77 товаров')">
      <div class="cat-ico" style="background:#f0fff8">⌚</div>
      <div class="cat-nm">Умные часы</div><div class="cat-cnt">77 товаров</div>
    </div>
    <div class="cat" onclick="showToast('🔌 Аксессуары — 512 товаров')">
      <div class="cat-ico" style="background:#fffdf0">🔌</div>
      <div class="cat-nm">Аксессуары</div><div class="cat-cnt">512 товаров</div>
    </div>
  </div>
</section>

<!-- PRODUCTS -->
<section id="catalog">
  <div class="sec-head"><h2 class="sec-title">🔥 Хиты продаж</h2><p class="sec-sub">Самое популярное этой недели</p></div>
  <div class="products">

    <div class="pcard po">
      <div class="pimg" style="background:linear-gradient(135deg,#fff5ee,#ffe0cc)">
        <span class="pbadge hot">HOT</span>
        <button class="pfav" onclick="fav(this)">🤍</button>
        <span style="filter:drop-shadow(0 4px 16px rgba(255,107,0,.4))">📱</span>
      </div>
      <div class="pinfo">
        <div class="pbrand">Samsung</div>
        <div class="pname">Galaxy S25 Ultra 512GB</div>
        <div class="prating"><span class="stars">★★★★★</span><span class="rnum">4.9 (1.2k)</span></div>
        <div class="pfoot">
          <div class="pprice"><span class="old">129 990 ₸</span>119 990 ₸</div>
          <button class="btn-add" onclick="add(this,'Galaxy S25 Ultra')">В корзину</button>
        </div>
      </div>
    </div>

    <div class="pcard pp">
      <div class="pimg" style="background:linear-gradient(135deg,#fff0f7,#ffd0e8)">
        <span class="pbadge newb">NEW</span>
        <button class="pfav" onclick="fav(this)">🤍</button>
        <span style="filter:drop-shadow(0 4px 16px rgba(255,45,120,.4))">💻</span>
      </div>
      <div class="pinfo">
        <div class="pbrand">Apple</div>
        <div class="pname">MacBook Air M4 13" 16GB</div>
        <div class="prating"><span class="stars">★★★★★</span><span class="rnum">5.0 (876)</span></div>
        <div class="pfoot">
          <div class="pprice">189 990 ₸</div>
          <button class="btn-add" onclick="add(this,'MacBook Air M4')">В корзину</button>
        </div>
      </div>
    </div>

    <div class="pcard pv">
      <div class="pimg" style="background:linear-gradient(135deg,#f5f0ff,#e0d0ff)">
        <span class="pbadge sale">−20%</span>
        <button class="pfav" onclick="fav(this)">🤍</button>
        <span style="filter:drop-shadow(0 4px 16px rgba(124,58,237,.45))">🎧</span>
      </div>
      <div class="pinfo">
        <div class="pbrand">Sony</div>
        <div class="pname">WH-1000XM6 Wireless</div>
        <div class="prating"><span class="stars">★★★★★</span><span class="rnum">4.8 (3.4k)</span></div>
        <div class="pfoot">
          <div class="pprice"><span class="old">89 990 ₸</span>71 990 ₸</div>
          <button class="btn-add" onclick="add(this,'Sony WH-1000XM6')">В корзину</button>
        </div>
      </div>
    </div>

    <div class="pcard pc">
      <div class="pimg" style="background:linear-gradient(135deg,#f0fcff,#c8f4ff)">
        <button class="pfav" onclick="fav(this)">🤍</button>
        <span style="filter:drop-shadow(0 4px 16px rgba(0,200,224,.5))">⌚</span>
      </div>
      <div class="pinfo">
        <div class="pbrand">Apple</div>
        <div class="pname">Watch Ultra 3 Titanium</div>
        <div class="prating"><span class="stars">★★★★☆</span><span class="rnum">4.7 (654)</span></div>
        <div class="pfoot">
          <div class="pprice">149 990 ₸</div>
          <button class="btn-add" onclick="add(this,'Apple Watch Ultra 3')">В корзину</button>
        </div>
      </div>
    </div>

    <div class="pcard py">
      <div class="pimg" style="background:linear-gradient(135deg,#fff8e0,#ffeda0)">
        <span class="pbadge hot">HOT</span>
        <button class="pfav" onclick="fav(this)">🤍</button>
        <span style="filter:drop-shadow(0 4px 16px rgba(255,208,0,.6))">🎮</span>
      </div>
      <div class="pinfo">
        <div class="pbrand">PlayStation</div>
        <div class="pname">PS5 Pro 2TB Digital Ed.</div>
        <div class="prating"><span class="stars">★★★★★</span><span class="rnum">4.9 (2.1k)</span></div>
        <div class="pfoot">
          <div class="pprice">239 990 ₸</div>
          <button class="btn-add" onclick="add(this,'PS5 Pro')">В корзину</button>
        </div>
      </div>
    </div>

    <div class="pcard pg">
      <div class="pimg" style="background:linear-gradient(135deg,#f0fff8,#c8ffe8)">
        <span class="pbadge newb">NEW</span>
        <button class="pfav" onclick="fav(this)">🤍</button>
        <span style="filter:drop-shadow(0 4px 16px rgba(0,196,122,.5))">📷</span>
      </div>
      <div class="pinfo">
        <div class="pbrand">Sony</div>
        <div class="pname">Alpha 7CR Full-Frame 61MP</div>
        <div class="prating"><span class="stars">★★★★★</span><span class="rnum">4.9 (312)</span></div>
        <div class="pfoot">
          <div class="pprice"><span class="old">499 990 ₸</span>449 990 ₸</div>
          <button class="btn-add" onclick="add(this,'Sony Alpha 7CR')">В корзину</button>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- PROMO BANNERS -->
<div class="promos">
  <div class="promo pr1" onclick="showToast('🍎 Apple — скидки до 40%!')">
    <div class="ptag">⚡ Мегаскидка</div>
    <div class="ptitle">До −40%<br>на Apple</div>
    <div class="pdesc">Только до конца месяца!</div>
    <div class="pcta">Смотреть →</div>
  </div>
  <div class="promo pr2" onclick="showToast('🎧 Наушники — лучшие цены!')">
    <div class="ptag">🎵 Для звука</div>
    <div class="ptitle">Топ наушники<br>от 14 990 ₸</div>
    <div class="pdesc">Sony, JBL, Bose, Apple</div>
    <div class="pcta">В каталог →</div>
  </div>
  <div class="promo pr3" onclick="showToast('🎮 Игровые устройства!')">
    <div class="ptag">🎮 Геймерам</div>
    <div class="ptitle">Игровой<br>уголок 2025</div>
    <div class="pdesc">PS5, Xbox, мониторы</div>
    <div class="pcta">Подробнее →</div>
  </div>
</div>

<!-- FEATURES -->
<section>
  <div class="sec-head"><h2 class="sec-title">Почему выбирают нас</h2></div>
  <div class="feats">
    <div class="feat"><span class="feat-ico">🚀</span><div><div class="ftitle">Быстрая доставка</div><div class="fdesc">1–2 дня по Казахстану. Экспресс за 4 часа в Алматы.</div></div></div>
    <div class="feat"><span class="feat-ico">🛡️</span><div><div class="ftitle">Гарантия 2 года</div><div class="fdesc">Официальная гарантия на все товары. Сервисные центры.</div></div></div>
    <div class="feat"><span class="feat-ico">💳</span><div><div class="ftitle">Рассрочка 0%</div><div class="fdesc">До 24 месяцев без переплат. Одобрение за 5 минут.</div></div></div>
    <div class="feat"><span class="feat-ico">🔄</span><div><div class="ftitle">Возврат 30 дней</div><div class="fdesc">Вернём деньги без лишних вопросов.</div></div></div>
  </div>
</section>

<!-- NEWSLETTER -->
<div class="newsletter">
  <div>
    <div class="nl-title"><span>Скидка 10%</span> за подписку!</div>
    <div class="nl-desc">Получайте акции и новинки первыми на email</div>
  </div>
  <div class="nl-form">
    <input class="nl-input" type="email" placeholder="Ваш email" id="emailIn">
    <button class="nl-btn" onclick="subscribe()">Подписаться 🎁</button>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="fl">Neo⚡Tech</div>
  <div class="flinks">
    <a href="#">О нас</a><a href="#">Доставка</a>
    <a href="#">Гарантия</a><a href="#">Контакты</a><a href="#">Вакансии</a>
  </div>
  <div class="fcopy">© 2025 NeoTech. Все права защищены.</div>
</footer>

<div id="toast"></div>

<script>
let n=0;
function add(btn,name){
  n++;document.getElementById('cnt').textContent=n;
  btn.textContent='✓ Добавлено';btn.classList.add('added');
  showToast('🛒 '+name+' добавлен в корзину!');
  setTimeout(()=>{btn.textContent='В корзину';btn.classList.remove('added');},2200);
}
function fav(btn){
  const on=btn.textContent==='❤️';
  btn.textContent=on?'🤍':'❤️';
  showToast(on?'Убрано из избранного':'❤️ Добавлено в избранное');
}
function openCart(){showToast(n===0?'🛒 Корзина пуста — добавьте товары!':'🛒 В корзине: '+n+' товар(а)');}
function subscribe(){
  const v=document.getElementById('emailIn').value.trim();
  if(!v||!v.includes('@')){showToast('📧 Введите корректный email');return;}
  showToast('🎁 Готово! Скидка 10% отправлена на '+v);
  document.getElementById('emailIn').value='';
}
let tid;
function showToast(m){
  const t=document.getElementById('toast');
  t.textContent=m;t.classList.add('show');
  clearTimeout(tid);tid=setTimeout(()=>t.classList.remove('show'),3000);
}
const io=new IntersectionObserver(es=>{
  es.forEach(e=>{
    if(e.isIntersecting){
      e.target.style.transition='opacity .5s ease, transform .5s ease';
      e.target.style.opacity='1';e.target.style.transform='translateY(0)';
      io.unobserve(e.target);
    }
  });
},{threshold:.08});
document.querySelectorAll('.pcard,.cat,.feat,.promo,.bc').forEach((el,i)=>{
  el.style.opacity='0';el.style.transform='translateY(18px)';
  el.style.transitionDelay=(i%4)*55+'ms';
  io.observe(el);
});
</script>
</body>
</html>
