<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover">
<meta name="theme-color" content="#2a1b3d">
<meta name="apple-mobile-web-app-capable" content="yes">
<title>Pati Aşkı 🐾</title>
<style>
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
  html,body{margin:0;padding:0;height:100%;overflow:hidden;background:#1b1230;
    font-family:"Segoe UI",-apple-system,Roboto,"Helvetica Neue",sans-serif;
    user-select:none;-webkit-user-select:none;overscroll-behavior:none;touch-action:manipulation}
  #app{position:fixed;inset:0;display:flex;flex-direction:column;overflow:hidden}

  /* ---------- ÜST BAR ---------- */
  #top{flex:0 0 auto;padding:calc(env(safe-area-inset-top) + 8px) 12px 8px;color:#fff;
    background:linear-gradient(180deg,rgba(42,27,61,.95),rgba(42,27,61,.55));
    backdrop-filter:blur(6px);z-index:30}
  .row{display:flex;align-items:center;gap:8px}
  .logo{font-size:17px;font-weight:800;letter-spacing:.4px;text-shadow:0 2px 6px #0006}
  .lvl{font-size:11px;font-weight:700;background:#ffd166;color:#4a2c00;padding:3px 9px;border-radius:999px;white-space:nowrap}
  .spacer{flex:1}
  .icon{width:34px;height:34px;border-radius:12px;border:1px solid #ffffff26;background:#ffffff14;
    color:#fff;font-size:15px;display:grid;place-items:center;padding:0}
  .icon:active{transform:scale(.92);background:#ffffff2a}
  #loveWrap{position:relative;height:12px;border-radius:999px;background:#0000004d;margin-top:8px;overflow:hidden}
  #loveBar{position:absolute;inset:0;width:0%;border-radius:999px;
    background:linear-gradient(90deg,#ff8fb1,#ffd166,#8ef7c5);transition:width .35s ease}
  #loveTxt{position:absolute;inset:0;font-size:9px;font-weight:800;color:#fff;text-align:center;
    line-height:12px;text-shadow:0 1px 2px #0009;letter-spacing:.5px}

  /* ---------- ODA ---------- */
  #room{flex:1 1 auto;position:relative;overflow:hidden;isolation:isolate}
  .wall{position:absolute;left:0;right:0;top:0;height:56%;
    background:
      radial-gradient(circle at 18% 30%,#ffdfa0 0 22%,transparent 23%),
      repeating-linear-gradient(90deg,#4a3163 0 26px,#452c5d 26px 52px);
    background-blend-mode:soft-light}
  .wall::after{content:"";position:absolute;inset:0;
    background:radial-gradient(ellipse at 50% 0%,#ffd9a0aa,transparent 60%)}
  .floor{position:absolute;left:0;right:0;bottom:0;height:46%;
    background:repeating-linear-gradient(90deg,#a9764d 0 30px,#96663f 30px 62px),
               linear-gradient(#8a5c39,#6d4527);
    box-shadow:inset 0 8px 18px #0006}
  .base{position:absolute;left:0;right:0;top:56%;height:7px;background:#2f1d44;opacity:.5}
  .rug{position:absolute;left:50%;bottom:5%;width:74%;height:26%;transform:translateX(-50%);
    background:radial-gradient(ellipse at 50% 40%,#c46b8a,#8d3f63);border-radius:50%;opacity:.75;
    box-shadow:0 12px 26px #0006,inset 0 0 0 8px #ffffff14}

  .window{position:absolute;right:5%;top:7%;width:26%;aspect-ratio:1/1.15;border-radius:14px;
    background:linear-gradient(180deg,#1b2a63,#4a3f8f 60%,#8c5fb0);
    border:6px solid #f3e6d2;box-shadow:0 10px 24px #0007}
  .window::before{content:"";position:absolute;left:50%;top:0;bottom:0;width:5px;background:#f3e6d2;transform:translateX(-50%)}
  .window::after{content:"";position:absolute;left:0;right:0;top:52%;height:5px;background:#f3e6d2}
  .moon{position:absolute;right:16%;top:12%;width:26%;aspect-ratio:1;border-radius:50%;
    background:#fdf6d8;box-shadow:0 0 22px #fdf6d899}
  .star{position:absolute;width:4px;height:4px;border-radius:50%;background:#fff;opacity:.85}

  .frame{position:absolute;width:52px;height:40px;border:5px solid #f3e6d2;border-radius:5px;
    background:#ffd166;box-shadow:0 6px 14px #0006}
  .frame.f1{left:6%;top:9%}
  .frame.f2{left:24%;top:22%;width:40px;height:40px;background:#8ef7c5}
  .frame::after{content:"🐾";position:absolute;inset:0;display:grid;place-items:center;font-size:15px;filter:grayscale(1) opacity(.55)}

  .tower{position:absolute;left:4%;bottom:14%;width:78px;pointer-events:none}
  .tower .p{width:100%;height:15px;border-radius:6px;background:#6b4a86;margin-bottom:3px;box-shadow:0 4px 8px #0006}
  .tower .p:nth-child(2){width:66%;background:#7d5a9b}
  .tower .post{width:16px;height:34px;background:#5a3c72;margin:0 auto 3px}
  .tower .ball{position:absolute;right:-2px;bottom:-14px;width:20px;height:20px;border-radius:50%;
    background:#ffd166;box-shadow:0 4px 8px #0007}

  .plant{position:absolute;right:6%;bottom:12%;width:56px;pointer-events:none}
  .plant .pot{width:38px;height:32px;margin:0 auto;background:linear-gradient(#d98b5f,#a9603c);border-radius:5px 5px 12px 12px}
  .plant .lf{position:absolute;left:50%;bottom:26px;width:14px;height:36px;border-radius:100% 0 100% 0;
    background:linear-gradient(#4fae63,#2f7a45);transform-origin:bottom center}
  .plant .lf:nth-child(1){transform:translateX(-50%) rotate(-34deg)}
  .plant .lf:nth-child(2){transform:translateX(-50%) rotate(0deg);height:46px;background:linear-gradient(#5ec072,#357f4c)}
  .plant .lf:nth-child(3){transform:translateX(-50%) rotate(34deg)}

  .cush{position:absolute;width:74px;height:34px;border-radius:34px;background:#7a5fa8;opacity:.85;
    box-shadow:0 8px 16px #0006}
  .cush.c1{left:44%;bottom:26%}
  .cush.c2{right:22%;bottom:34%;background:#c98ab0;width:56px}

  /* ---------- KEDİLER ---------- */
  .cat{position:absolute;left:0;top:0;width:clamp(62px,19vw,104px);z-index:10;
    will-change:transform;filter:drop-shadow(0 10px 12px #0007)}
  .cat svg{width:100%;display:block;overflow:visible}
  .cat .shadow{position:absolute;left:50%;bottom:2%;width:76%;height:9px;transform:translateX(-50%);
    background:#00000059;border-radius:50%;filter:blur(2px)}
  .cat.walk .body{animation:walk .42s ease-in-out infinite alternate}
  .cat.idle .body{animation:breathe 2.6s ease-in-out infinite}
  .cat.happy .body{animation:hop .5s ease-in-out 3}
  .cat.sleep .body{animation:sleepb 3.2s ease-in-out infinite}
  @keyframes walk{from{transform:translateY(0) rotate(-1.5deg)}to{transform:translateY(-2px) rotate(1.5deg)}}
  @keyframes breathe{0%,100%{transform:scale(1,1)}50%{transform:scale(1.03,.97)}}
  @keyframes hop{0%{transform:translateY(0) scale(1)}40%{transform:translateY(-16px) scale(1.06,.94)}100%{transform:translateY(0) scale(1)}}
  @keyframes sleepb{0%,100%{transform:translateY(0) scale(1,1)}50%{transform:translateY(1px) scale(1.05,.93)}}
  .eyes{animation:blink 5.2s infinite;transform-box:fill-box;transform-origin:center}
  @keyframes blink{0%,94%,100%{transform:scaleY(1)}96.5%{transform:scaleY(.08)}}
  .zzz{position:absolute;left:70%;top:-6px;font-size:15px;font-weight:800;color:#fff;
    text-shadow:0 2px 5px #000a;animation:zz 2.4s ease-in infinite}
  @keyframes zz{0%{opacity:0;transform:translate(0,6px) scale(.7)}30%{opacity:1}100%{opacity:0;transform:translate(10px,-30px) scale(1.1)}}

  /* ---------- PARÇACIKLAR ---------- */
  .fx{position:absolute;font-size:22px;pointer-events:none;z-index:25;will-change:transform,opacity}
  @keyframes heartUp{0%{opacity:0;transform:translate(-50%,0) scale(.4)}
    18%{opacity:1;transform:translate(-50%,-14px) scale(1.15)}
    100%{opacity:0;transform:translate(-50%,-92px) scale(.75) rotate(12deg)}}
  .fx.heart{animation:heartUp 1.1s ease-out forwards}
  .fx.star{animation:heartUp 1.4s ease-out forwards}
  .float{position:absolute;font-size:14px;font-weight:900;pointer-events:none;z-index:26;
    color:#fff;text-shadow:0 2px 4px #000b;animation:floatUp 1s ease-out forwards;white-space:nowrap}
  @keyframes floatUp{0%{opacity:0;transform:translate(-50%,0) scale(.7)}
    20%{opacity:1;transform:translate(-50%,-10px) scale(1.1)}
    100%{opacity:0;transform:translate(-50%,-56px) scale(1)}}
  .confetti{position:absolute;width:9px;height:14px;border-radius:2px;z-index:28;pointer-events:none;
    animation:fall linear forwards}
  @keyframes fall{to{transform:translateY(105vh) rotate(720deg);opacity:.15}}

  /* ---------- ALT PANEL ---------- */
  #panel{flex:0 0 auto;z-index:30;background:linear-gradient(180deg,#2a1b3df2,#1b1230);
    border-top:1px solid #ffffff1f;padding:8px 12px calc(env(safe-area-inset-bottom) + 8px);
    box-shadow:0 -10px 26px #0006}
  #catName{font-size:13px;font-weight:800;color:#ffd166;display:flex;align-items:center;gap:6px;min-height:18px}
  #catName small{color:#ffffff8c;font-weight:600;font-size:10px}
  .bars{display:grid;grid-template-columns:1fr 1fr 1fr;gap:7px;margin:6px 0 8px}
  .bar{font-size:9px;color:#ffffffb0;font-weight:700}
  .track{height:9px;border-radius:999px;background:#00000059;overflow:hidden;margin-top:3px}
  .fill{height:100%;border-radius:999px;width:50%;transition:width .3s ease}
  .f1{background:linear-gradient(90deg,#ffb56b,#ffd166)}
  .f2{background:linear-gradient(90deg,#ff8fb1,#ff5c8a)}
  .f3{background:linear-gradient(90deg,#7ee6ff,#5b8cff)}
  #dock{display:grid;grid-template-columns:repeat(4,1fr);gap:8px}
  .act{border:0;border-radius:16px;padding:8px 4px 7px;font-size:10px;font-weight:800;color:#2a1b3d;
    display:grid;gap:2px;justify-items:center;box-shadow:0 6px 0 #0000004d;touch-action:manipulation}
  .act em{font-size:20px;font-style:normal;line-height:1}
  .act:active{transform:translateY(4px);box-shadow:0 2px 0 #0000004d}
  .a1{background:linear-gradient(#ffd98a,#ffb648)}
  .a2{background:linear-gradient(#a8f0d0,#63d9a8)}
  .a3{background:linear-gradient(#c9b6ff,#9b7dff)}
  .a4{background:linear-gradient(#9fd0ff,#5f9dff);color:#fff}
  .act.cool{filter:grayscale(.75);opacity:.5}
  #hint{font-size:10px;color:#ffffff8a;text-align:center;margin-top:6px}

  /* ---------- KAPLAMALAR ---------- */
  .veil{position:fixed;inset:0;z-index:60;display:grid;place-items:center;padding:20px;
    background:radial-gradient(circle at 50% 30%,#3d2760f0,#140d24fa);backdrop-filter:blur(4px);
    transition:opacity .35s ease}
  .veil.hide{opacity:0;pointer-events:none}
  .card{width:100%;max-width:380px;max-height:92vh;overflow:auto;background:linear-gradient(180deg,#3a2560,#241741);
    border:1px solid #ffffff22;border-radius:24px;padding:22px 20px;color:#fff;text-align:center;
    box-shadow:0 24px 60px #0009;animation:pop .45s cubic-bezier(.2,1.3,.4,1)}
  @keyframes pop{from{transform:scale(.86) translateY(14px);opacity:0}to{transform:none;opacity:1}}
  .card h1{margin:0 0 6px;font-size:26px;letter-spacing:.3px}
  .card h2{margin:0 0 10px;font-size:19px;color:#ffd166}
  .card p{margin:8px 0;font-size:13.5px;line-height:1.55;color:#f0e6ff}
  .card .envelope{font-size:46px;animation:wave 1.6s ease-in-out infinite}
  @keyframes wave{0%,100%{transform:rotate(-8deg)}50%{transform:rotate(8deg)}}
  .paper{background:#fff8ec;color:#3b2a1c;border-radius:16px;padding:16px;text-align:left;
    font-size:13.5px;line-height:1.7;box-shadow:0 10px 22px #0006;margin:12px 0}
  .paper b{color:#c0392b}
  .paper .sig{text-align:right;margin-top:10px;font-style:italic;color:#8a6a4a}
  input[type=text]{width:100%;padding:12px 14px;border-radius:14px;border:1px solid #ffffff33;background:#ffffff14;
    color:#fff;font-size:15px;font-weight:700;text-align:center;margin:6px 0 4px;outline:none}
  input[type=text]:focus{border-color:#ffd166}
  .btn{width:100%;margin-top:12px;padding:14px;border:0;border-radius:16px;font-size:16px;font-weight:900;
    color:#4a2c00;background:linear-gradient(#ffe08a,#ffb648);box-shadow:0 6px 0 #b9761a;touch-action:manipulation}
  .btn:active{transform:translateY(4px);box-shadow:0 2px 0 #b9761a}
  .btn.ghost{background:#ffffff14;color:#fff;box-shadow:0 6px 0 #0000004d;font-size:13px;padding:11px}
  .note{font-size:10.5px;color:#ffffff70;margin-top:10px;line-height:1.5}
  .tag{display:inline-block;background:#ffd166;color:#4a2c00;font-size:10px;font-weight:900;
    padding:4px 10px;border-radius:999px;margin-bottom:8px}
</style>
</head>
<body>
<div id="app">

  <div id="top">
    <div class="row">
      <div class="logo">🐾 PATİ AŞKI</div>
      <div class="lvl" id="lvlTxt">Seviye 1</div>
      <div class="spacer"></div>
      <button class="icon" id="btnLetter" title="Mektup">💌</button>
      <button class="icon" id="btnSound" title="Ses">🔊</button>
    </div>
    <div id="loveWrap">
      <div id="loveBar"></div>
      <div id="loveTxt">AŞK DOLUMU</div>
    </div>
  </div>

  <div id="room">
    <div class="wall"></div>
    <div class="floor"></div>
    <div class="base"></div>
    <div class="window"><div class="moon"></div></div>
    <div class="frame f1"></div>
    <div class="frame f2"></div>
    <div class="tower"><div class="p"></div><div class="p"></div><div class="post"></div><div class="ball"></div></div>
    <div class="plant"><div class="lf"></div><div class="lf"></div><div class="lf"></div><div class="pot"></div></div>
    <div class="rug"></div>
    <div class="cush c1"></div>
    <div class="cush c2"></div>
  </div>

  <div id="panel">
    <div id="catName">Bir kediye dokun 🐾</div>
    <div class="bars">
      <div class="bar">🍚 Tokluk<div class="track"><div class="fill f1" id="b1"></div></div></div>
      <div class="bar">💗 Mutluluk<div class="track"><div class="fill f2" id="b2"></div></div></div>
      <div class="bar">⚡ Enerji<div class="track"><div class="fill f3" id="b3"></div></div></div>
    </div>
    <div id="dock">
      <button class="act a1" data-act="feed"><em>🐟</em>Mama</button>
      <button class="act a2" data-act="toy"><em>🪶</em>Tüy</button>
      <button class="act a3" data-act="brush"><em>🪮</em>Tarak</button>
      <button class="act a4" data-act="sleep"><em>💤</em>Uyu</button>
    </div>
    <div id="hint">Kediye dokun = sarıl & 🏆 enerjik sarılmalar ×3 puan</div>
  </div>
</div>

<!-- BAŞLANGIÇ -->
<div class="veil" id="startVeil">
  <div class="card">
    <div class="envelope">💌</div>
    <h1 id="stTitle">Pati Aşkı</h1>
    <div class="tag">Sana özel bir oyun</div>
    <p id="stText">Küçük bir dünya hazırladım. Burası senin: dört patili dostlarını besle, tüylerini tara, sarıl. Sevgin büyüdükçe evimize yeni kediler geliyor.</p>
    <input type="text" id="inpName" placeholder="Sevgilinin adı..." maxlength="18" autocomplete="off">
    <button class="btn" id="btnStart">Başlayalım 🐾</button>
    <p class="note">İpucu: Kedileri elle tutarak sürükleyebilir, üstüne dokunarak sarılabilirsin.</p>
  </div>
</div>

/* SEVİYE / BİTİŞ */
<div class="veil hide" id="upVeil">
  <div class="card">
    <div class="envelope" id="upEmo">🎉</div>
    <h2 id="upTitle">Seviye 2!</h2>
    <p id="upText"></p>
    <button class="btn" id="btnUpOk">Devam et 🐾</button>
  </div>
</div>

<!-- MEKTUP -->
<div class="veil hide" id="letterVeil">
  <div class="card">
    <div class="envelope">💌</div>
    <h2>Sana bir mektup</h2>
    <div class="paper" id="letterBody"></div>
    <button class="btn" id="btnLetterOk">Kapat</button>
  </div>
</div>

<script>
/* =========================================================
   KİŞİSELLEŞTİRME — sadece burayı düzenle
   ========================================================= */
const CONFIG = {
  baslik: "Pati Aşkı",
  kisi: "Sevgilim",
  girisMetni: "Burası senin için. Dört patili dostları besle, tüylerini tara, sarıl. Sevgin büyüdükçe evimize yeni kediler geliyor.",
  mektup:
    "Seni çok seviyorum. Yüzünden her sabah uyandığımda, kahvaltıda gülümsediğinde, yorulduğunda seni görünce içimden bir şeyler 'tamam' diyor. " +
    "Sen benim evimsin. Bu oyunu senin için yaptım — içindeki her kedinin gülümsemesi, aslında senin gülüşün.",
  imza: "Seni çok seven [İsmin]",
  // Seviye atlarken gösterilen satırlar:
  seviyeNotlari: [
    "Boncuk, göğsünde biriken tüyleri birbirine karıştırdı ve sana özel bir salon kurdu. 🐾",
    "Odaya yeni bir kedi katıldı: Tekir. \"Bu evde yer var mı?\" diye soruyor, gözleri falan. 😸",
    "Pamuk uyuduğunda yanına bir minder bıraktı. Biri senin için. 💗",
    "Fındık masaya çıktı, gözlerini kıstı ve mırıldamaya başladı. Biliyorsun ne demek istediğini. 😻",
    "Artık evimiz dolu. Ama asıl sıcaklık seninle geliyor. 💌"
  ]
};

/* =========================================================
   VERİ
   ========================================================= */
const CAT_KIND = [
  { ad:"Boncuk", renk:"#f3b23c", koyu:"#d18a24", desen:"cizgi", goz:"#3f7d3f", aksesuar:"yok" },
  { ad:"Tekir",  renk:"#8d8d95", koyu:"#5f5f68", desen:"yama",   goz:"#e0a020", aksesuar:"papa" },
  { ad:"Pamuk",  renk:"#f6f1e4", koyu:"#cfc4ae", desen:"yok",    goz:"#5aa9e6", aksesuar:"halka" },
  { ad:"Fındık", renk:"#a9714b", koyu:"#82512f", desen:"cizgi", goz:"#7ac74f", aksesuar:"yok" },
  { ad:"Şeftali",renk:"#f0b7a4", koyu:"#d18d78", desen:"yok",    goz:"#8b6ad1", aksesuar:"papa" },
  { ad:"Kömür",  renk:"#4a4a52", koyu:"#2c2c33", desen:"yok",    goz:"#ffd166", aksesuar:"yok" }
];
const SEVIYE_ESIK = [0, 0, 34, 90, 175, 300];   // seviye 2..6 için gereken aşk
const BASLANGIC_KEDI = 2;

const ODA = document.getElementById("room");
const panel = {
  ad: document.getElementById("catName"),
  b1: document.getElementById("b1"), b2: document.getElementById("b2"), b3: document.getElementById("b3")
};
const elSeviye = document.getElementById("lvlTxt");
const elBar = document.getElementById("loveBar");
const elTxt = document.getElementById("loveTxt");

const S = { bas:false, seviye:1, ask:0, combo:0, comboT:0, secili:null, kalan:{}, toplamSarilma:0, isim:"Sevgilim" };
let cats = [], W = 300, H = 300, son = 0, t0 = 0;

/* =========================================================
   SES (harici dosya yok, tamamı sentez)
   ========================================================= */
const Snd = (() => {
  let ac = null, acik = true;
  const ctx = () => {
    if (!ac) { const C = window.AudioContext || window.webkitAudioContext; if (C) ac = new C(); }
    if (ac && ac.state === "suspended") ac.resume();
    return ac;
  };
  function tone(f1, f2, dur, type, vol, vib) {
    if (!acik) return; const c = ctx(); if (!c) return;
    const o = c.createOscillator(), g = c.createGain();
    o.type = type || "sine"; o.frequency.setValueAtTime(f1, c.currentTime);
    if (f2) o.frequency.exponentialRampToValueAtTime(Math.max(40, f2), c.currentTime + dur);
    g.gain.setValueAtTime(0, c.currentTime);
    g.gain.linearRampToValueAtTime(vol || .12, c.currentTime + .02);
    g.gain.exponentialRampToValueAtTime(.0001, c.currentTime + dur);
    if (vib) { const l = c.createOscillator(), lg = c.createGain();
      l.frequency.value = vib; lg.gain.value = (vol || .12) * .6;
      l.connect(lg); lg.connect(g.gain); l.start(); l.stop(c.currentTime + dur); }
    o.connect(g); g.connect(c.destination); o.start(); o.stop(c.currentTime + dur + .02);
  }
  function noise(dur, vol) {
    if (!acik) return; const c = ctx(); if (!c) return;
    const n = c.createBufferSource(), buf = c.createBuffer(1, c.sampleRate * dur, c.sampleRate);
    const d = buf.getChannelData(0);
    for (let i = 0; i < d.length; i++) d[i] = (Math.random() * 2 - 1) * (1 - i / d.length);
    n.buffer = buf;
    const f = c.createBiquadFilter(); f.type = "bandpass"; f.frequency.value = 900; f.Q.value = .9;
    const g = c.createGain(); g.gain.value = vol || .1;
    n.connect(f); f.connect(g); g.connect(c.destination); n.start();
  }
  return {
    get acik() { return acik; },
    toggle() { acik = !acik; return acik; },
    purr() { tone(78, 62, .45, "sawtooth", .055, 26); },
    meow() { tone(560, 900, .13, "triangle", .1); setTimeout(() => tone(880, 420, .26, "triangle", .09), 110); },
    eat() { noise(.09, .09); setTimeout(() => noise(.08, .07), 120); },
    toy() { tone(300, 1500, .18, "sine", .07); },
    brush() { noise(.3, .045); },
    up() { [523, 659, 784, 1046].forEach((f, i) => setTimeout(() => tone(f, f, .2, "sine", .11), i * 95)); }
  };
})();

const tik = (ms) => { try { navigator.vibrate && navigator.vibrate(ms || 8); } catch (e) {} };

/* =========================================================
   KEDİ ÇİZİMİ (SVG)
   ========================================================= */
function kediSVG(k, boyut) {
  const r = k.renk, d = k.koyu, desen = "";
  if (k.desen === "cizgi") {
    desen = `<g fill="${d}" opacity=".55">
      <rect x="45" y="20" width="4" height="12" rx="2"/><rect x="53" y="18" width="4" height="14" rx="2"/>
      <rect x="61" y="21" width="4" height="11" rx="2"/>
      <rect x="36" y="70" width="4" height="14" rx="2"/><rect x="54" y="70" width="4" height="14" rx="2"/>
      <rect x="66" y="70" width="4" height="14" rx="2"/></g>`;
  } else if (k.desen === "yama") {
    desen = `<g fill="${d}" opacity=".7"><ellipse cx="38" cy="32" rx="11" ry="9"/>
      <ellipse cx="63" cy="27" rx="8" ry="7"/><ellipse cx="60" cy="76" rx="12" ry="10"/></g>`;
  }
  const ak = k.aksesuar;
  const aksesuar = ak === "papa"
    ? `<g transform="translate(62,14) rotate(18)"><path d="M0 0 C-12 -12 -22 -2 -10 4 C-20 12 -4 16 2 5 Z" fill="#ff6f9c"/>
       <circle cx="2" cy="4" r="3.4" fill="#ffd166"/></g>`
    : ak === "halka"
    ? `<g transform="translate(50,92)"><rect x="-16" y="-4" width="32" height="8" rx="4" fill="#ff5c8a"/>
       <circle cx="16" cy="0" r="5" fill="#ffd166" stroke="#ff5c8a" stroke-width="2"/></g>`
    : "";
  return `<svg viewBox="0 0 100 104" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <g class="body">
      <ellipse cx="50" cy="99" rx="13" ry="4.5" fill="${d}" opacity=".35"/>
      <path d="M74 84 C92 84 96 66 86 60 C90 74 76 76 68 74 Z" fill="${r}" stroke="${d}" stroke-width="2"/>
      <ellipse cx="50" cy="76" rx="24" ry="20" fill="${r}" stroke="${d}" stroke-width="2"/>
      ${desen}
      <ellipse cx="50" cy="80" rx="12" ry="12" fill="#ffffff" opacity=".18"/>
      <path d="M27 26 L22 4 L43 16 Z" fill="${r}" stroke="${d}" stroke-width="2.4" stroke-linejoin="round"/>
      <path d="M73 26 L78 4 L57 16 Z" fill="${r}" stroke="${d}" stroke-width="2.4" stroke-linejoin="round"/>
      <path d="M30 24 L27 11 L40 18 Z" fill="#ffb3c6" opacity=".85"/>
      <path d="M70 24 L73 11 L60 18 Z" fill="#ffb3c6" opacity=".85"/>
      <circle cx="50" cy="42" r="25" fill="${r}" stroke="${d}" stroke-width="2.4"/>
      <g class="eyes">
        <ellipse cx="40" cy="40" rx="4.6" ry="5.6" fill="${k.goz}"/>
        <ellipse cx="60" cy="40" rx="4.6" ry="5.6" fill="${k.goz}"/>
        <ellipse cx="40" cy="38.6" rx="1.6" ry="2" fill="#fff" opacity=".9"/>
        <ellipse cx="60" cy="38.6" rx="1.6" ry="2" fill="#fff" opacity=".9"/>
      </g>
      <path d="M46.5 48.5 L53.5 48.5 L50 52 Z" fill="#ff8fa3"/>
      <path d="M50 52 q-4 4 -7.5 .6 M50 52 q4 4 7.5 .6" fill="none" stroke="${d}" stroke-width="1.8" stroke-linecap="round"/>
      <g stroke="${d}" stroke-width="1.6" stroke-linecap="round" opacity=".8">
        <path d="M32 50 L18 46"/><path d="M32 54 L17 55"/><path d="M68 50 L82 46"/><path d="M68 54 L83 55"/>
      </g>
      <ellipse cx="32" cy="58" rx="5" ry="3.2" fill="#ff8fa3" opacity=".35"/>
      <ellipse cx="68" cy="58" rx="5" ry="3.2" fill="#ff8fa3" opacity=".35"/>
      ${aksesuar}
    </g>
  </svg>`;
}

/* =========================================================
   KEDİ YÖNETİMİ
   ========================================================= */
function olusturKedi(i) {
  const k = Object.assign({}, CAT_KIND[i % CAT_KIND.length]);
  k.id = i;
  k.el = document.createElement("div");
  k.el.className = "cat idle";
  k.el.innerHTML = `<div class="shadow"></div>${kediSVG(k)}${k.zzzEl ? "" : '<div class="zzz" hidden>z</div>'}`;
  k.zzzEl = k.el.querySelector(".zzz");
  ODA.appendChild(k.el);
  k.tokluk = 62 + Math.random() * 25;
  k.mutluluk = 60 + Math.random() * 30;
  k.enerji = 60 + Math.random() * 30;
  k.durum = Math.random() < .35 ? "sleep" : "idle";
  k.hedefX = 40 + Math.random() * 100;
  k.hedefY = 40 + Math.random() * 55;
  k.x = Math.random() * 70;
  k.y = 45 + Math.random() * 40;
  k.vx = 0; k.vy = 0; k.yon = 1; k.bekle = 1 + Math.random() * 3;
  k.hiz = 7 + Math.random() * 6;
  k.olcek = .82 + Math.random() * .3;
  k.el.style.zIndex = String(10 + Math.floor(k.y / 8));
  return k;
}
function kediEkle(i) {
  const c = olusturKedi(i);
  cats.push(c);
  const z = document.createElement("div");
  z.className = "fx star"; z.textContent = "✨";
  z.style.left = "50%"; z.style.top = "42%";
  ODA.appendChild(z);
  setTimeout(() => z.remove(), 1500);
  return c;
}
function kediSil(c) { c.el.remove(); cats = cats.filter(x => x !== c); }

/* =========================================================
   EFEKTLER
   ========================================================= */
function parca(x, y, karakter, sure) {
  const f = document.createElement("div");
  f.className = "fx" + (karakter === "★" ? " star" : " heart");
  f.textContent = karakter;
  f.style.left = x + "px"; f.style.top = y + "px";
  f.style.animationDuration = (sure || 1.1) + "s";
  f.style.fontSize = (16 + Math.random() * 14) + "px";
  ODA.appendChild(f);
  setTimeout(() => f.remove(), (sure || 1.1) * 1000 + 60);
}
function yazi(x, y, txt, renk) {
  const f = document.createElement("div");
  f.className = "float"; f.textContent = txt;
  if (renk) f.style.color = renk;
  f.style.left = x + "px"; f.style.top = y + "px";
  ODA.appendChild(f);
  setTimeout(() => f.remove(), 1050);
}
function konfeti(n) {
  const renk = ["#ffd166", "#ff8fb1", "#8ef7c5", "#9fd0ff", "#c9b6ff"];
  for (let i = 0; i < n; i++) {
    const c = document.createElement("div");
    c.className = "confetti";
    c.style.left = Math.random() * 100 + "%";
    c.style.top = "-20px";
    c.style.background = renk[i % renk.length];
    c.style.animationDuration = (1.6 + Math.random() * 1.6) + "s";
    c.style.animationDelay = (Math.random() * .5) + "s";
    ODA.appendChild(c);
    setTimeout(() => c.remove(), 3800);
  }
}

/* =========================================================
   OYUN
   ========================================================= */
function saril(c, sessiz) {
  if (!S.bas) return;
  S.combo++; S.comboT = 1.5;
  const carpan = Math.min(3, 1 + Math.floor((S.combo - 1) / 4));
  c.mutluluk = Math.min(100, c.mutluluk + 7);
  c.enerji = Math.max(0, c.enerji - .6);
  S.toplamSarilma++;
  const puan = Math.round(2 * carpan);
  S.ask += puan;
  const r = c.el.getBoundingClientRect(), o = ODA.getBoundingClientRect();
  const cx = r.left - o.left + r.width / 2, cy = r.top - o.top + r.height * .35;
  parca(cx + (Math.random() * 40 - 20), cy, ["💗", "💕", "🐾", "💛", "✨"][Math.floor(Math.random() * 5)]);
  if (carpan > 1) yazi(cx, cy - 10, "×" + carpan + "!", "#ffd166");
  if (c.durum === "sleep") c.durum = "idle";
  c.el.classList.remove("happy"); void c.el.offsetWidth; c.el.classList.add("happy");
  setTimeout(() => c.el.classList.remove("happy"), 1500);
  if (!sessiz) Snd.purr();
  tik(6);
  seviyeKontrol();
  panelGuncelle();
}

function hedefKedi() {
  if (S.secili && cats.indexOf(S.secili) > -1) return S.secili;
  return cats[Math.floor(Math.random() * cats.length)];
}
function tumKediler(komsu) { return cats.map(c => komsu(c)); }

function eylem(tur) {
  if (!S.bas) return;
  const c = hedefKedi();
  if (!c) return;
  const r = c.el.getBoundingClientRect(), o = ODA.getBoundingClientRect();
  const cx = r.left - o.left + r.width / 2, cy = r.top - o.top + r.height * .35;
  let not = "";
  if (tur === "feed") {
    c.tokluk = Math.min(100, c.tokluk + 40);
    c.mutluluk = Math.min(100, c.mutluluk + 8);
    not = "+40 tokluk"; Snd.eat(); parca(cx, cy, "🐟");
    c.durum = "idle";
  } else if (tur === "toy") {
    c.mutluluk = Math.min(100, c.mutluluk + 22);
    c.enerji = Math.max(0, c.enerji - 7);
    not = "+22 mutluluk"; Snd.toy(); parca(cx, cy, "🪶");
    c.durum = "play"; c.bekle = 2;
  } else if (tur === "brush") {
    c.mutluluk = Math.min(100, c.mutluluk + 13);
    c.tokluk = Math.min(100, c.tokluk + 5);
    not = "tüyler tarandı ✨"; Snd.brush(); parca(cx, cy, "✨");
  } else if (tur === "sleep") {
    c.durum = c.durum === "sleep" ? "idle" : "sleep";
    c.bekle = .5;
    not = c.durum === "sleep" ? "uyuyor 💤" : "uyandı!";
    Snd.meow();
  }
  S.ask += 3;
  yazi(cx, cy - 14, not, "#8ef7c5");
  tik(10);
  seviyeKontrol();
  panelGuncelle();
}

function seviyeKontrol() {
  while (S.seviye < 6 && S.ask >= SEVIYE_ESIK[S.seviye]) {
    S.seviye++;
    S.ask -= SEVIYE_ESIK[S.seviye - 1];
    S.combo = 0;
    Snd.up(); konfeti(30); tik([12, 40, 12, 40, 24]);
    if (cats.length < CAT_KIND.length) kediEkle(cats.length);
    const not = CONFIG.seviyeNotlari[S.seviye - 2] || "Yeni bir kedi arkadaşımız daha var!";
    seviyeGoster(not);
  }
  if (S.seviye >= 6 && S.ask >= SEVIYE_ESIK[5] - SEVIYE_ESIK[5]) { /* sonsuza kadar oynanır */ }
  uiGuncelle();
}
function seviyeGoster(not) {
  const v = document.getElementById("upVeil");
  document.getElementById("upTitle").textContent = "Seviye " + S.seviye + "!";
  document.getElementById("upEmo").textContent = S.seviye >= 5 ? "💌" : (S.seviye >= 4 ? "😻" : "🎉");
  document.getElementById("upText").textContent = not + (S.seviye >= 5 ? " Mektubu okumak için üstteki 💌 düğmesine dokun." : "");
  v.classList.remove("hide");
  try { localStorage.setItem("pati_seviye", S.seviye); } catch (e) {}
}

function uiGuncelle() {
  elSeviye.textContent = "Seviye " + S.seviye;
  const hedef = S.seviye < 6 ? SEVIYE_ESIK[S.seviye] : SEVIYE_ESIK[5] + 260;
  const taban = S.seviye < 6 ? SEVIYE_ESIK[S.seviye - 1] : SEVIYE_ESIK[5];
  const y = Math.max(0, Math.min(100, (S.ask - taban) / (hedef - taban) * 100));
  elBar.style.width = y + "%";
  elTxt.textContent = S.seviye < 6 ? ("SEVİYE " + S.seviye + " · AŞK " + Math.round(S.ask) + "/" + hedef)
                                  : ("SONSUZ AŞK · " + Math.round(S.ask) + " ❤️");
  panelGuncelle();
}
function panelGuncelle() {
  const c = S.secili && cats.indexOf(S.secili) > -1 ? S.secili : null;
  if (!c) {
    panel.ad.innerHTML = '<span>🐾 Bir kediye dokun</span><small>seç</small>';
    panel.b1.style.width = panel.b2.style.width = panel.b3.style.width = "0%";
    return;
  }
  const uyku = c.durum === "sleep";
  panel.ad.innerHTML = "<span>😻 " + c.ad + "</span><small>" + (uyku ? "uyuyor · enerji doluyor" : "seçili · sarılabilirsin") + "</small>";
  panel.b1.style.width = c.tokluk + "%";
  panel.b2.style.width = c.mutluluk + "%";
  panel.b3.style.width = c.enerji + "%";
}

/* ---------- ANA DÖNGÜ ---------- */
function boyutla() {
  const r = ODA.getBoundingClientRect();
  W = r.width; H = r.height;
  cats.forEach(c => { c.x = Math.min(c.x, Math.max(4, W - 78)); c.y = Math.min(c.y, Math.max(6, H - 96)); });
}
function adim(dt) {
  t0 += dt;
  cats.forEach(c => {
    // ihtiyaçlar zamanla azalır
    c.tokluk = Math.max(0, c.tokluk - .30 * dt);
    c.mutluluk = Math.max(0, c.mutluluk - .22 * dt);
    c.enerji = Math.max(0, c.enerji - .16 * dt);

    if (c.durum === "sleep") {
      c.enerji = Math.min(100, c.enerji + 9 * dt);
      c.mutluluk = Math.max(0, c.mutluluk - .06 * dt);
      c.zzzEl.hidden = false;
      c.el.className = "cat sleep";
      if (c.enerji >= 100 || (c.bekle -= dt) < -30) { c.durum = "idle"; c.bekle = 1 + Math.random() * 2; }
    } else {
      c.zzzEl.hidden = true;
      if (c.enerji < 22 && Math.random() < .01) { c.durum = "sleep"; c.bekle = 0; }
      c.bekle -= dt;
      if (c.bekle <= 0) {
        c.hedefX = 30 + Math.random() * (W - 70);
        c.hedefY = H * (.42 + Math.random() * .46);
        c.bekle = 2.5 + Math.random() * 4;
        c.durum = Math.random() < .18 ? "sleep" : "idle";
      }
      const dx = c.hedefX - c.x, dy = c.hedefY - c.y;
      const dd = Math.hypot(dx, dy) || 1;
      const sp = c.durum === "play" ? c.hiz * 1.7 : c.hiz;
      c.x += dx / dd * sp * dt;
      c.y += dy / dd * sp * dt;
      if (Math.abs(dx) > 3) c.yon = dx > 0 ? 1 : -1;
      c.el.className = "cat " + (dd > 8 ? "walk" : "idle");
    }
    c.x = Math.max(2, Math.min(W - 74, c.x));
    c.y = Math.max(4, Math.min(H - 92, c.y));
    c.el.style.transform = "translate3d(" + c.x.toFixed(1) + "px," + c.y.toFixed(1) + "px,0) scale(" +
      c.yon + "," + c.olcek + ")";
    c.el.style.zIndex = String(10 + Math.floor(c.y / 6));
  });

  if (S.comboT > 0) { S.comboT -= dt; if (S.comboT <= 0) S.combo = 0; }
  // acıkan kediler zamanla biraz mutsuzlaşır
  if (Math.random() < dt * .25) panelGuncelle();
}
function dongu(z) {
  const dt = Math.min(.05, (z - son) / 1000 || 0);
  son = z;
  if (S.bas) adim(dt);
  requestAnimationFrame(dongu);
}

/* =========================================================
   DOKUNMA / SÜRÜKLEME
   ========================================================= */
let suruklen = null;
ODA.addEventListener("pointerdown", e => {
  if (!S.bas) return;
  const el = e.target.closest ? e.target.closest(".cat") : null;
  if (!el) return;
  const c = cats.find(k => k.el === el);
  if (!c) return;
  S.secili = c;
  panelGuncelle();
  const o = ODA.getBoundingClientRect();
  suruklen = { c: c, ox: e.clientX - o.left - c.x, oy: e.clientY - o.top - c.y, hareket: 0, sx: e.clientX, sy: e.clientY };
  c.durum = c.durum === "sleep" ? "idle" : c.durum;
  c.el.setPointerCapture && c.el.setPointerCapture(e.pointerId);
});
window.addEventListener("pointermove", e => {
  if (!suruklen) return;
  const o = ODA.getBoundingClientRect(), c = suruklen.c;
  const nx = e.clientX - o.left - suruklen.ox, ny = e.clientY - o.top - suruklen.oy;
  suruklen.hareket += Math.abs(nx - c.x) + Math.abs(ny - c.y);
  c.x = Math.max(2, Math.min(W - 74, nx));
  c.y = Math.max(4, Math.min(H - 92, ny));
  c.hedefX = c.x; c.hedefY = c.y;
  if (Math.abs(e.clientX - suruklen.sx) + Math.abs(e.clientY - suruklen.sy) > 6) suruklen.hareket = 999;
});
window.addEventListener("pointerup", () => {
  if (!suruklen) return;
  const c = suruklen.c;
  if (suruklen.hareket < 12) { saril(c); c.bekle = 1.5 + Math.random() * 2; }
  suruklen = null;
});
window.addEventListener("pointercancel", () => { suruklen = null; });

document.getElementById("dock").addEventListener("pointerdown", e => {
  const b = e.target.closest(".act");
  if (b) eylem(b.dataset.act);
});

/* =========================================================
   ARAYÜZ
   ========================================================= */
function ac(sel) { document.querySelector(sel).classList.remove("hide"); }
function kapa(sel) { document.querySelector(sel).classList.add("hide"); }
function kapatVeBaslat() {
  kapa("#startVeil");
  S.bas = true;
  boyutla();
  uiGuncelle();
  Snd.meow();
  setTimeout(() => { parca(W * .5, H * .55, "💗"); }, 400);
}
document.getElementById("btnStart").addEventListener("click", () => {
  const v = document.getElementById("inpName").value.trim();
  S.isim = v || CONFIG.kisi;
  document.getElementById("stTitle").textContent = "Pati Aşkı, " + S.isim + "!";
  try { localStorage.setItem("pati_isim", S.isim); } catch (e) {}
  kapatVeBaslat();
});
document.getElementById("inpName").addEventListener("keydown", e => { if (e.key === "Enter") document.getElementById("btnStart").click(); });
document.getElementById("btnUpOk").addEventListener("click", () => kapa("#upVeil"));
document.getElementById("btnLetterOk").addEventListener("click", () => kapa("#letterVeil"));
document.getElementById("btnLetter").addEventListener("click", () => {
  document.getElementById("letterBody").innerHTML =
    '<p><b>' + S.isim + "</b>,</p><p>" + CONFIG.mektup + "</p>" +
    '<p style="text-align:center;font-size:12px;opacity:.7">— Günümüz: ' +
    new Date().toLocaleDateString("tr-TR", { day: "numeric", month: "long", year: "numeric" }) + "</p>" +
    '<p class="sig">' + CONFIG.imza.replace("[İsmin]", S.isim === "Sevgilim" ? "…" : S.isim) + "</p>";
  ac("#letterVeil");
  Snd.meow();
});
document.getElementById("btnSound").addEventListener("click", e => {
  const a = Snd.toggle();
  e.currentTarget.textContent = a ? "🔊" : "🔇";
  if (a) Snd.purr();
});
document.addEventListener("visibilitychange", () => { if (!document.hidden) son = performance.now(); });
window.addEventListener("resize", boyutla);
window.addEventListener("orientationchange", () => setTimeout(boyutla, 250));

/* =========================================================
   AÇILIŞ
   ========================================================= */
(function baslat() {
  const yildiz = document.createElement("div");
  yildiz.className = "star"; yildiz.style.left = "12%"; yildiz.style.top = "8%";
  const y2 = document.createElement("div"); y2.className = "star"; y2.style.left = "34%"; y2.style.top = "5%"; y2.style.opacity = ".6";
  ODA.appendChild(yildiz); ODA.appendChild(y2);

  document.getElementById("stTitle").textContent = CONFIG.baslik;
  document.getElementById("stText").textContent = CONFIG.girisMetni;
  for (let i = 0; i < BASLANGIC_KEDI; i++) kediEkle(i);
  try {
    const v = localStorage.getItem("pati_isim");
    if (v) { S.isim = v; document.getElementById("inpName").placeholder = v + " ♥"; }
  } catch (e) {}
  boyutla();
  uiGuncelle();
  requestAnimationFrame(dongu);
  // düğmeler için tıklama (masaüstü) desteği
  document.querySelectorAll("#dock .act, .btn, .icon").forEach(b => {
    b.addEventListener("click", () => { if (b.dataset && b.dataset.act) eylem(b.dataset.act); });
  });
})();
</script>
</body>
</html>
