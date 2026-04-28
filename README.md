# REPARTOS-RAPIDOS


<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🚚Food zoom</title>

<!-- 🔥 ICONOS MODERNOS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/lucide-static@latest/dist/umd/lucide.js">
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
<link rel="stylesheet" href="https://unpkg.com/leaflet-routing-machine@latest/dist/leaflet-routing-machine.css"/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-routing-machine@latest/dist/leaflet-routing-machine.js"></script>

<style>
/* 🔥 CSS MODERNO - GRADIENTES + GLASSMORPHISM */
* { 
  margin:0; padding:0; box-sizing:border-box; 
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

:root {
  --primary: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --success: linear-gradient(135deg, #00c851, #00b894);
  --danger: linear-gradient(135deg, #ff416c, #ff4b2b);
  --warning: linear-gradient(135deg, #ffa726, #fb8c00);
  --info: linear-gradient(135deg, #00d4ff, #0099cc);
  --glass: rgba(255,255,255,0.1);
  --glass-hover: rgba(255,255,255,0.2);
  --shadow: 0 25px 50px -12px rgba(0,0,0,0.25);
  --shadow-hover: 0 35px 60px -12px rgba(0,0,0,0.35);
}

body { 
  height:100vh; background: 
  radial-gradient(ellipse at top, #1e3c72 0%, transparent 50%),
  radial-gradient(ellipse at bottom, #2a5298 0%, transparent 50%),
  linear-gradient(135deg, #0f0f23 0%, #1a1a2e 50%, #16213e 100%);
  color:#fff; overflow:hidden;
  backdrop-filter: blur(20px);
}

/* 🔥 SIDEBAR ANIMADO CON SCROLL */
#sidebar {
  width:400px; height:100vh;
  background: linear-gradient(180deg, rgba(26,26,46,0.98), rgba(15,15,35,0.98));
  backdrop-filter: blur(20px);
  padding:30px 25px;
  position:fixed; left:0; top:0;
  border-right: 2px solid transparent;
  background-clip: padding-box;
  box-shadow: var(--shadow);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 100;
  
  /* 🔥 SCROLL PRINCIPAL */
  overflow-y: auto;
  overflow-x: hidden;
}

#sidebar::-webkit-scrollbar {
  width: 6px;
}

#sidebar::-webkit-scrollbar-track {
  background: rgba(255,255,255,0.05);
  border-radius: 10px;
  margin: 10px 0;
}

#sidebar::-webkit-scrollbar-thumb {
  background: linear-gradient(135deg, #00d4ff, #0099cc);
  border-radius: 10px;
  border: 2px solid transparent;
  background-clip: content-box;
}

#sidebar::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(135deg, #0099cc, #00d4ff);
  box-shadow: 0 0 10px rgba(0,212,255,0.5);
}

#sidebar::before {
  content: '';
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  background: linear-gradient(135deg, #00d4ff, #0099cc);
  opacity: 0.08;
  z-index: -1;
}

/* 🔥 CONTENIDO PRINCIPAL */
#main-content {
  margin-left: 400px;
  height: 100vh;
  position: relative;
}

/* 🔥 STATUS PREMIUM */
#status {
  text-align:center; 
  padding:20px; 
  border-radius:25px; 
  font-weight:700; 
  margin-bottom:25px;
  backdrop-filter: blur(15px);
  border: 1px solid var(--glass);
  position: relative;
  overflow: hidden;
}

#status::before {
  content: ''; position: absolute; top:0; left:-100%; width:100%; height:100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
  transition: left 0.5s;
}

#status:hover::before { left: 100%; }

.online { 
  background: var(--success); 
  box-shadow: 0 0 30px rgba(0,200,81,0.4);
  animation: pulse-green 2s infinite;
}
@keyframes pulse-green {
  0%, 100% { box-shadow: 0 0 30px rgba(0,200,81,0.4); }
  50% { box-shadow: 0 0 50px rgba(0,200,81,0.7); }
}

.offline { 
  background: var(--danger); 
  box-shadow: 0 0 30px rgba(255,65,108,0.4);
}

/* 🔥 CONTENEDOR PEDIDOS CON SCROLL */
#ordersPanel {
  padding-bottom: 100px; /* espacio para botones fijos */
  min-height: 100vh;
}

/* 🔥 ORDENES - CARDS GLASS */
.order {
  background: var(--glass); 
  backdrop-filter: blur(15px);
  margin-bottom:20px; 
  padding:25px; 
  border-radius:20px; 
  border: 1px solid var(--glass-hover);
  border-left: 5px solid #00d4ff;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  max-height: 400px; /* límite por tarjeta */
  overflow-y: auto;
}

.order::-webkit-scrollbar {
  width: 4px;
}

.order::-webkit-scrollbar-track {
  background: rgba(255,255,255,0.05);
}

.order::-webkit-scrollbar-thumb {
  background: rgba(255,215,0,0.7);
  border-radius: 10px;
}

.order::before {
  content: ''; 
  position: absolute; 
  top: 0; left: 0; 
  right: 0; 
  height: 4px; 
  background: var(--info);
}

.order:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-hover);
  border-color: rgba(0,212,255,0.3);
}

/* 🔥 BOTONES PREMIUM */
.order button {
  width:100%; margin:8px 0; padding:14px 20px; 
  border:none; border-radius:16px; 
  cursor:pointer; font-weight:600;
  font-size: 14px; letter-spacing: 0.5px;
  backdrop-filter: blur(10px);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative; overflow: hidden;
}

.order button::before {
  content: ''; position: absolute; top:0; left:-100%; width:100%; height:100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
  transition: left 0.5s;
}

.order button:hover::before { left: 100%; }

.accept { 
  background: var(--success); 
  box-shadow: 0 8px 25px rgba(0,200,81,0.4);
}
.accept:hover { transform: translateY(-2px); box-shadow: 0 12px 35px rgba(0,200,81,0.6); }

.route { 
  background: var(--info); 
  box-shadow: 0 8px 25px rgba(0,212,255,0.4);
}
.route:hover { transform: translateY(-2px); box-shadow: 0 12px 35px rgba(0,212,255,0.6); }

.cancel { 
  background: var(--danger); 
  box-shadow: 0 8px 25px rgba(255,65,108,0.4);
}
.cancel:hover { transform: translateY(-2px); box-shadow: 0 12px 35px rgba(255,65,108,0.6); }

/* 🔥 TABS FLOTANTES */
.tab-container {
  position:fixed; top:20px; left:50%; 
  transform: translateX(-50%);
  z-index:1000; display: flex; gap: 12px;
  backdrop-filter: blur(20px); padding: 12px 24px;
  background: var(--glass); border-radius: 25px;
  border: 1px solid var(--glass-hover);
  box-shadow: var(--shadow);
}

.tab-btn {
  background: var(--glass); color:#fff; 
  border:none; padding:14px 24px; 
  border-radius:20px; cursor:pointer; 
  font-weight:600; font-size: 14px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  backdrop-filter: blur(15px);
  border: 1px solid transparent;
}

.tab-btn:hover {
  background: var(--glass-hover);
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
}

.tab-btn.active { 
  background: var(--info); 
  box-shadow: 0 10px 30px rgba(0,212,255,0.4);
  border-color: rgba(0,212,255,0.3);
}

/* 🔥 PANEL REPARTIDORES CON SCROLL */
#repartidoresPanel {
  position:absolute; top:0; left:0; 
  width:100%; height:100vh; 
  background: rgba(15,15,35,0.98);
  backdrop-filter: blur(20px);
  padding:90px 30px 30px; 
  display:none; 
  overflow-y: auto;
  overflow-x: hidden;
  box-shadow: var(--shadow);
}

#repartidoresPanel::-webkit-scrollbar {
  width: 6px;
}

#repartidoresPanel::-webkit-scrollbar-track {
  background: rgba(255,255,255,0.05);
}

#repartidoresPanel::-webkit-scrollbar-thumb {
  background: linear-gradient(135deg, #00c851, #00b894);
  border-radius: 10px;
}

#repartidoresPanel h2 {
  color:#00d4ff; font-size: 28px; 
  font-weight: 800; margin-bottom: 30px;
  text-align: center;
  background: linear-gradient(135deg, #00d4ff, #0099cc);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* 🔥 FORM REPARTIDOR */
.rep-form {
  background: var(--glass); 
  backdrop-filter: blur(15px);
  padding:25px; margin-bottom:30px; 
  border-radius:20px; border: 1px solid var(--glass-hover);
}

.rep-form input {
  width:100%; padding:16px 20px; 
  margin-bottom:16px; border:none; 
  border-radius:16px; font-size:16px;
  background: rgba(255,255,255,0.15);
  backdrop-filter: blur(10px);
  color:#fff; transition: all 0.3s ease;
}

.rep-form input::placeholder { color: rgba(255,255,255,0.7); }
.rep-form input:focus {
  outline: none; 
  background: rgba(255,255,255,0.25);
  box-shadow: 0 0 0 3px rgba(0,212,255,0.3);
  transform: scale(1.02);
}

/* 🔥 BOTÓN REGISTRAR */
.btn-registrar {
  width:100%; padding:18px; background: var(--success);
  border:none; border-radius:16px; color:#fff;
  font-weight:700; font-size:16px; cursor:pointer;
  box-shadow: 0 10px 30px rgba(0,200,81,0.4);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-registrar:hover {
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 15px 40px rgba(0,200,81,0.6);
}

/* 🔥 REPARTIDORES LIST CON SCROLL */
.repartidor {
  background: var(--glass); 
  backdrop-filter: blur(15px);
  padding:25px; margin-bottom:20px; 
  border-radius:20px; 
  border-left:5px solid #00c851;
  border: 1px solid var(--glass-hover);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  max-height: 200px;
  overflow-y: auto;
}

.repartidor::-webkit-scrollbar {
  width: 3px;
}

.repartidor::-webkit-scrollbar-thumb {
  background: rgba(0,230,118,0.8);
}

.repartidor:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-hover);
  border-left-width: 6px;
}

.estado {
  padding:8px 16px; border-radius:20px; 
  font-weight:600; font-size:13px;
  display: inline-block; margin-top:8px;
}

.estado.libre { 
  background: rgba(0,230,118,0.2); 
  color:#00e676; 
  box-shadow: 0 4px 15px rgba(0,230,118,0.3);
}
.estado.ocupado { 
  background: rgba(255,107,129,0.2); 
  color:#ff6b81; 
  box-shadow: 0 4px 15px rgba(255,107,129,0.3);
}
.estado.entregando { 
  background: rgba(0,212,255,0.2); 
  color:#00d4ff; 
  box-shadow: 0 4px 15px rgba(0,212,255,0.3);
  animation: pulse 2s infinite;
}

/* 🔥 MAPA FULLSCREEN */
#map { 
  height:100vh; width:100%;
  border-radius: 0;
  filter: drop-shadow(0 0 50px rgba(0,0,0,0.5));
}

/* 🔥 RESPONSIVE */
@media (max-width: 768px) {
  #sidebar { 
    width: 100%; 
    transform: translateX(0);
  }
  #main-content { 
    margin-left: 0; 
  }
  .tab-container { 
    position: relative; left: 0; 
    transform: none; top: 10px;
    flex-wrap: wrap; justify-content: center;
    padding: 10px;
  }
  #repartidoresPanel { 
    padding: 120px 20px 20px; 
  }
  #sidebar {
    position: fixed;
    z-index: 999;
  }
}

/* 🔥 ANIMACIONES */
@keyframes pulse { 
  0%,100%{transform:scale(1);} 
  50%{transform:scale(1.05);} 
}

/* 🔥 LOADING */
.loading {
  display: inline-block; width: 20px; height: 20px;
  border: 3px solid rgba(255,255,255,0.3);
  border-radius: 50%; border-top-color: #fff;
  animation: spin 1s ease-in-out infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }

/* 🔥 SCROLLBAR GLOBAL CUSTOM */
*::-webkit-scrollbar { width: 6px; }
*::-webkit-scrollbar-track { 
  background: rgba(255,255,255,0.05); 
  border-radius: 10px; 
}
*::-webkit-scrollbar-thumb { 
  background: linear-gradient(135deg, #00d4ff, #0099cc);
  border-radius: 10px; 
  border: 1px solid rgba(255,255,255,0.1);
}
*::-webkit-scrollbar-thumb:hover { 
  background: linear-gradient(135deg, #0099cc, #00d4ff);
}

/* 🔥 SCROLL ESPECÍFICO PRODUCTOS */
.order .productos-scroll,
.order div[style*="overflow-y:auto"] {
  max-height: 150px;
  overflow-y: auto;
  padding-right: 5px;
}

.order .productos-scroll::-webkit-scrollbar,
.order div[style*="overflow-y:auto"]::-webkit-scrollbar {
  width: 4px;
}

.order .productos-scroll::-webkit-scrollbar-thumb,
.order div[style*="overflow-y:auto"]::-webkit-scrollbar-thumb {
  background: rgba(255,215,0,0.8);
  border-radius: 10px;
}

.order .producto-item {
  background: rgba(255,255,255,0.05);
  padding: 12px;
  margin: 6px 0;
  border-radius: 12px;
  border-left: 3px solid #ffd700;
  transition: all 0.2s ease;
}

.order .producto-item:hover {
  background: rgba(255,255,255,0.1);
  transform: translateX(5px);
}
.order.minimizado {
  max-height: 80px;
  overflow: hidden;
  opacity: 0.7;
  transform: scale(0.95);
}
</style>

</head>

<body>
  <div id="modalPedidos" style="
  position:fixed;
  top:0; left:0;
  width:100%; height:100%;
  background:rgba(0,0,0,0.7);
  display:none;
  align-items:center;
  justify-content:center;
  z-index:9999;
">
  <div style="
    background:#1a1a2e;
    padding:25px;
    border-radius:20px;
    width:90%;
    max-width:400px;
    max-height:80vh;
    overflow-y:auto;
  ">
    <h3 style="text-align:center; margin-bottom:15px;">📦 Seleccionar Pedido</h3>
    <div id="listaPedidosModal"></div>
    <button onclick="cerrarModal()" style="
      width:100%;
      margin-top:15px;
      padding:12px;
      border:none;
      border-radius:12px;
      background:#ff416c;
      color:white;
      font-weight:600;
    ">Cerrar</button>
  </div>
</div>

<!-- 🔥 funcion agregada  -->
<div id="panelPreparando" style="
  position:absolute;
  right:0;
  top:0;
  width:350px;
  height:100vh;
  overflow-y:auto;
  padding:20px;
  background:rgba(0,0,0,0.3);
  backdrop-filter:blur(15px);
  border-left:2px solid rgba(255,255,255,0.1);
  z-index:200;
">
  <h3 style="text-align:center; margin-bottom:15px;">👨‍🍳 Preparando</h3>
</div>
<!-- 🔥 TABS FLOTANTES -->
<div class="tab-container">
  <button onclick="mostrar('pedidos', this)" class="tab-btn active" id="tabPedidos">
    📦 <span id="countPedidos">0</span> Pedidos
  </button>
  <button onclick="mostrar('repartidores', this)" class="tab-btn" id="tabRepartidores">
    🛵 <span id="countRepartidores">0</span> Repartidores
  </button>
</div>

<!-- 🔥 SIDEBAR PRINCIPAL -->
<div id="sidebar">
  <!-- PANEL PEDIDOS -->
  <div id="ordersPanel">
    <div id="status" class="offline">🔴 Conectando...</div>
    <!-- Las tarjetas .order van aquí -->
  </div>
  
  <!-- PANEL REPARTIDORES -->
  <div id="repartidoresPanel">
    <h2>🛵 Repartidores</h2>
    <div class="rep-form">
  <div class="rep-form">
    <input id="repNombre" placeholder="👤 Nombre del repartidor">
    <input id="repTelefono" placeholder="📱 Teléfono (10 dígitos)">
    <button class="btn-registrar" onclick="registrarRepartidor()">
      ➕ Registrar Repartidor
    </button>
  </div>

  <input type="hidden" id="repId">
  <div id="listaRepartidores"></div>
</div>


<!-- 🔥 MAPA PRINCIPAL -->
<div id="map"></div>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
import { 
  getFirestore, collection, onSnapshot, doc, updateDoc, deleteDoc,
  serverTimestamp, addDoc, query, where, orderBy
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyAAqy5cTbBCO9NCmVBGiYKdu1uZDQAWTpY", // 🔥 CONFIG REAL
  authDomain: "vok-chinese-2024.firebaseapp.com",
  projectId: "vok-chinese-2024",
  storageBucket: "vok-chinese-2024.firebasestorage.app",
  messagingSenderId: "1034716143333",
  appId: "1:1034716143333:web:04f978334bf8933e51be0c"
};
const panelPreparando = document.getElementById("panelPreparando");
const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
// 🔥 MAPA MEJORADO
const map = L.map('map').setView([16.75, -93.12], 12);
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  attribution: '© OpenStreetMap | Didi Food Admin PRO'
}).addTo(map);

// Custom icons
const clienteIcon = L.divIcon({
  className: 'custom-div-icon',
  html: '<div style="background:linear-gradient(135deg,#ff6b6b,#ee5a52);width:45px;height:45px;border-radius:50%;border:4px solid white;box-shadow:0 6px 20px rgba(255,107,107,0.4);display:flex;align-items:center;justify-content:center;font-size:20px;color:white;font-weight:bold;">📍</div>',
  iconSize: [45, 45], iconAnchor: [22, 22]
});

const repartidorIcon = L.divIcon({
  className: 'custom-div-icon',
  html: '<div style="background:linear-gradient(135deg,#4CAF50,#45a049);width:50px;height:50px;border-radius:50%;border:5px solid white;box-shadow:0 8px 25px rgba(76,175,80,0.5);display:flex;align-items:center;justify-content:center;font-size:22px;color:white;font-weight:bold;animation:pulse 2s infinite;">🛵</div>',
  iconSize: [50, 50], iconAnchor:
    [25, 25]
});

let markers = {};
let repartidorMarkers = {};
let rutas = {};

// 🔥 ELEMENTOS DOM
const ordersPanel = document.getElementById("ordersPanel");
const repartidoresPanel = document.getElementById("repartidoresPanel");
const orders = document.getElementById("ordersPanel");
const listaRepartidores = document.getElementById("listaRepartidores");
const statusDiv = document.getElementById("status");
const countPedidos = document.getElementById("countPedidos");
const countRepartidores = document.getElementById("countRepartidores");

// 🔥 PANEL NAVEGACIÓN MEJORADA
window.mostrar = function(panel, el = null) {
  ordersPanel.style.display = panel === 'pedidos' ? 'block' : 'none';
  repartidoresPanel.style.display = panel === 'repartidores' ? 'block' : 'none';

  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  if (el) el.classList.add('active');
  
  // 🔥 Auto-fit map cuando cambia panel
  setTimeout(() => map.invalidateSize(), 300);
};

// 🔥 NOTIFICACIONES PREMIUM
function mostrarMensaje(texto, color = "#00d4ff", icon = "✅") {
  const msg = document.createElement("div");
  msg.innerHTML = `${icon} ${texto}`;
  msg.style.cssText = `
    position:fixed; bottom:30px; left:50%; transform:translateX(-50%);
    padding:20px 30px; border-radius:25px; font-weight:700; font-size:16px;
    z-index:9999; backdrop-filter:blur(20px); border:1px solid rgba(255,255,255,0.2);
    background:${color}; box-shadow:var(--shadow);
    animation: slideUp 0.4s cubic-bezier(0.4,0,0.2,1);
  `;
  document.body.appendChild(msg);
  
  setTimeout(() => {
    msg.style.animation = 'slideDown 0.4s cubic-bezier(0.4,0,0.2,1)';
    setTimeout(() => msg.remove(), 400);
  }, 3000);
}

// 🔥 ANIMACIONES CSS
const style = document.createElement('style');
style.textContent = `
  @keyframes slideUp { from { transform: translateX(-50%) translateY(100px); opacity: 0; } to { transform: translateX(-50%) translateY(0); opacity: 1; } }
  @keyframes slideDown { from { transform: translateX(-50%) translateY(0); opacity: 1; } to { transform: translateX(-50%) translateY(100px); opacity: 0; } }
  @keyframes pulse { 0%,100%{transform:scale(1);} 50%{transform:scale(1.05);} }
`;
document.head.appendChild(style);

// 🔥 RENDER PEDIDO MEJORADO
// 🔥 RENDER PEDIDO CON PRODUCTOS DETALLADOS
function renderPedido(p,id){
  let contadorHTML = "";

if(p.estado === "en camino" && p.fechaUpdate){
  contadorHTML = `<div id="timer-${id}" style="
    margin-top:10px;
    text-align:center;
    font-weight:700;
    color:#00d4ff;
  ">⏱️ 0s</div>`;
}
 const div = document.createElement("div");
 div.className = "order";
 div.setAttribute("data-estado", p.estado || "pendiente");
 div.setAttribute("data-id", id);

const esPreparando = 
  p.estado === "preparando" || 
  p.estado === "listo" || 
  p.estado === "en camino";

  // 🔥 PRODUCTOS DETALLADOS
  let productosHTML = '<p style="color:#ff9800; padding:15px; text-align:center;">📋 Sin productos</p>';
  
  if(p.productos && p.productos.length > 0){
    productosHTML = p.productos.map(item => `
      <div style="background:rgba(255,255,255,0.05); padding:12px; margin:6px 0; border-radius:12px; border-left:3px solid #ffd700; transition:all 0.2s;">
        <div style="display:flex; justify-content:space-between;">
          <span style="font-weight:600; max-width:60%;">${item.name}</span>
          <span style="color:#ffd700; font-weight:700;">x${item.qty}</span>
        </div>
        ${item.subtotal ? `<div style="font-size:12px; color:rgba(255,255,255,0.7);">$${item.subtotal}</div>` : ''}
      </div>
    `).join('');
  }

  const tiempo = p.fechaUpdate?.toDate ? 
    p.fechaUpdate.toDate().toLocaleTimeString('es-MX') : 'Ahora';
let nombreRepartidor = "Sin asignar";

if(p.repartidorId && repartidoresData[p.repartidorId]){
  nombreRepartidor = repartidoresData[p.repartidorId].nombre;
}
div.innerHTML = `
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;">
    <b style="font-size:18px;">${p.cliente}</b>
    <span style="background:rgba(255,215,0,0.2);color:#ffd700;padding:5px 12px;border-radius:15px;font-size:12px;font-weight:600;">
      ${p.estado || "pendiente"}
    </span>
  </div>

  <p style="color:rgba(255,255,255,0.8);margin:5px 0;font-size:14px;">
    📍 ${p.direccion}
  </p>

  <!-- 🔥 TELEFONO -->
  ${p.telefono ? `
    <p style="color:#00e676;font-size:14px;margin:5px 0;">
      📱 ${p.telefono}
    </p>

    <a href="tel:${p.telefono}" style="
      display:inline-block;
      margin-bottom:10px;
      padding:8px 12px;
      border-radius:10px;
      background:#22c55e;
      color:white;
      text-decoration:none;
      font-size:13px;
      font-weight:600;
    ">
      📞 Llamar
    </a>
  ` : ''}

  ${p.referencias ? `
    <p style="color:#00d4ff;background:rgba(0,212,255,0.1);padding:8px;border-radius:8px;margin:8px 0;font-size:13px;">
      📝 ${p.referencias}
    </p>` : ''}
  
  <div style="margin:15px 0;padding:15px;background:rgba(255,215,0,0.08);border-radius:12px;border-left:4px solid #ffd700;">
    <div style="font-size:16px;font-weight:700;color:#ffd700;margin-bottom:10px;">
      🛒 Productos (${p.productos?.length || 0})
    </div>
    <div style="max-height:140px;overflow-y:auto;padding-right:5px;">
      ${productosHTML}
    </div>
  </div>
  
  <p style="color:#ffd700;font-size:20px;font-weight:800;margin:12px 0 8px 0;text-align:center;">
    💰 Total: $${p.total}
    <br>🛵 Repartidor: <b style="color:#00e676;">${nombreRepartidor}</b>
  </p>

  <p style="color:rgba(255,255,255,0.6);font-size:12px;text-align:center;">
    🕒 ${tiempo} | 💳 ${p.pago || 'Efectivo'}
  </p>

  ${contadorHTML}

  <div style="display:flex;gap:8px;margin-top:20px;">
    <button class="accept" style="flex:1;padding:12px;">
      ${esPreparando ? "🍽️ Pedido listo" : "✅ Aceptar"}
    </button>
    <button class="route" style="flex:1;padding:12px;">🚚 En camino</button>
    <button class="cancel" style="flex:1;padding:12px;">❌ Cancelar</button>
  </div>
`;
  // ✅ EVENTOS DINÁMICOS
 const btnAccept = div.querySelector(".accept");

if(p.estado === "pendiente"){
  btnAccept.innerText = "✅ Aceptar";
  btnAccept.onclick = () => aceptar(id);

}else if(p.estado === "preparando"){
  btnAccept.innerText = "🍽️ Pedido listo";
  btnAccept.onclick = () => pedidoListo(id);

}else if(p.estado === "listo"){
  btnAccept.innerText = "🛵 Asignar repartidor";
  btnAccept.onclick = () => asignarDesdePedido(id);

}else{
  btnAccept.style.display = "none"; // 🔥 desaparece
}
const btnRoute = div.querySelector(".route");

if(p.estado === "en camino"){
  btnRoute.style.display = "none";
}else{
  btnRoute.onclick = () => enCamino(id);
}
  div.querySelector(".cancel").onclick=()=>cancelar(id);

  // 🔥 UBICACIÓN DINÁMICA DEL CARD
  if(esPreparando){
    panelPreparando.appendChild(div); // 👉 lado derecho
  }else{
    ordersPanel.appendChild(div); // 👉 lado izquierdo
  }

  // ✅ MAPA (NO TOCAR)
  if(p.coords){
    const [lat,lng]=p.coords.split(",");
    markers[id]=L.marker([parseFloat(lat),parseFloat(lng)]).addTo(map)
      .bindPopup(`${p.cliente}<br>$${p.total}<br>${p.productos?.length || 0} productos`);
  }
  if(p.estado === "en camino" && p.fechaUpdate){
  iniciarContador(id, p.fechaUpdate);
}
}
// 🔥 FUNCIONES PEDIDOS MEJORADAS
async function aceptar(id) {
  await updateDoc(doc(db, "pedidos", id), {
    estado: "preparando",
    fechaUpdate: serverTimestamp()
  });

  const btn = event.target;
  btn.innerHTML = '<span class="loading"></span>';
  btn.disabled = true;

  try {
    await updateDoc(doc(db, "pedidos", id), {
      estado: "preparando",
      fechaUpdate: serverTimestamp(),
      asignado: true
    });

    mostrarMensaje("👨‍🍳 Pedido en preparación", "#00c851");
  } catch (error) {
    mostrarMensaje("❌ Error al aceptar", "#ff416c");
  } finally {
    btn.innerHTML = "✅ Aceptar";
    btn.disabled = false;
  }
}


async function enCamino(id) {
  const btn = event.target;
  btn.innerHTML = '<span class="loading"></span> Actualizando...';
  btn.disabled = true;

  try {
    await updateDoc(doc(db, "pedidos", id), {
      estado: "en camino",
      fechaUpdate: serverTimestamp()
    });
// 🔥 OBTENER DATOS DEL PEDIDO
const pedidoDoc = await getDoc(doc(db, "pedidos", id));
const pedido = pedidoDoc.data();

if(pedido.repartidorId){
  seguirRepartidorTiempoReal(pedido.repartidorId, pedido);
}
    // 🔥 MINIMIZAR VISUAL
    const card = document.querySelector(`.order[data-id="${id}"]`);
    if(card){
      card.classList.add("minimizado");
    }

    mostrarMensaje("🚚 Pedido en camino", "#00d4ff", "🛵");

  } catch (error) {
    mostrarMensaje("❌ Error al actualizar", "#ff416c", "⚠️");
  } finally {
    btn.innerHTML = "🚚 En camino";
    btn.disabled = false;
  }
}

function calcularDistancia(lat1, lng1, lat2, lng2) {
  const R = 6371;
  const dLat = (lat2-lat1) * Math.PI/180;
  const dLng = (lng2-lng1) * Math.PI/180;

  const a =
    Math.sin(dLat/2) * Math.sin(dLat/2) +
    Math.cos(lat1*Math.PI/180) * Math.cos(lat2*Math.PI/180) *
    Math.sin(dLng/2) * Math.sin(dLng/2);

  const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
  return R * c; // km
}
async function cancelar(id) {
  if (!confirm("¿Confirmar cancelación del pedido?")) return;
  
  try {
    await deleteDoc(doc(db, "pedidos", id));
    mostrarMensaje("❌ Pedido cancelado", "#ff416c", "🗑️");
  } catch (error) {
    mostrarMensaje("❌ Error al cancelar", "#ff416c", "⚠️");
  }
}

// 🔥 LISTENER PEDIDOS REALTIME (ORDENADOS POR FECHA)
const pedidosQuery = query(
  collection(db, "pedidos"), 
  orderBy("fecha", "desc")
);

onSnapshot(pedidosQuery, (snap) => {
  ordersPanel.innerHTML = '';
  ordersPanel.appendChild(statusDiv);
panelPreparando.innerHTML = '<h3 style="text-align:center; margin-bottom:15px;">👨‍🍳 Preparando</h3>';
  const count = snap.size;
  countPedidos.textContent = count;
  statusDiv.className = count > 0 ? "online" : "offline";
  statusDiv.innerHTML = count > 0 
    ? `🟢 ${count} pedido${count > 1 ? 's' : ''} activo${count > 1 ? 's' : ''}`
    : "🟢 Conexión activa - Esperando pedidos";

  // 🔥 LIMPIAR MARCADORES
  Object.values(markers).forEach(m => map.removeLayer(m));
  markers = {};

  snap.forEach(d => renderPedido(d.data(), d.id));
  
  // 🔥 NOTIFICACIÓN NUEVO PEDIDO
  if (snap.docs.length > 0) {
    const ultimo = snap.docs[0].data();
    if (ultimo.estado === "pendiente") {
      mostrarMensaje(`🆕 Nuevo pedido de ${ultimo.cliente}`, "#ffa726", "🚨");
    }
  }
  Object.keys(repartidoresData).forEach(repId => {
  const rep = repartidoresData[repId];

  if(!rep.coords) return;

  const [repLat, repLng] = rep.coords.split(",");

  document.querySelectorAll('.order').forEach(async card => {
    const pedidoId = card.getAttribute("data-id");

    const pedidoDoc = await getDoc(doc(db, "pedidos", pedidoId));
    const pedido = pedidoDoc.data();

    if(!pedido || pedido.estado !== "en camino" || pedido.repartidorId !== repId) return;
    if(!pedido.coords) return;

    const [cliLat, cliLng] = pedido.coords.split(",");

    const distancia = calcularDistancia(
      parseFloat(repLat),
      parseFloat(repLng),
      parseFloat(cliLat),
      parseFloat(cliLng)
    );

    // 🔥 SI ESTÁ A MENOS DE 50 METROS
    if(distancia < 0.05){
      await marcarEntregado(pedidoId);
    }
  });
  const pedidosDerecha = snap.docs.filter(d => {
  const estado = d.data().estado;
  return estado === "preparando" || estado === "listo" || estado === "en camino";
});

if(pedidosDerecha.length === 0){
  panelPreparando.style.display = "none";
}else{
  panelPreparando.style.display = "block";
}
});
});

// 🔥 REGISTRAR REPARTIDOR MEJORADO
window.registrarRepartidor = async () => {
  const nombre = document.getElementById("repNombre").value.trim();
  const telefono = document.getElementById("repTelefono").value.trim();

  if (!nombre || !telefono) {
    mostrarMensaje("⚠️ Completa nombre y teléfono", "#ff416c");
    return;
  }

  if (telefono.length !== 10 || isNaN(telefono)) {
    mostrarMensaje("⚠️ Teléfono inválido (10 dígitos)", "#ff416c");
    return;
  }

  const btn = event.target;
  btn.innerHTML = '<span class="loading"></span> Registrando...';
  btn.disabled = true;

  try {
    const pos = await new Promise((resolve, reject) => {
      navigator.geolocation.getCurrentPosition(resolve, reject, {
        enableHighAccuracy: true,
        timeout: 10000,
        maximumAge: 0
      });
    });

    const coords = `${pos.coords.latitude},${pos.coords.longitude}`;
    const docRef = await addDoc(collection(db, "repartidores"), {
      nombre, telefono, estado: "libre", coords,
      fechaRegistro: serverTimestamp()
    });

    document.getElementById("repId").value = docRef.id;
    activarGPS(docRef.id);

    mostrarMensaje(`🛵 ${nombre} registrado correctamente`, "#00c851", "✅");
    
    document.getElementById("repNombre").value = "";
    document.getElementById("repTelefono").value = "";
  } catch (error) {
    mostrarMensaje("❌ Error de geolocalización. Activa GPS", "#ff416c", "📍");
  } finally {
    btn.innerHTML = "➕ Registrar Repartidor";
    btn.disabled = false;
  }
};

// 🔥 GPS EN TIEMPO REAL MEJORADO
function activarGPS(id) {
  const watchId = navigator.geolocation.watchPosition(
    async (pos) => {
      const coords = `${pos.coords.latitude},${pos.coords.longitude}`;
      try {
        await updateDoc(doc(db, "repartidores", id), {
          coords,
          ultimaActualizacion: serverTimestamp()
        });
      } catch (error) {
        console.error("Error GPS:", error);
      }
    },
    (error) => console.error("GPS Error:", error),
    {
      enableHighAccuracy: true,
      timeout: 5000,
      maximumAge: 10000
    }
  );

  // 🔥 Auto-limpiar si se detiene
  setTimeout(() => navigator.geolocation.clearWatch(watchId), 300000); // 5 min
}

// 🔥 RENDER REPARTIDOR MEJORADO
function renderRepartidor(r, id) {
  const div = document.createElement("div");
  div.className = "repartidor";
  
  const tiempo = r.ultimaActualizacion?.toDate ? 
    new Date(r.ultimaActualizacion.toDate()).toLocaleTimeString('es-MX') : 
    'Sin datos';

  div.innerHTML = `
    <div style="display:flex; justify-content:space-between; align-items:center;">
      <b style="font-size:18px;">${r.nombre}</b>
      <span class="estado ${r.estado || 'libre'}">${r.estado?.toUpperCase() || 'LIBRE'}</span>
    </div>
    <p style="color:rgba(255,255,255,0.8); margin:8px 0;">📱 ${r.telefono || 'Sin teléfono'}</p>
    <p style="color:rgba(255,255,255,0.6); font-size:13px;">🕒 Última actualización: ${tiempo}</p>
    <div style="margin-top:15px; padding-top:15px; border-top:1px solid rgba(255,255,255,0.1);">
      <div style="margin-top:15px; padding-top:15px; border-top:1px solid rgba(255,255,255,0.1);">
  
  <button onclick="abrirSelectorPedidos('${id}')" style="width:32%; padding:12px; background:var(--warning); color:white; border:none; border-radius:12px; font-weight:600; cursor:pointer;">
    📦 Asignar
  </button>

  <button onclick="cambiarEstado('${id}', 'ocupado')" style="width:32%; padding:12px; background:var(--danger); color:white; border:none; border-radius:12px; font-weight:600; cursor:pointer;">
    ❌ Ocupado
  </button>

  <button onclick="cambiarEstado('${id}', 'libre')" style="width:32%; padding:12px; background:var(--success); color:white; border:none; border-radius:12px; font-weight:600; cursor:pointer;">
    ✅ Libre
  </button>

</div>
  `;

  listaRepartidores.appendChild(div);
}

// 🔥 FUNCIONES REPARTIDORES
window.cambiarEstado = async (id, estado) => {
  try {
    await updateDoc(doc(db, "repartidores", id), { estado });
    mostrarMensaje(`Estado actualizado a ${estado}`, "#00d4ff");
  } catch (error) {
    mostrarMensaje("Error al actualizar estado", "#ff416c");
  }
};

let repartidoresData = {};
let repartidorSeleccionado = null;

window.abrirSelectorPedidos = (repId) => {
  repartidorSeleccionado = repId;

  const modal = document.getElementById("modalPedidos");
  const lista = document.getElementById("listaPedidosModal");

  lista.innerHTML = "";

  document.querySelectorAll('.order').forEach(card => {
    const estado = card.getAttribute("data-estado");

    if(estado !== "pendiente" && estado !== "listo") return;

    const id = card.getAttribute("data-id");
    const nombre = card.querySelector("b").innerText;

    const btn = document.createElement("button");
    btn.innerText = `📦 ${nombre}`;
    btn.style.cssText = `
      width:100%;
      margin:6px 0;
      padding:12px;
      border:none;
      border-radius:12px;
      background:#00d4ff;
      color:white;
      font-weight:600;
    `;

    btn.onclick = () => asignarPedidoSeleccionado(id);

    lista.appendChild(btn);
  });

  modal.style.display = "flex";
};

window.cerrarModal = () => {
  document.getElementById("modalPedidos").style.display = "none";
};
window.asignarPedidoSeleccionado = async (pedidoId) => {

  if(!repartidorSeleccionado) return;

  try{
    await updateDoc(doc(db,"pedidos",pedidoId),{
      repartidorId: repartidorSeleccionado,
      estado:"preparando"
    });

    await updateDoc(doc(db,"repartidores",repartidorSeleccionado),{
      estado:"ocupado"
    });

    mostrarMensaje("🛵 Pedido asignado correctamente", "#00c851");

    cerrarModal();

  }catch(e){
    mostrarMensaje("❌ Error al asignar", "#ff416c");
  }
};
window.asignarPedido = async (repartidorId) => {
  const pendientes = document.querySelectorAll('.order[data-estado="pendiente"]');

  if (pendientes.length === 0) {
    mostrarMensaje("No hay pedidos pendientes", "#ffa726");
    return;
  }

  const pedidoId = pendientes[0].getAttribute("data-id");

  try {
    await updateDoc(doc(db, "pedidos", pedidoId), {
      repartidorId: repartidorId,
      estado: "preparando"
    });

    await updateDoc(doc(db, "repartidores", repartidorId), {
      estado: "ocupado"
    });

    mostrarMensaje("📦 Pedido asignado al repartidor", "#00c851");
  } catch (error) {
    mostrarMensaje("❌ Error al asignar", "#ff416c");
  }
};
// 🔥 LISTENER REPARTIDORES REALTIME
onSnapshot(collection(db, "repartidores"), (snap) => {

  repartidoresData = {}; // 🔥 cache limpio

  listaRepartidores.innerHTML = `<h3 style="color:#00d4ff; margin-bottom:20px;">🟢 ${snap.size} repartidor${snap.size > 1 ? 'es' : ''} conectado${snap.size > 1 ? 's' : ''}</h3>`;

  countRepartidores.textContent = snap.size;

  Object.values(repartidorMarkers).forEach(m => map.removeLayer(m));
  repartidorMarkers = {};

  snap.forEach(d => {
    const r = d.data();

    // 🔥 GUARDAR EN CACHE
    repartidoresData[d.id] = r;

    renderRepartidor(r, d.id);

    if (r.coords) {
      const [lat, lng] = r.coords.split(",");
      repartidorMarkers[d.id] = L.marker(
        [parseFloat(lat), parseFloat(lng)], 
        { icon: repartidorIcon }
      )
      .addTo(map)
      .bindPopup(`
        <b>🛵 ${r.nombre}</b><br>
        📱 ${r.telefono || 'Sin teléfono'}<br>
        <span style="color:#00e676; font-weight:bold;">${r.estado || 'LIBRE'}</span>
      `);
    }
  });

  if (Object.keys(repartidorMarkers).length > 0) {
    map.fitBounds(
      Object.values(repartidorMarkers).map(m => m.getLatLng()),
      { padding: [30, 30], maxZoom: 15 }
    );
  }
});
// 🔥 CONEXIÓN STATUS
setTimeout(() => {
  statusDiv.className = "online";
  statusDiv.innerHTML = "🟢 Conexión establecida";
}, 2000);

// 🔥 DOUBLE-CLICK MAPA → NUEVA ZONA
map.on('dblclick', (e) => {
  L.marker(e.latlng).addTo(map)
    .bindPopup('Nueva zona de entrega 📍')
    .openPopup();
});

// 🔥 INIT
mostrar('pedidos');
console.log("🚀 Didi Food Admin PRO v2.0 - Listo para producción 💎");

async function pedidoListo(id){
  await updateDoc(doc(db, "pedidos", id), {
    estado: "listo",
    fechaUpdate: serverTimestamp()
  });

  let nombreRep = "Sin asignar";

  const pedidoDoc = await getDoc(doc(db, "pedidos", id));
  const data = pedidoDoc.data();

  if(data.repartidorId && repartidoresData[data.repartidorId]){
    nombreRep = repartidoresData[data.repartidorId].nombre;
  }

  mostrarMensaje(`🍽️ Pedido listo - Repartidor: ${nombreRep}`, "#00c851");
}
import { getDoc } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

async function marcarEntregado(id){

  const pedidoRef = doc(db, "pedidos", id);
  const pedidoSnap = await getDoc(pedidoRef);

  if(!pedidoSnap.exists()) return;

  const data = pedidoSnap.data();

  if(data.estado === "entregado") return;

  // 🔥 LIBERAR REPARTIDOR
  if(data.repartidorId){
    await updateDoc(doc(db,"repartidores",data.repartidorId),{
      estado:"libre"
    });
  }

  await addDoc(collection(db, "historial"), {
    ...data,
    estado: "entregado",
    fechaEntrega: serverTimestamp()
  });

  await deleteDoc(pedidoRef);

  mostrarMensaje("📦 Pedido entregado", "#00c851", "🏁");
}
window.asignarDesdePedido = async (pedidoId) => {

  const libres = Object.keys(repartidoresData)
    .filter(id => repartidoresData[id].estado === "libre");

  if(libres.length === 0){
    mostrarMensaje("⚠️ No hay repartidores libres", "#ffa726");
    return;
  }

  const repId = libres[0]; // 👉 el primero libre

  try{
    await updateDoc(doc(db,"pedidos",pedidoId),{
      repartidorId: repId
    });

    await updateDoc(doc(db,"repartidores",repId),{
      estado:"ocupado"
    });

    mostrarMensaje("🛵 Repartidor asignado", "#00c851");

  }catch(e){
    mostrarMensaje("❌ Error al asignar", "#ff416c");
  }
};
function iniciarContador(id, fecha){
  const el = document.getElementById(`timer-${id}`);
  if(!el) return;

  const inicio = fecha.toDate().getTime();

  setInterval(()=>{
    const ahora = Date.now();
    const seg = Math.floor((ahora - inicio)/1000);

    el.innerText = `⏱️ ${seg}s`;
  },1000);
}
function seguirRepartidorTiempoReal(repId, pedido){

  const repRef = doc(db, "repartidores", repId);

  onSnapshot(repRef, (snap) => {

    const rep = snap.data();
    if(!rep || !rep.coords) return;

    const [lat, lng] = rep.coords.split(",").map(Number);

    // 🔥 MOVER marcador en tiempo real
    if(repartidorMarkers[repId]){
      repartidorMarkers[repId].setLatLng([lat, lng]);
    }else{
      repartidorMarkers[repId] = L.marker([lat, lng], { icon: repartidorIcon }).addTo(map);
    }

    // 🔥 CENTRAR MAPA OPCIONAL
    map.panTo([lat, lng]);
if(pedido.coords){
  mostrarRutaReal(rep.coords, pedido.coords);
}
  });

}
function mostrarRutaReal(repCoords, clienteCoords){

  const [repLat, repLng] = repCoords.split(",").map(Number);
  const [cliLat, cliLng] = clienteCoords.split(",").map(Number);

  if(rutas["activa"]) {
    map.removeControl(rutas["activa"]);
  }

  rutas["activa"] = L.Routing.control({
    waypoints: [
      L.latLng(repLat, repLng),
      L.latLng(cliLat, cliLng)
    ],
    routeWhileDragging: false,
    addWaypoints: false,
    draggableWaypoints: false,
    show: false
  }).addTo(map);
}
</script>

</body>
</html>
