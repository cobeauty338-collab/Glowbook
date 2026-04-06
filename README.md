<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>GlowBook 💄</title>
<style>
*{margin:0;padding:0;box-sizing:border-box}
body{background:#0f0e0e;color:#f0ece4;font-family:'Helvetica Neue',sans-serif;max-width:420px;margin:0 auto;min-height:100vh}
input,button,textarea{font-family:inherit}
::-webkit-scrollbar{display:none}
/* SPLASH */
.splash{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:100vh;padding:40px 28px;background:radial-gradient(ellipse at 60% 20%,#2e1f0e 0%,#0f0e0e 60%)}
.role-card{width:100%;background:#1a1818;border:1px solid #2e2b28;border-radius:20px;padding:22px 24px;margin-bottom:12px;cursor:pointer;display:flex;align-items:center;gap:16px;transition:transform .15s}
.role-card:active{transform:scale(.98)}
/* LAYOUT */
.header{padding:14px 16px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid #2e2b28;position:sticky;top:0;background:#0f0e0e;z-index:100}
.sec{padding:14px 14px 0}
.sec-t{font-size:11px;font-weight:700;color:#8a857d;text-transform:uppercase;letter-spacing:.1em;margin-bottom:10px}
.card{background:#1a1818;border:1px solid #2e2b28;border-radius:14px;padding:14px;margin-bottom:10px}
/* INPUTS */
input,textarea{width:100%;background:#111;border:1px solid #2e2b28;border-radius:10px;padding:11px 13px;color:#f0ece4;font-size:15px;box-sizing:border-box;margin-bottom:10px;outline:none}
input:focus,textarea:focus{border-color:#e8b86d}
textarea{resize:none;height:70px}
/* BUTTONS */
.btn{width:100%;background:#e8b86d;color:#1a1410;border:none;border-radius:14px;padding:15px;font-size:16px;font-weight:800;cursor:pointer;margin-top:6px;transition:opacity .15s}
.btn:disabled{opacity:.5;cursor:not-allowed}
.btn-o{width:100%;background:transparent;color:#e8b86d;border:1px solid #e8b86d;border-radius:14px;padding:13px;font-size:14px;font-weight:700;cursor:pointer;margin-top:6px}
.btn-s{background:#e8b86d;color:#1a1410;border:none;border-radius:8px;padding:7px 13px;font-size:12px;font-weight:700;cursor:pointer}
.btn-r{background:rgba(255,100,100,.1);color:#ff8080;border:1px solid rgba(255,100,100,.2);border-radius:8px;padding:7px 13px;font-size:12px;font-weight:700;cursor:pointer}
/* BADGES */
.badge{display:inline-flex;align-items:center;background:rgba(232,184,109,.12);color:#e8b86d;border-radius:8px;padding:3px 8px;font-size:11px;font-weight:600}
.err{color:#ff8080;font-size:13px;margin-bottom:8px;padding:8px 12px;background:rgba(255,100,100,.08);border-radius:8px}
/* TABS */
.tab-bar{display:flex;background:#1a1818;border-top:1px solid #2e2b28;position:sticky;bottom:0;z-index:100}
.tab{flex:1;padding:11px 4px;text-align:center;cursor:pointer;font-size:10px;font-weight:600;border:none;background:none;color:#8a857d}
.tab.on{color:#e8b86d}
/* FEED PINTEREST */
.feed-grid{columns:2;gap:8px;padding:8px}
.feed-item{break-inside:avoid;margin-bottom:8px;border-radius:14px;overflow:hidden;background:#1a1818;cursor:pointer;border:1px solid #2e2b28;position:relative}
.feed-item img{width:100%;display:block;object-fit:cover}
.feed-item-info{padding:10px}
.feed-placeholder{width:100%;aspect-ratio:3/4;background:linear-gradient(135deg,#2e1f0e,#1a1818);display:flex;align-items:center;justify-content:center;font-size:40px}
/* DAYS/SLOTS */
.days-row{display:flex;gap:6px;overflow-x:auto;padding-bottom:6px;margin-bottom:12px}
.dc{flex-shrink:0;padding:7px 11px;border-radius:10px;font-size:12px;font-weight:600;cursor:pointer;border:1px solid #2e2b28;background:transparent;color:#f0ece4}
.dc.on{background:#e8b86d;color:#1a1410;border-color:#e8b86d}
.slots{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px}
.slot{padding:10px 4px;border-radius:10px;text-align:center;font-size:12px;font-weight:600;cursor:pointer;border:1px solid #2e2b28;background:transparent;color:#f0ece4}
.slot.on{background:#e8b86d;color:#1a1410;border-color:#e8b86d}
.slot.tk{opacity:.3;cursor:not-allowed;text-decoration:line-through}
/* PHOTOS */
.photos-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin-bottom:12px}
.ph{aspect-ratio:1;border-radius:10px;overflow:hidden;background:#111;border:1px solid #2e2b28}
.ph img{width:100%;height:100%;object-fit:cover}
.ph-add{aspect-ratio:1;border-radius:10px;border:2px dashed #2e2b28;display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:28px;background:#111;flex-direction:column;gap:4px}
/* PAYMENT */
.pay-opt{background:#1a1818;border:2px solid #2e2b28;border-radius:14px;padding:14px;margin-bottom:10px;cursor:pointer;display:flex;align-items:center;gap:14px}
.pay-opt.on{border-color:#e8b86d;background:rgba(232,184,109,.06)}
/* PLAN CARDS */
.plan-card{background:#1a1818;border:2px solid #2e2b28;border-radius:16px;padding:16px;margin-bottom:10px;cursor:pointer}
.plan-card.on{border-color:#e8b86d}
/* MISC */
.link{color:#e8b86d;font-size:13px;cursor:pointer;text-align:center;margin-top:10px;display:block}
.pb80{padding-bottom:80px}
.svc-row{display:flex;justify-content:space-between;align-items:center;padding:12px 0;border-bottom:1px solid #2e2b28}
.svc-row:last-child{border-bottom:none}
.stat{background:#1a1818;border:1px solid #2e2b28;border-radius:14px;padding:14px;text-align:center}
.booking-card{background:#1a1818;border:1px solid #2e2b28;border-radius:14px;padding:14px;margin-bottom:10px}
.modal{position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,.85);z-index:200;display:flex;align-items:flex-end;max-width:420px;margin:0 auto}
.modal-content{background:#1a1818;border-radius:20px 20px 0 0;padding:24px 20px;width:100%;max-height:90vh;overflow-y:auto}
</style>
</head>
<body>
<div id="app"></div>
<script>
const SB="https://xecvmzamdyzjggoqpccr.supabase.co";
const KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InhlY3ZtemFtZHl6amdnb3FwY2NyIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzUxNTMxNDksImV4cCI6MjA5MDcyOTE0OX0.PaYTrpbWInqZuq2I6B-cV2IQof-0j98a8vnF3QIay9c";

const db=async(table,method="GET",body=null,filter="")=>{
  const r=await fetch(`${SB}/rest/v1/${table}${filter}`,{
    method,
    headers:{"Content-Type":"application/json","apikey":KEY,"Authorization":"Bearer "+KEY,"Prefer":method==="POST"?"return=representation":""},
    body:body?JSON.stringify(body):null
  });
  if(!r.ok)throw new Error(await r.text());
  const t=await r.text();return t?JSON.parse(t):[];
};

const TIMES=["09:00","10:00","11:00","12:00","13:00","14:00","15:00","16:00","17:00"];
const DAYS=["Lun 7","Mar 8","Mer 9","Jeu 10","Ven 11","Sam 12","Dim 13"];
const PLANS={
  starter:{label:"Starter",price:0,commission:8,photos:5,color:"#8a857d"},
  standard:{label:"Standard",price:5000,commission:5,photos:50,color:"#e8b86d"},
  premium:{label:"Premium",price:12000,commission:3,photos:999,color:"#e88fa0"}
};

let S={
  page:"splash",
  // client
  cView:"home",client:null,cName:"",cPhone:"",cPass:"",cAuthMode:"login",
  feed:[],salon:null,svcs:[],svc:null,
  day:null,time:null,takenSlots:[],
  payMethod:"mtn",payPhone:"",booked:false,
  // provider
  pView:"setup",provSalon:null,
  pSalonName:"",pAddress:"",pPhone:"",pPass:"",pAuthMode:"login",
  pTab:"agenda",pBookings:[],pSvcs:[],pPortfolio:[],
  svcName:"",svcDur:"",svcPrice:"",
  // upload modal
  showUploadModal:false,
  uploadPhoto:null,uploadPreview:"",
  uploadName:"",uploadTotal:"",uploadLabor:"",
  // filter
  filterDay:"all",
  loading:false,err:""
};

const $=id=>document.getElementById(id);
const R=()=>{$("app").innerHTML=build();bind()};

function build(){
  if(S.page==="splash")return splash();
  if(S.page==="client")return clientPage();
  if(S.page==="provider")return providerPage();
  return "";
}

// ===== SPLASH =====
function splash(){
  return`<div class="splash">
    <div style="font-size:58px;margin-bottom:10px">💄</div>
    <div style="font-size:32px;font-weight:800;color:#e8b86d;margin-bottom:6px">GlowBook</div>
    <div style="font-size:13px;color:#8a857d;text-align:center;margin-bottom:48px;line-height:1.6">La beauté à Brazzaville,<br>réservée en quelques secondes.</div>
    <div class="role-card" id="go-c" style="border-color:rgba(232,184,109,.3)">
      <div style="font-size:32px">👤</div>
      <div><div style="font-size:16px;font-weight:700;margin-bottom:2px">Je suis Client(e)</div><div style="font-size:12px;color:#8a857d">Découvrir & réserver</div></div>
      <div style="margin-left:auto;color:#e8b86d;font-size:18px">→</div>
    </div>
    <div class="role-card" id="go-p" style="border-color:rgba(232,143,160,.3)">
      <div style="font-size:32px">💼</div>
      <div><div style="font-size:16px;font-weight:700;margin-bottom:2px">Je suis Prestataire</div><div style="font-size:12px;color:#8a857d">Gérer mon salon</div></div>
      <div style="margin-left:auto;color:#e88fa0;font-size:18px">→</div>
    </div>
  </div>`;
}

// ===== CLIENT =====
function clientPage(){
  const hdr=`<div class="header">
    ${S.cView!=="home"?`<button id="c-back" style="background:none;border:none;color:#e8b86d;font-size:15px;cursor:pointer">← Retour</button>`:`<div style="font-size:17px;font-weight:700">💄 GlowBook</div>`}
    ${S.client?`<div style="display:flex;align-items:center;gap:8px">
      <span style="font-size:12px;color:#8a857d">${S.client.name}</span>
      <button id="c-logout" style="background:none;border:none;color:#8a857d;font-size:11px;cursor:pointer">Déco</button>
    </div>`:`<button id="go-cauth" style="background:none;border:none;color:#e8b86d;font-size:13px;font-weight:600;cursor:pointer">Connexion</button>`}
  </div>`;

  if(S.booked)return`<div>${hdr}${bookedView()}</div>`;
  if(S.cView==="auth")return`<div>${hdr}${clientAuth()}</div>`;
  if(S.cView==="home")return`<div>${hdr}${feedView()}</div>`;
  if(S.cView==="salon")return`<div>${hdr}${salonView()}</div>`;
  if(S.cView==="book")return`<div>${hdr}${bookView()}</div>`;
  if(S.cView==="pay")return`<div>${hdr}${payView()}</div>`;
  return`<div>${hdr}${feedView()}</div>`;
}

function clientAuth(){
  if(S.cAuthMode==="register")return`<div class="sec" style="padding-top:24px">
    <div style="font-size:21px;font-weight:800;margin-bottom:4px">Créer un compte</div>
    <div style="color:#8a857d;font-size:13px;margin-bottom:18px">Rejoignez GlowBook gratuitement</div>
    <input id="c-name" placeholder="Votre nom complet" value="${S.cName}"/>
    <input id="c-phone" placeholder="Numéro MTN/Airtel" type="tel" value="${S.cPhone}"/>
    <input id="c-pass" placeholder="Mot de passe" type="password" value="${S.cPass}"/>
    ${S.err?`<div class="err">${S.err}</div>`:""}
    <button class="btn" id="c-register" ${S.loading?"disabled":""}>
      ${S.loading?"Création...":"Créer mon compte"}
    </button>
    <span class="link" id="go-login">Déjà un compte ? Se connecter</span>
  </div>`;
  return`<div class="sec" style="padding-top:24px">
    <div style="font-size:21px;font-weight:800;margin-bottom:4px">Connexion</div>
    <div style="color:#8a857d;font-size:13px;margin-bottom:18px">Bon retour sur GlowBook 👋</div>
    <input id="c-phone" placeholder="Numéro de téléphone" type="tel" value="${S.cPhone}"/>
    <input id="c-pass" placeholder="Mot de passe" type="password" value="${S.cPass}"/>
    ${S.err?`<div class="err">${S.err}</div>`:""}
    <button class="btn" id="c-login" ${S.loading?"disabled":""}>
      ${S.loading?"Connexion...":"Se connecter"}
    </button>
    <span class="link" id="go-register">Pas encore de compte ? S'inscrire</span>
  </div>`;
}

function feedView(){
  const items=S.feed.length===0
    ?`<div style="grid-column:span 2;text-align:center;padding:60px 20px;color:#8a857d">
        <div style="font-size:40px;margin-bottom:12px">📸</div>
        <div style="font-size:15px;font-weight:600;margin-bottom:6px">Aucune réalisation pour l'instant</div>
        <div style="font-size:13px">Les prestataires publieront bientôt leurs coiffures</div>
      </div>`
    :S.feed.map(item=>`
      <div class="feed-item" data-fid="${item.id}" data-sid="${item.salon_id}">
        ${item.photo_url
          ?`<img src="${item.photo_url}" loading="lazy" style="width:100%;display:block"/>`
          :`<div class="feed-placeholder">💇‍♀️</div>`}
        <div class="feed-item-info">
          <div style="font-size:13px;font-weight:700;margin-bottom:3px">${item.hairstyle_name||"Coiffure"}</div>
          <div style="font-size:12px;color:#e8b86d;font-weight:700;margin-bottom:3px">${item.total_price?Number(item.total_price).toLocaleString()+" FCFA":""}</div>
          ${item.labor_price?`<div style="font-size:11px;color:#8a857d">Main d'œuvre: ${Number(item.labor_price).toLocaleString()} FCFA</div>`:""}
          <div style="font-size:11px;color:#8a857d;margin-top:4px">💇 ${item.salon_name||"Salon"}</div>
        </div>
      </div>`).join("");
  return`<div class="pb80">
    <div style="padding:12px 14px 6px">
      <div style="font-size:12px;color:#8a857d;margin-bottom:4px">📍 Brazzaville</div>
      <div style="font-size:18px;font-weight:700">Découvrez les coiffures</div>
    </div>
    <div class="feed-grid">${items}</div>
  </div>`;
}

function salonView(){
  if(!S.salon)return feedView();
  const portfolio=S.salon.portfolio||[];
  const portfolioHtml=portfolio.length>0
    ?`<div style="display:flex;gap:6px;overflow-x:auto;padding-bottom:8px;margin-bottom:14px">
        ${portfolio.map(p=>`<div style="flex-shrink:0;width:90px;border-radius:10px;overflow:hidden;background:#111;cursor:pointer">
          <img src="${p.photo_url}" style="width:90px;height:90px;object-fit:cover;display:block" loading="lazy"/>
          <div style="padding:5px 6px">
            <div style="font-size:10px;font-weight:700">${p.hairstyle_name||""}</div>
            <div style="font-size:10px;color:#e8b86d">${p.total_price?Number(p.total_price).toLocaleString()+" F":""}</div>
          </div>
        </div>`).join("")}
      </div>`:"";
  const svcs=S.svcs.length===0
    ?`<div style="color:#8a857d;text-align:center;padding:16px">Aucun service disponible</div>`
    :S.svcs.map(sv=>`
      <div class="svc-row" data-svid="${sv.id}" style="cursor:pointer;background:${S.svc&&S.svc.id===sv.id?"rgba(232,184,109,.08)":"transparent"};border-radius:10px;padding:12px 8px">
        <div>
          <div style="font-size:14px;font-weight:600">${sv.name} ${S.svc&&S.svc.id===sv.id?"✓":""}</div>
          <div style="font-size:11px;color:#8a857d">⏱ ${sv.duration_minutes} min</div>
        </div>
        <div style="font-size:14px;font-weight:700;color:#e8b86d">${Number(sv.price).toLocaleString()} FCFA</div>
      </div>`).join("");
  return`<div class="sec pb80">
    <div style="text-align:center;padding:14px 0 16px">
      <div style="font-size:48px">💇‍♀️</div>
      <div style="font-size:19px;font-weight:800;margin-bottom:3px">${S.salon.name}</div>
      <div style="font-size:12px;color:#8a857d">📍 ${S.salon.location||S.salon.address||""}</div>
    </div>
    ${portfolio.length>0?`<div class="sec-t">Portfolio</div>${portfolioHtml}`:""}
    <div class="sec-t">Services</div>
    <div>${svcs}</div>
    ${S.svc?`<button class="btn" id="go-book">Choisir un créneau →</button>`:""}
  </div>`;
}

function bookView(){
  const daysHtml=DAYS.map(d=>`<div class="dc ${S.day===d?"on":""}" data-d="${d}">${d}</div>`).join("");
  const slotsHtml=S.day?TIMES.map(t=>{const tk=S.takenSlots.includes(t);return`<div class="slot ${tk?"tk":""} ${S.time===t&&!tk?"on":""}" data-t="${t}">${t}</div>`}).join(""):"";
  return`<div class="sec pb80">
    <div style="background:rgba(232,184,109,.08);border:1px solid #e8b86d;border-radius:12px;padding:12px 14px;margin-bottom:16px">
      <div style="font-weight:700">${S.svc.name}</div>
      <div style="font-size:12px;color:#8a857d">⏱ ${S.svc.duration_minutes} min · <span style="color:#e8b86d">${Number(S.svc.price).toLocaleString()} FCFA</span></div>
    </div>
    ${!S.client?`<div class="err">⚠️ Connectez-vous pour réserver</div><button class="btn" id="go-auth-book">Se connecter / S'inscrire</button>`:
    `<div class="sec-t">Choisissez un jour</div>
    <div class="days-row">${daysHtml}</div>
    ${S.day?`<div class="sec-t">Créneaux disponibles</div><div class="slots">${slotsHtml}</div>`:""}
    ${S.err?`<div class="err">${S.err}</div>`:""}
    ${S.time?`<button class="btn" id="go-pay">Continuer vers le paiement →</button>`:""}`}
  </div>`;
}

function payView(){
  return`<div class="sec pb80">
    <div style="font-size:18px;font-weight:800;margin-bottom:4px">Paiement</div>
    <div style="color:#8a857d;font-size:12px;margin-bottom:16px">Payez en toute sécurité</div>
    <div class="card" style="margin-bottom:14px">
      <div style="font-size:11px;color:#8a857d;margin-bottom:4px">RÉCAPITULATIF</div>
      <div style="font-weight:700">${S.svc.name} · ${S.salon.name}</div>
      <div style="font-size:12px;color:#8a857d">${S.day} à ${S.time}</div>
      <div style="font-size:20px;font-weight:800;color:#e8b86d;margin-top:6px">${Number(S.svc.price).toLocaleString()} FCFA</div>
    </div>
    <div class="sec-t">Moyen de paiement</div>
    <div class="pay-opt ${S.payMethod==="mtn"?"on":""}" id="pay-mtn">
      <div style="font-size:26px">📱</div>
      <div><div style="font-weight:700">MTN Mobile Money</div><div style="font-size:11px;color:#8a857d">Payer avec MTN</div></div>
    </div>
    <div class="pay-opt ${S.payMethod==="airtel"?"on":""}" id="pay-airtel">
      <div style="font-size:26px">📲</div>
      <div><div style="font-weight:700">Airtel Money</div><div style="font-size:11px;color:#8a857d">Payer avec Airtel</div></div>
    </div>
    <input id="pay-phone" placeholder="Numéro ${S.payMethod==="mtn"?"MTN":"Airtel"}" type="tel" value="${S.payPhone}" style="margin-top:10px"/>
    ${S.err?`<div class="err">${S.err}</div>`:""}
    <button class="btn" id="do-pay" ${S.loading?"disabled":""}>${S.loading?"Traitement...":"✓ Confirmer et payer"}</button>
    <div style="font-size:11px;color:#8a857d;text-align:center;margin-top:8px">🔒 Paiement sécurisé</div>
  </div>`;
}

function bookedView(){
  return`<div style="display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:80vh;padding:40px 24px;text-align:center">
    <div style="font-size:56px;margin-bottom:14px">✅</div>
    <div style="font-size:20px;font-weight:800;margin-bottom:6px">Réservation confirmée !</div>
    <div style="color:#8a857d;font-size:13px;margin-bottom:20px">Votre RDV a été envoyé au salon.</div>
    <div class="card" style="width:100%;text-align:left;margin-bottom:16px">
      <div style="margin-bottom:8px"><span style="color:#8a857d;font-size:11px">SALON</span><br><strong>${S.salon?.name}</strong></div>
      <div style="margin-bottom:8px"><span style="color:#8a857d;font-size:11px">SERVICE</span><br><strong>${S.svc?.name}</strong></div>
      <div style="display:flex;gap:16px;margin-bottom:8px">
        <div><span style="color:#8a857d;font-size:11px">JOUR</span><br><strong>${S.day}</strong></div>
        <div><span style="color:#8a857d;font-size:11px">HEURE</span><br><strong>${S.time}</strong></div>
      </div>
      <div><span style="color:#8a857d;font-size:11px">PAIEMENT</span><br><strong style="color:#7ec8a0">✓ ${Number(S.svc?.price).toLocaleString()} FCFA · ${S.payMethod==="mtn"?"MTN Money":"Airtel Money"}</strong></div>
    </div>
    <button class="btn" id="new-book">Nouvelle réservation</button>
  </div>`;
}

// ===== PROVIDER =====
function providerPage(){
  if(S.pView==="auth")return providerAuth();
  if(S.pView==="setup")return providerSetup();
  return providerDashboard();
}

function providerAuth(){
  if(S.pAuthMode==="register")return`
    <div class="header"><div style="font-size:17px;font-weight:700">💼 Inscription</div><button id="p-tosplash" style="background:none;border:none;color:#8a857d;font-size:12px;cursor:pointer">Accueil</button></div>
    <div class="sec" style="padding-top:20px">
      <input id="p-phone" placeholder="Numéro de téléphone" type="tel" value="${S.pPhone}"/>
      <input id="p-pass" placeholder="Mot de passe" type="password" value="${S.pPass}"/>
      ${S.err?`<div class="err">${S.err}</div>`:""}
      <button class="btn" id="p-register" ${S.loading?"disabled":""}>${S.loading?"...":"S'inscrire"}</button>
      <span class="link" id="p-tologin">Déjà un compte ? Se connecter</span>
    </div>`;
  return`
    <div class="header"><div style="font-size:17px;font-weight:700">💼 Connexion</div><button id="p-tosplash" style="background:none;border:none;color:#8a857d;font-size:12px;cursor:pointer">Accueil</button></div>
    <div class="sec" style="padding-top:20px">
      <input id="p-phone" placeholder="Numéro de téléphone" type="tel" value="${S.pPhone}"/>
      <input id="p-pass" placeholder="Mot de passe" type="password" value="${S.pPass}"/>
      ${S.err?`<div class="err">${S.err}</div>`:""}
      <button class="btn" id="p-login" ${S.loading?"disabled":""}>${S.loading?"...":"Se connecter"}</button>
      <span class="link" id="p-toregister">S'inscrire</span>
    </div>`;
}

function providerSetup(){
  return`
    <div class="header"><div style="font-size:17px;font-weight:700">💼 Créer mon salon</div><button id="p-tosplash" style="background:none;border:none;color:#8a857d;font-size:12px;cursor:pointer">Accueil</button></div>
    <div class="sec" style="padding-top:20px">
      <div style="font-size:19px;font-weight:800;margin-bottom:4px">Bienvenue !</div>
      <div style="color:#8a857d;font-size:13px;margin-bottom:16px">Configurez votre salon pour recevoir des réservations</div>
      <input id="p-sname" placeholder="Nom du salon *" value="${S.pSalonName}"/>
      <input id="p-addr" placeholder="Adresse du salon *" value="${S.pAddress}"/>
      <input id="p-phone" placeholder="Numéro de téléphone *" type="tel" value="${S.pPhone}"/>
      <input id="p-pass" placeholder="Mot de passe *" type="password" value="${S.pPass}"/>
      ${S.err?`<div class="err">${S.err}</div>`:""}
      <button class="btn" id="p-create" ${S.loading?"disabled":""}>${S.loading?"Création...":"Créer mon salon →"}</button>
      <span class="link" id="p-toauth">Déjà un salon ? Se connecter</span>
    </div>`;
}

function providerDashboard(){
  const modal=S.showUploadModal?uploadModal():"";
  return`<div>
    <div class="header">
      <div>
        <div style="font-size:11px;color:#8a857d">Prestataire</div>
        <div style="font-size:15px;font-weight:700">💇‍♀️ ${S.provSalon?.name||""}</div>
      </div>
      <div style="display:flex;align-items:center;gap:8px">
        <span class="badge">${PLANS[S.provSalon?.subscription||"starter"]?.label||"Starter"}</span>
        <button id="p-logout" style="background:none;border:none;color:#8a857d;font-size:11px;cursor:pointer">Déco</button>
      </div>
    </div>
    <div class="pb80">
      ${S.pTab==="agenda"?agendaTab():""}
      ${S.pTab==="portfolio"?portfolioTab():""}
      ${S.pTab==="services"?servicesTab():""}
      ${S.pTab==="stats"?statsTab():""}
      ${S.pTab==="abonnement"?abonnementTab():""}
    </div>
    <div class="tab-bar">
      <button class="tab ${S.pTab==="agenda"?"on":""}" id="pt-agenda"><div style="font-size:17px">📅</div>Agenda</button>
      <button class="tab ${S.pTab==="portfolio"?"on":""}" id="pt-portfolio"><div style="font-size:17px">🖼️</div>Portfolio</button>
      <button class="tab ${S.pTab==="services"?"on":""}" id="pt-services"><div style="font-size:17px">✂️</div>Services</button>
      <button class="tab ${S.pTab==="stats"?"on":""}" id="pt-stats"><div style="font-size:17px">📊</div>Stats</button>
      <button class="tab ${S.pTab==="abonnement"?"on":""}" id="pt-abo"><div style="font-size:17px">💳</div>Plan</button>
    </div>
    ${modal}
  </div>`;
}

function uploadModal(){
  return`<div class="modal" id="modal-bg">
    <div class="modal-content">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px">
        <div style="font-size:17px;font-weight:700">Publier une réalisation</div>
        <button id="close-modal" style="background:none;border:none;color:#8a857d;font-size:20px;cursor:pointer">✕</button>
      </div>
      ${S.uploadPreview?`<img src="${S.uploadPreview}" style="width:100%;border-radius:12px;margin-bottom:12px;max-height:200px;object-fit:cover"/>`
      :`<div id="pick-photo" style="width:100%;height:140px;background:#111;border:2px dashed #2e2b28;border-radius:12px;display:flex;align-items:center;justify-content:center;cursor:pointer;margin-bottom:12px;flex-direction:column;gap:6px">
          <div style="font-size:32px">📷</div>
          <div style="font-size:13px;color:#8a857d">Choisir une photo</div>
        </div>`}
      <input type="file" id="photo-file" accept="image/*" style="display:none"/>
      <input id="up-name" placeholder="Nom de la coiffure *" value="${S.uploadName}"/>
      <input id="up-total" placeholder="Prix total (FCFA) *" type="number" value="${S.uploadTotal}"/>
      <input id="up-labor" placeholder="Prix main d'œuvre seule (FCFA)" type="number" value="${S.uploadLabor}"/>
      ${S.err?`<div class="err">${S.err}</div>`:""}
      <button class="btn" id="do-upload" ${S.loading?"disabled":""}>${S.loading?"Publication...":"Publier la réalisation"}</button>
    </div>
  </div>`;
}

function agendaTab(){
  const pending=S.pBookings.filter(b=>b.status==="pending").length;
  const filtered=S.filterDay==="all"?S.pBookings:S.pBookings.filter(b=>b.booking_date===S.filterDay);
  const daysHtml=["all",...DAYS].map(d=>`<div class="dc ${S.filterDay===d?"on":""}" style="font-size:11px" data-fd="${d}">${d==="all"?"Tous":d}</div>`).join("");
  const bookings=filtered.length===0
    ?`<div style="color:#8a857d;text-align:center;padding:40px">Aucune réservation</div>`
    :filtered.map(b=>`<div class="booking-card">
        <div style="display:flex;justify-content:space-between;margin-bottom:6px">
          <strong style="font-size:14px">${b.client_name||"Client"}</strong>
          <span style="font-size:11px;font-weight:700;border-radius:6px;padding:3px 8px;background:${b.status==="confirmed"?"rgba(126,200,160,.12)":b.status==="cancelled"?"rgba(255,100,100,.12)":"rgba(232,184,109,.12)"};color:${b.status==="confirmed"?"#7ec8a0":b.status==="cancelled"?"#ff8080":"#e8b86d"}">
            ${b.status==="confirmed"?"Confirmé":b.status==="cancelled"?"Annulé":"En attente"}
          </span>
        </div>
        <div style="font-size:12px;color:#8a857d;margin-bottom:6px">${b.service_name}</div>
        <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:6px">
          <span style="font-size:11px;background:#2e2b28;border-radius:6px;padding:2px 8px">📅 ${b.booking_date}</span>
          <span style="font-size:11px;background:#2e2b28;border-radius:6px;padding:2px 8px">🕐 ${b.booking_time?.slice(0,5)}</span>
          ${b.amount?`<span style="font-size:11px;background:#2e2b28;border-radius:6px;padding:2px 8px;color:#e8b86d">${Number(b.amount).toLocaleString()} F</span>`:""}
          ${b.payment_method?`<span style="font-size:11px;background:#2e2b28;border-radius:6px;padding:2px 8px">${b.payment_method==="mtn"?"📱 MTN":"📲 Airtel"}</span>`:""}
        </div>
        ${b.client_phone?`<div style="font-size:11px;color:#8a857d;margin-bottom:8px">📞 ${b.client_phone}</div>`:""}
        ${b.status==="pending"?`<div style="display:flex;gap:8px">
          <button class="btn-s accept-b" data-bid="${b.id}">✓ Accepter</button>
          <button class="btn-r cancel-b" data-bid="${b.id}">✕ Refuser</button>
        </div>`:""}
      </div>`).join("");
  return`<div class="sec">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
      <div class="sec-t" style="margin-bottom:0">Réservations</div>
      ${pending>0?`<span class="badge">${pending} en attente</span>`:""}
    </div>
    <div class="days-row">${daysHtml}</div>
    ${bookings}
  </div>`;
}

function portfolioTab(){
  const photos=S.pPortfolio||[];
  const grid=photos.map(p=>`
    <div class="ph" style="position:relative">
      <img src="${p.photo_url}" loading="lazy"/>
      <div style="position:absolute;bottom:0;left:0;right:0;background:rgba(0,0,0,.7);padding:4px 6px;font-size:10px">
        <div style="font-weight:700;color:#fff">${p.hairstyle_name||""}</div>
        <div style="color:#e8b86d">${p.total_price?Number(p.total_price).toLocaleString()+" F":""}</div>
      </div>
    </div>`).join("");
  return`<div class="sec">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
      <div class="sec-t" style="margin-bottom:0">Mes réalisations (${photos.length})</div>
    </div>
    <div class="photos-grid">
      ${grid}
      <div class="ph-add" id="add-photo">
        <div style="font-size:26px">+</div>
        <div style="font-size:10px;color:#8a857d">Ajouter</div>
      </div>
    </div>
    <div style="color:#8a857d;font-size:12px;text-align:center;margin-top:4px">
      Ces photos apparaissent dans le feed client 📸
    </div>
  </div>`;
}

function servicesTab(){
  const svcs=S.pSvcs.map(s=>`
    <div class="svc-row">
      <div><div style="font-weight:600;font-size:14px">${s.name}</div><div style="font-size:11px;color:#8a857d">⏱ ${s.duration_minutes} min</div></div>
      <div style="color:#e8b86d;font-weight:700;font-size:14px">${Number(s.price).toLocaleString()} FCFA</div>
    </div>`).join("");
  return`<div class="sec">
    <div class="sec-t">Mes services</div>
    <div class="card">${S.pSvcs.length===0?`<div style="color:#8a857d;text-align:center;padding:10px">Aucun service</div>`:svcs}</div>
    <div class="sec-t" style="margin-top:16px">Ajouter un service</div>
    <input id="svc-name" placeholder="Nom du service" value="${S.svcName}"/>
    <input id="svc-dur" placeholder="Durée (minutes)" type="number" value="${S.svcDur}"/>
    <input id="svc-price" placeholder="Prix (FCFA)" type="number" value="${S.svcPrice}"/>
    ${S.err?`<div class="err">${S.err}</div>`:""}
    <button class="btn" id="add-svc" ${S.loading?"disabled":""}>${S.loading?"Ajout...":"+ Ajouter le service"}</button>
  </div>`;
}

function statsTab(){
  const total=S.pBookings.length;
  const confirmed=S.pBookings.filter(b=>b.status==="confirmed").length;
  const pending=S.pBookings.filter(b=>b.status==="pending").length;
  const revenue=S.pBookings.filter(b=>b.status==="confirmed").reduce((s,b)=>s+(Number(b.amount)||0),0);
  return`<div class="sec">
    <div class="sec-t">Tableau de bord</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:16px">
      <div class="stat"><div style="font-size:24px;font-weight:800;color:#e8b86d;margin-bottom:3px">${total}</div><div style="font-size:11px;color:#8a857d">Total RDV</div></div>
      <div class="stat"><div style="font-size:24px;font-weight:800;color:#7ec8a0;margin-bottom:3px">${confirmed}</div><div style="font-size:11px;color:#8a857d">Confirmés</div></div>
      <div class="stat"><div style="font-size:24px;font-weight:800;color:#e88fa0;margin-bottom:3px">${pending}</div><div style="font-size:11px;color:#8a857d">En attente</div></div>
      <div class="stat"><div style="font-size:20px;font-weight:800;color:#e8b86d;margin-bottom:3px">${revenue.toLocaleString()}</div><div style="font-size:11px;color:#8a857d">FCFA reçus</div></div>
    </div>
    <div class="sec-t">Portfolio</div>
    <div class="card" style="text-align:center">
      <div style="font-size:24px;font-weight:800;color:#e8b86d">${(S.pPortfolio||[]).length}</div>
      <div style="font-size:11px;color:#8a857d">photos publiées</div>
    </div>
  </div>`;
}

function abonnementTab(){
  const current=S.provSalon?.subscription||"starter";
  return`<div class="sec">
    <div class="sec-t">Mon abonnement</div>
    <div class="card" style="margin-bottom:16px;border-color:#e8b86d">
      <div style="font-size:13px;color:#8a857d;margin-bottom:4px">PLAN ACTUEL</div>
      <div style="font-size:18px;font-weight:800;color:#e8b86d">${PLANS[current].label}</div>
      <div style="font-size:12px;color:#8a857d">Commission GlowBook : ${PLANS[current].commission}%</div>
    </div>
    <div class="sec-t">Changer de plan</div>
    ${Object.entries(PLANS).map(([k,p])=>`
      <div class="plan-card ${k===current?"on":""}" style="border-color:${k===current?p.color:"#2e2b28"}">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px">
          <div style="font-weight:700;color:${p.color};font-size:15px">${p.label} ${k===current?"✓ Actif":""}</div>
          <div style="font-weight:800;font-size:15px">${p.price===0?"Gratuit":p.price.toLocaleString()+" FCFA/mois"}</div>
        </div>
        <div style="font-size:12px;color:#8a857d">Commission ${p.commission}% · ${p.photos===999?"Photos illimitées":p.photos+" photos max"}</div>
        ${k!==current?`<button class="btn-s" style="margin-top:10px;width:100%;text-align:center" data-plan="${k}">
          Passer au ${p.label} ${p.price>0?"· Payer par Mobile Money":""}
        </button>`:""}
      </div>`).join("")}
    <div style="font-size:12px;color:#8a857d;text-align:center;margin-top:12px">
      🔒 Paiement sécurisé par MTN/Airtel Mobile Money
    </div>
  </div>`;
}

// ===== LOAD DATA =====
async function loadFeed(){
  try{
    const data=await db("portfolio","GET",null,"?select=*,salons(name)&order=created_at.desc&limit=50");
    S.feed=data.map(item=>({...item,salon_name:item.salons?.name||"Salon"}));
  }catch(e){console.log(e);}
}

async function loadProviderData(){
  if(!S.provSalon)return;
  try{
    const[b,sv,pt]=await Promise.all([
      db("bookings","GET",null,`?salon_id=eq.${S.provSalon.id}&select=*&order=created_at.desc`),
      db("services","GET",null,`?salon_id=eq.${S.provSalon.id}&select=*`),
      db("portfolio","GET",null,`?salon_id=eq.${S.provSalon.id}&select=*&order=created_at.desc`)
    ]);
    S.pBookings=b;S.pSvcs=sv;S.pPortfolio=pt;
  }catch(e){console.log(e);}
}

// ===== BIND =====
function bind(){
  const on=(id,fn)=>{const el=$(id);if(el)el.onclick=fn};
  const onAll=(sel,fn)=>document.querySelectorAll(sel).forEach(el=>el.onclick=fn);

  // splash
  on("go-c",async()=>{S.page="client";S.cView="home";S.err="";R();await loadFeed();R();bind();});
  on("go-p",()=>{S.page="provider";S.pView="setup";S.err="";R();});

  // client nav
  on("go-cauth",()=>{S.cView="auth";S.cAuthMode="login";S.err="";R();bind();});
  on("c-back",()=>{
    if(S.cView==="auth"||S.cView==="salon")S.cView="home";
    else if(S.cView==="book")S.cView="salon";
    else if(S.cView==="pay")S.cView="book";
    S.err="";R();bind();
  });
  on("c-logout",()=>{S.client=null;S.cView="home";R();bind();});
  on("go-auth-book",()=>{S.cView="auth";S.cAuthMode="login";S.err="";R();bind();});
  on("go-login",()=>{S.cAuthMode="login";S.err="";R();bind();});
  on("go-register",()=>{S.cAuthMode="register";S.err="";R();bind();});

  // client inputs
  const inp=(id,key)=>{const el=$(id);if(el)el.oninput=e=>S[key]=e.target.value;};
  inp("c-name","cName");inp("c-phone","cPhone");inp("c-pass","cPass");

  on("c-register",async()=>{
    if(!S.cName||!S.cPhone||!S.cPass){S.err="Tous les champs sont obligatoires";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      const exists=await db("users","GET",null,`?phone=eq.${S.cPhone}&select=id`);
      if(exists&&exists.length>0){S.err="Ce numéro est déjà utilisé";S.loading=false;R();bind();return;}
      const data=await db("users","POST",{name:S.cName,phone:S.cPhone,password:S.cPass,role:"client"});
      S.client=Array.isArray(data)?data[0]:data;
      S.cView="home";S.loading=false;R();bind();
      await loadFeed();R();bind();
    }catch(e){S.err="Erreur: "+e.message;S.loading=false;R();bind();}
  });

  on("c-login",async()=>{
    if(!S.cPhone||!S.cPass){S.err="Remplis tous les champs";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      const data=await db("users","GET",null,`?phone=eq.${S.cPhone}&password=eq.${S.cPass}&select=*`);
      if(!data||data.length===0){S.err="Numéro ou mot de passe incorrect";S.loading=false;R();bind();return;}
      S.client=data[0];S.cView="home";S.loading=false;R();bind();
      await loadFeed();R();bind();
    }catch(e){S.err="Erreur: "+e.message;S.loading=false;R();bind();}
  });

  // feed click → salon
  onAll(".feed-item",async function(){
    const sid=this.dataset.sid;
    S.loading=true;
    try{
      const salons=await db("salons","GET",null,`?id=eq.${sid}&select=*`);
      if(salons&&salons.length>0){
        S.salon=salons[0];
        const pt=await db("portfolio","GET",null,`?salon_id=eq.${sid}&select=*&order=created_at.desc`);
        S.salon.portfolio=pt;
        const svcs=await db("services","GET",null,`?salon_id=eq.${sid}&select=*`);
        S.svcs=svcs;
        S.svc=null;S.cView="salon";
      }
    }catch(e){console.log(e);}
    S.loading=false;R();bind();
  });

  // service select
  onAll(".svc-row",function(){S.svc=S.svcs.find(s=>s.id===this.dataset.svid);R();bind();});
  on("go-book",()=>{S.cView="book";S.err="";R();bind();});

  // day/time
  onAll("[data-d]",async function(){
    S.day=this.dataset.d;S.time=null;R();bind();
    const idx=DAYS.indexOf(S.day);
    const dt=`2026-04-${String(idx+7).padStart(2,"0")}`;
    try{
      const taken=await db("bookings","GET",null,`?salon_id=eq.${S.salon.id}&booking_date=eq.${dt}&status=neq.cancelled&select=booking_time`);
      S.takenSlots=taken.map(b=>b.booking_time?.slice(0,5));
    }catch{}
    R();bind();
  });
  onAll(".slot:not(.tk)",function(){S.time=this.dataset.t;R();bind();});
  on("go-pay",()=>{S.cView="pay";S.err="";R();bind();});

  // payment
  on("pay-mtn",()=>{S.payMethod="mtn";R();bind();});
  on("pay-airtel",()=>{S.payMethod="airtel";R();bind();});
  inp("pay-phone","payPhone");
  on("do-pay",async()=>{
    if(!S.payPhone){S.err="Entre ton numéro "+( S.payMethod==="mtn"?"MTN":"Airtel");R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      const idx=DAYS.indexOf(S.day);
      await db("bookings","POST",{
        client_name:S.client?.name||"Client",client_phone:S.client?.phone||S.payPhone,
        salon_id:S.salon.id,service_name:S.svc.name,
        booking_date:`2026-04-${String(idx+7).padStart(2,"0")}`,
        booking_time:S.time,status:"pending",amount:S.svc.price,
        payment_method:S.payMethod,payment_phone:S.payPhone
      });
      S.booked=true;
    }catch(e){S.err="Erreur: "+e.message;}
    S.loading=false;R();bind();
  });
  on("new-book",()=>{S.booked=false;S.svc=null;S.day=null;S.time=null;S.payPhone="";S.cView="home";R();bind();});

  // provider setup
  on("p-tosplash",()=>{S.page="splash";R();});
  on("p-toauth",()=>{S.pView="auth";S.pAuthMode="login";S.err="";R();bind();});
  on("p-tologin",()=>{S.pAuthMode="login";S.err="";R();bind();});
  on("p-toregister",()=>{S.pAuthMode="register";S.err="";R();bind();});
  inp("p-phone","pPhone");inp("p-pass","pPass");inp("p-sname","pSalonName");inp("p-addr","pAddress");

  on("p-create",async()=>{
    if(!S.pSalonName||!S.pAddress||!S.pPhone||!S.pPass){S.err="Tous les champs sont obligatoires";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      const data=await db("salons","POST",{name:S.pSalonName,location:S.pAddress,phone:S.pPhone,password:S.pPass,subscription:"starter",photos:[]});
      S.provSalon=Array.isArray(data)?data[0]:data;
      S.pView="dashboard";S.loading=false;
      await loadProviderData();R();bind();
    }catch(e){S.err="Erreur: "+e.message;S.loading=false;R();bind();}
  });

  on("p-login",async()=>{
    if(!S.pPhone||!S.pPass){S.err="Remplis tous les champs";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      const data=await db("salons","GET",null,`?phone=eq.${S.pPhone}&password=eq.${S.pPass}&select=*`);
      if(!data||data.length===0){S.err="Identifiants incorrects";S.loading=false;R();bind();return;}
      S.provSalon=data[0];S.pView="dashboard";S.loading=false;
      await loadProviderData();R();bind();
    }catch(e){S.err="Erreur: "+e.message;S.loading=false;R();bind();}
  });

  on("p-register",async()=>{
    if(!S.pPhone||!S.pPass){S.err="Remplis tous les champs";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      const data=await db("salons","POST",{name:"Mon Salon",phone:S.pPhone,password:S.pPass,subscription:"starter",photos:[]});
      S.provSalon=Array.isArray(data)?data[0]:data;
      S.pView="dashboard";S.loading=false;
      await loadProviderData();R();bind();
    }catch(e){S.err="Erreur: "+e.message;S.loading=false;R();bind();}
  });

  on("p-logout",()=>{S.provSalon=null;S.pView="setup";S.page="splash";R();});

  // provider tabs
  const ptab=(id,tab)=>on(id,async()=>{S.pTab=tab;await loadProviderData();R();bind();});
  ptab("pt-agenda","agenda");ptab("pt-portfolio","portfolio");
  ptab("pt-services","services");ptab("pt-stats","stats");ptab("pt-abo","abonnement");

  // filter
  onAll("[data-fd]",function(){S.filterDay=this.dataset.fd;R();bind();});

  // bookings
  onAll(".accept-b",async function(){
    await db("bookings","PATCH",{status:"confirmed"},`?id=eq.${this.dataset.bid}`);
    await loadProviderData();R();bind();
  });
  onAll(".cancel-b",async function(){
    await db("bookings","PATCH",{status:"cancelled"},`?id=eq.${this.dataset.bid}`);
    await loadProviderData();R();bind();
  });

  // services
  inp("svc-name","svcName");inp("svc-dur","svcDur");inp("svc-price","svcPrice");
  on("add-svc",async()=>{
    if(!S.svcName||!S.svcPrice){S.err="Nom et prix requis";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      await db("services","POST",{salon_id:S.provSalon.id,name:S.svcName,duration_minutes:parseInt(S.svcDur)||60,price:parseInt(S.svcPrice)});
      S.svcName="";S.svcDur="";S.svcPrice="";
      await loadProviderData();
    }catch(e){S.err="Erreur: "+e.message;}
    S.loading=false;R();bind();
  });

  // portfolio upload
  on("add-photo",()=>{S.showUploadModal=true;S.uploadPreview="";S.uploadName="";S.uploadTotal="";S.uploadLabor="";S.err="";R();bind();});
  on("close-modal",()=>{S.showUploadModal=false;R();bind();});
  on("pick-photo",()=>{$("photo-file")?.click();});
  const pf=$("photo-file");
  if(pf)pf.onchange=function(){
    const file=this.files[0];
    if(!file)return;
    S.uploadPhoto=file;
    S.uploadPreview=URL.createObjectURL(file);
    R();bind();
  };
  inp("up-name","uploadName");inp("up-total","uploadTotal");inp("up-labor","uploadLabor");

  on("do-upload",async()=>{
    if(!S.uploadPhoto||!S.uploadName||!S.uploadTotal){S.err="Photo, nom et prix total sont obligatoires";R();bind();return;}
    S.loading=true;S.err="";R();bind();
    try{
      // Save as data URL (base64) since storage bucket not configured
      const reader=new FileReader();
      reader.onload=async(e)=>{
        const photoUrl=e.target.result;
        await db("portfolio","POST",{
          salon_id:S.provSalon.id,
          photo_url:photoUrl,
          hairstyle_name:S.uploadName,
          total_price:parseInt(S.uploadTotal),
          labor_price:S.uploadLabor?parseInt(S.uploadLabor):null
        });
        S.showUploadModal=false;S.uploadPhoto=null;S.uploadPreview="";
        S.uploadName="";S.uploadTotal="";S.uploadLabor="";
        await loadProviderData();
        S.loading=false;R();bind();
      };
      reader.readAsDataURL(S.uploadPhoto);
    }catch(e){S.err="Erreur: "+e.message;S.loading=false;R();bind();}
  });

  // plan change
  onAll("[data-plan]",async function(){
    const plan=this.dataset.plan;
    if(plan==="starter"){
      await db("salons","PATCH",{subscription:"starter"},`?id=eq.${S.provSalon.id}`);
      S.provSalon.subscription="starter";R();bind();
    } else {
      alert(`Pour passer au plan ${PLANS[plan].label} (${PLANS[plan].price.toLocaleString()} FCFA/mois), appelez le service client GlowBook.`);
    }
  });
}

R();
</script>
</body>
</html>
