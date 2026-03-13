<!DOCTYPE html>  
  
<html lang="en">  
<head>  
<meta charset="UTF-8"/>  
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0"/>  
<title>Staff Time Zones</title>  
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>  
<style>  
:root {  
  --bg:        #0c0d11;  
  --bg2:       #111318;  
  --surface:   #161820;  
  --surface2:  #1d2029;  
  --surface3:  #252836;  
  --border:    #252836;  
  --border2:   #2e3245;  
  --accent:    #7c6dfa;  
  --accent2:   #a78bfa;  
  --glow:      rgba(124,109,250,0.18);  
  --cyan:      #22d3ee;  
  --teal:      #2dd4bf;  
  --text:      #f0f1f6;  
  --sub:       #8b8fa8;  
  --muted:     #4a4f6a;  
  --danger:    #f87171;  
  --radius:    16px;  
  --radius-sm: 10px;  
}  
  
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }  
html { font-size: 16px; }  
  
body {  
background: var(–bg);  
color: var(–text);  
font-family: ‘Syne’, sans-serif;  
min-height: 100vh;  
overflow-x: hidden;  
-webkit-font-smoothing: antialiased;  
}  
  
/* ── SUBTLE MESH BG ── */  
body::before {  
content: ‘’;  
position: fixed; inset: 0; z-index: 0; pointer-events: none;  
background:  
radial-gradient(ellipse 70% 50% at 15% 0%, rgba(124,109,250,0.08) 0%, transparent 60%),  
radial-gradient(ellipse 50% 40% at 85% 100%, rgba(34,211,238,0.05) 0%, transparent 55%),  
radial-gradient(ellipse 40% 60% at 50% 50%, rgba(124,109,250,0.03) 0%, transparent 70%);  
}  
  
/* ── HEADER ── */  
header {  
position: sticky; top: 0; z-index: 100;  
background: rgba(12,13,17,0.85);  
backdrop-filter: blur(24px);  
-webkit-backdrop-filter: blur(24px);  
border-bottom: 1px solid var(–border);  
padding: 0 20px;  
height: 62px;  
display: flex; align-items: center; justify-content: space-between;  
}  
  
.header-left { display: flex; align-items: center; gap: 10px; }  
  
.header-icon {  
width: 32px; height: 32px;  
border-radius: 9px;  
background: linear-gradient(135deg, var(–accent) 0%, var(–cyan) 100%);  
display: flex; align-items: center; justify-content: center;  
font-size: 15px;  
box-shadow: 0 0 16px rgba(124,109,250,0.35);  
flex-shrink: 0;  
}  
  
.header-title {  
font-size: 16px;  
font-weight: 700;  
color: var(–text);  
letter-spacing: -0.2px;  
}  
  
.live-badge {  
display: flex; align-items: center; gap: 5px;  
padding: 4px 10px;  
border-radius: 20px;  
background: rgba(45,212,191,0.08);  
border: 1px solid rgba(45,212,191,0.2);  
font-family: ‘JetBrains Mono’, monospace;  
font-size: 10px; font-weight: 500;  
color: var(–teal);  
letter-spacing: 0.5px;  
}  
.live-dot {  
width: 5px; height: 5px; border-radius: 50%;  
background: var(–teal);  
box-shadow: 0 0 6px var(–teal);  
animation: pulse 2.5s ease-in-out infinite;  
}  
@keyframes pulse {  
0%,100% { opacity:1; transform:scale(1); }  
50%      { opacity:0.5; transform:scale(0.7); }  
}  
  
/* ── MAIN ── */  
main {  
position: relative; z-index: 1;  
max-width: 680px; margin: 0 auto;  
padding: 22px 16px 120px;  
}  
  
/* ── STATS ── */  
.stats {  
display: grid; grid-template-columns: repeat(3,1fr);  
gap: 10px; margin-bottom: 22px;  
}  
.stat {  
background: var(–surface);  
border: 1px solid var(–border);  
border-radius: var(–radius);  
padding: 16px;  
position: relative; overflow: hidden;  
transition: border-color 0.2s;  
}  
.stat::before {  
content: ‘’;  
position: absolute; top: 0; left: 0; right: 0; height: 1px;  
background: linear-gradient(90deg, transparent, var(–border2), transparent);  
}  
.stat:hover { border-color: var(–border2); }  
.stat-val {  
font-family: ‘JetBrains Mono’, monospace;  
font-size: 28px; font-weight: 500;  
color: var(–text);  
line-height: 1;  
letter-spacing: -1px;  
}  
.stat-label {  
font-size: 11px; font-weight: 500;  
color: var(–muted);  
margin-top: 5px;  
text-transform: uppercase; letter-spacing: 0.8px;  
}  
  
/* ── SECTION LABEL ── */  
.section-label {  
font-size: 11px; font-weight: 600;  
color: var(–muted);  
text-transform: uppercase; letter-spacing: 1.2px;  
margin-bottom: 10px;  
padding-left: 2px;  
}  
  
/* ── CARDS ── */  
.cards { display: flex; flex-direction: column; gap: 8px; }  
  
.card {  
background: var(–surface);  
border: 1px solid var(–border);  
border-radius: var(–radius);  
padding: 16px 18px;  
display: grid;  
grid-template-columns: 38px 1fr auto auto;  
align-items: center;  
gap: 14px;  
transition: border-color 0.2s, box-shadow 0.2s, transform 0.15s;  
animation: cardIn 0.28s cubic-bezier(0.34,1.56,0.64,1);  
position: relative; overflow: hidden;  
}  
.card::before {  
content: ‘’;  
position: absolute; top: 0; left: 0; bottom: 0; width: 2px;  
background: linear-gradient(180deg, var(–accent), var(–cyan));  
opacity: 0;  
transition: opacity 0.2s;  
}  
.card:hover { border-color: var(–border2); box-shadow: 0 4px 24px rgba(0,0,0,0.4); transform: translateY(-1px); }  
.card:hover::before { opacity: 1; }  
  
@keyframes cardIn {  
from { opacity:0; transform:translateY(10px) scale(0.98); }  
to   { opacity:1; transform:translateY(0) scale(1); }  
}  
  
.card-num {  
width: 38px; height: 38px;  
border-radius: 10px;  
background: var(–surface2);  
border: 1px solid var(–border2);  
display: flex; align-items: center; justify-content: center;  
font-family: ‘JetBrains Mono’, monospace;  
font-size: 12px; font-weight: 400;  
color: var(–muted);  
flex-shrink: 0;  
}  
  
.card-info { min-width: 0; }  
.card-name {  
font-size: 15px; font-weight: 700;  
color: var(–text);  
white-space: nowrap; overflow: hidden; text-overflow: ellipsis;  
letter-spacing: -0.2px;  
}  
.card-loc {  
font-size: 12px; font-weight: 400;  
color: var(–sub);  
margin-top: 3px;  
white-space: nowrap; overflow: hidden; text-overflow: ellipsis;  
}  
  
/* ── CLOCK ── */  
.dig-clock {  
display: flex; align-items: center; gap: 0;  
flex-shrink: 0;  
background: var(–surface2);  
border: 1px solid var(–border2);  
border-radius: var(–radius-sm);  
padding: 7px 11px;  
box-shadow: inset 0 1px 0 rgba(255,255,255,0.03);  
}  
.dig-seg {  
font-family: ‘JetBrains Mono’, monospace;  
font-size: clamp(13px, 3.2vw, 18px);  
font-weight: 500;  
color: var(–accent2);  
font-variant-numeric: tabular-nums;  
min-width: 2ch;  
text-align: center;  
line-height: 1;  
}  
.dig-sep {  
font-family: ‘JetBrains Mono’, monospace;  
font-size: clamp(11px, 2.8vw, 15px);  
font-weight: 300;  
color: var(–muted);  
padding: 0 1px;  
line-height: 1;  
animation: blink 1s steps(1) infinite;  
}  
@keyframes blink { 0%,49%{opacity:1;} 50%,100%{opacity:0.25;} }  
  
.card-actions { display: flex; gap: 5px; flex-shrink: 0; }  
.icon-btn {  
width: 32px; height: 32px;  
border-radius: 8px;  
border: 1px solid var(–border2);  
background: var(–surface2);  
display: flex; align-items: center; justify-content: center;  
cursor: pointer;  
font-size: 13px; color: var(–muted);  
transition: all 0.15s;  
}  
.icon-btn:hover { transform: scale(1.08); }  
.btn-edit:hover { background: rgba(124,109,250,0.15); color: var(–accent2); border-color: rgba(124,109,250,0.35); }  
.btn-del:hover  { background: rgba(248,113,113,0.1);  color: var(–danger);  border-color: rgba(248,113,113,0.3); }  
  
/* ── EDIT MODE ── */  
.card.editing {  
grid-template-columns: 38px 1fr;  
border-color: var(–accent);  
box-shadow: 0 0 0 3px var(–glow), 0 4px 24px rgba(0,0,0,0.4);  
}  
.card.editing::before { opacity: 1; }  
.edit-fields { grid-column: 2/-1; display: flex; flex-direction: column; gap: 8px; }  
  
.edit-input {  
background: var(–surface2);  
border: 1px solid var(–border2);  
border-radius: var(–radius-sm);  
padding: 9px 13px;  
font-family: ‘Syne’, sans-serif;  
font-size: 14px; font-weight: 500;  
color: var(–text);  
outline: none; width: 100%;  
transition: border-color 0.2s, box-shadow 0.2s;  
}  
.edit-input:focus { border-color: var(–accent); box-shadow: 0 0 0 3px var(–glow); }  
.edit-input::placeholder { color: var(–muted); }  
  
.loc-btn-edit {  
background: var(–surface2);  
border: 1px solid var(–border2);  
border-radius: var(–radius-sm);  
padding: 9px 13px;  
font-family: ‘Syne’, sans-serif;  
font-size: 13px; color: var(–sub);  
cursor: pointer; width: 100%;  
display: flex; align-items: center; justify-content: space-between; gap: 8px;  
transition: border-color 0.2s;  
}  
.loc-btn-edit:hover { border-color: var(–accent); color: var(–text); }  
.loc-btn-edit span { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }  
  
.edit-actions { display: flex; gap: 8px; }  
.btn-sm {  
padding: 8px 18px;  
border-radius: var(–radius-sm);  
border: none; cursor: pointer;  
font-family: ‘Syne’, sans-serif;  
font-size: 13px; font-weight: 600;  
transition: all 0.15s;  
}  
.btn-save {  
background: linear-gradient(135deg, var(–accent) 0%, var(–accent2) 100%);  
color: #fff;  
box-shadow: 0 2px 12px rgba(124,109,250,0.35);  
}  
.btn-save:hover { transform: translateY(-1px); box-shadow: 0 4px 18px rgba(124,109,250,0.5); }  
.btn-cancel { background: var(–surface3); color: var(–sub); border: 1px solid var(–border2); }  
.btn-cancel:hover { color: var(–text); background: var(–border2); }  
  
/* ── EMPTY ── */  
.empty { text-align: center; padding: 60px 20px; color: var(–muted); }  
.empty-icon { font-size: 42px; margin-bottom: 14px; opacity: 0.3; }  
.empty p { font-size: 14px; font-weight: 500; color: var(–muted); line-height: 1.6; }  
  
/* ── ADD BAR ── */  
.add-bar {  
position: fixed; bottom: 0; left: 0; right: 0; z-index: 100;  
background: rgba(12,13,17,0.92);  
backdrop-filter: blur(24px);  
-webkit-backdrop-filter: blur(24px);  
border-top: 1px solid var(–border);  
padding: 12px 16px 16px;  
}  
.add-inner { max-width: 680px; margin: 0 auto; }  
.add-row { display: flex; gap: 8px; align-items: stretch; }  
  
.add-input {  
flex: 1; min-width: 0;  
background: var(–surface);  
border: 1px solid var(–border2);  
border-radius: var(–radius-sm);  
padding: 10px 14px;  
font-family: ‘Syne’, sans-serif;  
font-size: 14px; color: var(–text);  
outline: none;  
transition: border-color 0.2s, box-shadow 0.2s;  
}  
.add-input:focus { border-color: var(–accent); box-shadow: 0 0 0 3px var(–glow); }  
.add-input::placeholder { color: var(–muted); }  
  
.loc-btn {  
flex: 1.5; min-width: 0;  
background: var(–surface);  
border: 1px solid var(–border2);  
border-radius: var(–radius-sm);  
padding: 10px 14px;  
font-family: ‘Syne’, sans-serif;  
font-size: 13px; color: var(–sub);  
cursor: pointer;  
display: flex; align-items: center; justify-content: space-between; gap: 6px;  
transition: border-color 0.2s, color 0.2s;  
}  
.loc-btn:hover { border-color: var(–accent); color: var(–text); }  
.loc-btn span { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }  
.loc-btn svg { flex-shrink: 0; opacity: 0.5; }  
  
.add-btn {  
flex-shrink: 0;  
background: linear-gradient(135deg, var(–accent) 0%, #6055e0 100%);  
color: #fff;  
border: none;  
border-radius: var(–radius-sm);  
padding: 10px 20px;  
font-family: ‘Syne’, sans-serif;  
font-size: 14px; font-weight: 700;  
cursor: pointer; white-space: nowrap;  
transition: all 0.15s;  
box-shadow: 0 2px 14px rgba(124,109,250,0.35);  
}  
.add-btn:hover { transform: translateY(-1px); box-shadow: 0 4px 20px rgba(124,109,250,0.5); }  
.add-btn:active { transform: translateY(0); }  
  
/* ── MODAL ── */  
.modal-overlay {  
display: none;  
position: fixed; inset: 0; z-index: 200;  
background: rgba(0,0,0,0.6);  
backdrop-filter: blur(6px);  
-webkit-backdrop-filter: blur(6px);  
align-items: flex-end; justify-content: center;  
}  
.modal-overlay.open { display: flex; animation: fadeIn 0.2s ease; }  
@keyframes fadeIn { from{opacity:0;} to{opacity:1;} }  
  
.modal {  
background: var(–surface);  
border: 1px solid var(–border2);  
border-radius: var(–radius) var(–radius) 0 0;  
width: 100%; max-width: 600px;  
max-height: 80vh;  
display: flex; flex-direction: column;  
box-shadow: 0 -16px 60px rgba(0,0,0,0.6);  
animation: slideUp 0.28s cubic-bezier(0.34,1.2,0.64,1);  
}  
@keyframes slideUp { from{transform:translateY(100%);} to{transform:translateY(0);} }  
  
.modal-handle {  
width: 36px; height: 3px;  
background: var(–border2);  
border-radius: 2px;  
margin: 10px auto 0;  
flex-shrink: 0;  
}  
.modal-header {  
padding: 14px 20px 12px;  
display: flex; align-items: center; justify-content: space-between;  
border-bottom: 1px solid var(–border);  
flex-shrink: 0;  
}  
.modal-title {  
font-size: 15px; font-weight: 700;  
color: var(–text); letter-spacing: -0.2px;  
}  
.modal-close {  
width: 28px; height: 28px;  
border-radius: 7px;  
border: 1px solid var(–border2);  
background: var(–surface2);  
color: var(–muted); cursor: pointer;  
font-size: 14px;  
display: flex; align-items: center; justify-content: center;  
transition: all 0.15s;  
}  
.modal-close:hover { background: var(–surface3); color: var(–text); }  
  
.modal-search {  
padding: 12px 16px; flex-shrink: 0;  
border-bottom: 1px solid var(–border);  
}  
.modal-search input {  
width: 100%;  
background: var(–surface2);  
border: 1px solid var(–border2);  
border-radius: var(–radius-sm);  
padding: 9px 14px;  
font-family: ‘Syne’, sans-serif;  
font-size: 14px; color: var(–text); outline: none;  
transition: border-color 0.2s, box-shadow 0.2s;  
}  
.modal-search input:focus { border-color: var(–accent); box-shadow: 0 0 0 3px var(–glow); }  
.modal-search input::placeholder { color: var(–muted); }  
  
.modal-list { overflow-y: auto; flex: 1; }  
  
.modal-group {  
padding: 10px 16px 4px;  
font-size: 10px; font-weight: 700;  
color: var(–muted);  
text-transform: uppercase; letter-spacing: 1.2px;  
position: sticky; top: 0;  
background: var(–surface); z-index: 1;  
border-bottom: 1px solid var(–border);  
}  
.modal-opt {  
padding: 12px 16px;  
cursor: pointer;  
font-size: 14px; font-weight: 500;  
color: var(–sub);  
display: flex; align-items: center; justify-content: space-between;  
border-bottom: 1px solid rgba(37,40,54,0.6);  
transition: background 0.1s, color 0.1s;  
}  
.modal-opt:hover { background: var(–surface2); color: var(–text); }  
.modal-opt.sel { color: var(–accent2); }  
.modal-opt .chk { color: var(–accent2); font-size: 12px; }  
  
::-webkit-scrollbar { width: 3px; }  
::-webkit-scrollbar-track { background: transparent; }  
::-webkit-scrollbar-thumb { background: var(–border2); border-radius: 2px; }  
  
/* ── RESPONSIVE ── */  
@media (max-width: 520px) {  
.card { grid-template-columns: 34px 1fr auto auto; gap: 10px; padding: 13px 14px; }  
.card-num { width: 34px; height: 34px; }  
.dig-clock { padding: 6px 8px; }  
.dig-seg { font-size: 13px; }  
.dig-sep { font-size: 11px; }  
.add-row { flex-wrap: wrap; }  
.add-input { flex: 1 1 100%; }  
.loc-btn { flex: 1; }  
.stats { gap: 8px; }  
.stat-val { font-size: 24px; }  
header { padding: 0 14px; }  
}  
</style>  
  
</head>  
<body>  
  
<header>  
  <div class="header-left">  
    <div class="header-icon">🌐</div>  
    <div class="header-title">Staff Time Zones</div>  
  </div>  
  <div class="live-badge">  
    <div class="live-dot"></div>  
    LIVE  
  </div>  
</header>  
  
<main>  
  <div class="stats">  
    <div class="stat">  
      <div class="stat-val" id="stat-count">0</div>  
      <div class="stat-label">Members</div>  
    </div>  
    <div class="stat">  
      <div class="stat-val" id="stat-zones">0</div>  
      <div class="stat-label">Zones</div>  
    </div>  
    <div class="stat">  
      <div class="stat-val" id="stat-date" style="font-size:15px;padding-top:4px;letter-spacing:-0.3px;"></div>  
      <div class="stat-label">Today</div>  
    </div>  
  </div>  
  
  <div class="section-label">Team</div>  
  <div class="cards" id="cards"></div>  
</main>  
  
<!-- ADD BAR -->  
  
<div class="add-bar">  
  <div class="add-inner">  
    <div class="add-row">  
      <input class="add-input" id="new-nick" type="text" placeholder="Name" autocomplete="off"/>  
      <button class="loc-btn" onclick="openModal('add')">  
        <span id="loc-btn-text">Select location…</span>  
        <svg width="12" height="12" viewBox="0 0 12 12" fill="none"><path d="M2 4l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>  
      </button>  
      <button class="add-btn" onclick="addRow()">Add</button>  
    </div>  
  </div>  
</div>  
  
<!-- MODAL -->  
  
<div class="modal-overlay" id="modal-overlay" onclick="handleOverlayClick(event)">  
  <div class="modal">  
    <div class="modal-handle"></div>  
    <div class="modal-header">  
      <div class="modal-title">Select Location</div>  
      <button class="modal-close" onclick="closeModal()">✕</button>  
    </div>  
    <div class="modal-search">  
      <input type="text" id="modal-search" placeholder="Search cities or states…" oninput="filterModal(this.value)"/>  
    </div>  
    <div class="modal-list" id="modal-list"></div>  
  </div>  
</div>  
  
<script>  
const GROUPS = [  
  { name:"🇺🇸 US States", places:[  
    ["Alabama, USA","America/Chicago"],["Alaska, USA","America/Anchorage"],  
    ["Arizona, USA","America/Phoenix"],["Arkansas, USA","America/Chicago"],  
    ["California, USA","America/Los_Angeles"],["Colorado, USA","America/Denver"],  
    ["Connecticut, USA","America/New_York"],["Delaware, USA","America/New_York"],  
    ["Florida, USA","America/New_York"],["Georgia, USA","America/New_York"],  
    ["Hawaii, USA","Pacific/Honolulu"],["Idaho, USA","America/Denver"],  
    ["Illinois, USA","America/Chicago"],["Indiana, USA","America/Indiana/Indianapolis"],  
    ["Iowa, USA","America/Chicago"],["Kansas, USA","America/Chicago"],  
    ["Kentucky, USA","America/New_York"],["Louisiana, USA","America/Chicago"],  
    ["Maine, USA","America/New_York"],["Maryland, USA","America/New_York"],  
    ["Massachusetts, USA","America/New_York"],["Michigan, USA","America/Detroit"],  
    ["Minnesota, USA","America/Chicago"],["Mississippi, USA","America/Chicago"],  
    ["Missouri, USA","America/Chicago"],["Montana, USA","America/Denver"],  
    ["Nebraska, USA","America/Chicago"],["Nevada, USA","America/Los_Angeles"],  
    ["New Hampshire, USA","America/New_York"],["New Jersey, USA","America/New_York"],  
    ["New Mexico, USA","America/Denver"],["New York, USA","America/New_York"],  
    ["North Carolina, USA","America/New_York"],["North Dakota, USA","America/Chicago"],  
    ["Ohio, USA","America/New_York"],["Oklahoma, USA","America/Chicago"],  
    ["Oregon, USA","America/Los_Angeles"],["Pennsylvania, USA","America/New_York"],  
    ["Rhode Island, USA","America/New_York"],["South Carolina, USA","America/New_York"],  
    ["South Dakota, USA","America/Chicago"],["Tennessee, USA","America/Chicago"],  
    ["Texas, USA","America/Chicago"],["Utah, USA","America/Denver"],  
    ["Vermont, USA","America/New_York"],["Virginia, USA","America/New_York"],  
    ["Washington, USA","America/Los_Angeles"],["Washington D.C., USA","America/New_York"],  
    ["West Virginia, USA","America/New_York"],["Wisconsin, USA","America/Chicago"],  
    ["Wyoming, USA","America/Denver"],  
  ]},  
  { name:"🌎 Americas", places:[  
    ["Toronto, Canada","America/Toronto"],["Vancouver, Canada","America/Vancouver"],  
    ["Calgary, Canada","America/Edmonton"],["Montreal, Canada","America/Toronto"],  
    ["Mexico City, Mexico","America/Mexico_City"],["Cancun, Mexico","America/Cancun"],  
    ["Sao Paulo, Brazil","America/Sao_Paulo"],["Buenos Aires, Argentina","America/Argentina/Buenos_Aires"],  
    ["Santiago, Chile","America/Santiago"],["Bogota, Colombia","America/Bogota"],  
    ["Lima, Peru","America/Lima"],["Caracas, Venezuela","America/Caracas"],  
    ["Panama City, Panama","America/Panama"],["Kingston, Jamaica","America/Jamaica"],  
    ["Havana, Cuba","America/Havana"],  
  ]},  
  { name:"🌍 Europe", places:[  
    ["London, UK","Europe/London"],["Paris, France","Europe/Paris"],  
    ["Berlin, Germany","Europe/Berlin"],["Madrid, Spain","Europe/Madrid"],  
    ["Rome, Italy","Europe/Rome"],["Amsterdam, Netherlands","Europe/Amsterdam"],  
    ["Brussels, Belgium","Europe/Brussels"],["Zurich, Switzerland","Europe/Zurich"],  
    ["Vienna, Austria","Europe/Vienna"],["Stockholm, Sweden","Europe/Stockholm"],  
    ["Oslo, Norway","Europe/Oslo"],["Copenhagen, Denmark","Europe/Copenhagen"],  
    ["Helsinki, Finland","Europe/Helsinki"],["Warsaw, Poland","Europe/Warsaw"],  
    ["Prague, Czech Republic","Europe/Prague"],["Budapest, Hungary","Europe/Budapest"],  
    ["Bucharest, Romania","Europe/Bucharest"],["Athens, Greece","Europe/Athens"],  
    ["Lisbon, Portugal","Europe/Lisbon"],["Dublin, Ireland","Europe/Dublin"],  
    ["Moscow, Russia","Europe/Moscow"],["Kyiv, Ukraine","Europe/Kiev"],  
    ["Istanbul, Turkey","Europe/Istanbul"],["Reykjavik, Iceland","Atlantic/Reykjavik"],  
    ["Belgrade, Serbia","Europe/Belgrade"],["Sofia, Bulgaria","Europe/Sofia"],  
    ["Vilnius, Lithuania","Europe/Vilnius"],["Riga, Latvia","Europe/Riga"],  
    ["Tallinn, Estonia","Europe/Tallinn"],  
  ]},  
  { name:"🕌 Middle East", places:[  
    ["Riyadh, Saudi Arabia","Asia/Riyadh"],["Dubai, UAE","Asia/Dubai"],  
    ["Jerusalem, Israel","Asia/Jerusalem"],["Doha, Qatar","Asia/Qatar"],  
    ["Kuwait City, Kuwait","Asia/Kuwait"],["Muscat, Oman","Asia/Muscat"],  
    ["Amman, Jordan","Asia/Amman"],["Beirut, Lebanon","Asia/Beirut"],  
    ["Tehran, Iran","Asia/Tehran"],["Baghdad, Iraq","Asia/Baghdad"],  
  ]},  
  { name:"🌍 Africa", places:[  
    ["Johannesburg, South Africa","Africa/Johannesburg"],["Lagos, Nigeria","Africa/Lagos"],  
    ["Nairobi, Kenya","Africa/Nairobi"],["Cairo, Egypt","Africa/Cairo"],  
    ["Accra, Ghana","Africa/Accra"],["Addis Ababa, Ethiopia","Africa/Addis_Ababa"],  
    ["Dar es Salaam, Tanzania","Africa/Dar_es_Salaam"],["Casablanca, Morocco","Africa/Casablanca"],  
    ["Dakar, Senegal","Africa/Dakar"],["Harare, Zimbabwe","Africa/Harare"],  
  ]},  
  { name:"🌏 Asia", places:[  
    ["Tokyo, Japan","Asia/Tokyo"],["Shanghai, China","Asia/Shanghai"],  
    ["Beijing, China","Asia/Shanghai"],["Mumbai, India","Asia/Kolkata"],  
    ["Delhi, India","Asia/Kolkata"],["Seoul, South Korea","Asia/Seoul"],  
    ["Singapore","Asia/Singapore"],["Hong Kong","Asia/Hong_Kong"],  
    ["Taipei, Taiwan","Asia/Taipei"],["Bangkok, Thailand","Asia/Bangkok"],  
    ["Ho Chi Minh City, Vietnam","Asia/Ho_Chi_Minh"],["Kuala Lumpur, Malaysia","Asia/Kuala_Lumpur"],  
    ["Jakarta, Indonesia","Asia/Jakarta"],["Manila, Philippines","Asia/Manila"],  
    ["Karachi, Pakistan","Asia/Karachi"],["Dhaka, Bangladesh","Asia/Dhaka"],  
    ["Colombo, Sri Lanka","Asia/Colombo"],["Kathmandu, Nepal","Asia/Kathmandu"],  
    ["Almaty, Kazakhstan","Asia/Almaty"],["Baku, Azerbaijan","Asia/Baku"],  
    ["Tbilisi, Georgia","Asia/Tbilisi"],["Yerevan, Armenia","Asia/Yerevan"],  
  ]},  
  { name:"🌏 Oceania", places:[  
    ["Sydney, Australia","Australia/Sydney"],["Melbourne, Australia","Australia/Melbourne"],  
    ["Brisbane, Australia","Australia/Brisbane"],["Perth, Australia","Australia/Perth"],  
    ["Adelaide, Australia","Australia/Adelaide"],["Auckland, New Zealand","Pacific/Auckland"],  
    ["Suva, Fiji","Pacific/Fiji"],  
  ]},  
];  
  
const TZ_MAP = {};  
GROUPS.forEach(g => g.places.forEach(([l,t]) => { TZ_MAP[l]=t; }));  
  
let rows = [  
  {id:1, name:"Big Mike", location:"Texas, USA"},  
  {id:2, name:"Sunny",    location:"California, USA"},  
  {id:3, name:"Ace",      location:"New York, USA"},  
];  
let nextId=4, editingId=null, selLoc="Texas, USA", modalTarget='add';  
const clockEls={};  
  
function buildClock(el) {  
  el.innerHTML=`<span class="dig-seg" data-p="h"></span><span class="dig-sep">:</span><span class="dig-seg" data-p="m"></span><span class="dig-sep">:</span><span class="dig-seg" data-p="s"></span>`;  
}  
function tickClock(el,tz){  
  if(!el)return;  
  try{  
    const fmt=new Intl.DateTimeFormat('en-US',{timeZone:tz,hour:'2-digit',minute:'2-digit',second:'2-digit',hour12:false});  
    const parts=fmt.formatToParts(new Date());  
    const get=t=>{const p=parts.find(x=>x.type===t);return p?(p.value==='24'?'00':p.value):'00';};  
    el.querySelector('[data-p="h"]').textContent=get('hour');  
    el.querySelector('[data-p="m"]').textContent=get('minute');  
    el.querySelector('[data-p="s"]').textContent=get('second');  
  }catch(e){}  
}  
function tickAll(){  
  Object.values(clockEls).forEach(({el,tz})=>tickClock(el,tz));  
  const d=new Date();  
  const sd=document.getElementById('stat-date');  
  if(sd) sd.textContent=d.toLocaleDateString('en-US',{month:'short',day:'numeric'});  
}  
  
function openModal(target){  
  modalTarget=target;  
  document.getElementById('modal-search').value='';  
  renderModalList('');  
  document.getElementById('modal-overlay').classList.add('open');  
  setTimeout(()=>document.getElementById('modal-search').focus(),150);  
}  
function closeModal(){ document.getElementById('modal-overlay').classList.remove('open'); }  
function handleOverlayClick(e){ if(e.target===document.getElementById('modal-overlay')) closeModal(); }  
function renderModalList(q){  
  const list=document.getElementById('modal-list');  
  list.innerHTML='';  
  const sq=q.toLowerCase();  
  let any=false;  
  GROUPS.forEach(g=>{  
    const hits=g.places.filter(([l])=>!sq||l.toLowerCase().includes(sq));  
    if(!hits.length)return;  
    any=true;  
    const gl=document.createElement('div');  
    gl.className='modal-group';gl.textContent=g.name;list.appendChild(gl);  
    hits.forEach(([label])=>{  
      const cur=modalTarget==='add'?selLoc:(rows.find(r=>r.id===modalTarget)?.location);  
      const opt=document.createElement('div');  
      opt.className='modal-opt'+(label===cur?' sel':'');  
      opt.innerHTML=`<span>${label}</span>${label===cur?'<span class="chk">✓</span>':''}`;  
      opt.onclick=()=>pickLoc(label);  
      list.appendChild(opt);  
    });  
  });  
  if(!any) list.innerHTML='<div style="padding:32px;text-align:center;color:#4a4f6a;font-size:14px;font-weight:500;">No results</div>';  
}  
function filterModal(q){renderModalList(q);}  
function pickLoc(label){  
  if(modalTarget==='add'){selLoc=label;document.getElementById('loc-btn-text').textContent=label;}  
  else{const el=document.getElementById('edit-loc-label-'+modalTarget);if(el)el.textContent=label;}  
  closeModal();  
}  
  
function render(){  
  const container=document.getElementById('cards');  
  container.innerHTML='';  
  Object.keys(clockEls).forEach(k=>delete clockEls[k]);  
  if(!rows.length){  
    container.innerHTML=`<div class="empty"><div class="empty-icon">🌐</div><p>No staff members yet.<br>Add one below.</p></div>`;  
    updateStats();return;  
  }  
  rows.forEach((row,i)=>{  
    const tz=TZ_MAP[row.location]||'UTC';  
    const cid='clock-'+row.id;  
    const card=document.createElement('div');  
    if(editingId===row.id){  
      card.className='card editing';  
      card.innerHTML=`  
        <div class="card-num">${String(i+1).padStart(2,'0')}</div>  
        <div class="edit-fields">  
          <input class="edit-input" id="edit-name-${row.id}" value="${row.name}" placeholder="Name" autocomplete="off"/>  
          <button class="loc-btn-edit" onclick="openModal(${row.id})">  
            <span id="edit-loc-label-${row.id}">${row.location}</span>  
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none"><path d="M2 4l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>  
          </button>  
          <div class="edit-actions">  
            <button class="btn-sm btn-save" onclick="saveEdit(${row.id})">Save</button>  
            <button class="btn-sm btn-cancel" onclick="cancelEdit()">Cancel</button>  
          </div>  
        </div>`;  
    } else {  
      card.className='card';  
      card.innerHTML=`  
        <div class="card-num">${String(i+1).padStart(2,'0')}</div>  
        <div class="card-info">  
          <div class="card-name">${row.name}</div>  
          <div class="card-loc">${row.location}</div>  
        </div>  
        <div class="dig-clock" id="${cid}"></div>  
        <div class="card-actions">  
          <button class="icon-btn btn-edit" onclick="startEdit(${row.id})">✎</button>  
          <button class="icon-btn btn-del"  onclick="deleteRow(${row.id})">✕</button>  
        </div>`;  
    }  
    container.appendChild(card);  
    if(editingId!==row.id){  
      const el=document.getElementById(cid);  
      buildClock(el);  
      clockEls[row.id]={el,tz};  
      tickClock(el,tz);  
    }  
  });  
  updateStats();  
}  
  
function updateStats(){  
  document.getElementById('stat-count').textContent=rows.length;  
  document.getElementById('stat-zones').textContent=new Set(rows.map(r=>TZ_MAP[r.location])).size;  
  document.getElementById('stat-date').textContent=new Date().toLocaleDateString('en-US',{month:'short',day:'numeric'});  
}  
  
function addRow(){  
  const name=document.getElementById('new-nick').value.trim();  
  if(!name){document.getElementById('new-nick').focus();return;}  
  if(selLoc.includes('…')){openModal('add');return;}  
  rows.push({id:nextId++,name,location:selLoc});  
  document.getElementById('new-nick').value='';  
  render();  
}  
function deleteRow(id){rows=rows.filter(r=>r.id!==id);if(editingId===id)editingId=null;render();}  
function startEdit(id){editingId=id;render();setTimeout(()=>document.getElementById('edit-name-'+id)?.focus(),50);}  
function saveEdit(id){  
  const name=document.getElementById('edit-name-'+id)?.value.trim();  
  const loc=document.getElementById('edit-loc-label-'+id)?.textContent;  
  if(!name)return;  
  rows=rows.map(r=>r.id===id?{...r,name,location:loc||r.location}:r);  
  editingId=null;render();  
}  
function cancelEdit(){editingId=null;render();}  
  
document.getElementById('new-nick').addEventListener('keydown',e=>{if(e.key==='Enter')addRow();});  
  
render();tickAll();setInterval(tickAll,1000);  
</script>  
  
</body>  
</html>  
