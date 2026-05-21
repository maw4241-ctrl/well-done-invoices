<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WELL DONE PRO — ניהול חשבונות</title>
<meta name="theme-color" content="#0F0D0B">
<link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;600;700;800;900&family=Frank+Ruhl+Libre:wght@400;700;900&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0F0D0B; --surface: #1A1714; --surface2: #231F1B; --surface3: #2D2824;
  --border: #3A332C; --border2: #4A4038; --red: #D94F3D; --red2: #B03A2A; --red-glow: rgba(217,79,61,0.15);
  --gold: #C9943A; --gold2: #A37828; --gold-light: #E8B86D; --cream: #F5ECD8;
  --text: #F0E8DC; --text2: #B8A898; --text3: #7A6E64; --green: #4CAF7D; --green2: #3A8F60;
  --blue: #4A90C4; --shadow: 0 4px 24px rgba(0,0,0,0.4); --shadow-lg: 0 16px 64px rgba(0,0,0,0.6);
  --radius: 12px; --radius-sm: 8px;
}
* { margin:0; padding:0; box-sizing:border-box; -webkit-tap-highlight-color: transparent; }
html { scroll-behavior: smooth; }
body { font-family: 'Heebo', sans-serif; background: var(--bg); color: var(--text); min-height: 100vh; direction: rtl; overflow-x: hidden; padding-bottom: 40px; }

/* ===== SCROLLBAR ===== */
::-webkit-scrollbar { width: 6px; height: 6px; }
::-webkit-scrollbar-track { background: var(--surface); }
::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 3px; }
::-webkit-scrollbar-thumb:hover { background: var(--gold2); }

/* ===== HEADER ===== */
.header { background: var(--surface); border-bottom: 1px solid var(--border); position: sticky; top: 0; z-index: 200; backdrop-filter: blur(10px); }
.header-inner { max-width: 1400px; margin: 0 auto; padding: 0 28px; display: flex; align-items: center; justify-content: space-between; height: 66px; }
.logo-group { display: flex; align-items: center; gap: 14px; }
.logo-mark { width: 42px; height: 42px; background: linear-gradient(135deg, var(--red), var(--red2)); border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 20px; box-shadow: 0 0 20px var(--red-glow); }
.logo-name { font-family: 'Frank Ruhl Libre', serif; font-size: 24px; font-weight: 900; color: var(--cream); letter-spacing: 3px; }
.logo-tag { font-size: 10px; font-weight: 700; color: var(--gold); letter-spacing: 4px; text-transform: uppercase; margin-top: -3px; }
.header-nav { display: flex; gap: 4px; }
.nav-btn { padding: 8px 18px; border-radius: var(--radius-sm); border: none; background: transparent; color: var(--text2); font-family: 'Heebo', sans-serif; font-size: 14px; font-weight: 600; cursor: pointer; transition: all 0.2s; display: flex; align-items: center; gap: 6px; }
.nav-btn:hover { background: var(--surface2); color: var(--text); }
.nav-btn.active { background: var(--red-glow); color: var(--red); border: 1px solid var(--red); }
.header-date { font-size: 13px; color: var(--text3); font-weight: 500; }

/* ===== LAYOUT ===== */
.app { max-width: 1400px; margin: 0 auto; padding: 28px; }
.page { display: none; animation: fadeIn 0.3s ease; }
.page.active { display: block; }
@keyframes fadeIn { from { opacity:0; transform:translateY(6px); } to { opacity:1; transform:translateY(0); } }

/* ===== DASHBOARD ===== */
.stats-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; margin-bottom: 28px; }
.stat-card { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius); padding: 22px 20px; position: relative; overflow: hidden; transition: border-color 0.2s; }
.stat-card:hover { border-color: var(--border2); }
.stat-card::before { content: ''; position: absolute; top: 0; right: 0; width: 3px; height: 100%; border-radius: 0 var(--radius) var(--radius) 0; }
.stat-card.red::before { background: var(--red); }
.stat-card.gold::before { background: var(--gold); }
.stat-card.green::before { background: var(--green); }
.stat-card.blue::before { background: var(--blue); }
.stat-label { font-size: 11px; color: var(--text3); font-weight: 700; letter-spacing: 1.5px; text-transform: uppercase; margin-bottom: 8px; }
.stat-value { font-size: 32px; font-weight: 900; color: var(--text); font-variant-numeric: tabular-nums; }
.stat-value.red { color: var(--red); }
.stat-value.gold { color: var(--gold); }
.stat-value.green { color: var(--green); }
.stat-sub { font-size: 12px; color: var(--text3); margin-top: 6px; }
.stat-icon { position: absolute; left: 20px; top: 50%; transform: translateY(-50%); font-size: 36px; opacity: 0.12; }
.dash-grid { display: grid; grid-template-columns: 1fr 380px; gap: 20px; }

/* ===== CARDS & FIELDS ===== */
.card { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius); overflow: hidden; margin-bottom: 16px; }
.card-head { padding: 18px 22px; border-bottom: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; }
.card-title { font-size: 15px; font-weight: 700; color: var(--text); display: flex; align-items: center; gap: 8px; }
.card-title-icon { width: 30px; height: 30px; background: var(--surface2); border-radius: 6px; display: flex; align-items: center; justify-content: center; font-size: 15px; }
.card-body { padding: 22px; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-bottom: 14px; }
.form-row.three { grid-template-columns: 1fr 1fr 1fr; }
.form-row.four { grid-template-columns: 1fr 1fr 1fr 1fr; }
.field { display: flex; flex-direction: column; gap: 6px; }
.field.full { grid-column: 1/-1; }
.label { font-size: 11px; font-weight: 700; color: var(--text3); letter-spacing: 1px; text-transform: uppercase; }
input[type=text], input[type=number], input[type=tel], input[type=date], select, textarea { font-family: 'Heebo', sans-serif; background: var(--surface2); border: 1.5px solid var(--border); border-radius: var(--radius-sm); padding: 10px 14px; color: var(--text); font-size: 14px; direction: rtl; width: 100%; transition: all 0.2s; outline: none; }
input:focus, select:focus, textarea:focus { border-color: var(--gold); background: var(--surface3); box-shadow: 0 0 0 3px rgba(201,148,58,0.12); }

/* ===== BUTTONS ===== */
.btn { font-family: 'Heebo', sans-serif; font-weight: 700; font-size: 13px; padding: 10px 18px; border-radius: var(--radius-sm); border: none; cursor: pointer; display: inline-flex; align-items: center; gap: 6px; transition: all 0.18s; white-space: nowrap; }
.btn-primary { background: var(--red); color: #fff; }
.btn-primary:hover { background: var(--red2); box-shadow: 0 4px 20px var(--red-glow); transform: translateY(-1px); }
.btn-gold { background: var(--gold); color: #fff; }
.btn-gold:hover { background: var(--gold2); transform: translateY(-1px); }
.btn-ghost { background: var(--surface2); color: var(--text2); border: 1px solid var(--border); }
.btn-ghost:hover { background: var(--surface3); color: var(--text); border-color: var(--border2); }
.btn-danger { background: transparent; color: var(--red); border: 1px solid rgba(217,79,61,0.3); }
.btn-danger:hover { background: var(--red); color: #fff; }
.btn-success { background: var(--green); color: #fff; }
.btn-sm { font-size: 12px; padding: 6px 12px; }
.btn-full { width: 100%; justify-content: center; }

/* ===== TABLES & BADGES ===== */
table { width: 100%; border-collapse: collapse; font-size: 13px; }
thead th { padding: 10px 14px; text-align: right; font-size: 10px; font-weight: 700; color: var(--text3); background: var(--surface2); border-bottom: 1px solid var(--border); }
tbody td { padding: 12px 14px; border-bottom: 1px solid rgba(58,51,44,0.5); color: var(--text2); }
tbody tr:hover td { background: var(--surface2); color: var(--text); }
.badge { display: inline-flex; align-items: center; padding: 3px 10px; border-radius: 20px; font-size: 11px; font-weight: 700; }
.badge-red { background: rgba(217,79,61,0.15); color: var(--red); border: 1px solid rgba(217,79,61,0.3); }
.badge-green { background: rgba(76,175,125,0.15); color: var(--green); border: 1px solid rgba(76,175,125,0.3); }
.badge-gold { background: rgba(201,148,58,0.15); color: var(--gold-light); border: 1px solid rgba(201,148,58,0.3); }

/* ===== CLIENT CARD (ROW) ===== */
.client-cards { display: flex; flex-direction: column; gap: 8px; }
.client-card { background: var(--surface2); border: 1px solid var(--border); border-radius: var(--radius-sm); padding: 14px 16px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; transition: all 0.18s; }
.client-card:hover { border-color: var(--gold); background: var(--surface3); }
.client-card-name { font-size: 15px; font-weight: 700; color: var(--text); }
.client-card-info { font-size: 12px; color: var(--text3); margin-top: 2px; }

/* ===== QUICK INVOICE BUILDER & SUGGESTIONS ===== */
.invoice-layout { display: grid; grid-template-columns: 1fr 360px; gap: 20px; align-items: start; }
.product-search-wrap { position: relative; margin-bottom: 14px; }
.product-suggestions { position: absolute; top: 100%; right: 0; left: 0; background: var(--surface2); border: 1px solid var(--border2); border-radius: 0 0 var(--radius-sm) var(--radius-sm); z-index: 50; max-height: 200px; overflow-y: auto; display: none; }
.product-suggestions.open { display: block; }
.suggestion-item { padding: 10px 14px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; border-bottom: 1px solid var(--border); }
.suggestion-item:hover { background: var(--surface3); }
.cat-tabs { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 14px; }
.cat-tab { padding: 5px 14px; border-radius: 20px; border: 1px solid var(--border); background: transparent; color: var(--text3); font-size: 12px; font-weight: 600; cursor: pointer; }
.cat-tab.active { background: var(--gold); color: #fff; border-color: var(--gold); }
.quick-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(130px, 1fr)); gap: 8px; max-height: 250px; overflow-y: auto; }
.quick-item { background: var(--surface2); border: 1px solid var(--border); border-radius: var(--radius-sm); padding: 10px 12px; cursor: pointer; display: flex; flex-direction: column; }
.quick-item:hover { border-color: var(--gold); background: var(--surface3); }

/* ===== MODALS & LOCK SCREEN ===== */
.modal-overlay { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.8); z-index: 500; align-items: center; justify-content: center; backdrop-filter: blur(4px); }
.modal-overlay.open { display: flex; }
.modal { background: var(--surface); border: 1px solid var(--border2); border-radius: 16px; width: 90%; max-width: 600px; max-height: 90vh; overflow-y: auto; box-shadow: var(--shadow-lg); }
.modal-head { padding: 18px 22px; border-bottom: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; }
.modal-body { padding: 22px; }
.modal-foot { padding: 14px 22px; border-top: 1px solid var(--border); display: flex; gap: 10px; justify-content: flex-start; }
.lock-screen { position: fixed; inset: 0; z-index: 99999; background: radial-gradient(circle at top, #2D2824 0%, #0F0D0B 55%); display: flex; align-items: center; justify-content: center; padding: 20px; }
.lock-screen.hidden { display: none !important; }
#toast { position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%) translateY(100px); background: #222; border: 1px solid var(--gold); color: #fff; padding: 12px 24px; border-radius: 30px; z-index: 100000; transition: transform 0.3s ease; font-size: 14px; font-weight: bold; }
#toast.show { transform: translateX(-50%) translateY(0); }

@media (max-width: 700px) {
  .stats-row { grid-template-columns: 1fr 1fr; }
  .header-inner { height: auto; padding: 10px; flex-direction: column; gap: 10px; }
  .header-nav { width: 100%; overflow-x: auto; white-space: nowrap; display: flex; }
  .invoice-layout { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<div class="lock-screen" id="lockScreen">
  <div class="card" style="width: 100%; max-width: 340px; padding: 24px; text-align: center; background: var(--surface);">
    <div style="font-size: 40px; margin-bottom: 10px;">🥩</div>
    <h2 font-family="Frank Ruhl Libre" style="margin-bottom: 4px; font-size: 24px;">WELL DONE</h2>
    <p style="color: var(--text3); font-size: 13px; margin-bottom: 20px;">כניסה מאובטחת למערכת</p>
    <div class="field" style="margin-bottom: 16px; text-align: right;">
      <label class="label">קוד גישה</label>
      <input type="password" id="loginPass" placeholder="הזן קוד (4241)" style="text-align: center; font-size: 20px; letter-spacing: 4px;">
    </div>
    <button class="btn btn-primary btn-full" onclick="loginApp()" style="padding: 12px;">כניסה למערכת</button>
  </div>
</div>

<header class="header">
  <div class="header-inner">
    <div class="logo-group">
      <div class="logo-mark">🥩</div>
      <div>
        <div class="logo-name">WELL DONE</div>
        <div class="logo-tag">מערכת ניהול מקצועית</div>
      </div>
    </div>
    <nav class="header-nav">
      <button class="nav-btn active" onclick="showPage('dashboard')" id="nav-dashboard">📊 דשבורד</button>
      <button class="nav-btn" onclick="showPage('invoice')" id="nav-invoice">📄 חשבונית חדשה</button>
      <button class="nav-btn" onclick="showPage('clients')" id="nav-clients">👥 לקוחות</button>
      <button class="nav-btn" onclick="showPage('history')" id="nav-history">📋 היסטוריה</button>
      <button class="nav-btn" onclick="showPage('pricelist')" id="nav-pricelist">💰 מחירון</button>
    </nav>
    <div class="header-date" id="headerDate">─</div>
    <button class="btn btn-ghost btn-sm" onclick="logoutApp()">🔒 יציאה</button>
  </div>
</header>

<div class="app">

  <div class="page active" id="page-dashboard">
    <div class="stats-row">
      <div class="stat-card red" onclick="showPage('clients')">
        <div class="stat-label">חובות פתוחים</div>
        <div class="stat-value red" id="stat-debt">₪0</div>
        <div class="stat-sub" id="stat-debt-sub">0 לקוחות בחוב</div>
        <div class="stat-icon">💸</div>
      </div>
      <div class="stat-card gold" onclick="showPage('history')">
        <div class="stat-label">מכירות החודש</div>
        <div class="stat-value gold" id="stat-monthly">₪0</div>
        <div class="stat-sub" id="stat-monthly-sub">0 חשבוניות</div>
        <div class="stat-icon">📈</div>
      </div>
      <div class="stat-card green" onclick="showPage('clients')">
        <div class="stat-label">סה"כ לקוחות</div>
        <div class="stat-value green" id="stat-clients">0</div>
        <div class="stat-sub">לקוחות במערכת</div>
        <div class="stat-icon">👥</div>
      </div>
      <div class="stat-card blue" onclick="showPage('history')">
        <div class="stat-label">חשבוניות</div>
        <div class="stat-value" id="stat-invoices">0</div>
        <div class="stat-sub">בארכיון</div>
        <div class="stat-icon">📄</div>
      </div>
    </div>
  </div>

  <div class="page" id="page-invoice">
    <div class="invoice-layout">
      <div class="card">
        <div class="card-head"><div class="card-title">📝 פרטי החשבונית פריטים</div></div>
        <div class="card-body">
          <div class="product-search-wrap">
            <input type="text" id="prodSearch" oninput="doProdSearch()" placeholder="🔎 הקלד לחיפוש טיפול/מוצר מהמחירון...">
            <div class="product-suggestions" id="prodSuggestions"></div>
          </div>
          <div class="cat-tabs" id="catTabs"></div>
          <div class="quick-grid" id="quickGrid"></div>
          
          <table style="margin-top:20px;" id="invoiceTable">
            <thead>
              <tr>
                <th>פריט / טיפול</th>
                <th style="width:80px;">מחיר</th>
                <th style="width:60px;">כמות</th>
                <th style="width:80px;">סה"כ</th>
                <th style="width:40px;"></th>
              </tr>
            </thead>
            <tbody id="invoiceItems"></tbody>
          </table>
        </div>
      </div>
      
      <div>
        <div class="card" style="padding:16px;">
          <div class="field" style="margin-bottom:12px;">
            <label class="label">בחר לקוח</label>
            <select id="invoiceClientSelect"></select>
          </div>
          <div style="display:flex; justify-content:space-between; margin-bottom:8px; font-size:14px;">
            <span>סה"כ לתשלום:</span>
            <span id="invTotal" style="font-weight:bold; color:var(--gold-light);">₪0</span>
          </div>
          <button class="btn btn-primary btn-full" onclick="createInvoice()">סגור חשבונית ועדכן חוב 💾</button>
        </div>
      </div>
    </div>
  </div>

  <div class="page" id="page-clients">
    <div class="card" style="padding:12px; display:flex; flex-direction:column; gap:10px;">
      <input type="text" id="searchBar" oninput="renderClients()" placeholder="🔍 חפש לקוח לפי שם או מספר טלפון...">
      <div style="display:flex; gap:10px;">
        <button class="btn btn-gold" onclick="openAddClientModal()">＋ לקוח חדש</button>
        <button class="btn btn-ghost" id="btnFilterAll" onclick="setClientFilter('all')" style="border-color:var(--gold);">הכל</button>
        <button class="btn btn-ghost" id="btnFilterDebt" onclick="setClientFilter('debt')">בעלי חוב</button>
      </div>
    </div>
    <div class="client-cards" id="clientsList"></div>
  </div>

  <div class="page" id="page-history">
    <div class="card">
      <div class="card-head"><div class="card-title">📋 ארכיון חשבוניות והיסטוריה</div></div>
      <div class="card-body">
        <table>
          <thead>
            <tr>
              <th>מספר</th>
              <th>לקוח</th>
              <th>תאריך</th>
              <th>סכום</th>
            </tr>
          </thead>
          <tbody id="historyList"></tbody>
        </table>
      </div>
    </div>
  </div>

  <div class="page" id="page-pricelist">
    <div class="card" style="margin-bottom:16px; padding:16px;">
      <h3 style="margin-bottom:10px; font-size:16px; color:var(--gold);">הוספת פריט חדש למחירון</h3>
      <div class="form-row three">
        <div class="field"><label class="label">שם הטיפול/מוצר</label><input type="text" id="newProgName"></div>
        <div class="field"><label class="label">מחיר (₪)</label><input type="number" id="newProgPrice"></div>
        <div class="field"><label class="label">קטגוריה</label>
          <select id="newProgCat">
            <option value="טיפולים">טיפולים</option>
            <option value="מוצרים">מוצרים</option>
            <option value="אחר">אחר</option>
          </select>
        </div>
      </div>
      <button class="btn btn-gold" onclick="addPricelistItem()" style="margin-top:6px;">שמור במחירון ✓</button>
    </div>
    <div class="card">
      <div class="card-head"><div class="card-title">💰 מחירון קבוע</div></div>
      <div class="card-body">
        <table>
          <thead>
            <tr>
              <th>טיפול / מוצר</th>
              <th>קטגוריה</th>
              <th>מחיר</th>
              <th style="width:50px;"></th>
            </tr>
          </thead>
          <tbody id="pricelistTableBody"></tbody>
        </table>
      </div>
    </div>
  </div>

</div>

<div class="modal-overlay" id="addClientModal">
  <div class="modal" style="max-width:400px;">
    <div class="modal-head"><div class="modal-title">הוספת לקוח חדש</div><button class="modal-close" onclick="closeModal('addClientModal')">×</button></div>
    <div class="modal-body">
      <div class="field" style="margin-bottom:12px;"><label class="label">שם מלא</label><input type="text" id="cName"></div>
      <div class="field" style="margin-bottom:12px;"><label class="label">טלפון</label><input type="tel" id="cPhone"></div>
      <div class="field" style="margin-bottom:12px;"><label class="label">חוב פתיחה ראשוני (₪)</label><input type="number" id="cDebt" value="0"></div>
    </div>
    <div class="modal-foot">
      <button class="btn btn-gold" onclick="saveNewClient()">שמור לקוח</button>
      <button class="btn btn-ghost" onclick="closeModal('addClientModal')">ביטול</button>
    </div>
  </div>
</div>

<div class="modal-overlay" id="clientActionModal">
  <div class="modal" style="max-width:420px;">
    <div class="modal-head"><div class="modal-title" id="actModalTitle">שם הלקוח</div><button class="modal-close" onclick="closeModal('clientActionModal')">×</button></div>
    <div class="modal-body">
      <p id="actModalStatus" style="color:var(--text2); margin-bottom:16px; font-size:14px;"></p>
      <div class="field" style="margin-bottom:12px;">
        <label class="label">סכום לשינוי (₪)</label>
        <input type="number" id="actAmount" placeholder="הזן סכום בשקלים...">
      </div>
      <div style="display:grid; grid-template-columns: 1fr 1fr; gap:10px; margin-top:14px;">
        <button class="btn btn-primary" onclick="quickModifyDebt('add')">＋ הוסף לחוב</button>
        <button class="btn btn-success" onclick="quickModifyDebt('sub')" style="background:var(--green);">− קבל תשלום</button>
      </div>
      <div style="margin-top:24px; padding-top:14px; border-top:1px solid var(--border); display:flex; justify-content:space-between;">
        <button class="btn btn-danger" style="background:none; border:none; font-size:12px;" onclick="deleteClientFast()">🗑 מחק לקוח לצמיתות</button>
        <button class="btn btn-ghost" onclick="closeModal('clientActionModal')">סגור</button>
      </div>
    </div>
  </div>
</div>

<div id="toast">הודעה</div>

<script>
// נתונים דיפולטיביים למחירון כדי שלא יהיה ריק
let defaultProducts = [
  {id:1, name:"טיפול פנים קלאסי", price:250, cat:"טיפולים"},
  {id:2, name:"פילינג עמוק", price:400, cat:"טיפולים"},
  {id:3, name:"קרם לחם יוקרתי", price:180, cat:"מוצרים"},
  {id:4, name:"סרום ויטמין C", price:220, cat:"מוצרים"}
];

let clients = [];
let invoices = [];
let pricelist = [];
let currentTab = 'all';
let selectedClientId = null;
let currentInvoiceItems = [];
let currentSelectedCat = 'הכל';

function loginApp() {
  if(document.getElementById('loginPass').value === '4241') {
    localStorage.setItem('wd_logged_passed', 'yes');
    document.getElementById('lockScreen').classList.add('hidden');
    showToast('המערכת פתוחה ✓');
  } else {
    showToast('קוד שגוי!');
  }
}

function checkAuth() {
  if(localStorage.getItem('wd_logged_passed') === 'yes') {
    document.getElementById('lockScreen').classList.add('hidden');
  }
}

function logoutApp() {
  localStorage.removeItem('wd_logged_passed');
  document.getElementById('loginPass').value = '';
  document.getElementById('lockScreen').classList.remove('hidden');
}

function loadAllData() {
  clients = JSON.parse(localStorage.getItem('wd_v3_clients')) || [];
  invoices = JSON.parse(localStorage.getItem('wd_v3_invoices')) || [];
  pricelist = JSON.parse(localStorage.getItem('wd_v3_pricelist')) || defaultProducts;
  
  // סנכרון ראשוני אם המחירון נמחק לחלוטין מהלוקאל
  if(pricelist.length === 0) pricelist = defaultProducts;

  renderDashboard();
  renderClients();
  renderPricelist();
  renderInvoiceSelectors();
  renderHistory();
}

function saveAllData() {
  localStorage.setItem('wd_v3_clients', JSON.stringify(clients));
  localStorage.setItem('wd_v3_invoices', JSON.stringify(invoices));
  localStorage.setItem('wd_v3_pricelist', JSON.stringify(pricelist));
  
  renderDashboard();
  renderClients();
  renderPricelist();
  renderInvoiceSelectors();
  renderHistory();
}

function showPage(pageId) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  
  document.getElementById('page-' + pageId).classList.add('active');
  const btn = document.getElementById('nav-' + pageId);
  if(btn) btn.classList.add('active');
}

/* ============ מחירון קבוע ============ */
function renderPricelist() {
  const tbody = document.getElementById('pricelistTableBody');
  tbody.innerHTML = '';
  pricelist.forEach(item => {
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td style="font-weight:bold; color:#fff;">${item.name}</td>
      <td><span class="badge badge-gray">${item.cat}</span></td>
      <td style="color:var(--gold-light); font-weight:bold;">₪${item.price}</td>
      <td><button class="btn btn-danger btn-xs" onclick="deletePricelistItem(${item.id})">×</button></td>
    `;
    tbody.appendChild(tr);
  });
  renderInvoiceQuickGrid();
}

function addPricelistItem() {
  const name = document.getElementById('newProgName').value.trim();
  const price = parseFloat(document.getElementById('newProgPrice').value);
  const cat = document.getElementById('newProgCat').value;

  if(!name || isNaN(price)) { showToast('נא למלא שם ומחיר תקינים'); return; }
  
  pricelist.push({ id: Date.now(), name, price, cat });
  saveAllData();
  
  document.getElementById('newProgName').value = '';
  document.getElementById('newProgPrice').value = '';
  showToast('הפריט נוסף למחירון!');
}

function deletePricelistItem(id) {
  if(confirm('למחוק פריט זה מהמחירון?')) {
    pricelist = pricelist.filter(i => i.id !== id);
    saveAllData();
  }
}

/* ============ דשבורד וסיכומים ============ */
function renderDashboard() {
  let totalDebt = 0;
  let debtCount = 0;
  clients.forEach(c => {
    if(c.balance > 0) { totalDebt += c.balance; debtCount++; }
  });

  let monthlyTotal = 0;
  const currentMonth = new Date().getMonth();
  const currentYear = new Date().getFullYear();
  invoices.forEach(inv => {
    const d = new Date(inv.date);
    if(d.getMonth() === currentMonth && d.getFullYear() === currentYear) {
      monthlyTotal += inv.total;
    }
  });

  document.getElementById('stat-debt').textContent = '₪' + totalDebt.toLocaleString();
  document.getElementById('stat-debt-sub').textContent = `${debtCount} לקוחות בחוב`;
  document.getElementById('stat-monthly').textContent = '₪' + monthlyTotal.toLocaleString();
  document.getElementById('stat-monthly-sub').textContent = `${invoices.length} חשבוניות החודש`;
  document.getElementById('stat-clients').textContent = clients.length;
  document.getElementById('stat-invoices').textContent = invoices.length;
}

/* ============ ניהול לקוחות + פעולות מהירות ============ */
function setClientFilter(type) {
  currentTab = type;
  document.getElementById('btnFilterAll').style.borderColor = type === 'all' ? 'var(--gold)' : 'var(--border)';
  document.getElementById('btnFilterDebt').style.borderColor = type === 'debt' ? 'var(--gold)' : 'var(--border)';
  renderClients();
}

function renderClients() {
  const list = document.getElementById('clientsList');
  const search = document.getElementById('searchBar').value.toLowerCase().trim();
  list.innerHTML = '';

  let filtered = clients.filter(c => {
    const matchFilter = currentTab === 'all' || (currentTab === 'debt' && c.balance > 0);
    const matchSearch = c.name.toLowerCase().includes(search) || (c.phone && c.phone.includes(search));
    return matchFilter && matchSearch;
  });

  filtered.sort((a,b) => b.balance - a.balance);

  if(filtered.length === 0) {
    list.innerHTML = '<p style="text-align:center; padding:20px; color:var(--text3);">אין לקוחות להצגה</p>';
    return;
  }

  filtered.forEach(c => {
    const div = document.createElement('div');
    div.className = 'client-card';
    div.onclick = () => openClientAction(c.id);
    
    const badgeClass = c.balance > 0 ? 'badge-red' : 'badge-green';
    const badgeText = c.balance > 0 ? `חוב: ₪${c.balance.toLocaleString()}` : 'מאוזן';

    div.innerHTML = `
      <div class="client-card-left">
        <div class="client-card-name">${c.name}</div>
        <div class="client-card-info">📱 ${c.phone || '—'}</div>
      </div>
      <span class="badge ${badgeClass}">${badgeText}</span>
    `;
    list.appendChild(div);
  });
}

function openAddClientModal() { document.getElementById('addClientModal').classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }

function saveNewClient() {
  const name = document.getElementById('cName').value.trim();
  const phone = document.getElementById('cPhone').value.trim();
  const balance = parseFloat(document.getElementById('cDebt').value) || 0;

  if(!name) { showToast('נא להזין שם לקוח'); return; }
  
  clients.push({ id: Date.now(), name, phone, balance });
  saveAllData();
  closeModal('addClientModal');
  
  document.getElementById('cName').value = '';
  document.getElementById('cPhone').value = '';
  document.getElementById('cDebt').value = '0';
  showToast('לקוח חדש נשמר בהצלחה!');
}

function openClientAction(id) {
  selectedClientId = id;
  const c = clients.find(item => item.id === id);
  if(!c) return;

  document.getElementById('actModalTitle').textContent = c.name;
  document.getElementById('actModalStatus').textContent = `מצב חשבון נוכחי: ` + (c.balance > 0 ? `חוב של ₪${c.balance.toLocaleString()}` : 'מאוזן (₪0)');
  document.getElementById('actAmount').value = '';
  document.getElementById('clientActionModal').classList.add('open');
}

function quickModifyDebt(type) {
  const amt = parseFloat(document.getElementById('actAmount').value);
  if(!amt || amt <= 0) { showToast('נא להזין סכום תקין'); return; }

  const c = clients.find(item => item.id === selectedClientId);
  if(!c) return;

  if(type === 'add') {
    c.balance += amt;
    showToast('החוב עודכן בהצלחה');
  } else {
    c.balance = Math.max(0, c.balance - amt);
    showToast('התשלום התקבל ועודכן');
  }
  saveAllData();
  closeModal('clientActionModal');
}

function deleteClientFast() {
  const c = clients.find(item => item.id === selectedClientId);
  if(!c) return;
  if(confirm(`האם למחוק לחלוטין את הלקוח ${c.name}? פעולה זו בלתי הפיכה!`)) {
    clients = clients.filter(item => item.id !== selectedClientId);
    saveAllData();
    closeModal('clientActionModal');
    showToast('הלקוח נמחק מהמערכת');
  }
}

/* ============ בניית חשבונית חכמה ============ */
function renderInvoiceSelectors() {
  const sel = document.getElementById('invoiceClientSelect');
  sel.innerHTML = '';
  clients.forEach(c => {
    const opt = document.createElement('option');
    opt.value = c.id;
    opt.textContent = c.name;
    sel.appendChild(opt);
  });
}

function renderInvoiceQuickGrid() {
  const tabs = document.getElementById('catTabs');
  const grid = document.getElementById('quickGrid');
  
  // קטגוריות
  let cats = ['הכל', ...new Set(pricelist.map(i => i.cat))];
  tabs.innerHTML = '';
  cats.forEach(cat => {
    const btn = document.createElement('button');
    btn.className = `cat-tab ${currentSelectedCat === cat ? 'active' : ''}`;
    btn.textContent = cat;
    btn.onclick = () => { currentSelectedCat = cat; renderInvoiceQuickGrid(); };
    tabs.appendChild(btn);
  });

  // פריטים בגריד
  grid.innerHTML = '';
  let items = pricelist.filter(i => currentSelectedCat === 'הכל' || i.cat === currentSelectedCat);
  items.forEach(item => {
    const div = document.createElement('div');
    div.className = 'quick-item';
    div.onclick = () => addProductToInvoice(item);
    div.innerHTML = `
      <span style="font-weight:bold; font-size:13px;">${item.name}</span>
      <span style="color:var(--gold-light); font-size:12px; margin-top:4px; font-weight:bold;">₪${item.price}</span>
    `;
    grid.appendChild(div);
  });
}

function doProdSearch() {
  const query = document.getElementById('prodSearch').value.toLowerCase().trim();
  const sug = document.getElementById('prodSuggestions');
  if(!query) { sug.classList.remove('open'); return; }

  let match = pricelist.filter(i => i.name.toLowerCase().includes(query));
  if(match.length === 0) { sug.classList.remove('open'); return; }

  sug.innerHTML = '';
  sug.classList.add('open');
  match.forEach(item => {
    const div = document.createElement('div');
    div.className = 'suggestion-item';
    div.onclick = () => { addProductToInvoice(item); sug.classList.remove('open'); document.getElementById('prodSearch').value = ''; };
    div.innerHTML = `<span>${item.name}</span><span style="color:var(--gold-light);">₪${item.price}</span>`;
    sug.appendChild(div);
  });
}

function addProductToInvoice(item) {
  const exist = currentInvoiceItems.find(i => i.id === item.id);
  if(exist) {
    exist.qty++;
  } else {
    currentInvoiceItems.push({ id: item.id, name: item.name, price: item.price, qty: 1 });
  }
  renderInvoiceItems();
}

function renderInvoiceItems() {
  const tbody = document.getElementById('invoiceItems');
  tbody.innerHTML = '';
  let total = 0;

  currentInvoiceItems.forEach((item, index) => {
    let rowTotal = item.price * item.qty;
    total += rowTotal;
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td style="font-weight:bold; color:#fff;">${item.name}</td>
      <td>₪${item.price}</td>
      <td><input type="number" value="${item.qty}" min="1" style="padding:4px; text-align:center;" oninput="updateQty(${index}, this.value)"></td>
      <td style="color:var(--gold-light); font-weight:bold;">₪${rowTotal}</td>
      <td><button class="btn btn-danger btn-xs" onclick="removeInvoiceItem(${index})">×</button></td>
    `;
    tbody.appendChild(tr);
  });

  document.getElementById('invTotal').textContent = '₪' + total.toLocaleString();
}

function updateQty(index, val) {
  let q = parseInt(val) || 1;
  currentInvoiceItems[index].qty = q;
  renderInvoiceItems();
}

function removeInvoiceItem(index) {
  currentInvoiceItems.splice(index, 1);
  renderInvoiceItems();
}

function createInvoice() {
  const clientId = document.getElementById('invoiceClientSelect').value;
  if(!clientId) { showToast('נא לבחור לקוח לחשבונית'); return; }
  if(currentInvoiceItems.length === 0) { showToast('החשבונית ריקה! הוסף מוצרים או טיפולים'); return; }

  let total = 0;
  currentInvoiceItems.forEach(i => total += (i.price * i.qty));

  // עדכון חוב הלקוח
  const c = clients.find(item => item.id == clientId);
  if(c) {
    c.balance += total;
  }

  // שמירת החשבונית בארכיון
  invoices.push({
    id: Date.now(),
    invoiceNum: invoices.length + 1001,
    clientName: c ? c.name : 'לקוח כללי',
    date: new Date().toISOString(),
    total: total
  });

  currentInvoiceItems = [];
  renderInvoiceItems();
  saveAllData();
  showToast('החשבונית נסגרה והחוב התווסף לחשבון הלקוח!');
  showPage('dashboard');
}

/* ============ ארכיון היסטוריה ============ */
function renderHistory() {
  const tbody = document.getElementById('historyList');
  tbody.innerHTML = '';
  
  // מציג מהחדש לישן
  let rev = [...invoices].reverse();
  
  if(rev.length === 0) {
    tbody.innerHTML = '<tr><td colspan="4" style="text-align:center; color:var(--text3); padding:20px;">אין חשבוניות בארכיון</td></tr>';
    return;
  }

  rev.forEach(inv => {
    const tr = document.createElement('tr');
    const dateStr = new Date(inv.date).toLocaleDateString('he-IL');
    tr.innerHTML = `
      <td style="font-weight:bold; color:var(--gold-light);">#${inv.invoiceNum}</td>
      <td style="color:#fff; font-weight:bold;">${inv.clientName}</td>
      <td>${dateStr}</td>
      <td style="color:var(--red); font-weight:bold;">₪${inv.total.toLocaleString()}</td>
    `;
    tbody.appendChild(tr);
  });
}

function showToast(m) {
  const t = document.getElementById('toast');
  t.textContent = m; t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3000);
}

window.addEventListener('DOMContentLoaded', () => {
  const now = new Date();
  document.getElementById('headerDate').textContent = now.toLocaleDateString('he-IL', {
    weekday: 'long', day: 'numeric', month: 'long', year: 'numeric'
  });
  checkAuth();
  loadAllData();
});
</script>
</body>
</html>
// ============================================================
//  BASIC LOGIN + PWA
// ============================================================
const APP_USERNAME = 'moshe';
const APP_PASSWORD = '4241';

function initAuth() {
  const ok = localStorage.getItem('wd_logged_in') === 'yes';
  document.getElementById('lockScreen').classList.toggle('open', !ok);
}
function loginApp() {
  const u = document.getElementById('loginUser').value.trim();
  const p = document.getElementById('loginPass').value.trim();
  if (u === APP_USERNAME && p === APP_PASSWORD) {
    localStorage.setItem('wd_logged_in','yes');
    document.getElementById('lockScreen').classList.remove('open');
    toast('נכנסת למערכת ✓','ok');
  } else {
    toast('שם משתמש או סיסמה לא נכונים','err');
  }
}
function logoutApp() {
  localStorage.removeItem('wd_logged_in');
  document.getElementById('loginPass').value = '';
  document.getElementById('lockScreen').classList.add('open');
}

if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('./service-worker.js').catch(()=>{});
  });
}

// ============================================================
//  INIT
// ============================================================
const now = new Date();
document.getElementById('headerDate').textContent =
  now.toLocaleDateString('he-IL',{weekday:'long',day:'numeric',month:'long',year:'numeric'});

loadDB();
importClientsFromEveryStorage();
mirrorClientsForSafety();
initAuth();
renderDashboard();
