[ecovision.html](https://github.com/user-attachments/files/32816410/ecovision.html)
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>EcoVision – Tıkla, Tara, Dönüştür</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,400;12..96,600;12..96,800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#EEF2EA; --panel:#FFFFFF; --ink:#14231C; --muted:#5D6F64; --pine:#123B2E; --lime:#B9E23F; --sun:#F0A93B; --line:#D5DDD0;
  --plastik:#F2C230; --cam:#2E9B5B; --kagit:#3A7BD5;
  box-sizing:border-box; padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){--bg:#0C1712;--panel:#15251D;--ink:#EAF2E6;--muted:#93A79A;--pine:#0A2A20;--line:#264034;}
}
:root[data-theme="dark"]{--bg:#0C1712;--panel:#15251D;--ink:#EAF2E6;--muted:#93A79A;--pine:#0A2A20;--line:#264034;}
*{box-sizing:border-box;margin:0}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
html,body{height:100%}
body{background:var(--bg);color:var(--ink);font-family:"Bricolage Grotesque",system-ui,-apple-system,"Segoe UI",sans-serif;display:flex;align-items:center;justify-content:center}
.phone{width:100%;max-width:400px;height:100%;max-height:820px;background:var(--panel);display:flex;flex-direction:column;overflow:hidden;position:relative}
@media(min-width:520px){.phone{border-radius:36px;border:1px solid var(--line);box-shadow:0 30px 60px -30px rgba(18,59,46,.45)}}
main{flex:1;overflow-y:auto;position:relative}
.screen{display:none;min-height:100%}
.screen.on{display:block}
button{font:inherit;color:inherit;cursor:pointer}
:focus-visible{outline:3px solid var(--sun);outline-offset:2px}

/* Home */
.top{background:var(--pine);color:#fff;padding:28px 22px 26px;border-radius:0 0 28px 28px}
.hi{font-size:15px;opacity:.75}
.name{font-size:22px;font-weight:600;margin-top:2px}
.pts{display:flex;align-items:baseline;gap:8px;margin-top:20px}
.pts b{font-size:64px;font-weight:800;line-height:1;letter-spacing:-2px;color:var(--lime)}
.pts span{font-size:16px;opacity:.85}
.bar{height:8px;background:rgba(255,255,255,.15);border-radius:8px;margin-top:14px;overflow:hidden}
.bar i{display:block;height:100%;background:var(--lime);border-radius:8px;transition:width .6s}
.barl{font-size:13px;opacity:.75;margin-top:8px}
.scanbtn{margin:-22px 22px 0;width:calc(100% - 44px);background:var(--lime);color:var(--pine);border:0;border-radius:22px;padding:18px;font-size:20px;font-weight:800;display:flex;align-items:center;justify-content:center;gap:12px;box-shadow:0 10px 24px -10px rgba(18,59,46,.6);position:relative}
.scanbtn svg{width:28px;height:28px}
.sec{padding:22px}
.sec h2{font-size:17px;font-weight:600;margin-bottom:10px}
.row{display:flex;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid var(--line)}
.row:last-child{border:0}
.dot{width:14px;height:14px;border-radius:50%;flex:none}
.row .t{flex:1;font-size:15px}
.row .t small{display:block;color:var(--muted);font-size:12.5px}
.row .p{font-weight:800;color:var(--cam)}
.empty{color:var(--muted);font-size:14px;padding:8px 0}

/* Scan */
.cam{position:relative;height:100%;min-height:560px;background:#0E1A14;overflow:hidden;display:flex;flex-direction:column}
.view{flex:1;position:relative;background:radial-gradient(circle at 50% 40%,#2b4a3b,#0c1611 70%);display:flex;align-items:center;justify-content:center;overflow:hidden}
video{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;display:none}
.frame{width:220px;height:220px;position:relative;transition:.3s}
.frame::before,.frame::after,.frame i::before,.frame i::after{content:"";position:absolute;width:38px;height:38px;border:4px solid var(--lime)}
.frame::before{top:0;left:0;border-right:0;border-bottom:0;border-radius:14px 0 0 0}
.frame::after{top:0;right:0;border-left:0;border-bottom:0;border-radius:0 14px 0 0}
.frame i::before{bottom:0;left:0;border-right:0;border-top:0;border-radius:0 0 0 14px}
.frame i::after{bottom:0;right:0;border-left:0;border-top:0;border-radius:0 0 14px 0}
.frame.busy{animation:pulse .9s infinite alternate}
@keyframes pulse{to{transform:scale(.94)}}
.hint{position:absolute;top:18px;left:0;right:0;text-align:center;color:#fff;font-size:14px;opacity:.85;padding:0 24px}
.result{background:var(--panel);border-radius:26px 26px 0 0;padding:20px 22px 22px;margin-top:-26px;position:relative}
.rt{display:flex;justify-content:space-between;align-items:baseline}
.rt b{font-size:24px;font-weight:800}
.acc{font-size:14px;color:var(--muted)}
.bin{display:flex;align-items:center;gap:10px;margin:12px 0 16px;font-size:15px}
.bin .sw{width:26px;height:26px;border-radius:8px}
.btns{display:flex;gap:10px}
.b1{flex:1;background:var(--pine);color:#fff;border:0;border-radius:16px;padding:14px;font-weight:600;font-size:16px}
.b2{background:transparent;border:1.5px solid var(--line);border-radius:16px;padding:14px 16px;font-weight:600}
.b1[disabled]{opacity:.4;cursor:default}
.tip{font-size:12.5px;color:var(--muted);margin-top:10px}

/* Rewards */
.map{margin:18px 22px 0;border-radius:24px;overflow:hidden;border:1px solid var(--line);background:#E4EBDD}
:root[data-theme="dark"] .map{background:#1A2F25}
@media (prefers-color-scheme: dark){:root:not([data-theme="light"]) .map{background:#1A2F25}}
.map svg{display:block;width:100%;height:auto}
.near{margin:12px 22px 0;display:flex;align-items:center;gap:12px;font-size:15px}
.near b{display:block}
.near small{color:var(--muted)}
.opts{padding:22px}
.opt{width:100%;text-align:left;display:flex;align-items:center;gap:14px;background:transparent;border:1.5px solid var(--line);border-radius:18px;padding:14px 16px;margin-bottom:10px}
.opt strong{display:block;font-size:16px}
.opt small{color:var(--muted)}
.opt .cost{margin-left:auto;font-weight:800;color:var(--pine)}
:root[data-theme="dark"] .opt .cost{color:var(--lime)}
.opt[aria-pressed="true"]{border-color:var(--pine);background:color-mix(in srgb,var(--lime) 25%,transparent)}
.go{width:100%;background:var(--sun);color:#2a1a00;border:0;border-radius:18px;padding:16px;font-size:18px;font-weight:800;margin-top:4px}
.go[disabled]{opacity:.45;cursor:default}

nav{display:flex;border-top:1px solid var(--line);background:var(--panel)}
nav button{flex:1;background:none;border:0;padding:10px 4px 12px;display:flex;flex-direction:column;align-items:center;gap:3px;font-size:12.5px;color:var(--muted)}
nav button svg{width:24px;height:24px}
nav button[aria-current="page"]{color:var(--pine);font-weight:800}
:root[data-theme="dark"] nav button[aria-current="page"]{color:var(--lime)}
@media (prefers-color-scheme: dark){:root:not([data-theme="light"]) nav button[aria-current="page"]{color:var(--lime)}}
.toast{position:absolute;left:22px;right:22px;bottom:84px;background:var(--pine);color:#fff;padding:13px 16px;border-radius:14px;font-size:14.5px;opacity:0;transform:translateY(10px);pointer-events:none;transition:.25s;z-index:5}
.toast.show{opacity:1;transform:none}
@media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
</style>
</head>
<body>
<div class="phone">
<main>

<!-- 1. ANA EKRAN -->
<section class="screen on" id="s-home" aria-label="Ana ekran">
  <div class="top">
    <div class="hi">Merhaba,</div>
    <div class="name">Ayşe Yılmaz</div>
    <div class="pts"><b id="pts">120</b><span>Toplam Puan</span></div>
    <div class="bar"><i id="barfill" style="width:60%"></i></div>
    <div class="barl" id="barl">Kent Kart indirimine 80 puan kaldı</div>
  </div>
  <button class="scanbtn" id="goScan">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 8V6a2 2 0 0 1 2-2h2M16 4h2a2 2 0 0 1 2 2v2M20 16v2a2 2 0 0 1-2 2h-2M8 20H6a2 2 0 0 1-2-2v-2"/><circle cx="12" cy="12" r="3.5"/></svg>
    Atık Tara
  </button>
  <div class="sec">
    <h2>Son Dönüştürülenler</h2>
    <div id="hist"></div>
  </div>
</section>

<!-- 2. TARAMA -->
<section class="screen" id="s-scan" aria-label="Atık tarama">
  <div class="cam">
    <div class="view" id="view">
      <video id="video" playsinline muted></video>
      <div class="hint" id="hint">Atığı çerçevenin içine yerleştir</div>
      <div class="frame" id="frame"><i></i></div>
    </div>
    <div class="result" aria-live="polite">
      <div class="rt"><b id="rName">Henüz tarama yok</b><span class="acc" id="rAcc"></span></div>
      <div class="bin"><span class="sw" id="rSw" style="background:var(--line)"></span><span id="rBin">Tara düğmesine bas, atığın türünü bulalım.</span></div>
      <div class="btns">
        <button class="b2" id="scanNow">Tara</button>
        <button class="b1" id="save" disabled>Kaydet (+10 puan)</button>
      </div>
      <div class="tip" id="tip"></div>
    </div>
  </div>
</section>

<!-- 3. ÖDÜL VE HARİTA -->
<section class="screen" id="s-reward" aria-label="Ödül ve harita">
  <div class="sec" style="padding-bottom:0"><h2 style="font-size:22px;font-weight:800">En yakın akıllı atık kutusu</h2></div>
  <div class="map" role="img" aria-label="Yakındaki akıllı atık kutularını gösteren harita">
    <svg viewBox="0 0 360 210">
      <rect width="360" height="210" fill="none"/>
      <path d="M0 150 Q90 120 180 140 T360 110 V210 H0Z" fill="#9FD0E6" opacity=".55"/>
      <g stroke="#fff" stroke-width="9" fill="none" opacity=".9"><path d="M-10 70 H370"/><path d="M110 -10 V220"/><path d="M250 -10 L210 220"/></g>
      <g stroke="#CBD6C3" stroke-width="1.5" fill="none"><path d="M-10 32 H370"/><path d="M40 -10 V100"/><path d="M310 -10 V120"/></g>
      <circle cx="110" cy="70" r="46" fill="#B9E23F" opacity=".25"/>
      <g fill="#123B2E"><circle cx="110" cy="70" r="11"/><circle cx="270" cy="52" r="8" opacity=".55"/><circle cx="60" cy="118" r="8" opacity=".55"/></g>
      <g fill="#B9E23F"><circle cx="110" cy="70" r="4"/></g>
      <circle cx="176" cy="104" r="9" fill="#3A7BD5" stroke="#fff" stroke-width="3"/>
      <text x="126" y="50" font-size="12" font-weight="700" fill="#123B2E" font-family="sans-serif">Kutu 1 · 350 m</text>
      <text x="190" y="128" font-size="11" fill="#123B2E" font-family="sans-serif">Sen</text>
    </svg>
  </div>
  <div class="near"><span class="dot" style="background:var(--cam);width:16px;height:16px"></span><div><b>Akıllı Kutu · Kuvayi Milliye Cd.</b><small>350 m · Cam, plastik, kağıt kabul eder</small></div></div>
  <div class="opts">
    <h2 style="font-size:17px;font-weight:600;margin-bottom:10px">Puanları aktar</h2>
    <button class="opt" data-cost="100" data-name="Mersin Kent Kart bakiyesi" aria-pressed="false"><div><strong>Mersin Kent Kart bakiyesi</strong><small>Toplu taşımada kullan</small></div><span class="cost">100 puan</span></button>
    <button class="opt" data-cost="150" data-name="Sosyal tesis indirimi" aria-pressed="false"><div><strong>Sosyal tesis indirimi</strong><small>Belediye tesislerinde geçerli</small></div><span class="cost">150 puan</span></button>
    <button class="go" id="transfer" disabled>Puanları Aktar</button>
    <div class="tip" style="margin-top:10px">Bu ekran bir prototiptir; puan değerleri örnektir.</div>
  </div>
</section>

</main>
<div class="toast" id="toast" role="status"></div>
<nav aria-label="Ana gezinme">
  <button data-go="home" aria-current="page"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 11l9-8 9 8v9a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1z"/></svg>Ana Sayfa</button>
  <button data-go="scan"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 8V6a2 2 0 0 1 2-2h2M16 4h2a2 2 0 0 1 2 2v2M20 16v2a2 2 0 0 1-2 2h-2M8 20H6a2 2 0 0 1-2-2v-2"/><circle cx="12" cy="12" r="3.5"/></svg>Tara</button>
  <button data-go="reward"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="8" width="18" height="4" rx="1"/><path d="M12 8v13M5 12v8a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1v-8M7.5 8a2.5 2.5 0 0 1 0-5C10 3 12 8 12 8s2-5 4.5-5a2.5 2.5 0 0 1 0 5"/></svg>Ödül</button>
</nav>
</div>

<script>
var WASTE = [
  {n:"Plastik Şişe", c:"var(--plastik)", bin:"Sarı kutu (plastik)", tip:"Kapağını tak, ezerek küçült."},
  {n:"Cam Kavanoz", c:"var(--cam)", bin:"Yeşil kutu (cam)", tip:"Kapağını çıkar, içini boşalt."},
  {n:"Kağıt / Defter", c:"var(--kagit)", bin:"Mavi kutu (kağıt)", tip:"Islak veya yağlı kağıtları ayırma, çöpe at."}
];
var state = {pts:120, hist:[{n:"Plastik Şişe",c:"var(--plastik)",p:10,t:"Dün"},{n:"Cam Kavanoz",c:"var(--cam)",p:10,t:"2 gün önce"},{n:"Kağıt / Defter",c:"var(--kagit)",p:10,t:"3 gün önce"}], cur:null, sel:null};
var $ = function(id){return document.getElementById(id)};
var GOAL = 200;

function toast(m){var t=$("toast");t.textContent=m;t.classList.add("show");clearTimeout(toast._t);toast._t=setTimeout(function(){t.classList.remove("show")},2200)}

function render(){
  $("pts").textContent = state.pts;
  var left = Math.max(GOAL-state.pts,0);
  $("barfill").style.width = Math.min(state.pts/GOAL*100,100)+"%";
  $("barl").textContent = left>0 ? "Kent Kart indirimine "+left+" puan kaldı" : "Kent Kart indirimi için yeterli puanın var";
  var h=$("hist"); h.innerHTML="";
  if(!state.hist.length){h.innerHTML='<div class="empty">Henüz kayıt yok. İlk atığını tara.</div>';return}
  state.hist.slice(0,5).forEach(function(x){
    var d=document.createElement("div");d.className="row";
    d.innerHTML='<span class="dot" style="background:'+x.c+'"></span><div class="t">1x '+x.n+'<small>'+x.t+'</small></div><span class="p">+'+x.p+' Puan</span>';
    h.appendChild(d);
  });
  document.querySelectorAll(".opt").forEach(function(o){ if(+o.dataset.cost>state.pts){o.setAttribute("aria-pressed","false"); if(state.sel===o)state.sel=null} });
  $("transfer").disabled = !state.sel;
}

function go(name){
  document.querySelectorAll(".screen").forEach(function(s){s.classList.remove("on")});
  $("s-"+name).classList.add("on");
  document.querySelectorAll("nav button").forEach(function(b){ if(b.dataset.go===name)b.setAttribute("aria-current","page"); else b.removeAttribute("aria-current") });
  document.querySelector("main").scrollTop=0;
  if(name==="scan")startCam(); else stopCam();
}
document.querySelectorAll("nav button").forEach(function(b){b.onclick=function(){go(b.dataset.go)}});
$("goScan").onclick=function(){go("scan")};

/* Kamera: izin verilmezse demo görünümü kullanılır */
var stream=null;
function startCam(){
  if(stream||!navigator.mediaDevices||!navigator.mediaDevices.getUserMedia)return;
  navigator.mediaDevices.getUserMedia({video:{facingMode:"environment"}}).then(function(s){
    stream=s;var v=$("video");v.srcObject=s;v.style.display="block";v.play();
  }).catch(function(){ $("hint").textContent="Kamera açılamadı, demo modu açık. Yine de Tara'ya basabilirsin."; });
}
function stopCam(){ if(stream){stream.getTracks().forEach(function(t){t.stop()});stream=null;$("video").style.display="none"} }

/* Tarama (prototipte simüle edilir; gerçek modelde Teachable Machine tahmini kullanılır) */
var idx=-1;
$("scanNow").onclick=function(){
  var f=$("frame");f.classList.add("busy");$("save").disabled=true;
  $("rName").textContent="Analiz ediliyor…";$("rAcc").textContent="";
  setTimeout(function(){
    f.classList.remove("busy");
    idx=(idx+1+Math.floor(Math.random()*2))%WASTE.length;
    var w=WASTE[idx], acc=91+Math.floor(Math.random()*9);
    state.cur=w;
    $("rName").textContent=w.n;$("rAcc").textContent="Doğruluk: %"+acc;
    $("rSw").style.background=w.c;$("rBin").textContent="Doğru atık kutusu: "+w.bin;
    $("tip").textContent=w.tip;$("save").disabled=false;
  },900);
};
$("save").onclick=function(){
  if(!state.cur)return;
  state.pts+=10;state.hist.unshift({n:state.cur.n,c:state.cur.c,p:10,t:"Az önce"});
  toast("+10 puan kazandın");state.cur=null;$("save").disabled=true;
  $("rName").textContent="Kaydedildi";$("rAcc").textContent="";$("rBin").textContent="Sıradaki atığı taramak için Tara'ya bas.";$("tip").textContent="";
  render();
};

/* Ödül */
document.querySelectorAll(".opt").forEach(function(o){
  o.onclick=function(){
    if(+o.dataset.cost>state.pts){toast("Yetersiz puan: "+o.dataset.cost+" puan gerekiyor");return}
    document.querySelectorAll(".opt").forEach(function(x){x.setAttribute("aria-pressed","false")});
    o.setAttribute("aria-pressed","true");state.sel=o;$("transfer").disabled=false;
  };
});
$("transfer").onclick=function(){
  if(!state.sel)return;
  var c=+state.sel.dataset.cost;
  state.pts-=c;toast(state.sel.dataset.name+" için "+c+" puan aktarıldı");state.sel.setAttribute("aria-pressed","false");state.sel=null;render();
};
render();
</script>
</body>
</html>
