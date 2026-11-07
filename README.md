<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>БериИДелай — аренда строительного инструмента в Кургане</title>
<meta name="description" content="БериИДелай — аренда строительного инструмента в Кургане почасово и посуточно. Скидка 10% за сутки.">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; scrollbar-gutter: stable; }
  body {
    font-family: 'Segoe UI', Arial, sans-serif;
    color: #e8e8e8;
    line-height: 1.6;
    background: #0d0d0f;
    -webkit-tap-highlight-color: transparent;
    overflow-x: hidden;
    width: 100%;
    transition: background-color .4s ease, color .4s ease;
  }
  body.menu-open { overflow: hidden; }

  .container {
    max-width: 480px;
    margin: 0 auto;
    padding: 0 16px;
    width: 100%;
  }

  /* ===== ШАПКА ===== */
  header {
    background: rgba(17,17,20,0.96);
    backdrop-filter: blur(14px);
    -webkit-backdrop-filter: blur(14px);
    padding: 10px 0 12px;
    position: sticky;
    top: 0;
    z-index: 100;
    border-bottom: 1px solid rgba(196,30,58,0.35);
    transition: box-shadow .45s cubic-bezier(0.4, 0, 0.2, 1),
                border-color .45s cubic-bezier(0.4, 0, 0.2, 1),
                background-color .45s cubic-bezier(0.4, 0, 0.2, 1);
  }
  header.scrolled { box-shadow: 0 4px 24px rgba(196,30,58,0.28); }

  .header-top {
    display: grid;
    grid-template-columns: 44px 1fr 44px;
    align-items: center;
    gap: 10px;
  }
  .burger {
    background: rgba(196,30,58,0.12);
    border: 1px solid #c41e3a;
    border-radius: 8px;
    width: 44px;
    height: 44px;
    cursor: pointer;
    position: relative;
    justify-self: start;
    transition: background-color .3s cubic-bezier(0.4, 0, 0.2, 1),
                transform .3s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .burger:hover { background: rgba(196,30,58,0.28); box-shadow: 0 0 18px rgba(196,30,58,0.35); }
  .burger:active { transform: scale(0.94); }
  .burger span, .burger span::before, .burger span::after {
    content: '';
    position: absolute;
    left: 50%;
    width: 20px;
    height: 2px;
    background: #e63950;
    transform: translateX(-50%);
    transition: all .35s cubic-bezier(0.4, 0, 0.2, 1);
    border-radius: 2px;
  }
  .burger span { top: 50%; margin-top: -1px; }
  .burger span::before { top: -6px; left: 0; transform: none; }
  .burger span::after  { top: 6px;  left: 0; transform: none; }

  .logo {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    text-decoration: none;
    justify-self: center;
    transition: transform .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .logo:hover { transform: scale(1.03); }
  .logo:active { transform: scale(0.97); }
  .logo-mark {
    width: 46px;
    height: 46px;
    border-radius: 50%;
    background: linear-gradient(135deg, #c41e3a, #e63950);
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 0 22px rgba(196,30,58,0.5);
    transition: transform .4s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .4s cubic-bezier(0.4, 0, 0.2, 1);
    flex-shrink: 0;
  }
  .logo:hover .logo-mark { transform: scale(1.08) rotate(-4deg); box-shadow: 0 0 34px rgba(196,30,58,0.8); }
  .logo-mark svg { width: 26px; height: 26px; }
  .logo-text { text-align: left; line-height: 1.05; }
  .logo-title {
    font-size: 18px;
    font-weight: 800;
    letter-spacing: 0.5px;
    background: linear-gradient(135deg, #e63950, #ff6b7d);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    transition: opacity .3s ease;
  }
  .logo-sub { font-size: 8px; color: #888; letter-spacing: 2px; text-transform: uppercase; transition: color .3s ease; }

  .phone-icon-btn {
    width: 44px;
    height: 44px;
    border-radius: 8px;
    border: 1px solid #c41e3a;
    background: rgba(196,30,58,0.12);
    color: #e63950;
    font-size: 20px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    justify-self: end;
    transition: background-color .3s cubic-bezier(0.4, 0, 0.2, 1),
                color .3s cubic-bezier(0.4, 0, 0.2, 1),
                transform .3s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .phone-icon-btn:hover { background: rgba(196,30,58,0.3); box-shadow: 0 0 18px rgba(196,30,58,0.35); }
  .phone-icon-btn:active { background: #c41e3a; color: #fff; transform: scale(0.94); }

  /* ===== БОКОВОЕ МЕНЮ ===== */
  .overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.75);
    backdrop-filter: blur(3px);
    opacity: 0;
    visibility: hidden;
    transition: opacity .4s cubic-bezier(0.4, 0, 0.2, 1),
                visibility .4s cubic-bezier(0.4, 0, 0.2, 1);
    z-index: 300;
  }
  .overlay.open { opacity: 1; visibility: visible; }

  .side-menu {
    position: fixed;
    top: 0;
    left: 0;
    height: 100dvh;
    width: 300px;
    max-width: 82vw;
    background: linear-gradient(180deg, #16161a, #0f0f12);
    border-right: 1px solid #c41e3a;
    z-index: 400;
    transform: translateX(-100%);
    transition: transform .45s cubic-bezier(0.4, 0, 0.2, 1);
    display: flex;
    flex-direction: column;
    box-shadow: 8px 0 40px rgba(0,0,0,0.6);
  }
  .side-menu.open { transform: translateX(0); }

  .side-head {
    padding: 22px 22px 18px;
    border-bottom: 1px solid #2a2a2e;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .side-head .logo-title { font-size: 18px; }
  .side-close {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    background: rgba(196,30,58,0.15);
    border: 1px solid #c41e3a;
    color: #e63950;
    font-size: 18px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    transition: all .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .side-close:hover { background: #c41e3a; color: #fff; transform: rotate(90deg); }
  .side-close:active { transform: rotate(90deg) scale(0.92); }

  .side-nav { flex: 1; padding: 14px 0; overflow-y: auto; }
  .side-nav a {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 15px 24px;
    color: #ccc;
    text-decoration: none;
    font-size: 16px;
    font-weight: 600;
    border-left: 3px solid transparent;
    transition: all .3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .side-nav a:hover, .side-nav a:active {
    background: rgba(196,30,58,0.1);
    border-left-color: #c41e3a;
    color: #e63950;
    padding-left: 30px;
  }
  .side-nav a .ico { font-size: 20px; width: 24px; text-align: center; transition: transform .3s ease; }
  .side-nav a:hover .ico { transform: scale(1.15); }

  .side-foot {
    padding: 18px 22px 24px;
    border-top: 1px solid #2a2a2e;
  }
  .side-foot .phone-foot {
    color: #e63950;
    font-weight: 800;
    font-size: 18px;
    text-decoration: none;
    display: block;
    margin-bottom: 8px;
    transition: color .3s ease, transform .3s ease;
  }
  .side-foot .phone-foot:hover { color: #ff6b7d; transform: translateX(3px); }
  .side-foot p { font-size: 12px; color: #777; margin-bottom: 4px; transition: color .3s ease; }
  .side-foot p:hover { color: #aaa; }

  /* ===== ГЕРОЙ ===== */
  .hero {
    min-height: calc(100vh - 100px);
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    background:
      radial-gradient(ellipse at 20% 20%, rgba(196,30,58,0.12), transparent 55%),
      radial-gradient(ellipse at 80% 80%, rgba(230,57,80,0.1), transparent 55%),
      linear-gradient(135deg, #111114 0%, #1a1a1e 100%);
    padding: 50px 0;
    position: relative;
    transition: background .6s ease;
  }
  .hero .container { position: relative; z-index: 1; }
  .hero h1 {
    font-size: 28px;
    margin-bottom: 18px;
    line-height: 1.2;
    animation: fadeUp .9s cubic-bezier(0.4, 0, 0.2, 1) both;
  }
  .hero h1 span {
    background: linear-gradient(135deg, #e63950, #ff6b7d);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero p {
    font-size: 14px;
    color: #aaa;
    margin: 0 auto 28px;
    animation: fadeUp .9s cubic-bezier(0.4, 0, 0.2, 1) .15s both;
  }
  .hero-btns {
    display: flex;
    flex-direction: column;
    gap: 12px;
    animation: fadeUp .9s cubic-bezier(0.4, 0, 0.2, 1) .3s both;
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .btn {
    display: inline-block;
    background: linear-gradient(135deg, #c41e3a, #e63950);
    color: #fff;
    padding: 15px 22px;
    border-radius: 10px;
    text-decoration: none;
    font-weight: 700;
    font-size: 15px;
    border: none;
    cursor: pointer;
    font-family: inherit;
    text-align: center;
    width: 100%;
    box-shadow: 0 4px 22px rgba(196,30,58,0.4);
    transition: transform .3s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .35s cubic-bezier(0.4, 0, 0.2, 1),
                background .35s cubic-bezier(0.4, 0, 0.2, 1),
                letter-spacing .3s ease;
  }
  .btn:hover { transform: translateY(-3px); box-shadow: 0 10px 34px rgba(196,30,58,0.65); letter-spacing: 0.3px; }
  .btn:active { transform: translateY(-1px) scale(0.98); box-shadow: 0 6px 18px rgba(196,30,58,0.5); }
  .btn-outline {
    background: transparent;
    border: 2px solid #c41e3a;
    color: #e63950;
    box-shadow: none;
    transition: all .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .btn-outline:hover { background: #c41e3a; color: #fff; box-shadow: 0 10px 34px rgba(196,30,58,0.5); }
  .btn-outline:active { background: #a01830; }

  /* ===== СЕКЦИИ ===== */
  .features { padding: 50px 0; background: #111114; transition: background-color .5s ease; }
  .section-title {
    text-align: center;
    font-size: 24px;
    margin-bottom: 8px;
    color: #fff;
    transition: color .3s ease;
  }
  .section-title::after {
    content: '';
    display: block;
    width: 56px;
    height: 3px;
    background: linear-gradient(90deg, #c41e3a, #e63950);
    margin: 14px auto 0;
    border-radius: 3px;
    transition: width .4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .section-title:hover::after { width: 90px; }
  .section-sub {
    text-align: center;
    color: #888;
    margin-bottom: 32px;
    font-size: 13px;
    transition: color .3s ease;
  }

  .features-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .feature {
    background: linear-gradient(145deg, #1a1a1e, #131316);
    padding: 22px 12px;
    border-radius: 12px;
    border: 1px solid #2a2a2e;
    text-align: center;
    transition: border-color .4s cubic-bezier(0.4, 0, 0.2, 1),
                transform .4s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .4s cubic-bezier(0.4, 0, 0.2, 1),
                background .4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .feature:hover {
    border-color: #c41e3a;
    transform: translateY(-4px);
    box-shadow: 0 12px 28px rgba(196,30,58,0.2);
    background: linear-gradient(145deg, #1f1f24, #151519);
  }
  .feature:active { transform: scale(0.98); }
  .feature .icon {
    font-size: 30px;
    margin-bottom: 8px;
    display: block;
    transition: transform .4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .feature:hover .icon { transform: scale(1.15) rotate(-5deg); }
  .feature h3 { font-size: 14px; margin-bottom: 6px; color: #e63950; transition: color .3s ease; }
  .feature p { font-size: 12px; color: #999; transition: color .3s ease; }
  .feature:hover p { color: #bbb; }

  /* ===== КАТАЛОГ ===== */
  .catalog { padding: 50px 0; background: #0d0d0f; transition: background-color .5s ease; }

  .rate-toggle {
    display: flex;
    justify-content: center;
    margin: 0 auto 12px;
    gap: 0;
    background: #16161a;
    border: 1px solid #2a2a2e;
    border-radius: 44px;
    padding: 4px;
    width: 100%;
    transition: border-color .35s ease, box-shadow .35s ease;
  }
  .rate-toggle:hover { border-color: #c41e3a; box-shadow: 0 0 20px rgba(196,30,58,0.15); }
  .rate-toggle button {
    flex: 1;
    padding: 11px 0;
    border: none;
    background: transparent;
    color: #888;
    font-size: 14px;
    font-weight: 700;
    border-radius: 40px;
    cursor: pointer;
    font-family: inherit;
    transition: all .4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .rate-toggle button:hover:not(.active) { color: #e63950; }
  .rate-toggle button.active {
    background: linear-gradient(135deg, #c41e3a, #e63950);
    color: #fff;
    box-shadow: 0 4px 16px rgba(196,30,58,0.45);
  }

  .discount-note {
    text-align: center;
    font-size: 12px;
    color: #e63950;
    margin-bottom: 24px;
    font-weight: 600;
    transition: color .3s ease;
  }
  .discount-note span {
    background: rgba(196,30,58,0.15);
    border: 1px solid rgba(196,30,58,0.4);
    padding: 4px 14px;
    border-radius: 20px;
    display: inline-block;
    transition: all .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .discount-note span:hover {
    background: rgba(196,30,58,0.25);
    transform: scale(1.04);
    box-shadow: 0 0 16px rgba(196,30,58,0.3);
  }

  .filters {
    display: flex;
    flex-wrap: nowrap;
    gap: 8px;
    justify-content: flex-start;
    margin-bottom: 28px;
    overflow-x: auto;
    padding-bottom: 6px;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none;
  }
  .filters::-webkit-scrollbar { display: none; }
  .filter-btn {
    padding: 8px 16px;
    border: 1px solid #333;
    background: #16161a;
    border-radius: 30px;
    cursor: pointer;
    font-size: 12px;
    font-weight: 600;
    color: #aaa;
    white-space: nowrap;
    font-family: inherit;
    flex-shrink: 0;
    transition: all .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .filter-btn:hover { border-color: #c41e3a; color: #e63950; transform: translateY(-2px); }
  .filter-btn.active {
    background: linear-gradient(135deg, #c41e3a, #e63950);
    border-color: #c41e3a;
    color: #fff;
    box-shadow: 0 4px 14px rgba(196,30,58,0.4);
  }
  .filter-btn:active { transform: scale(0.96); }

  .cards {
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;
  }
  .card {
    background: linear-gradient(145deg, #1a1a1e, #121215);
    border-radius: 14px;
    overflow: hidden;
    border: 1px solid #2a2a2e;
    display: flex;
    flex-direction: column;
    cursor: pointer;
    transition: transform .4s cubic-bezier(0.4, 0, 0.2, 1),
                border-color .4s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .4s cubic-bezier(0.4, 0, 0.2, 1),
                background .4s cubic-bezier(0.4, 0, 0.2, 1);
    animation: cardIn .6s cubic-bezier(0.4, 0, 0.2, 1) both;
  }
  @keyframes cardIn {
    from { opacity: 0; transform: translateY(20px) scale(0.98); }
    to { opacity: 1; transform: translateY(0) scale(1); }
  }
  .card:hover {
    transform: translateY(-5px);
    border-color: #c41e3a;
    box-shadow: 0 14px 40px rgba(196,30,58,0.28);
    background: linear-gradient(145deg, #1f1f24, #141417);
  }
  .card:active { transform: translateY(-2px) scale(0.99); }
  .card-img {
    height: 200px;
    background: #1a1a1e;
    overflow: hidden;
    position: relative;
  }
  .card-img img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: brightness(0.9) contrast(1.05);
    transition: transform .8s cubic-bezier(0.4, 0, 0.2, 1),
                filter .5s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .card:hover .card-img img { transform: scale(1.09); filter: brightness(1.05) contrast(1.08); }
  .card-discount-badge {
    position: absolute;
    top: 12px;
    right: 12px;
    background: linear-gradient(135deg, #c41e3a, #e63950);
    color: #fff;
    font-size: 11px;
    font-weight: 800;
    padding: 5px 12px;
    border-radius: 20px;
    box-shadow: 0 4px 14px rgba(196,30,58,0.5);
    z-index: 2;
    transition: transform .3s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .card:hover .card-discount-badge { transform: scale(1.08) rotate(-3deg); box-shadow: 0 6px 20px rgba(196,30,58,0.7); }
  .card-body { padding: 16px; flex: 1; display: flex; flex-direction: column; }
  .card-tag {
    display: inline-block;
    font-size: 10px;
    background: rgba(196,30,58,0.15);
    color: #e63950;
    padding: 3px 10px;
    border-radius: 20px;
    margin-bottom: 8px;
    align-self: flex-start;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    font-weight: 700;
    border: 1px solid rgba(196,30,58,0.35);
    transition: all .3s ease;
  }
  .card:hover .card-tag { background: rgba(196,30,58,0.25); }
  .card h3 {
    font-size: 16px;
    margin-bottom: 6px;
    color: #fff;
    transition: color .3s ease;
  }
  .card:hover h3 { color: #ff8a99; }
  .card .desc {
    font-size: 13px;
    color: #888;
    margin-bottom: 14px;
    flex: 1;
    transition: color .3s ease;
  }
  .card:hover .desc { color: #a5a5a5; }
  .card-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-top: 1px solid #2a2a2e;
    padding-top: 12px;
    gap: 8px;
    transition: border-color .3s ease;
  }
  .card:hover .card-footer { border-color: rgba(196,30,58,0.35); }
  .price-box { line-height: 1.2; }
  .price {
    font-size: 20px;
    font-weight: 800;
    color: #e63950;
    transition: color .3s ease, transform .3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .card:hover .price { color: #ff6b7d; }
  .price small { font-size: 11px; font-weight: 400; color: #777; display: block; transition: color .3s ease; }
  .price-old {
    font-size: 12px;
    color: #666;
    text-decoration: line-through;
    display: block;
    animation: fadeIn .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(-3px); } to { opacity: 1; transform: translateY(0); } }
  .rent-btn {
    background: transparent;
    color: #e63950;
    border: 1px solid #c41e3a;
    padding: 10px 16px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 12px;
    font-weight: 700;
    white-space: nowrap;
    font-family: inherit;
    transition: all .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .rent-btn:hover {
    background: #c41e3a;
    color: #fff;
    transform: scale(1.05);
    box-shadow: 0 4px 16px rgba(196,30,58,0.5);
  }
  .rent-btn:active { transform: scale(0.97); }

  /* ===== МОДАЛЬНОЕ ОКНО ===== */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(6px);
    z-index: 500;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    opacity: 0;
    visibility: hidden;
    transition: opacity .4s cubic-bezier(0.4, 0, 0.2, 1),
                visibility .4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .modal-overlay.open { opacity: 1; visibility: visible; }
  .modal {
    background: #16161a;
    border: 1px solid #c41e3a;
    border-radius: 22px 22px 0 0;
    width: 100%;
    max-width: 480px;
    max-height: 92vh;
    overflow-y: auto;
    position: relative;
    transform: translateY(100%);
    transition: transform .5s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 -12px 60px rgba(196,30,58,0.35);
  }
  .modal-overlay.open .modal { transform: translateY(0); }
  .modal::-webkit-scrollbar { width: 4px; }
  .modal::-webkit-scrollbar-thumb { background: #c41e3a; border-radius: 4px; }

  .modal::before {
    content: '';
    position: absolute;
    top: 8px;
    left: 50%;
    transform: translateX(-50%);
    width: 44px;
    height: 4px;
    background: #444;
    border-radius: 4px;
    z-index: 4;
    transition: background .3s ease, width .3s ease;
  }
  .modal:hover::before { background: #c41e3a; width: 60px; }

  .modal-close {
    position: absolute;
    top: 18px;
    right: 14px;
    width: 38px;
    height: 38px;
    border-radius: 50%;
    background: rgba(196,30,58,0.25);
    border: 1px solid #c41e3a;
    color: #e63950;
    font-size: 18px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 3;
    backdrop-filter: blur(6px);
    transition: all .4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .modal-close:hover { background: #c41e3a; color: #fff; transform: rotate(90deg) scale(1.1); }
  .modal-close:active { transform: rotate(90deg) scale(0.95); }

  .modal-img {
    width: 100%;
    height: 210px;
    object-fit: cover;
    border-radius: 22px 22px 0 0;
    transition: transform .6s cubic-bezier(0.4, 0, 0.2, 1), filter .4s ease;
  }
  .modal-img:hover { filter: brightness(1.06); }
  .modal-body { padding: 20px; }
  .modal-tag {
    display: inline-block;
    font-size: 11px;
    background: rgba(196,30,58,0.15);
    color: #e63950;
    padding: 4px 12px;
    border-radius: 20px;
    margin-bottom: 10px;
    text-transform: uppercase;
    font-weight: 700;
    letter-spacing: 0.5px;
    border: 1px solid rgba(196,30,58,0.35);
    transition: all .3s ease;
  }
  .modal-tag:hover { background: rgba(196,30,58,0.25); transform: scale(1.03); }
  .modal-body h2 { font-size: 20px; color: #fff; margin-bottom: 12px; }
  .modal-desc { font-size: 14px; color: #bbb; margin-bottom: 20px; line-height: 1.7; }

  .modal-section { margin-bottom: 20px; }
  .modal-section h4 {
    font-size: 12px;
    color: #e63950;
    margin-bottom: 10px;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: 800;
    padding-bottom: 6px;
    border-bottom: 1px solid #2a2a2e;
    transition: color .3s ease, border-color .3s ease;
  }
  .modal-section:hover h4 { color: #ff6b7d; border-color: rgba(196,30,58,0.4); }
  .modal-section ul { list-style: none; }
  .modal-section ul li {
    font-size: 13px;
    color: #bbb;
    padding: 6px 0 6px 22px;
    position: relative;
    line-height: 1.5;
    transition: color .3s ease, padding-left .3s ease;
  }
  .modal-section ul li:hover { color: #fff; padding-left: 26px; }
  .modal-section ul li::before {
    content: '✓';
    position: absolute;
    left: 0;
    color: #e63950;
    font-weight: 800;
    transition: color .3s ease, transform .3s ease;
  }
  .modal-section ul li:hover::before { color: #ff6b7d; transform: scale(1.2); }

  .modal-specs table { width: 100%; border-collapse: collapse; }
  .modal-specs td {
    padding: 9px 0;
    font-size: 13px;
    border-bottom: 1px solid #2a2a2e;
    color: #ccc;
    transition: background .3s ease, color .3s ease, padding-left .3s ease;
  }
  .modal-specs tr { transition: background .3s ease; }
  .modal-specs tr:hover td { background: rgba(196,30,58,0.06); color: #fff; }
  .modal-specs tr:hover td:first-child { padding-left: 6px; }
  .modal-specs td:first-child { color: #888; width: 48%; transition: color .3s ease; }
  .modal-specs tr:hover td:first-child { color: #e63950; }
  .modal-specs td:last-child { text-align: right; color: #fff; font-weight: 600; }

  .modal-price-row {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    background: #111114;
    border: 1px solid #2a2a2e;
    border-radius: 12px;
    padding: 16px;
    margin-bottom: 12px;
    gap: 14px;
    transition: border-color .35s ease, box-shadow .35s ease;
  }
  .modal-price-row:hover { border-color: #c41e3a; box-shadow: 0 0 22px rgba(196,30,58,0.18); }
  .modal-price { font-size: 26px; font-weight: 800; color: #e63950; line-height: 1.2; transition: color .3s ease; }
  .modal-price small { font-size: 12px; font-weight: 400; color: #888; display: block; }
  .modal-price-old { font-size: 13px; color: #666; text-decoration: line-through; display: block; margin-top: 2px; }
  .modal-body .btn { width: 100%; text-align: center; }

  /* ===== ФОРМА ===== */
  .order {
    background: linear-gradient(180deg, #111114, #0d0d0f);
    padding: 50px 0;
    border-top: 1px solid #2a2a2e;
    border-bottom: 1px solid #2a2a2e;
    transition: background .5s ease;
  }
  .form-row { margin-bottom: 14px; }
  .form-row label {
    display: block;
    font-size: 13px;
    margin-bottom: 6px;
    color: #bbb;
    font-weight: 600;
    transition: color .3s ease;
  }
  .form-row:focus-within label { color: #e63950; }
  .form-row input, .form-row select, .form-row textarea {
    width: 100%;
    padding: 14px 15px;
    border-radius: 10px;
    border: 1px solid #333;
    background: #16161a;
    color: #fff;
    font-size: 16px;
    font-family: inherit;
    outline: none;
    transition: border-color .35s cubic-bezier(0.4, 0, 0.2, 1),
                box-shadow .35s cubic-bezier(0.4, 0, 0.2, 1),
                background .35s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .form-row input:hover, .form-row select:hover, .form-row textarea:hover {
    border-color: #555;
    background: #181820;
  }
  .form-row input:focus, .form-row select:focus, .form-row textarea:focus {
    border-color: #c41e3a;
    box-shadow: 0 0 0 3px rgba(196,30,58,0.18);
    background: #1a1a20;
  }
  .form-row input::placeholder, .form-row textarea::placeholder { color: #555; transition: color .3s ease; }
  .form-row input:focus::placeholder, .form-row textarea:focus::placeholder { color: #888; }
  .form-row textarea { resize: vertical; min-height: 80px; }
  .order .btn { margin-top: 8px; }

  /* ===== ПОДВАЛ ===== */
  footer {
    background: #0d0d0f;
    color: #888;
    padding: 40px 0 20px;
    font-size: 14px;
    border-top: 1px solid #1a1a1e;
    transition: background .5s ease;
  }
  .footer-grid { display: grid; grid-template-columns: 1fr; gap: 24px; margin-bottom: 24px; }
  .footer-grid h4 { color: #e63950; margin-bottom: 10px; font-size: 15px; transition: color .3s ease; }
  .footer-grid h4:hover { color: #ff6b7d; }
  .footer-grid p, .footer-grid a {
    color: #888;
    text-decoration: none;
    display: block;
    margin-bottom: 6px;
    font-size: 13px;
    transition: color .3s ease, transform .3s ease;
  }
  .footer-grid a:hover { color: #e63950; transform: translateX(3px); }
  .footer-grid .phone-foot { color: #e63950; font-weight: 700; font-size: 16px; }
  .copy {
    text-align: center;
    border-top: 1px solid #1a1a1e;
    padding-top: 18px;
    font-size: 12px;
    color: #555;
    transition: color .3s ease;
  }
  .copy:hover { color: #888; }

  /* ===== УВЕДОМЛЕНИЕ ===== */
  .toast {
    position: fixed;
    bottom: 16px;
    right: 16px;
    left: 16px;
    max-width: 448px;
    margin-left: auto;
    background: linear-gradient(135deg, #c41e3a, #e63950);
    color: #fff;
    padding: 15px 20px;
    border-radius: 12px;
    box-shadow: 0 10px 34px rgba(196,30,58,0.5);
    transform: translateY(180%) scale(0.95);
    opacity: 0;
    transition: transform .5s cubic-bezier(0.4, 0, 0.2, 1),
                opacity .4s cubic-bezier(0.4, 0, 0.2, 1);
    z-index: 600;
    font-weight: 700;
    font-size: 14px;
  }
  .toast.show { transform: translateY(0) scale(1); opacity: 1; }

  /* ===== ПЛАВНОЕ ПОЯВЛЕНИЕ ===== */
  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity .8s cubic-bezier(0.4, 0, 0.2, 1),
                transform .8s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      transition-duration: 0.01ms !important;
      animation-duration: 0.01ms !important;
    }
    html { scroll-behavior: auto; }
  }
</style>
</head>
<body>

<header id="header">
  <div class="container">
    <div class="header-top">
      <button class="burger" id="burger" aria-label="Открыть меню"><span></span></button>
      <a href="#" class="logo">
        <div class="logo-mark">
          <svg viewBox="0 0 32 32" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M6 26 L13 19" stroke-width="2.6"/>
            <path d="M11 16 L16 21" stroke-width="2.2"/>
            <rect x="12.5" y="10" width="9" height="6" rx="1.2" transform="rotate(45 17 13)" fill="#fff" stroke="none"/>
            <path d="M26 6 L20 12" stroke-width="2.4"/>
            <circle cx="25.5" cy="6.5" r="2.4" stroke-width="1.8" fill="none"/>
            <path d="M24.2 5.2 L26.8 7.8" stroke-width="1.4"/>
            <path d="M18 8 L23 3" stroke-width="2.6"/>
            <rect x="20.5" y="1.5" width="6" height="3.2" rx="0.8" transform="rotate(45 23.5 3.1)" fill="#fff" stroke="none"/>
          </svg>
        </div>
        <div class="logo-text">
          <div class="logo-title">БериИДелай</div>
          <div class="logo-sub">г. Курган</div>
        </div>
      </a>
      <a href="tel:+79956749750" class="phone-icon-btn" aria-label="Позвонить">📞</a>
    </div>
  </div>
</header>

<div class="overlay" id="overlay"></div>
<aside class="side-menu" id="sideMenu">
  <div class="side-head">
    <div class="logo-text">
      <div class="logo-title">БериИДелай</div>
      <div class="logo-sub" style="text-align:left;">г. Курган</div>
    </div>
    <button class="side-close" id="sideClose" aria-label="Закрыть">✕</button>
  </div>
  <nav class="side-nav">
    <a href="#support"><span class="ico">🛟</span> Поддержка</a>
    <a href="#catalog"><span class="ico">🛠️</span> Каталог</a>
    <a href="#order"><span class="ico">📝</span> Оставить заявку</a>
    <a href="tel:+79956749750"><span class="ico">📞</span> Позвонить</a>
  </nav>
  <div class="side-foot">
    <a href="tel:+79956749750" class="phone-foot">+7 (995) 674-97-50</a>
    <p>Ежедневно 8:00 – 20:00</p>
    <p>г. Курган, ул. Куйбышева, 25</p>
  </div>
</aside>

<section class="hero">
  <div class="container">
    <h1>Аренда инструмента <span>в Кургане</span></h1>
    <p>БериИДелай — берите инструмент на час или на сутки. За сутки — скидка 10%. Доставка за 2 часа.</p>
    <div class="hero-btns">
      <a href="#catalog" class="btn">Смотреть каталог</a>
      <a href="#order" class="btn btn-outline">Оставить заявку</a>
    </div>
  </div>
</section>

<section class="features" id="support">
  <div class="container">
    <h2 class="section-title reveal">Поддержка</h2>
    <p class="section-sub reveal">Более 500 единиц инструмента в наличии</p>
    <div class="features-grid">
      <div class="feature reveal">
        <span class="icon">⏱️</span>
        <h3>По часам</h3>
        <p>Платите только за время работы.</p>
      </div>
      <div class="feature reveal">
        <span class="icon">🎁</span>
        <h3>−10% за сутки</h3>
        <p>Скидка автоматически.</p>
      </div>
      <div class="feature reveal">
        <span class="icon">🚚</span>
        <h3>Доставка 2 ч</h3>
        <p>По всему Кургану.</p>
      </div>
      <div class="feature reveal">
        <span class="icon">📞</span>
        <h3>24/7</h3>
        <p>Всегда на связи.</p>
      </div>
    </div>
  </div>
</section>

<section class="catalog" id="catalog">
  <div class="container">
    <h2 class="section-title reveal">Каталог</h2>
    <p class="section-sub reveal">Нажмите на карточку — узнаете подробности</p>

    <div class="rate-toggle reveal">
      <button class="active" data-rate="hour">За час</button>
      <button data-rate="day">За сутки</button>
    </div>
    <p class="discount-note reveal"><span>🎁 −10% за сутки</span></p>

    <div class="filters reveal">
      <button class="filter-btn active" data-filter="all">Все</button>
      <button class="filter-btn" data-filter="electric">Электро</button>
      <button class="filter-btn" data-filter="power">Силовая</button>
      <button class="filter-btn" data-filter="concrete">Бетон</button>
      <button class="filter-btn" data-filter="weld">Сварка</button>
      <button class="filter-btn" data-filter="heat">Обогрев</button>
      <button class="filter-btn" data-filter="other">Прочее</button>
    </div>

    <div class="cards" id="cards">

      <!-- 1. Перфоратор -->
      <div class="card" data-category="electric" data-tool="Перфоратор Bosch GBH 2-26" data-hour="200" data-day="1399" data-img="https://images.unsplash.com/photo-1504148455328-c376907d081c?w=600&q=80" data-tag="Электроинструмент" data-desc="Универсальный перфоратор для профессиональных и бытовых задач: сверление бетона, кирпича, камня, а также режим долбления. Отлично подходит для монтажа анкеров, дюбелей, штробления." data-specs='{"Мощность":"800 Вт","Сила удара":"3,0 Дж","Патрон":"SDS-Plus","Макс. диаметр бетон":"26 мм","Макс. диаметр сталь":"13 мм","Макс. диаметр дерево":"30 мм","Частота ударов":"4000 уд/мин","Напряжение":"220 В","Вес":"2,7 кг"}' data-kit='["Перфоратор Bosch GBH 2-26","Бур SDS-Plus 8×150 мм","Бур SDS-Plus 10×150 мм","Зубило SDS-Plus","Боковая рукоять","Ограничитель глубины","Фирменный кейс Bosch"]' data-terms='["Залог 5 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 300 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Испытательный срок 10 минут при получении","Замена буров — по факту износа"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1504148455328-c376907d081c?w=600&q=80" alt="Перфоратор Bosch" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>Перфоратор Bosch GBH 2-26</h3>
          <p class="desc">Мощность 800 Вт. Для бетона, кирпича и камня. В комплекте буры.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="200" data-day="1259">200 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Перфоратор Bosch GBH 2-26">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 2. Циркулярная пила -->
      <div class="card" data-category="electric" data-tool="Циркулярная пила Makita" data-hour="180" data-day="1299" data-img="https://images.unsplash.com/photo-1572981779307-38b8cabb2407?w=600&q=80" data-tag="Электроинструмент" data-desc="Циркулярная пила для точного и быстрого продольного и поперечного раскроя дерева, ДСП, МДФ, фанеры. Плавная регулировка глубины пропила и угла наклона до 45°." data-specs='{"Мощность":"1600 Вт","Диск":"190 мм","Посадочный диаметр":"30 мм","Глубина пропила 90°":"65 мм","Глубина пропила 45°":"44 мм","Обороты":"5000 об/мин","Угол наклона":"0–45°","Напряжение":"220 В","Вес":"3,9 кг"}' data-kit='["Пила циркулярная Makita","Диск пильный 190×30 мм, 24 зуба","Параллельный упор","Ключ для смены диска","Патрубок для пылесоса","Инструкция","Кейс для переноски"]' data-terms='["Залог 5 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 300 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Диск в комплекте, замена при поломке — бесплатно","Работа только по дереву и мягким материалам"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1572981779307-38b8cabb2407?w=600&q=80" alt="Циркулярная пила" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>Циркулярная пила Makita</h3>
          <p class="desc">Диск 190 мм, плавная регулировка глубины пропила. Для дерева.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="180" data-day="1169">180 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Циркулярная пила Makita">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 3. УШМ -->
      <div class="card" data-category="electric" data-tool="УШМ DeWalt 125" data-hour="120" data-day="899" data-img="https://images.unsplash.com/photo-1621478264020-7c1c6f8b0f3c?w=600&q=80" data-tag="Электроинструмент" data-desc="Углошлифовальная машина для резки и шлифовки металла, камня, бетона. Используется при монтаже, сварке, отделке. В комплекте защитный кожух и боковая рукоять." data-specs='{"Мощность":"1400 Вт","Диск":"125 мм","Посадочный диаметр":"22,2 мм","Обороты":"2800–10000 об/мин","Резьба шпинделя":"M14","Защита от случайного пуска":"Есть","Напряжение":"220 В","Вес":"2,6 кг"}' data-kit='["УШМ DeWalt 125 мм","Отрезной диск по металлу","Защитный кожух","Боковая рукоять","Ключ для смены диска","Инструкция","Кейс"]' data-terms='["Залог 5 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 300 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Работа только с защитным кожухом","Не использовать диски больше 125 мм"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1621478264020-7c1c6f8b0f3c?w=600&q=80" alt="УШМ болгарка" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>УШМ (болгарка) DeWalt 125</h3>
          <p class="desc">Мощность 1400 Вт, диаметр диска 125 мм. Резка металла и камня.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="120" data-day="809">120 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="УШМ DeWalt 125">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 4. Шуруповёрт -->
      <div class="card" data-category="electric" data-tool="Шуруповёрт Makita DF333D" data-hour="100" data-day="749" data-img="https://images.unsplash.com/photo-1581141849530-1c5c6c4b8b43?w=600&q=80" data-tag="Электроинструмент" data-desc="Аккумуляторный шуруповёрт для сборки мебели, монтажа гипсокартона, работы с деревом и металлом. Два аккумулятора 12V в комплекте, быстрая зарядка за 30 минут." data-specs='{"Напряжение":"12 В","Крутящий момент":"30 Н·м","Патрон":"1–10 мм","Скорость":"0–450 / 0–1700 об/мин","Аккумулятор":"2×2.0 Ач Li-Ion","Тип аккумулятора":"Литий-ионный","Вес":"1,0 кг"}' data-kit='["Шуруповёрт Makita DF333D","2 аккумулятора 12V 2.0 Ач","Зарядное устройство","Битодержатель","Набор бит (10 шт)","Двухсторонняя бита","Кейс для переноски"]' data-terms='["Залог 5 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 300 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Аккумуляторы заряжены на момент выдачи","При полном разряде — замена бесплатно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1581141849530-1c5c6c4b8b43?w=600&q=80" alt="Шуруповёрт" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>Шуруповёрт Makita DF333D</h3>
          <p class="desc">Аккумуляторный, 12 В, 2 АКБ в комплекте. Для сборки и монтажа.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="100" data-day="674">100 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Шуруповёрт Makita DF333D">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 5. Штроборез -->
      <div class="card" data-category="electric" data-tool="Штроборез Makita SG150" data-hour="250" data-day="1799" data-img="https://images.unsplash.com/photo-1572981779307-38b8cabb2407?w=600&q=80" data-tag="Электроинструмент" data-desc="Штроборез для быстрой и аккуратной резки штроб в бетоне, кирпиче и газобетоне под электропроводку и трубы. Два алмазных диска, глубина до 35 мм." data-specs='{"Мощность":"1400 Вт","Диски":"2×150 мм","Глубина штробы":"до 35 мм","Ширина штробы":"до 40 мм","Посадочный диаметр":"22,2 мм","Обороты":"6600 об/мин","Напряжение":"220 В","Вес":"5,5 кг"}' data-kit='["Штроборез Makita SG150","2 алмазных диска 150 мм","Защитный кожух","Боковая рукоять","Патрубок для пылесоса","Комплект ключей","Инструкция"]' data-terms='["Залог 8 000 ₽ (возврат после сдачи)","Минимальный срок — 2 часа","Доставка по Кургану — 500 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Работа только с защитным кожухом","Рекомендуется использовать пылесос"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1572981779307-38b8cabb2407?w=600&q=80" alt="Штроборез" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>Штроборез Makita SG150</h3>
          <p class="desc">Штробы до 40 мм в бетоне и кирпиче. Два алмазных диска.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="250" data-day="1619">250 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Штроборез Makita SG150">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 6. Штроборез с пылесосом (НОВЫЙ) -->
      <div class="card" data-category="electric" data-tool="Штроборез с пылесосом Bosch GNF 35" data-hour="350" data-day="2399" data-img="https://images.unsplash.com/photo-1581092918056-0c4c3acd3789?w=600&q=80" data-tag="Электроинструмент" data-desc="Профессиональный штроборез Bosch GNF 35 CA с встроенным пылесосом. Режет штробы в бетоне, кирпиче и газобетоне без пыли. Глубина до 35 мм, два алмазных диска. Идеален для работ в жилых помещениях." data-specs='{"Мощность":"1400 Вт","Диски":"2×150 мм","Глубина штробы":"до 35 мм","Ширина штробы":"до 40 мм","Пылесос":"Встроенный, HEPA-фильтр","Контейнер для пыли":"2 л","Напряжение":"220 В","Вес":"6,8 кг"}' data-kit='["Штроборез Bosch GNF 35 CA","Встроенный пылесос","2 алмазных диска 150 мм","HEPA-фильтр","Защитный кожух","Боковая рукоять","Комплект ключей","Инструкция"]' data-terms='["Залог 10 000 ₽ (возврат после сдачи)","Минимальный срок — 2 часа","Доставка по Кургану — 500 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Работа без пыли — встроенный пылесос","Замена фильтра — бесплатно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1581092918056-0c4c3acd3789?w=600&q=80" alt="Штроборез с пылесосом" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>Штроборез с пылесосом Bosch GNF 35</h3>
          <p class="desc">Штробы без пыли. Встроенный HEPA-пылесос, глубина до 35 мм.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="350" data-day="2159">350 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Штроборез с пылесосом Bosch GNF 35">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 7. Краскопульт -->
      <div class="card" data-category="electric" data-tool="Краскопульт электрический Wagner" data-hour="150" data-day="1199" data-img="https://images.unsplash.com/photo-1562259949-e8e7689d7828?w=600&q=80" data-tag="Электроинструмент" data-desc="Электрический краскопульт для быстрой покраски стен, потолков, заборов, мебели. Распыляет краску, лак, грунтовку, антисептик. Бак 800 мл, регулировка факела." data-specs='{"Мощность":"600 Вт","Бак":"800 мл","Производительность":"600 мл/мин","Факел":"до 300 мм","Вязкость краски":"до 100 DIN","Напряжение":"220 В","Вес":"1,8 кг"}' data-kit='["Краскопульт Wagner","Бак 800 мл","Сопло 1,5 мм","Сопло 2,5 мм","Иглы для чистки","Воронка фильтр","Инструкция"]' data-terms='["Залог 5 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 300 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Промывка после работы — обязательно","Краска разводится до нужной вязкости"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1562259949-e8e7689d7828?w=600&q=80" alt="Краскопульт" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Электроинструмент</span>
          <h3>Краскопульт Wagner</h3>
          <p class="desc">Покраска стен, потолков, заборов. Бак 800 мл, факел до 300 мм.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="150" data-day="1079">150 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Краскопульт Wagner">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 8. Тепловая пушка (НОВАЯ) -->
      <div class="card" data-category="heat" data-tool="Тепловая пушка 3 кВт" data-hour="150" data-day="999" data-img="https://images.unsplash.com/photo-1581094271901-8022df4466f9?w=600&q=80" data-tag="Обогрев" data-desc="Электрическая тепловая пушка для обогрева стройплощадок, гаражей, складов, дач. Быстрый нагрев, три режима мощности, термостат. Работает от сети 220 В." data-specs='{"Мощность":"3 кВт","Режимы":"1,5 / 2 / 3 кВт","Напряжение":"220 В","Площадь обогрева":"до 35 м²","Расход воздуха":"250 м³/ч","Термостат":"Есть","Защита":"От перегрева","Вес":"2,8 кг"}' data-kit='["Тепловая пушка 3 кВт","Термостат","Рукоять для переноски","Инструкция по эксплуатации","Паспорт изделия","Гарантийный талон"]' data-terms='["Залог 5 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 300 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Только для сухих помещений","Не накрывать во время работы"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1581094271901-8022df4466f9?w=600&q=80" alt="Тепловая пушка" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Обогрев</span>
          <h3>Тепловая пушка 3 кВт</h3>
          <p class="desc">Обогрев до 35 м². Три режима, термостат, защита от перегрева.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="150" data-day="899">150 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Тепловая пушка 3 кВт">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 9. Бензогенератор -->
      <div class="card" data-category="power" data-tool="Бензогенератор 5 кВт" data-hour="400" data-day="2499" data-img="https://images.unsplash.com/photo-1618090584176-7132b9911fd0?w=600&q=80" data-tag="Силовая техника" data-desc="Бензиновый генератор для автономного электроснабжения строительного объекта, дачи, мероприятий. Электростартер, защита от перегрузок, стабильное напряжение 220 В." data-specs='{"Мощность":"5 кВт","Напряжение":"220 В","Бак":"22 л","Время работы":"до 9 часов","Запуск":"Электростартер","Расход топлива":"2,5 л/ч","Уровень шума":"72 дБ","Розетки":"2×16 А, 1×32 А","Вес":"80 кг"}' data-kit='["Бензогенератор 5 кВт","Аккумулятор для электростартера","Комплект ключей","Воронка для топлива","Инструкция по эксплуатации","Паспорт изделия"]' data-terms='["Залог 10 000 ₽ (возврат после сдачи)","Минимальный срок — 2 часа","Доставка по Кургану — 500 ₽, бесплатно от 5 000 ₽","Скидка 10% при аренде на сутки","Топливо за счёт арендатора (АИ-92)","Запуск и инструктаж при выдаче — бесплатно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1618090584176-7132b9911fd0?w=600&q=80" alt="Бензогенератор" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Силовая техника</span>
          <h3>Бензогенератор 5 кВт</h3>
          <p class="desc">Автономное электроснабжение на объекте. Расход топлива 2,5 л/ч.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="400" data-day="2249">400 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Бензогенератор 5 кВт">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 10. Отбойный молоток -->
      <div class="card" data-category="power" data-tool="Отбойный молоток Bosch GSH 11 E" data-hour="300" data-day="1999" data-img="https://images.unsplash.com/photo-1581141849291-1125c7b692b5?w=600&q=80" data-tag="Силовая техника" data-desc="Электрический отбойный молоток для демонтажа бетонных конструкций, кирпичной кладки, снятия плитки и асфальта. Высокая энергия удара, виброзащита." data-specs='{"Мощность":"1500 Вт","Сила удара":"16,8 Дж","Патрон":"SDS-Max","Частота ударов":"1300–2600 уд/мин","Напряжение":"220 В","Виброзащита":"Есть","Вес":"10,1 кг"}' data-kit='["Отбойный молоток Bosch GSH 11 E","Пика SDS-Max","Зубило SDS-Max","Боковая рукоять","Защитные очки","Перчатки","Инструкция","Кейс"]' data-terms='["Залог 8 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 500 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Работа только в защитных очках","Вес 10 кг — работайте вдвоём при переноске"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1581141849291-1125c7b692b5?w=600&q=80" alt="Отбойный молоток" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Силовая техника</span>
          <h3>Отбойный молоток Bosch GSH 11 E</h3>
          <p class="desc">Электрический, 1500 Вт. Для демонтажных работ и сноса.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="300" data-day="1799">300 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Отбойный молоток Bosch GSH 11 E">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 11. Бетономешалка 160 л -->
      <div class="card" data-category="concrete" data-tool="Бетономешалка 160 л" data-hour="250" data-day="1599" data-img="https://images.unsplash.com/photo-1581094794329-c8112a89af12?w=600&q=80" data-tag="Бетонные работы" data-desc="Бетономешалка гравитационного типа для приготовления бетона, раствора, штукатурки. Барабан 160 л, чугунный венец, электрический двигатель 650 Вт. Идеальна для фундаментов, стяжек, кладки." data-specs='{"Объём барабана":"160 л","Объём готовой смеси":"120 л","Мощность":"650 Вт","Напряжение":"220 В","Скорость вращения":"28 об/мин","Венец":"Чугунный","Вес":"58 кг"}' data-kit='["Бетономешалка 160 л","Комплект колёс","Лопасть для замеса","Инструкция по эксплуатации","Паспорт изделия","Комплект ключей"]' data-terms='["Залог 8 000 ₽ (возврат после сдачи)","Минимальный срок — 2 часа","Доставка по Кургану — 500 ₽, бесплатно от 5 000 ₽","Скидка 10% при аренде на сутки","Работа только на ровной поверхности","Промывка барабана после работы — обязательно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1581094794329-c8112a89af12?w=600&q=80" alt="Бетономешалка 160 л" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Бетонные работы</span>
          <h3>Бетономешалка 160 л</h3>
          <p class="desc">Гравитационная, 160 л, 650 Вт. Для бетона, раствора, штукатурки.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="250" data-day="1439">250 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Бетономешалка 160 л">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 12. Бетономешалка 250 л (НОВАЯ) -->
      <div class="card" data-category="concrete" data-tool="Бетономешалка 250 л" data-hour="350" data-day="2199" data-img="https://images.unsplash.com/photo-1590496793907-4d66e9f4b8b7?w=600&q=80" data-tag="Бетонные работы" data-desc="Профессиональная бетономешалка 250 л для больших объёмов: фундаменты, стяжки, кладка, отмостки. Усиленный чугунный венец, двигатель 900 Вт. Готовая смесь до 180 л за замес." data-specs='{"Объём барабана":"250 л","Объём готовой смеси":"180 л","Мощность":"900 Вт","Напряжение":"220 В","Скорость вращения":"28 об/мин","Венец":"Чугунный усиленный","Вес":"75 кг"}' data-kit='["Бетономешалка 250 л","Комплект колёс","Лопасть для замеса","Инструкция по эксплуатации","Паспорт изделия","Комплект ключей"]' data-terms='["Залог 10 000 ₽ (возврат после сдачи)","Минимальный срок — 2 часа","Доставка по Кургану — 800 ₽, бесплатно от 5 000 ₽","Скидка 10% при аренде на сутки","Работа только на ровной поверхности","Промывка барабана после работы — обязательно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1590496793907-4d66e9f4b8b7?w=600&q=80" alt="Бетономешалка 250 л" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Бетонные работы</span>
          <h3>Бетономешалка 250 л</h3>
          <p class="desc">Профессиональная, 250 л, 900 Вт. Готовая смесь до 180 л за замес.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="350" data-day="1979">350 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Бетономешалка 250 л">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 13. Сварочный инвертор -->
      <div class="card" data-category="weld" data-tool="Сварочный инвертор Ресанта САИ 220" data-hour="250" data-day="1599" data-img="https://images.unsplash.com/photo-1504328345606-18bbc8c9d7d1?w=600&q=80" data-tag="Сварка" data-desc="Сварочный инвертор для ручной дуговой сварки (MMA). Подходит для металла толщиной до 8 мм. В комплекте сварочный кабель, держатель, зажим массы и маска-хамелеон." data-specs='{"Сварочный ток":"10–220 А","Напряжение":"220 В","Диаметр электрода":"1,6–5,0 мм","Толщина металла":"до 8 мм","ПВ на 100%":"80%","Напряжение холостого хода":"80 В","Вес":"5,5 кг"}' data-kit='["Сварочный инвертор Ресанта САИ 220","Сварочный кабель 3 м с держателем","Кабель массы 2 м с зажимом","Маска-хамелеон","Щётка для зачистки швов","Набор электродов (10 шт)","Инструкция"]' data-terms='["Залог 8 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 500 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Работа только в маске и перчатках","Проверка аппарата при выдаче — 10 минут"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1504328345606-18bbc8c9d7d1?w=600&q=80" alt="Сварочный инвертор" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Сварка</span>
          <h3>Сварочный инвертор Ресанта САИ 220</h3>
          <p class="desc">Ручная дуговая сварка, 220 А. Металл до 8 мм. Маска в комплекте.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="250" data-day="1439">250 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Сварочный инвертор Ресанта САИ 220">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 14. Строительные леса -->
      <div class="card" data-category="other" data-tool="Строительные леса" data-hour="300" data-day="1999" data-img="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=600&q=80" data-tag="Прочее" data-desc="Комплект строительных лесов 2×6 м с настилом и лестницей. Оцинкованная сталь, устойчивые, собираются без инструментов. Для фасадных и отделочных работ." data-specs='{"Размер":"2×6 м","Нагрузка":"200 кг/м²","Материал":"Сталь оцинк.","Высота":"до 20 м","Диаметр трубы":"42 мм","Толщина стали":"2 мм","Вес комплекта":"85 кг"}' data-kit='["2 рамы с лестницей","4 диагональные связи","2 продольные связи","Настил деревянный 2×1 м","4 домкрата регулируемых","Колёса для перемещения","Комплект крепежа"]' data-terms='["Залог 10 000 ₽ (возврат после сдачи)","Минимальный срок — 1 сутки","Доставка по Кургану — 800 ₽, бесплатно от 5 000 ₽","Скидка 10% при аренде на сутки","Сборка по инструкции — бесплатно","Запрещено превышать нагрузку 200 кг/м²"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=600&q=80" alt="Строительные леса" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Прочее</span>
          <h3>Строительные леса</h3>
          <p class="desc">Комплект 2×6 м с настилом. Оцинкованная сталь, устойчивые.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="300" data-day="1799">300 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Строительные леса">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 15. Виброплита -->
      <div class="card" data-category="other" data-tool="Виброплита бензиновая" data-hour="350" data-day="2199" data-img="https://images.unsplash.com/photo-1517089596392-fb9a9033e05b?w=600&q=80" data-tag="Прочее" data-desc="Бензиновая виброплита для уплотнения грунта, песка, щебня и асфальта при благоустройстве, укладке тротуарной плитки и дорожных работах." data-specs='{"Вес":"80 кг","Двигатель":"5,5 л.с.","Глубина уплотнения":"30 см","Площадь":"до 500 м²/смена","Плита":"50×36 см","Частота вибрации":"5600 уд/мин","Расход топлива":"1,2 л/ч"}' data-kit='["Виброплита бензиновая","Комплект ключей","Воронка для топлива","Инструкция по эксплуатации","Паспорт изделия","Защитные перчатки"]' data-terms='["Залог 8 000 ₽ (возврат после сдачи)","Минимальный срок — 2 часа","Доставка по Кургану — 500 ₽, бесплатно от 5 000 ₽","Скидка 10% при аренде на сутки","Топливо за счёт арендатора (АИ-92)","Запуск и инструктаж при выдаче — бесплатно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1517089596392-fb9a9033e05b?w=600&q=80" alt="Виброплита" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Прочее</span>
          <h3>Виброплита бензиновая</h3>
          <p class="desc">Уплотнение грунта и асфальта. Вес 80 кг, двигатель 5,5 л.с.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="350" data-day="1979">350 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Виброплита бензиновая">Арендовать</button>
          </div>
        </div>
      </div>

      <!-- 16. Мотобур -->
      <div class="card" data-category="other" data-tool="Мотобур бензиновый" data-hour="300" data-day="1899" data-img="https://images.unsplash.com/photo-1503387762-592deb58ef4e?w=600&q=80" data-tag="Прочее" data-desc="Бензиновый мотобур для установки столбов, свай, ограждений, посадки деревьев. Диаметр бура до 200 мм, глубина бурения до 1,5 м. В комплекте бур 150 мм." data-specs='{"Двигатель":"2-тактный, 52 см³","Мощность":"1,9 л.с.","Диаметр бура":"100–200 мм","Глубина бурения":"до 1,5 м","Топливо":"АИ-92 + масло 1:25","Объём бака":"1,2 л","Вес":"9,5 кг"}' data-kit='["Мотобур бензиновый","Бур 150 мм","Удлинитель бура 50 см","Комплект ключей","Воронка для топлива","Защитные очки","Инструкция"]' data-terms='["Залог 8 000 ₽ (возврат после сдачи)","Минимальный срок — 1 час","Доставка по Кургану — 500 ₽, бесплатно от 3 000 ₽","Скидка 10% при аренде на сутки","Топливо за счёт арендатора (АИ-92 + масло)","Запуск и инструктаж при выдаче — бесплатно"]'>
        <div class="card-img">
          <span class="card-discount-badge">−10%</span>
          <img src="https://images.unsplash.com/photo-1503387762-592deb58ef4e?w=600&q=80" alt="Мотобур" loading="lazy">
        </div>
        <div class="card-body">
          <span class="card-tag">Прочее</span>
          <h3>Мотобур бензиновый</h3>
          <p class="desc">Для столбов и свай. Бур до 200 мм, глубина до 1,5 м.</p>
          <div class="card-footer">
            <div class="price-box">
              <div class="price" data-hour="300" data-day="1709">300 ₽<small>/ час</small></div>
            </div>
            <button class="rent-btn" data-tool="Мотобур бензиновый">Арендовать</button>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="modal-overlay" id="modalOverlay">
  <div class="modal">
    <button class="modal-close" id="modalClose">✕</button>
    <img class="modal-img" id="modalImg" src="" alt="">
    <div class="modal-body">
      <span class="modal-tag" id="modalTag"></span>
      <h2 id="modalTitle"></h2>
      <p class="modal-desc" id="modalDesc"></p>

      <div class="modal-section">
        <h4>Комплектация</h4>
        <ul id="modalKit"></ul>
      </div>

      <div class="modal-section">
        <h4>Условия аренды</h4>
        <ul id="modalTerms"></ul>
      </div>

      <div class="modal-section modal-specs">
        <h4>Характеристики</h4>
        <table id="modalSpecs"></table>
      </div>

      <div class="modal-price-row">
        <div>
          <div class="modal-price" id="modalPrice">—</div>
          <small id="modalPriceUnit" style="color:#888; font-size:12px;"></small>
          <span class="modal-price-old" id="modalPriceOld" style="display:none;"></span>
        </div>
        <button class="btn" id="modalRentBtn">Арендовать</button>
      </div>
    </div>
  </div>
</div>

<section class="order" id="order">
  <div class="container">
    <h2 class="section-title reveal">Заявка</h2>
    <p class="section-sub reveal">Перезвоним за 15 минут</p>
    <form id="orderForm" class="reveal">
      <div class="form-row"><label for="name">Имя *</label><input type="text" id="name" required placeholder="Иван"></div>
      <div class="form-row"><label for="phone">Телефон *</label><input type="tel" id="phone" required placeholder="+7 (___) ___-__-__"></div>
      <div class="form-row"><label for="tool">Инструмент</label><input type="text" id="tool" placeholder="Например: Перфоратор Bosch"></div>
      <div class="form-row"><label for="period">Срок аренды</label><select id="period"><option>1 час</option><option>2–4 часа</option><option>1 сутки (−10%)</option><option>2–3 суток</option><option>до 7 суток</option><option>более 7 суток</option></select></div>
      <div class="form-row"><label for="comment">Комментарий</label><textarea id="comment" placeholder="Адрес доставки..."></textarea></div>
      <button type="submit" class="btn">Отправить заявку</button>
    </form>
  </div>
</section>

<footer>
  <div class="container">
    <div class="footer-grid">
      <div>
        <h4>БериИДелай</h4>
        <p>Аренда инструмента в Кургане и области. Скидка 10% при аренде на сутки.</p>
      </div>
      <div>
        <h4>Контакты</h4>
        <a href="tel:+79956749750" class="phone-foot">📞 +7 (995) 674-97-50</a>
        <a href="mailto:info@beriidelai45.ru">✉️ info@beriidelai45.ru</a>
        <p>📍 г. Курган, ул. Куйбышева, 25</p>
      </div>
      <div>
        <h4>Режим работы</h4>
        <p>Пн–Пт: 8:00 – 20:00</p>
        <p>Сб–Вс: 9:00 – 18:00</p>
      </div>
    </div>
    <div class="copy">© 2026 БериИДелай. Все права защищены.</div>
  </div>
</footer>

<div class="toast" id="toast">Заявка отправлена! Мы вам перезвоним.</div>

<script>
  // ===== БОКОВОЕ МЕНЮ =====
  const burger = document.getElementById('burger');
  const sideMenu = document.getElementById('sideMenu');
  const overlay = document.getElementById('overlay');
  const sideClose = document.getElementById('sideClose');

  function openMenu() {
    sideMenu.classList.add('open');
    overlay.classList.add('open');
    document.body.classList.add('menu-open');
  }
  function closeMenu() {
    sideMenu.classList.remove('open');
    overlay.classList.remove('open');
    document.body.classList.remove('menu-open');
  }
  burger.addEventListener('click', openMenu);
  sideClose.addEventListener('click', closeMenu);
  overlay.addEventListener('click', closeMenu);
  sideMenu.querySelectorAll('.side-nav a').forEach(a => a.addEventListener('click', closeMenu));
  document.addEventListener('keydown', e => { if (e.key === 'Escape') closeMenu(); });

  // ===== ШАПКА ПРИ ПРОКРУТКЕ =====
  const header = document.getElementById('header');
  window.addEventListener('scroll', () => {
    header.classList.toggle('scrolled', window.scrollY > 20);
  }, { passive: true });

  // ===== ФИЛЬТРАЦИЯ =====
  const filterBtns = document.querySelectorAll('.filter-btn');
  const cards = document.querySelectorAll('.card');
  filterBtns.forEach(btn => {
    btn.addEventListener('click', (e) => {
      e.stopPropagation();
      filterBtns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const filter = btn.dataset.filter;
      cards.forEach((card, i) => {
        if (filter === 'all' || card.dataset.category === filter) {
          card.style.display = 'flex';
          card.style.animation = 'none';
          void card.offsetWidth;
          card.style.animation = `cardIn .5s cubic-bezier(0.4, 0, 0.2, 1) ${i * 0.04}s both`;
        } else {
          card.style.display = 'none';
        }
      });
    });
  });

  // ===== ПЕРЕКЛЮЧАТЕЛЬ ЧАС/СУТКИ =====
  const rateBtns = document.querySelectorAll('.rate-toggle button');
  let currentRate = 'hour';
  const DISCOUNT = 0.9;

  function updatePrices() {
    document.querySelectorAll('.price[data-hour]').forEach(el => {
      const hour = +el.dataset.hour;
      const day = +el.dataset.day;
      el.style.transform = 'scale(0.92)';
      el.style.opacity = '0.5';
      setTimeout(() => {
        if (currentRate === 'hour') {
          el.innerHTML = hour + ' ₽<small>/ час</small>';
        } else {
          const old = Math.round(day / DISCOUNT);
          el.innerHTML = day + ' ₽<small>/ сутки</small>' +
            (old > day ? '<span class="price-old">' + old + ' ₽</span>' : '');
        }
        el.style.transform = 'scale(1)';
        el.style.opacity = '1';
      }, 180);
    });
  }
  rateBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      rateBtns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      currentRate = btn.dataset.rate;
      updatePrices();
    });
  });

  // ===== МОДАЛЬНОЕ ОКНО =====
  const overlayM = document.getElementById('modalOverlay');
  const modalImg = document.getElementById('modalImg');
  const modalTag = document.getElementById('modalTag');
  const modalTitle = document.getElementById('modalTitle');
  const modalDesc = document.getElementById('modalDesc');
  const modalSpecs = document.getElementById('modalSpecs');
  const modalKit = document.getElementById('modalKit');
  const modalTerms = document.getElementById('modalTerms');
  const modalPrice = document.getElementById('modalPrice');
  const modalPriceUnit = document.getElementById('modalPriceUnit');
  const modalPriceOld = document.getElementById('modalPriceOld');
  const modalRentBtn = document.getElementById('modalRentBtn');

  function fillList(el, items) {
    el.innerHTML = '';
    items.forEach((item, i) => {
      const li = document.createElement('li');
      li.textContent = item;
      li.style.opacity = '0';
      li.style.transform = 'translateX(-8px)';
      li.style.transition = 'opacity .4s ease, transform .4s ease';
      li.style.transitionDelay = (i * 0.04) + 's';
      el.appendChild(li);
      requestAnimationFrame(() => {
        li.style.opacity = '1';
        li.style.transform = 'translateX(0)';
      });
    });
  }

  function openModal(card) {
    const tool = card.dataset.tool;
    modalImg.src = card.dataset.img;
    modalImg.alt = tool;
    modalTag.textContent = card.dataset.tag;
    modalTitle.textContent = tool;
    modalDesc.textContent = card.dataset.desc;
    modalRentBtn.dataset.tool = tool;

    modalSpecs.innerHTML = '';
    try {
      const specs = JSON.parse(card.dataset.specs);
      Object.entries(specs).forEach(([k, v]) => {
        const tr = document.createElement('tr');
        tr.innerHTML = '<td>' + k + '</td><td>' + v + '</td>';
        modalSpecs.appendChild(tr);
      });
    } catch(e) {}

    try {
      fillList(modalKit, JSON.parse(card.dataset.kit));
    } catch(e) { fillList(modalKit, []); }

    try {
      fillList(modalTerms, JSON.parse(card.dataset.terms));
    } catch(e) { fillList(modalTerms, []); }

    const hour = +card.dataset.hour;
    const day = +card.dataset.day;
    if (currentRate === 'hour') {
      modalPrice.textContent = hour + ' ₽';
      modalPriceUnit.textContent = 'за час';
      modalPriceOld.style.display = 'none';
    } else {
      modalPrice.textContent = day + ' ₽';
      modalPriceUnit.textContent = 'за сутки (скидка 10%)';
      modalPriceOld.textContent = 'без скидки: ' + Math.round(day / DISCOUNT) + ' ₽';
      modalPriceOld.style.display = 'block';
    }

    overlayM.classList.add('open');
    document.body.classList.add('menu-open');
  }

  function closeModal() {
    overlayM.classList.remove('open');
    document.body.classList.remove('menu-open');
  }

  cards.forEach(card => {
    card.addEventListener('click', (e) => {
      if (e.target.closest('.rent-btn')) return;
      openModal(card);
    });
  });

  document.getElementById('modalClose').addEventListener('click', closeModal);
  overlayM.addEventListener('click', (e) => { if (e.target === overlayM) closeModal(); });
  document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModal(); });

  // ===== КНОПКА "АРЕНДОВАТЬ" =====
  const toolInput = document.getElementById('tool');
  document.querySelectorAll('.rent-btn').forEach(btn => {
    btn.addEventListener('click', (e) => {
      e.stopPropagation();
      toolInput.value = btn.dataset.tool;
      closeModal();
      document.getElementById('order').scrollIntoView({ behavior: 'smooth' });
      setTimeout(() => document.getElementById('name').focus(), 500);
    });
  });
  modalRentBtn.addEventListener('click', () => {
    toolInput.value = modalRentBtn.dataset.tool;
    closeModal();
    document.getElementById('order').scrollIntoView({ behavior: 'smooth' });
    setTimeout(() => document.getElementById('name').focus(), 500);
  });

  // ===== ОТПРАВКА ФОРМЫ =====
  const toast = document.getElementById('toast');
  document.getElementById('orderForm').addEventListener('submit', e => {
    e.preventDefault();
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 4000);
    e.target.reset();
  });

  // ===== ПЛАВНОЕ ПОЯВЛЕНИЕ =====
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.12, rootMargin: '0px 0px -30px 0px' });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  updatePrices();
</script>

</body>
</html>
