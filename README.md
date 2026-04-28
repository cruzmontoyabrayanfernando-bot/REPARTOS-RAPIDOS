# REPARTOS-RAPIDOS

<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VOK CHINESEFOOD</title>

    <!-- 🔥 LEAFLET -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    
    <!-- Firebase -->


<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";

// ✅ CORREGIDO - Un solo import completo
import { 
  getFirestore, 
  collection, 
  addDoc, 
  serverTimestamp,
  getDocs, 
  getDoc, 
  doc, 
  query, 
  where, 
  onSnapshot,
  orderBy  // ✅ AGREGADO
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyAAqy5cTbBCO9NCmVBGiYKdu1uZDQAWTpY",
  authDomain: "vok-chinese-2024.firebaseapp.com",
  projectId: "vok-chinese-2024",
  storageBucket: "vok-chinese-2024.firebasestorage.app",
  messagingSenderId: "1034716143333",
  appId: "1:1034716143333:web:04f978334bf8933e51be0c"
};


const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

// ✅ SOLO para guardar pedidos
 window.db = db;
        window.addDoc = addDoc;
        window.collection = collection;
        window.serverTimestamp = serverTimestamp;
        window.onSnapshot = onSnapshot;
        window.query = query;
        window.orderBy = orderBy;

console.log("✅ Cliente listo - solo guarda pedidos");
</script>

<style>
/* ========================================
   🎨 CSS ULTRA-OPTIMIZADO VOK CHINESEFOOD
   ✨ Sin bugs, responsive, animaciones premium
======================================== */

* {
    box-sizing: border-box;
}

:root {
    --primary-gold: #fff346;
    --primary-orange: #ff6b35;
    --primary-red: #ff4757;
    --bg-light: #fffefe;
    --text-dark: #2c3e50;
    --shadow-light: rgba(0,0,0,0.1);
    --shadow-heavy: rgba(0,0,0,0.2);
}

body {
    font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, sans-serif;
    margin: 0;
    padding: 0;
    background: linear-gradient(135deg, var(--bg-light) 0%, #f8f9ff 100%);
    color: var(--text-dark);
    line-height: 1.6;
    overflow-x: hidden;
}

/* HEADER STICKY MEJORADO */
#topUI {
    position: sticky;
    top: 0;
    z-index: 1000;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

#topUI.hide {
    transform: translateY(-100%);
}

header {
    background: linear-gradient(135deg, var(--primary-gold) 0%, #ffe600 50%, #ffcd00 100%);
    color: #1a1a1a;
    padding: clamp(16px, 4vw, 24px);
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 8px 32px rgba(255, 243, 70, 0.4);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(255,255,255,0.2);
}

.header-left {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.header-left h1 {
    margin: 0;
    font-size: clamp(18px, 4.5vw, 24px);
    font-weight: 800;
    letter-spacing: -0.5px;
}

.header-left p {
    margin: 0;
    font-size: clamp(12px, 3vw, 14px);
    color: #666;
    font-weight: 500;
}

.header-logo {
    width: clamp(50px, 12vw, 60px);
    height: clamp(50px, 12vw, 60px);
    border-radius: 16px;
    object-fit: cover;
    box-shadow: 0 8px 24px var(--shadow-heavy);
    border: 3px solid rgba(255,255,255,0.8);
}

/* CARRUSEL PREMIUM */
.carousel {
    position: relative;
    width: clamp(280px, 70vw, 340px);
    height: clamp(160px, 40vw, 200px);
    margin-left: clamp(12px, 3vw, 20px);
    overflow: hidden;
    border-radius: 24px;
    box-shadow: 0 16px 48px var(--shadow-heavy);
    background: linear-gradient(135deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255,255,255,0.3);
}

.carousel-track {
    display: flex;
    height: 100%;
    transition: transform 0.8s cubic-bezier(0.22, 1, 0.36, 1);
}

.slide {
    min-width: 100%;
    height: 100%;
    position: relative;
    background-size: cover;
    background-position: center;
    display: flex;
    align-items: center;
    justify-content: center;
}

.slide::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(45deg, rgba(0,0,0,0.6), rgba(0,0,0,0.3));
    border-radius: 24px;
}

.slide-content {
    position: relative;
    z-index: 2;
    text-align: center;
    color: white;
    padding: 24px;
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(20px);
    border-radius: 20px;
    border: 1px solid rgba(255,255,255,0.3);
    max-width: 90%;
}

.slide h3 { 
    margin: 0 0 8px 0; 
    font-size: clamp(18px, 5vw, 22px); 
    font-weight: 800; 
}

.slide p { 
    margin: 0; 
    font-size: clamp(13px, 3.5vw, 16px); 
    opacity: 0.95; 
}

.arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 48px;
    height: 48px;
    border-radius: 50%;
    border: none;
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(20px);
    color: #333;
    font-size: 20px;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    box-shadow: 0 8px 24px var(--shadow-heavy);
    opacity: 0;
    transition: all 0.3s ease;
    z-index: 3;
}

.carousel:hover .arrow { opacity: 1; }
.left { left: 12px; }
.right { right: 12px; }
.arrow:hover { 
    transform: translateY(-50%) scale(1.1); 
    background: white; 
}
.arrow:active { 
    transform: translateY(-50%) scale(0.95); 
}

.dots {
    position: absolute;
    bottom: 16px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 8px;
}

.dots span {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: rgba(255,255,255,0.5);
    cursor: pointer;
    transition: all 0.3s ease;
}

.dots .active {
    width: 32px;
    border-radius: 16px;
    background: white;
    box-shadow: 0 4px 12px var(--shadow-heavy);
}

/* CONTENIDO PRINCIPAL */
.container {
    padding: clamp(20px, 5vw, 32px);
    max-width: 1200px;
    margin: 0 auto;
}

.categories {
    display: flex;
    overflow-x: auto;
    gap: 12px;
    margin-bottom: 24px;
    padding-bottom: 12px;
    scrollbar-width: none;
    -ms-overflow-style: none;
}

.categories::-webkit-scrollbar { display: none; }

.categories button {
    padding: 12px 20px;
    border-radius: 25px;
    border: none;
    background: #f0f0f0;
    cursor: pointer;
    font-weight: 700;
    font-size: 14px;
    white-space: nowrap;
    transition: all 0.3s ease;
    box-shadow: 0 4px 12px var(--shadow-light);
    flex-shrink: 0;
}

.categories button.active {
    background: linear-gradient(135deg, var(--primary-gold), #ffe600);
    color: #1a1a1a;
    box-shadow: 0 8px 24px rgba(255, 243, 70, 0.4);
    transform: translateY(-2px);
}

h2 {
    font-size: clamp(24px, 6vw, 32px);
    font-weight: 800;
    margin: 0 0 32px 0;
    background: linear-gradient(135deg, var(--primary-orange), #f7931e);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

/* GRID PRODUCTOS */
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 20px;
    margin-top: 16px;
}

/* CARDS ULTRA PREMIUM */
.card {
    background: white;
    padding: 20px;
    border-radius: 24px;
    box-shadow: 0 12px 40px var(--shadow-light);
    text-align: center;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    border: 1px solid rgba(255,255,255,0.8);
    position: relative;
    overflow: hidden;
}

.card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary-orange), #f7931e, var(--primary-orange));
}

.card:hover {
    transform: translateY(-12px) scale(1.02);
    box-shadow: 0 24px 64px var(--shadow-heavy);
}

.product-img {
    width: 100%;
    height: 140px;
    object-fit: cover;
    border-radius: 20px;
    margin-bottom: 16px;
    transition: all 0.4s ease;
}

.card:hover .product-img {
    transform: scale(1.08);
    box-shadow: 0 12px 32px var(--shadow-heavy);
}

.card h3 {
    font-size: clamp(14px, 3.5vw, 16px);
    font-weight: 700;
    margin: 0 0 8px 0;
    color: var(--text-dark);
}

.card p {
    margin: 4px 0;
    font-size: clamp(13px, 3vw, 15px);
    font-weight: 600;
    color: var(--primary-orange);
}

.descripcion {
    font-size: 13px;
    color: #7f8c8d;
    min-height: 44px;
    max-height: 44px;
    overflow: hidden;
    line-height: 1.4;
    margin: 12px 0;
    transition: all 0.3s ease;
}

.card:hover .descripcion { max-height: 88px; }

input[type="number"] {
    width: 100%;
    padding: 12px;
    margin: 12px 0;
    border-radius: 16px;
    border: 2px solid #f0f0f0;
    font-size: 16px;
    font-weight: 600;
    text-align: center;
    transition: all 0.3s ease;
}

input[type="number"]:focus {
    outline: none;
    border-color: var(--primary-gold);
    box-shadow: 0 0 0 4px rgba(255, 243, 70, 0.2);
}

/* BOTONES PREMIUM */
button {
    background: linear-gradient(135deg, var(--primary-gold) 0%, #ffd000 100%);
    color: #1a1a1a;
    border: none;
    padding: 14px 24px;
    border-radius: 20px;
    cursor: pointer;
    font-weight: 700;
    font-size: 15px;
    letter-spacing: 0.5px;
    box-shadow: 0 8px 24px rgba(255, 243, 70, 0.4);
    transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    position: relative;
    overflow: hidden;
    width: 100%;
    margin-top: auto;
}

button:hover {
    transform: translateY(-3px);
    box-shadow: 0 16px 40px rgba(255, 243, 70, 0.6);
    background: linear-gradient(135deg, #ffe600 0%, var(--primary-gold) 100%);
}

button:active { transform: scale(0.97); }

.remove-btn {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--primary-red), #ff3838);
    color: white;
    border: none;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 6px 20px rgba(255, 71, 87, 0.4);
    transition: all 0.3s ease;
}

.remove-btn:hover {
    transform: scale(1.15);
    box-shadow: 0 12px 32px rgba(255, 71, 87, 0.6);
}

button:disabled {
    background: #ccc;
    color: #666;
    cursor: not-allowed;
    box-shadow: none;
    transform: none;
}

/* CARRITO FLOTANTE */
#cartBox {
    position: fixed;
    bottom: 24px;
    right: 24px;
    display: flex;
    align-items: center;
    gap: 16px;
    background: linear-gradient(135deg, var(--primary-orange) 0%, #f7931e 100%);
    color: white;
    padding: 16px 24px;
    border-radius: 50px;
    cursor: pointer;
    box-shadow: 0 16px 48px rgba(255, 107, 53, 0.4);
    backdrop-filter: blur(20px);
    z-index: 999;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    max-width: 340px;
}

#cartBox:hover {
    transform: translateY(-8px) scale(1.05);
    box-shadow: 0 24px 64px rgba(255, 107, 53, 0.6);
}

#cartBox img {
    width: 52px;
    height: 52px;
    border-radius: 50%;
    background: white;
    padding: 4px;
    box-shadow: 0 4px 16px var(--shadow-heavy);
}

#cartBox > div {
    flex: 1;
    min-width: 0;
}

#cartBox span {
    font-size: 14px;
    opacity: 0.9;
    display: block;
}

#cartBox p {
    margin: 0;
    font-size: 20px;
    font-weight: 800;
}

#cartCount {
    position: absolute;
    top: -6px;
    right: -6px;
    background: #ff3838;
    color: white;
    font-size: 13px;
    font-weight: 800;
    padding: 6px 10px;
    border-radius: 20px;
    box-shadow: 0 4px 16px rgba(255, 56, 56, 0.6);
    min-width: 28px;
    text-align: center;
}

/* MODAL ULTRA MODERNO */
#modal {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.7);
    backdrop-filter: blur(20px);
    z-index: 10000;
    justify-content: center;
    align-items: flex-start;
    padding: 24px;
    overflow-y: auto;
}

.modal-content {
    background: rgba(255,255,255,0.98);
    backdrop-filter: blur(40px);
    padding: 32px;
    border-radius: 32px;
    width: 100%;
    max-width: 480px;
    max-height: 90vh;
    overflow-y: auto;
    box-shadow: 0 32px 96px rgba(0,0,0,0.4);
    animation: modalSlideIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    border: 1px solid rgba(255,255,255,0.3);
    position: relative;
}

@keyframes modalSlideIn {
    from { opacity: 0; transform: translateY(48px) scale(0.95); }
    to { opacity: 1; transform: translateY(0) scale(1); }
}

.close {
    position: absolute;
    top: 20px;
    right: 24px;
    font-size: 28px;
    font-weight: bold;
    color: var(--primary-red);
    cursor: pointer;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    transition: all 0.3s ease;
}

.close:hover {
    background: rgba(255, 71, 87, 0.1);
    transform: scale(1.1);
}

.modal-content h2 {
    margin: 0 0 24px 0;
    font-size: clamp(22px, 5vw, 28px);
    text-align: center;
    font-weight: 800;
    
    /* 1. GRADIENTE PRIMERO */
    background: linear-gradient(135deg, var(--primary-orange), #fffb00);
    
    /* 2. CLIP STANDARD */
    background-clip: text;
    
    /* 3. WEBKIT CLIP */
    -webkit-background-clip: text;
    
    /* 4. FILL TRANSPARENTE (CRÍTICO) */
    -webkit-text-fill-color: transparent;
    
    /* 5. FALLBACK */
    color: var(--primary-orange);
}

.modal-content h3 {
    margin: 24px 0 16px 0;
    font-size: 20px;
    font-weight: 700;
    color: var(--text-dark);
    border-bottom: 2px solid #f0f0f0;
    padding-bottom: 8px;
}

.modal-content hr {
    border: none;
    height: 1px;
    background: linear-gradient(to right, transparent, #ddd, transparent);
    margin: 24px 0;
}

#cartList div {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #f8f9fa;
    padding: 16px 20px
    
}

.form-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-top: 20px;
    background: #fafafa;
    padding: 20px;
    border-radius: 20px;
}

.form-group.full { grid-column: 1 / -1; }

.form-group label {
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 8px;
    color: var(--text-dark);
    display: block;
}

.form-group input,
.form-group select,
.form-group textarea {
    width: 100%;
    padding: 14px 16px;
    border-radius: 16px;
    border: 2px solid #f0f0f0;
    font-size: 16px;
    font-weight: 500;
    transition: all 0.3s ease;
    background: white;
}
#cartList div {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #f8f9fa;
    padding: 16px 20px;
    margin-bottom: 12px;
    border-radius: 20px;
    box-shadow: 0 4px 16px rgba(0,0,0,0.08);
    font-size: 16px;
    font-weight: 600;
    transition: all 0.3s ease;
    border: 1px solid rgba(255,255,255,0.6);
}

#cartList div:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.12);
    background: white;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
    outline: none;
    border-color: var(--primary-gold);
    box-shadow: 0 0 0 4px rgba(255, 243, 70, 0.2);
}

textarea {
    resize: vertical;
    min-height: 80px;
    font-family: inherit;
}

#btnEnviar {
    width: 100%;
    background: linear-gradient(135deg, var(--primary-red) 0%, #ff3838 100%);
    color: white;
    font-size: 18px;
    font-weight: 800;
    padding: 20px;
    margin-top: 32px;
    border-radius: 24px;
    box-shadow: 0 12px 40px rgba(255, 71, 87, 0.4);
}

#btnEnviar:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 56px rgba(255, 71, 87, 0.6);
}

#btnEnviar:disabled {
    background: #ccc;
    transform: none;
    box-shadow: none;
    cursor: not-allowed;
}

/* TOAST PREMIUM */
#toast {
    position: fixed;
    bottom: 100px;
    left: 50%;
    transform: translateX(-50%) translateY(20px);
    background: linear-gradient(135deg, #2c3e50, #34495e);
    color: white;
    padding: 16px 32px;
    border-radius: 50px;
    font-size: 16px;
    font-weight: 600;
    opacity: 0;
    pointer-events: none;
    box-shadow: 0 16px 48px rgba(0,0,0,0.3);
    z-index: 10001;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    white-space: nowrap;
    max-width: 90vw;
}

#toast.show {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
}

/* ANIMACIONES */
@keyframes pop {
    0% { transform: scale(1); }
    50% { transform: scale(1.12); }
    100% { transform: scale(1); }
}

@keyframes bounceCart {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.15); }
}

@keyframes modalFade {
    from { transform: translateY(40px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
}

.card.added { animation: pop 0.5s ease; }
#cartBox.animate { animation: bounceCart 0.6s ease; }

.fly-img {
    position: fixed;
    z-index: 10001;
    width: 64px;
    height: 64px;
    object-fit: cover;
    border-radius: 16px;
    pointer-events: none;
    box-shadow: 0 8px 24px var(--shadow-heavy);
    transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
}

/* SEGUIMIENTO */
#seguimientoView {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: clamp(20px, 5vw, 40px);
    animation: fadeIn 0.6s ease;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
    0% { transform: scale(1); box-shadow: 0 6px 20px var(--shadow-heavy); }
    50% { transform: scale(1.1); box-shadow: 0 10px 30px rgba(76,175,80,0.6); }
    100% { transform: scale(1); box-shadow: 0 6px 20px var(--shadow-heavy); }
}

#seguimientoView h2 {
    text-align: center;
    color: white;
    font-size: clamp(24px, 6vw, 32px);
    margin: 32px 0;
    font-weight: 800;
}

.progress-container {
    background: rgba(255,255,255,0.2);
    height: 12px;
    border-radius: 20px;
    margin: 32px auto;
    overflow: hidden;
    backdrop-filter: blur(20px);
    max-width: 400px;
}

#progresoBarra {
    height: 100%;
    background: linear-gradient(90deg, #4CAF50, #45a049);
    width: 0%;
    transition: width 0.8s ease;
    border-radius: 20px;
    box-shadow: 0 4px 16px rgba(76, 175, 80, 0.4);
}

#map, #mapSeguimiento {
    height: clamp(280px, 60vw, 400px);
    border-radius: 24px;
    margin: 24px 0;
    box-shadow: 0 16px 48px rgba(0,0,0,0.3);
    border: 1px solid rgba(255,255,255,0.2);
}

.repartidor-info {
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(20px);
    padding: 24px;
    border-radius: 24px;
    margin: 24px auto;
    box-shadow: 0 16px 48px rgba(0,0,0,0.2);
    border: 1px solid rgba(255,255,255,0.3);
    max-width: 400px;
}

.repartidor-info h3 {
    margin: 0 0 16px 0;
    color: var(--text-dark);
    font-size: 22px;
}

.repartidor-info p {
    margin: 8px 0;
    font-size: 16px;
    color: #555;
}

.custom-div-icon {
    background: transparent;
    border: none;
}

/* TEXTOS FINALES */
#subtotalText, #envioText, #totalText {
    font-size: 14px;
    margin: 4px 0;
}

#totalText {
    font-weight: bold;
    font-size: 16px;
    color: var(--primary-orange);
}

#changeText {
    font-weight: bold;
    margin-top: 10px;
    font-size: 16px;
}

/* FIREBASE STATUS */
#firebaseStatus {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #4CAF50;
    color: white;
    padding: 12px 20px;
    border-radius: 25px;
    font-size: 14px;
    font-weight: 600;
    z-index: 9999;
    box-shadow: 0 8px 24px rgba(76, 175, 80, 0.4);
    animation: slideInRight 0.5s ease;
}

@keyframes slideInRight {
    from { transform: translateX(100%); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
}

/* RESPONSIVE PERFECTO */
@media (max-width: 768px) {
    .grid { grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 16px; }
    .carousel { width: 100%; max-width: 320px; margin-left: 0; margin-top: 16px; }
    #cartBox { left: 20px; right: 20px; bottom: 20px; justify-content: center; }
    .modal-content { margin-top: 24px; padding: 24px; border-radius: 24px; }
    .form-grid { grid-template-columns: 1fr; gap: 12px; }
    header { flex-direction: column; gap: 16px; text-align: center; padding: 20px; }
    .header-left { order: 2; }
    .header-logo { order: 1; }
}

@media (max-width: 480px) {
    .container { padding: 16px 12px; }
    .grid { grid-template-columns: repeat(2, 1fr); gap: 12px; }
    .card { padding: 16px; }
    .product-img { height: 120px; }
    #toast { font-size: 14px; padding: 12px 24px; max-width: 95vw; }
}
#firebaseStatus.registered {
    background: linear-gradient(135deg, #4CAF50, #45a049) !important;
}
.welcome-banner {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    padding: 16px;
    border-radius: 20px;
    text-align: center;
    margin-bottom: 24px;
    box-shadow: 0 8px 32px rgba(102,126,234,0.4);
}

/* UTILIDADES */
.text-center { text-align: center; }
.mb-4 { margin-bottom: 16px; }
.mt-4 { margin-top: 16px; }
</style>
<button onclick="window.location.href='./?registro=1'" style="
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    border: none;
    padding: 12px 20px;
    border-radius: 25px;
    font-weight: 700;
    margin-left: 10px;
    box-shadow: 0 4px 15px rgba(102,126,234,0.4);
    cursor: pointer;
">
🔍 Mis Pedidos
</button>
</head>

<body>
    <div id="firebaseStatus" style="
position:fixed;
top:10px;
right:10px;
background:#222;
color:white;
padding:10px 15px;
border-radius:10px;
font-size:14px;
z-index:9999;
box-shadow:0 4px 12px rgba(0,0,0,0.3);
">
🔥 Conectando a Firebase...
</div>
<div id="topUI">

<header id="mainHeader">
    
    <div class="header-left">
        <h1>🍣 VOK CHINESEFOOD</h1>
        <h1>Los mejores makis a la puerta de tu casa</h1>
    </div>

    <div>
        <img class="header-logo" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTuICRBKRwGbom4-ncU4xT6UY0bwsKu0uQXDg&s">
    </div>

    <!-- 🔥 CARRUSEL DENTRO -->
    <div class="carousel">
                <button class="arrow left" onclick="prevSlide()">❮</button>
                <div class="carousel-track" id="carouselTrack">
                    <div class="slide" style="background-image: url('https://media.cupondorado.pe/images/offers/450x270/makifurai-178.webp');">
                        <div class="slide-content">
                            <h3>🔥 Promo Especial</h3>
                            <p>2 rollos por $280</p>
                        </div>
                    </div>
                    <div class="slide" style="background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTcRp8gK0gXKUxLS3gc7oOh-CimQZhg_u4GvQ&s');">
                        <div class="slide-content">
                            <h3>🍣 Los mejores makis</h3>
                            <p> TUXTLA GUTIERREZ</p>
                        </div>
                    </div>
                    <div class="slide" style="background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRyEaoS81_V2mYtL1563vbTc3tA6Ocrqg4sIA&s');">
                        <div class="slide-content">
                            <h3>🚚 Envíos rápidos</h3>
                            <p>A la puerta de tu casa</p>
                        </div>
                    </div>
                </div>
                <button class="arrow right" onclick="nextSlide()">❯</button>
                <div class="dots" id="dots"></div>
            </div>

</header>

</div>
<div class="container">
    <div class="categories" id="categories"></div> <!-- categorias -->
    <h2>Productos</h2>
    <div class="grid" id="products"></div>
</div>

<!-- CARRITO -->
<div id="cartBox" onclick="openModal()">
    
    <img src="https://png.pngtree.com/png-vector/20260413/ourlarge/pngtree-cute-sushi-rolls-in-cartoon-car-transportation-concept-png-image_18984593.webp">

    <div>
        <span>Tu pedido</span>
        <p>$<span id="total">0</span></p>
    </div>

    <div id="cartCount">0</div>

</div>

<!-- MODAL -->
<!-- MODAL ULTRA MODERNO -->
<div id="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal()">×</span>
        
        <div class="modal-header">
            <h2>🧾 Tu Pedido</h2>
            <div class="order-summary">
                <span id="itemsCount">0 items</span>
                <span id="totalModal">$0</span>
            </div>
        </div>

        <div id="cartList"></div>

        <div class="divider"></div>
        
        <h3>📍 Datos de entrega</h3>
        
        <!-- BOTONES RÁPIDOS -->
        <div class="quick-actions">
            <button onclick="getLocation()" class="btn-location">
                📍 Mi ubicación GPS
            </button>
           
        </div>

        <!-- MAPA -->
        <div id="map" class="map-container"></div>

        <!-- FORMULARIO MODERNO -->
        <div class="form-grid">
            <div class="form-group">
                <label>👤 Nombre completo</label>
                <input type="text" id="name" placeholder="Juan Pérez" required>
            </div>

            <div class="form-group">
                <label>📍 Dirección exacta</label>
                <input type="text" id="address" placeholder="Calle 123 #45, Colonia Centro" required>
            </div>

            <div class="form-group full">
                <label>📝 Referencias (opcional)</label>
                <textarea id="references" placeholder="Frente a la farmacia, casa blanca con rejas verdes..."></textarea>
            </div>
  <div class="form-group">
                <label>📞 NUMERO</label>
                <input type="text" id="address" placeholder="ESCRIBE TU NUMERO" required>
            </div>
            <div class="form-row">
                <div class="form-group">
                    <label>💳 Pago</label>
                    <select id="payment">
                        <option value="Efectivo">💵 Efectivo</option>
                        <option value="Transferencia">💳 Transferencia</option>
                        <option value="Tarjeta">💳 Tarjeta</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>⏰ Entrega</label>
                    <select id="schedule">
                        <option>🚀 Ya saliendo (15min)</option>
                        <option>🌅 Tarde (2-4pm)</option>
                        <option>🌙 Noche (6-9pm)</option>
                        <option>🌅 Mañana</option>
                    </select>
                </div>
            </div>

            <!-- DESGLOSE TOTAL -->
            <div class="total-breakdown">
                <div class="breakdown-row">
                    <span>Subtotal:</span>
                    <span id="subtotalText">$0</span>
                </div>
                <div class="breakdown-row">
                    <span>🚚 Envío:</span>
                    <span id="envioText">$0</span>
                </div>
                <div class="breakdown-row total-row">
                    <span>TOTAL:</span>
                    <span id="totalText">$0</span>
                </div>
            </div>

            <div class="form-group full">
                <label>💰 Efectivo recibido</label>
                <input type="number" id="cash" placeholder="0" min="0" oninput="calculateChange()">
                <div id="changeText" class="change-info"></div>
            </div>

            <div class="form-group full">
                <label>📝 Nota especial (opcional)</label>
                <textarea id="extra" placeholder="Sin cebolla, picante extra, etc..."></textarea>
            </div>
        </div>

        <!-- BOTONES ACCIÓN -->
        <div class="modal-actions">
            <button onclick="closeModal()" class="btn-secondary">Cancelar</button>
            <button id="btnEnviar" onclick="sendWhatsApp(event)" class="btn-primary">
                🚀 Confirmar Pedido
                <span class="btn-loader" style="display:none;">⏳</span>
            </button>
        </div>
    </div>
</div>

<!-- VISTA SEGUIMIENTO MODERNA -->
<div id="seguimientoView" style="display:none;">
    <div class="seguimiento-container">
        <!-- HEADER -->
        <div class="seguimiento-header">
            <div class="status-card" id="statusCard">
                <div class="status-icon">🚚</div>
                <div>
                    <h2 id="estadoPedido">Preparando tu pedido...</h2>
                    <div id="tiempoEstimado" class="eta">ETA: 15-20 min</div>
                </div>
            </div>
        </div>

        <!-- BARRA PROGRESO -->
        <div class="progress-section">
            <div class="progress-container">
                <div id="progresoBarra" class="progress-bar"></div>
            </div>
            <div class="progress-steps">
                <span class="step active">1. Recibido</span>
                <span class="step">2. Preparando</span>
                <span class="step">3. En camino</span>
                <span class="step">4. Entregado</span>
            </div>
        </div>

        <!-- MAPA PRINCIPAL -->
        <div id="mapSeguimiento" class="map-seguimiento"></div>

        <!-- REPARTIDOR -->
        <div class="repartidor-card">
            <div class="repartidor-header">
                <div class="repartidor-avatar">👨‍🍳</div>
                <div>
                    <h3 id="detalleRepartidor">Juan Pérez</h3>
                    <div class="repartidor-status">En ruta</div>
                </div>
            </div>
            <div class="repartidor-details">
                <div class="detail-row">
                    <span>📱 Teléfono:</span>
                    <span id="telRepartidor">+52 961 123 4567</span>
                </div>
                <div class="detail-row">
                    <span>🚗 Placa:</span>
                    <span id="placaAuto">ABC-1234</span>
                </div>
            </div>
            <button onclick="llamarRepartidor()" class="btn-call">
                📞 Llamar ahora
            </button>
        </div>

        <!-- ACCIONES -->
        <div class="seguimiento-actions">
            <button onclick="window.history.back()" class="btn-back">← Volver</button>
        </div>
    </div>
</div>
<div id="toast"></div>
<script>
// ===== VARIABLES GLOBALES (FUSIONADAS) =====
const urlParams = new URLSearchParams(window.location.search);
const modoSeguimiento = urlParams.get('seguimiento') === '1';
const modoRegistro = urlParams.get('registro') === '1';
const modoCliente = urlParams.get('cliente');

const products = [
    { id: 1,name: "CALIFORNIA ROLL", price: 140, category: "Crudos", stock: 100000, img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSauS-zHHVQodLhxhSLbG-RX6KbuvKZXkVDYw&s",descripcion: "Relleno: Queso philadelfia, Camaron empanizado, Pepino, Embuelto en aguacate " },
    { id: 2,name: "Banana ROLL", price: 140, category: "Crudos", stock: 1000, img: "https://tofuu.getjusto.com/orioneat-local/resized2/tQNMB3LduLcADBg5f-2400-x.webp",descripcion: "Relleno: Queso philadelfia, Camaron empanizado, Aguacate, Embuelto en platano " },
    { id: 3,name: "SURIMI ROLL", price: 140, category: "Crudos",stock: 100000,img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQfSo4dgWNk-gWMeEuJPG71lQ5PzRRC6FZvhw&s" ,descripcion: "Relleno: Queso philadelfia, Camaron empanizado, Aguacate, Embuelto en platano " },
    { id: 4,name: "NEVADO ROLL", price: 140, category: "Crudos", stock: 100000, img: "https://www.cocinavital.mx/wp-content/uploads/2017/08/sushi-de-camaron-asado-con-chipotle-y-aguacate.jpg" },
    {id: 5, name: "MAR Y TIERRA ROLL", price: 160, category: "Empanizados",stock: 100000, img: "https://sushitophx.com/wp-content/uploads/2020/04/Mar-y-Tierra.jpg" ,descripcion: "Relleno: Queso philadelfia, Camaron empanizado, Aguacate, Embuelto en platano " },
    { id: 6,name: "HOT ROLL", price: 140, category: "Empanizados",stock: 100000, img: "https://evelynrickemberepe2.weebly.com/uploads/3/0/9/3/30935101/7731471_orig.jpg" },
    { id: 7,name: "SNACK ESPECIAL", price: 140, category: "Empanizados",stock: 100000, img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRohOOYb2hCAWLXXlkuQ593tABui0nqX2m4NQ&s" },
    { id: 8,name: "CHIKEN ROLL", price:140, category: "Empanizados",stock: 100000,img: "https://www.bakenroll.az/en/image/chicken-cheese-1x1.jpg" }
];

let cart = JSON.parse(localStorage.getItem("cart")) || [];
let total = 0, envio = 0, totalFinal = 0;
let userCoords = "";
let userData = JSON.parse(localStorage.getItem("userData")) || null;
let currentPedidoId = null;

const zonas = [
    { nombre: "Centro", lat: 16.75, lng: -93.12, radio: 3, costo: 20 },
    { nombre: "Periferia", lat: 16.75, lng: -93.12, radio: 6, costo: 30 }
];

let map, marker, mapSeguimiento, markerCliente, markerRepartidor, rutaLinea;
let progreso = 0, intervaloActualizacion;
let posicionRepartidor = { lat: 16.75, lng: -93.12 };
let repartidorInfo = { nombre: "Juan Pérez", telefono: "9611234567", placa: "ABC-1234" };
let latClienteSeguimiento, lngClienteSeguimiento;

// ===== CARRITO Y PRODUCTOS (TUS FUNCIONES ORIGINALES) =====
const container = document.getElementById("products");
const categories = ["Todos", "Empanizados", "Crudos"];
let currentCategory = "Todos";

// Render categorías
const categoriesContainer = document.getElementById("categories");
categories.forEach(cat => {
    const btn = document.createElement("button");
    btn.innerText = cat;
    if (cat === "Todos") btn.classList.add("active");
    btn.onclick = () => {
        currentCategory = cat;
        document.querySelectorAll(".categories button").forEach(b => b.classList.remove("active"));
        btn.classList.add("active");
        renderProducts();
    };
    categoriesContainer.appendChild(btn);
});

function renderProducts() {
    container.innerHTML = "";
    products.forEach((p, i) => {
        if (currentCategory !== "Todos" && p.category !== currentCategory) return;
        const div = document.createElement("div");
        div.className = "card";
        div.innerHTML = `
            <img src="${p.img}" class="product-img">
            <h3>${p.name}</h3>
            <p>$${p.price} / Rollo de 10 pz</p>
            <p class="descripcion">${p.descripcion || ""}</p>
            <input type="number" id="qty${i}" min="1" value="1">
            <span style="font-size:12px;">Rollo de 10 pz</span>
            <button onclick="addToCart(${i})">Agregar</button>
        `;
        container.appendChild(div);
    });
}

// ===== TUS FUNCIONES DE CARRITO (SIN CAMBIOS) =====
function addToCart(i) {
    const card = document.getElementById(`qty${i}`).closest(".card");
    card.classList.add("added");
    const cartBox = document.getElementById("cartBox");
    cartBox.classList.add("animate");
    
    setTimeout(() => { cartBox.classList.remove("animate"); card.classList.remove("added"); }, 400);
    
    const qty = parseInt(document.getElementById(`qty${i}`).value);
    if (!qty || qty <= 0) { alert("Cantidad inválida"); return; }
    
    const product = products[i];
    const img = document.getElementById(`qty${i}`).closest(".card").querySelector("img");
    flyToCart(img);
    hablar(`${product.name}`);
    
    if (qty > product.stock) { alert(`Stock insuficiente. Solo hay ${product.stock}`); return; }
    
    const subtotal = product.price * qty;
    cart.push({ id: product.id, name: product.name, qty, subtotal });
    
    total = cart.reduce((acc, item) => acc + item.subtotal, 0);
    updateTotal();
    mostrarToast(`✅ ${product.name} agregado`);
    localStorage.setItem("cart", JSON.stringify(cart));
    updateCartCount();
}

function updateTotal() {
    localStorage.setItem("total", total);
    totalFinal = total + envio;
    document.getElementById("total").innerText = totalFinal;
    calculateChange();
}

function removeFromCart(index) {
    cart.splice(index, 1);
    total = cart.reduce((acc, item) => acc + item.subtotal, 0);
    renderCart();
    updateTotal();
    localStorage.setItem("cart", JSON.stringify(cart));
    updateCartCount();
}

function renderCart() {
    const list = document.getElementById("cartList");
    list.innerHTML = "";
    if (cart.length === 0) {
        list.innerHTML = "<p>Carrito vacío</p>";
        return;
    }
    cart.forEach((item, i) => {
        list.innerHTML += `
            <div>
               ${item.name} - ${item.qty} rollos = $${item.subtotal}
                <button class="remove-btn" onclick="removeFromCart(${i})">✕</button>
            </div>
        `;
    });
}

// ===== NUEVAS FUNCIONES REGISTRO Y SEGUIMIENTO (INTEGRADAS) =====

// 🎯 REGISTRO DE CLIENTE
function mostrarRegistroCliente() {
    document.querySelector("#topUI").style.display = "none";
    document.querySelector(".container").style.display = "none";
    document.getElementById("cartBox").style.display = "none";
    
    const modal = document.getElementById("modal");
    modal.innerHTML = `
        <div class="modal-content">
            <span class="close" onclick="cerrarRegistro()">×</span>
            <h2>👤 Registro Cliente</h2>
            <div class="form-grid">
                <div class="form-group">
                    <label>📧 Email</label>
                    <input type="email" id="regEmail" placeholder="tucorreo@email.com" required>
                </div>
                <div class="form-group">
                    <label>📱 Teléfono</label>
                    <input type="tel" id="regTelefono" placeholder="9611234567" required>
                </div>
                <div class="form-group full">
                    <label>👤 Nombre</label>
                    <input type="text" id="regNombre" placeholder="Juan Pérez" required>
                </div>
                <button id="btnRegistrar" onclick="registrarCliente()" class="btn-primary">
                    ✅ Registrarme
                </button>
            </div>
        </div>
    `;
    modal.style.display = "flex";
}

async function registrarCliente() {
    const email = document.getElementById("regEmail").value;
    const telefono = document.getElementById("regTelefono").value;
    const nombre = document.getElementById("regNombre").value;
    
    if (!email || !telefono || !nombre) {
        alert("Completa todos los campos");
        return;
    }
    
    const codigoCliente = Math.floor(100000 + Math.random() * 900000).toString();
    
    userData = { email, telefono, nombre, codigo: codigoCliente };
    localStorage.setItem("userData", JSON.stringify(userData));
    
    mostrarToast("✅ Registrado correctamente");
    
    // ✅ NO REDIRIGIR - VOLVER AL MENU PRINCIPAL
    setTimeout(() => {
        cerrarRegistro();
        // Recargar para mostrar menu principal
        window.location.href = "./";
    }, 1500);
}
function cerrarRegistro() {
    document.getElementById("modal").style.display = "none";
    // ✅ MOSTRAR TODO DE NUEVO
    document.querySelector("#topUI").style.display = "block";
    document.querySelector(".container").style.display = "block";
    document.getElementById("cartBox").style.display = "flex";
}

// 🎯 BUSCAR PEDIDO PARA SEGUIMIENTO
async function buscarPedidoCliente() {
    const codigo = document.getElementById("codigoSeguimiento").value;
    if (!codigo || codigo.length !== 6) {
        alert("Ingresa un código de 6 dígitos");
        return;
    }
    
    try {
        const q = query(collection(db, "pedidos"), where("codigo_seguimiento", "==", codigo));
        const snapshot = await getDocs(q);
        
        if (snapshot.empty) {
            alert("Pedido no encontrado");
            return;
        }
        
        const pedido = snapshot.docs[0].data();
        currentPedidoId = snapshot.docs[0].id;
        window.location.href = `./?seguimiento=1&pedido=${currentPedidoId}&codigo=${codigo}`;
        
    } catch(error) {
        alert("Error al buscar pedido");
    }
}

// ===== sendWhatsApp MEJORADO CON REGISTRO =====
async function sendWhatsApp(e) {
    e.preventDefault();
    
    // ✅ VERIFICAR REGISTRO
    if (!userData) {
        alert("👤 Regístrate primero");
        mostrarRegistroCliente();
        return;
    }
    
    const btn = document.getElementById("btnEnviar");
    btn.disabled = true;
    btn.innerText = "Enviando...";
    
    try {
        const name = document.getElementById("name").value;
        const address = document.getElementById("address").value;
        const references = document.getElementById("references").value || "";
        const payment = document.getElementById("payment").value;
        
        if (!name || !address || cart.length === 0) {
            throw new Error("Datos incompletos");
        }
        
        const codigoSeguimiento = Math.floor(100000 + Math.random() * 900000).toString();
        
        const docRef = await addDoc(collection(window.db, "pedidos"), {
            cliente: name,
            cliente_email: userData.email,
            cliente_telefono: userData.telefono,
            codigo_seguimiento: codigoSeguimiento,
            direccion: address,
            referencias: references,
            pago: payment,
            total: totalFinal,
            productos: cart,
            estado: "pendiente",
            coords: userCoords || "",
            fecha: serverTimestamp()
        });
        
        const numeroAdmin = "529613267670";
        const mensaje = `🆕 PEDIDO #${docRef.id}\n👤 ${name}\n📱 ${userData.telefono}\n💰 $${totalFinal}\n🔍 Código: ${codigoSeguimiento}`;
        window.open(`https://wa.me/${numeroAdmin}?text=${encodeURIComponent(mensaje)}`, '_blank');
        
        mostrarToast(`✅ Pedido enviado! Tu código: ${codigoSeguimiento}`);
        alert(`¡Pedido confirmado! Guarda este código para seguimiento:\n🔍 ${codigoSeguimiento}`);
        
        cart = [];
        localStorage.removeItem("cart");
        updateTotal();
        closeModal();
        
    } catch(error) {
        console.error("❌ ERROR:", error);
        alert("Error: " + error.message);
    }
    
    btn.disabled = false;
    btn.innerText = "🚀 Confirmar Pedido";
}

// ===== TUS FUNCIONES ORIGINALES (MAPA, CARRITO, ETC.) =====
function openModal() {
    if (!userData) {
        mostrarToast("👤 Regístrate para continuar");
        setTimeout(mostrarRegistroCliente, 1000);
        return;
    }
    
    renderCart();
    if (cart.length === 0) { alert("El carrito está vacío"); return; }
    
    document.getElementById("modal").style.display = "flex";
    document.getElementById("cartBox").style.display = "none";
    document.getElementById("mainHeader").style.display = "none";
    
    setTimeout(() => {
        if (!map) initMap();
        else map.invalidateSize();
    }, 300);
}

function closeModal() {
    document.getElementById("modal").style.display = "none";
    document.getElementById("cartBox").style.display = "flex";
    document.getElementById("mainHeader").style.display = "flex";
}

function getLocation() {
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
            async function(position) {
                const lat = position.coords.latitude;
                const lng = position.coords.longitude;
                userCoords = lat + "," + lng;
                calcularEnvio(lat, lng);
                updateTotal();

                if (map) {
                    map.setView([lat, lng], 16);
                    if (marker) map.removeLayer(marker);
                    marker = L.marker([lat, lng]).addTo(map);
                }

                document.getElementById("address").value = `Ubicación GPS: ${lat}, ${lng}`;

                try {
                    const response = await fetch(`https://nominatim.openstreetmap.org/reverse?format=json&lat=${lat}&lon=${lng}`);
                    const data = await response.json();
                    if (data && data.display_name) {
                        document.getElementById("address").value = data.display_name;
                    }
                } catch (error) {
                    console.log("No se pudo obtener dirección exacta");
                }

                mostrarToast("Ubicación agregada 📍");
            },
            function(error) {
                alert("Activa la ubicación en tu celular ❌");
            },
            { enableHighAccuracy: true, timeout: 10000, maximumAge: 0 }
        );
    } else {
        alert("Tu navegador no soporta ubicación");
    }
}

function calcularEnvio(lat, lng) {
    envio = 50;
    zonas.forEach(z => {
        const distancia = calcularDistancia(lat, lng, z.lat, z.lng);
        if (distancia <= z.radio) envio = z.costo;
    });
    updateTotal();
}

function calculateChange() {
    const cash = parseFloat(document.getElementById("cash").value) || 0;
    const subtotalText = document.getElementById("subtotalText");
    const envioText = document.getElementById("envioText");
    const totalText = document.getElementById("totalText");
    const changeText = document.getElementById("changeText");

    subtotalText.innerText = `Subtotal: $${total}`;
    envioText.innerText = `Envío: $${envio}`;
    totalText.innerText = `Total: $${totalFinal}`;

    if (cash === 0) {
        changeText.innerText = "";
        return;
    }

    if (cash >= totalFinal) {
        const cambio = cash - totalFinal;
        changeText.innerText = `Cambio: $${cambio}`;
        changeText.style.color = "green";
    } else {
        const falta = totalFinal - cash;
        changeText.innerText = `Faltan: $${falta}`;
        changeText.style.color = "red";
    }
}

function initMap() {
    map = L.map('map').setView([16.75, -93.12], 13);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; OpenStreetMap'
    }).addTo(map);
    
    map.on('click', function(e) {
        const lat = e.latlng.lat;
        const lng = e.latlng.lng;
        userCoords = lat + "," + lng;
        calcularEnvio(lat, lng);
        updateTotal();

        if (marker) map.removeLayer(marker);
        marker = L.marker([lat, lng]).addTo(map);
        document.getElementById("address").value = `Ubicación seleccionada: ${lat}, ${lng}`;
    });
}

// ===== SEGUIMIENTO MEJORADO (TUS FUNCIONES + NUEVAS) =====
async function iniciarMapaSeguimiento(){
    const pedidoId = urlParams.get('pedido');
    
    if (!pedidoId) {
        document.getElementById("seguimientoView").innerHTML = "<h2 style='text-align:center; padding:50px;'>❌ Error: No se encontró el pedido</h2>}"
        return;
    }
    
    try {
        const docRef = doc(db, "pedidos", pedidoId);
        const docSnap = await getDoc(docRef);
        
        if (!docSnap.exists()) {
            document.getElementById("seguimientoView").innerHTML = "<h2 style='text-align:center; padding:50px;'>❌ Pedido no encontrado</h2>";
            return;
        }
        
        const pedido = docSnap.data();
        currentPedidoId = pedidoId;
        
        const centro = [16.75, -93.12];
        mapSeguimiento = L.map('mapSeguimiento').setView(centro, 13);
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(mapSeguimiento);
        
        document.getElementById("estadoPedido").textContent = `Pedido de ${pedido.cliente}`;
        document.getElementById("detalleRepartidor").textContent = pedido.cliente;
        document.getElementById("telRepartidor").textContent = pedido.cliente_telefono || "+52 961 123 4567";
        
        escucharPedidoActual(pedidoId);
        
    } catch(error) {
        console.error("Error:", error);
    }

}

function escucharPedidoActual(pedidoId) {
    const docRef = doc(db, "pedidos", pedidoId);
    onSnapshot(docRef, (docSnap) => {
        if (docSnap.exists()) {
            const pedido = docSnap.data();
            actualizarEstadoUI(pedido.estado || "pendiente");
        }
    });
}

function actualizarEstadoUI(estado) {
    const estadoTexto = document.getElementById("estadoPedido");
    const barra = document.getElementById("progresoBarra");

    if (!estadoTexto || !barra) return;

    if (estado === "pendiente") {
        estadoTexto.innerText = "🕐 Pendiente";
        barra.style.width = "20%";
    } else if (estado === "preparando") {
        estadoTexto.innerText = "👨‍🍳 Preparando";
        barra.style.width = "50%";
    } else if (estado === "en camino") {
        estadoTexto.innerText = "🚚 En camino";
        barra.style.width = "80%";
    } else if (estado === "entregado") {
        estadoTexto.innerText = "✅ Entregado";
        barra.style.width = "100%";
    }
}

// ===== UTILIDADES (TUS FUNCIONES ORIGINALES) =====
function calcularDistancia(lat1, lon1, lat2, lon2) {
    const R = 6371;
    const dLat = (lat2 - lat1) * Math.PI/180;
    const dLon = (lon2 - lon1) * Math.PI/180;
    const a = Math.sin(dLat/2) * Math.sin(dLat/2) +
        Math.cos(lat1 * Math.PI/180) * Math.cos(lat2 * Math.PI/180) *
        Math.sin(dLon/2) * Math.sin(dLon/2);
    return R * (2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a)));
}

function mostrarToast(mensaje) {
    const toast = document.getElementById("toast");
    toast.innerText = mensaje;
    toast.classList.add("show");
    setTimeout(() => toast.classList.remove("show"), 2000);
}

function hablar(texto) {
    speechSynthesis.cancel();
    const mensaje = new SpeechSynthesisUtterance(texto);
    mensaje.lang = "es-MX";
    mensaje.rate = 1.2;
    mensaje.pitch = 1.3;

    const voces = speechSynthesis.getVoices();
    const vozFemenina = voces.find(v =>
        v.name.toLowerCase().includes("female") ||
        v.name.toLowerCase().includes("mujer") ||
        v.name.toLowerCase().includes("paulina") ||
        v.name.toLowerCase().includes("sofia") ||
        v.name.toLowerCase().includes("maria") ||
        v.lang.includes("es")
    );

    if (vozFemenina) mensaje.voice = vozFemenina;
    speechSynthesis.speak(mensaje);
}

function updateCartCount() {
    const count = cart.reduce((acc, item) => acc + item.qty, 0);
    document.getElementById("cartCount").innerText = count;
}

function flyToCart(imgElement) {
    const cart = document.getElementById("cartBox");
    const flyingImg = imgElement.cloneNode(true);
    flyingImg.classList.add("fly-img");

    const rect = imgElement.getBoundingClientRect();
    flyingImg.style.top = rect.top + "px";
    flyingImg.style.left = rect.left + "px";
    document.body.appendChild(flyingImg);

    const cartRect = cart.getBoundingClientRect();
    setTimeout(() => {
        flyingImg.style.top = cartRect.top + "px";
        flyingImg.style.left = cartRect.left + "px";
        flyingImg.style.width = "20px";
        flyingImg.style.height = "20px";
        flyingImg.style.opacity = "0.5";
    }, 10);

    setTimeout(() => {
        cart.classList.add("animate");
        setTimeout(() => cart.classList.remove("animate"), 300);
        flyingImg.remove();
    }, 800);
}

// ===== CARRUSEL Y SCROLL (TUS FUNCIONES) =====
let currentIndex = 0;
const track = document.getElementById("carouselTrack");
const slides = document.querySelectorAll(".slide");
const dotsContainer = document.getElementById("dots");

slides.forEach((_, i) => {
    const dot = document.createElement("span");
    dot.onclick = () => goToSlide(i);
    dotsContainer.appendChild(dot);
});

const dots = document.querySelectorAll(".dots span");

function updateCarousel() {
    track.style.transform = `translateX(-${currentIndex * 100}%)`;
    dots.forEach(dot => dot.classList.remove("active"));
    dots[currentIndex].classList.add("active");
}

function nextSlide() {
    currentIndex = (currentIndex + 1) % slides.length;
    updateCarousel();
}

function prevSlide() {
    currentIndex = (currentIndex - 1 + slides.length) % slides.length;
    updateCarousel();
}

function goToSlide(index) {
    currentIndex = index;
    updateCarousel();
}

setInterval(nextSlide, 4000);
updateCarousel();

let lastScroll = 0;
const topUI = document.getElementById("topUI");
window.addEventListener("scroll", () => {
    const currentScroll = window.pageYOffset;
    if (currentScroll > lastScroll && currentScroll > 80) {
        topUI.classList.add("hide");
    } else {
        topUI.classList.remove("hide");
    }
    lastScroll = currentScroll;
});

// ===== INICIALIZACIÓN COMPLETA =====
document.addEventListener('DOMContentLoaded', function() {
    // ✅ VERIFICAR USUARIO REGISTRADO
    if (userData) {
        mostrarToast(`👋 Bienvenido ${userData.nombre}`);
        document.getElementById("firebaseStatus").textContent = `👤 ${userData.nombre}`;
    }
    
    updateTotal();
    updateCartCount();
    renderProducts();
    
    // 🔥 MODO CLIENTE - MOSTRAR MENSAJE
    if (modoCliente) {
        mostrarToast(`✅ Cliente ${modoCliente} - ¡Ya puedes pedir!`);
        document.querySelector("#topUI").style.display = "block";
        document.querySelector(".container").style.display = "block";
    }
    updateTotal();
    updateCartCount();
    renderProducts();
    
    // 🔥 MODOS DIFERENTES
    if (modoSeguimiento) {
        document.querySelector("#topUI").style.display = "none";
        document.querySelector(".container").style.display = "none";
        document.getElementById("cartBox").style.display = "none";
        document.getElementById("seguimientoView").style.display = "block";
        setTimeout(() => iniciarMapaSeguimiento(), 500);
    } 
    else if (modoRegistro) {
        mostrarRegistroCliente();
    }
    
    // Botón registro en modal
    const btnRegistro = document.createElement("button");
    btnRegistro.innerText = "👤 Registrarme";
    btnRegistro.className = "btn-secondary";
    btnRegistro.onclick = mostrarRegistroCliente;
    const modalActions = document.querySelector(".modal-actions");
    if (modalActions) modalActions.appendChild(btnRegistro);
    
    // Conectar botón WhatsApp
    const btnEnviar = document.getElementById("btnEnviar");
    if (btnEnviar) {
        btnEnviar.addEventListener("click", sendWhatsApp);
    }
});

// 🔥 TEST FUNCTIONS (OPCIONALES)
window.testGuardar = async () => {
    try {
        const docRef = await addDoc(collection(db, "pedidos"), {
            test: "Hola desde cliente",
            fecha: serverTimestamp()
        });
        console.log("✅ TEST OK:", docRef.id);
        alert("✅ Test OK - Revisa Firebase Console");
    } catch(e) {
        console.error("❌ Test falla:", e);
    }
};

console.log("✅ SCRIPT COMPLETO CARGADO - Registro + Seguimiento + Carrito");
</script>
 </body>
</html>
