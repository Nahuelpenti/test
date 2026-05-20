[malli-v3.html](https://github.com/user-attachments/files/28071146/malli-v3.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Malli — Procurement</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Instrument+Serif:ital@0;1&family=Syne:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --bg:#eef3ea;
  --g1:#e3ebe0;
  --ink:#0c1a0f;
  --gold:#8a6a00;
  --gold2:#b08a10;
  --goldb:#c4a020;
  --muted:rgba(12,26,15,0.42);
  --faint:rgba(12,26,15,0.09);
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--ink);font-family:'Syne',sans-serif;cursor:none;overflow-x:hidden}

#cursor{position:fixed;width:10px;height:10px;border-radius:50%;background:var(--goldb);pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:width 0.2s,height 0.2s}
#cursor-ring{position:fixed;width:36px;height:36px;border-radius:50%;border:1px solid rgba(180,140,20,0.45);pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:width 0.3s,height 0.3s,opacity 0.3s}

nav{position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:1.6rem 4vw;background:rgba(238,243,234,0.88);backdrop-filter:blur(12px);border-bottom:1px solid var(--faint)}
.logo-mark{font-family:'Bebas Neue',sans-serif;font-size:1.5rem;letter-spacing:0.18em;color:var(--ink)}
.logo-mark span{color:var(--gold2)}
nav ul{display:flex;gap:3rem;list-style:none}
nav a{text-decoration:none;color:var(--muted);font-size:0.72rem;letter-spacing:0.18em;text-transform:uppercase;font-weight:400;transition:color 0.2s}
nav a:hover{color:var(--gold)}

.hero{min-height:100vh;display:flex;flex-direction:column;justify-content:flex-end;padding:0 4vw 6vw;position:relative;overflow:hidden}
.hero-line{position:absolute;top:0;left:4vw;width:1px;height:100%;background:linear-gradient(to bottom,transparent,var(--faint) 30%,var(--faint) 70%,transparent)}
.hero-top{position:absolute;top:0;right:4vw;padding-top:10rem;text-align:right}
.hero-tag{font-size:0.7rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--muted);line-height:2.2}
.hero-tag strong{color:var(--gold);font-weight:500}

.big-title{font-family:'Bebas Neue',sans-serif;font-size:clamp(5rem,13vw,13rem);line-height:0.92;color:var(--ink);letter-spacing:0.02em}
.big-title .accent{-webkit-text-stroke:1.5px var(--goldb);color:transparent}

.hero-sub{display:flex;align-items:flex-end;justify-content:space-between;margin-top:2rem;border-top:1px solid var(--faint);padding-top:1.5rem}
.hero-desc{font-size:0.9rem;line-height:1.8;color:var(--muted);max-width:420px;font-weight:300;font-family:'Instrument Serif',serif;font-style:italic}
.hero-cta{display:flex;align-items:center;gap:1.2rem;text-decoration:none;color:var(--ink);font-size:0.75rem;letter-spacing:0.2em;text-transform:uppercase;font-weight:500;transition:gap 0.3s}
.hero-cta:hover{gap:2rem;color:var(--gold)}
.cta-arrow{width:38px;height:38px;border-radius:50%;border:1px solid rgba(140,110,0,0.35);display:flex;align-items:center;justify-content:center;font-size:1rem;transition:background 0.3s,border-color 0.3s,color 0.3s}
.hero-cta:hover .cta-arrow{background:var(--goldb);border-color:var(--goldb);color:#fff}

.ticker{overflow:hidden;border-top:1px solid var(--faint);border-bottom:1px solid var(--faint);padding:0.9rem 0;background:var(--g1)}
.ticker-inner{display:flex;gap:4rem;white-space:nowrap;animation:tick 22s linear infinite;font-size:0.7rem;letter-spacing:0.2em;text-transform:uppercase;color:var(--muted)}
.ticker-inner span{color:var(--gold2);margin-right:2rem}
@keyframes tick{from{transform:translateX(0)}to{transform:translateX(-50%)}}

.stats-row{display:grid;grid-template-columns:repeat(4,1fr);border-bottom:1px solid var(--faint)}
.stat{padding:4rem 4vw 3rem;border-right:1px solid var(--faint);position:relative;overflow:hidden;background:var(--bg);transition:background 0.3s}
.stat:last-child{border-right:none}
.stat:hover{background:var(--g1)}
.stat-n{font-family:'Bebas Neue',sans-serif;font-size:clamp(2.4rem,4vw,4rem);color:var(--gold);line-height:1;margin-bottom:0.6rem}
.stat p{font-size:0.78rem;color:var(--muted);line-height:1.6;font-weight:300}
.stat-hl{position:absolute;bottom:0;left:0;width:0;height:2px;background:var(--goldb);transition:width 0.5s ease}
.stat:hover .stat-hl{width:100%}

.services{padding:6rem 4vw}
.services-header{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:4rem;border-bottom:1px solid var(--faint);padding-bottom:2rem}
.services-header h2{font-family:'Bebas Neue',sans-serif;font-size:clamp(2.5rem,5vw,5rem);letter-spacing:0.04em;line-height:1;color:var(--ink)}
.services-header p{font-size:0.8rem;color:var(--muted);max-width:260px;text-align:right;line-height:1.7;font-weight:300}

.svc{display:grid;grid-template-columns:80px 1fr auto;align-items:center;gap:3rem;padding:1.8rem 0;border-bottom:1px solid var(--faint);position:relative;overflow:hidden;cursor:default;transition:padding-left 0.4s}
.svc::before{content:'';position:absolute;inset:0;background:var(--g1);transform:translateX(-100%);transition:transform 0.4s cubic-bezier(0.4,0,0.2,1);z-index:0}
.svc:hover::before{transform:translateX(0)}
.svc:hover{padding-left:1.5rem}
.svc>*{position:relative;z-index:1}
.svc-num{font-family:'Bebas Neue',sans-serif;font-size:1rem;letter-spacing:0.15em;color:var(--muted);transition:color 0.3s}
.svc:hover .svc-num{color:var(--gold2)}
.svc-name{font-size:clamp(1rem,2vw,1.4rem);font-weight:400;letter-spacing:0.04em;color:var(--ink);transition:color 0.3s}
.svc:hover .svc-name{color:var(--gold)}
.svc-desc{font-size:0.78rem;color:var(--muted);max-width:300px;text-align:right;line-height:1.7;font-weight:300;opacity:0;transform:translateX(8px);transition:opacity 0.3s 0.1s,transform 0.3s 0.1s}
.svc:hover .svc-desc{opacity:1;transform:translateX(0)}

.mq{padding:3rem 0;border-top:1px solid var(--faint);border-bottom:1px solid var(--faint);overflow:hidden;background:var(--bg)}
.mq-inner{display:flex;gap:5rem;font-family:'Bebas Neue',sans-serif;font-size:clamp(3rem,7vw,7rem);letter-spacing:0.05em;white-space:nowrap;animation:tick 18s linear infinite;color:transparent;-webkit-text-stroke:1px rgba(12,26,15,0.12)}
.mq-inner .f{color:var(--ink);-webkit-text-stroke:0}

.about{display:grid;grid-template-columns:1fr 1.6fr;min-height:80vh}
.about-l{border-right:1px solid var(--faint);padding:6rem 4vw;display:flex;flex-direction:column;justify-content:space-between;background:var(--g1)}
.abt-lbl{font-size:0.7rem;letter-spacing:0.22em;text-transform:uppercase;color:var(--gold)}
.abt-name{font-family:'Bebas Neue',sans-serif;font-size:clamp(2rem,4vw,3.8rem);letter-spacing:0.04em;line-height:1.1;margin-top:1rem;color:var(--ink)}
.abt-ttl{font-size:0.8rem;color:var(--muted);letter-spacing:0.08em;margin-top:0.5rem}
.exp-list{margin-top:3rem;display:flex;flex-direction:column;gap:1.2rem}
.exp-row{display:flex;gap:1.5rem;align-items:flex-start;padding-bottom:1.2rem;border-bottom:1px solid var(--faint)}
.exp-row:last-child{border-bottom:none}
.exp-dot{width:6px;height:6px;border-radius:50%;background:var(--goldb);margin-top:0.5rem;flex-shrink:0}
.exp-co{font-size:0.82rem;color:var(--gold);font-weight:500}
.exp-ro{font-size:0.75rem;color:var(--muted);margin-top:0.2rem;line-height:1.5}

.about-r{padding:6rem 4vw;display:flex;flex-direction:column;justify-content:center;background:var(--bg)}
.big-q{font-family:'Instrument Serif',serif;font-size:clamp(1.4rem,3vw,2.4rem);line-height:1.4;font-style:italic;color:var(--ink);margin-bottom:3rem;max-width:680px}
.big-q em{color:var(--gold);font-style:normal}
.abt-body{font-size:0.88rem;line-height:1.9;color:var(--muted);max-width:560px;font-weight:300;margin-top:1.2rem}

.contact{min-height:90vh;display:flex;flex-direction:column;justify-content:center;padding:8rem 4vw;position:relative;overflow:hidden;border-top:1px solid var(--faint);background:var(--ink)}
.ctbg{position:absolute;bottom:-3vw;left:0;font-family:'Bebas Neue',sans-serif;font-size:clamp(6rem,18vw,20rem);letter-spacing:0.04em;color:transparent;-webkit-text-stroke:1px rgba(238,243,234,0.06);pointer-events:none;white-space:nowrap;user-select:none}
.ct-lbl{font-size:0.7rem;letter-spacing:0.22em;text-transform:uppercase;color:var(--goldb);margin-bottom:1.5rem}
.ct-title{font-family:'Bebas Neue',sans-serif;font-size:clamp(3.5rem,8vw,9rem);line-height:0.95;letter-spacing:0.02em;margin-bottom:3rem;max-width:900px;color:#eef3ea}
.ct-open{-webkit-text-stroke:1px var(--goldb);color:transparent}
.ct-body{font-size:.88rem;color:rgba(238,243,234,0.5);max-width:460px;line-height:1.8;font-weight:300;margin-bottom:3rem}
.ct-row{display:flex;gap:3rem;align-items:center;flex-wrap:wrap;margin-top:1rem}
.ct-link{display:flex;align-items:center;gap:0.75rem;text-decoration:none;color:#eef3ea;font-size:0.9rem;font-weight:400;letter-spacing:0.04em;transition:color 0.25s;border-bottom:1px solid rgba(238,243,234,0.1);padding-bottom:0.4rem}
.ct-link:hover{color:var(--goldb);border-color:var(--goldb)}
.ct-link svg{opacity:0.45;transition:opacity 0.25s}
.ct-link:hover svg{opacity:1}

footer{display:flex;justify-content:space-between;align-items:center;padding:1.5rem 4vw;border-top:1px solid rgba(238,243,234,0.08);background:var(--ink);flex-wrap:wrap;gap:1rem}
footer p{font-size:0.7rem;color:rgba(238,243,234,0.22);letter-spacing:0.1em}
.f-logo{font-family:'Bebas Neue',sans-serif;font-size:1.1rem;letter-spacing:0.18em;color:rgba(238,243,234,0.7)}
.f-logo span{color:var(--goldb)}

.reveal{opacity:0;transform:translateY(28px);transition:opacity 0.75s ease,transform 0.75s ease}
.reveal.in{opacity:1;transform:translateY(0)}

@media(max-width:768px){
  .stats-row{grid-template-columns:1fr 1fr}
  .stat{border-right:none;border-bottom:1px solid var(--faint)}
  .about{grid-template-columns:1fr}
  .about-l{border-right:none;border-bottom:1px solid var(--faint)}
  .svc{grid-template-columns:50px 1fr}
  .svc-desc{display:none}
  nav ul{display:none}
}
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>

<nav>
  <div class="logo-mark">M<span>ALLI</span></div>
  <ul>
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#nosotros">Nosotros</a></li>
    <li><a href="#contacto">Contacto</a></li>
  </ul>
</nav>

<section class="hero">
  <div class="hero-line"></div>
  <div class="hero-top">
    <div class="hero-tag">Procurement Consulting<br><strong>Madrid · España · Europa</strong><br>Est. 2025</div>
  </div>
  <div class="big-title reveal">
    <div>REDUCE</div>
    <div>TU <span class="accent">GASTO.</span></div>
    <div>CRECE.</div>
  </div>
  <div class="hero-sub reveal">
    <p class="hero-desc">La gestión de compras estratégica no es solo para grandes corporaciones. Es para cualquier empresa que quiera ganar más de lo que gasta.</p>
    <a href="#contacto" class="hero-cta">Diagnóstico gratuito <span class="cta-arrow">→</span></a>
  </div>
</section>

<div class="ticker">
  <div class="ticker-inner">
    <span>✦</span>Reducción de costos<span>✦</span>Indirect Spend<span>✦</span>Contract Negotiation<span>✦</span>Category Management<span>✦</span>SAP Ariba<span>✦</span>Cash Flow Optimization<span>✦</span>KPI Design<span>✦</span>Strategic Sourcing &nbsp;&nbsp;&nbsp;
    <span>✦</span>Reducción de costos<span>✦</span>Indirect Spend<span>✦</span>Contract Negotiation<span>✦</span>Category Management<span>✦</span>SAP Ariba<span>✦</span>Cash Flow Optimization<span>✦</span>KPI Design<span>✦</span>Strategic Sourcing &nbsp;&nbsp;&nbsp;
  </div>
</div>

<div class="stats-row">
  <div class="stat reveal"><div class="stat-n" data-target="m">$1.5M+</div><p>Cash flow mensual liberado en cliente LATAM</p><div class="stat-hl"></div></div>
  <div class="stat reveal" style="transition-delay:.1s"><div class="stat-n" data-target="7">0%</div><p>Ahorro anual sobre $40M en presupuesto gestionado</p><div class="stat-hl"></div></div>
  <div class="stat reveal" style="transition-delay:.2s"><div class="stat-n" data-target="47" data-pre="-">0%</div><p>Reducción en lead time de órdenes de compra</p><div class="stat-hl"></div></div>
  <div class="stat reveal" style="transition-delay:.3s"><div class="stat-n" data-target="8" data-suf=" años">0</div><p>Experiencia en procurement internacional LATAM & EMEA</p><div class="stat-hl"></div></div>
</div>

<section class="services" id="servicios">
  <div class="services-header reveal">
    <h2>Servicios</h2>
    <p>Soluciones concretas para empresas que saben que en sus compras hay dinero esperando ser recuperado.</p>
  </div>
  <div class="svc reveal"><span class="svc-num">01</span><span class="svc-name">Diagnóstico de Gasto Indirecto</span><span class="svc-desc">Mapeamos dónde se va el dinero en categorías no productivas y cuantificamos el ahorro potencial real.</span></div>
  <div class="svc reveal" style="transition-delay:.05s"><span class="svc-num">02</span><span class="svc-name">Negociación y Contratos</span><span class="svc-desc">Ejecutamos negociaciones estratégicas con proveedores clave para mejorar precios, plazos y condiciones.</span></div>
  <div class="svc reveal" style="transition-delay:.1s"><span class="svc-num">03</span><span class="svc-name">Optimización de Procesos</span><span class="svc-desc">Rediseñamos el ciclo de compras: menos fricción, más velocidad, trazabilidad total del gasto.</span></div>
  <div class="svc reveal" style="transition-delay:.15s"><span class="svc-num">04</span><span class="svc-name">Category Management</span><span class="svc-desc">Estrategia de abastecimiento por categoría, consolidación de proveedores y análisis de mercado.</span></div>
  <div class="svc reveal" style="transition-delay:.2s"><span class="svc-num">05</span><span class="svc-name">KPIs y Dashboards</span><span class="svc-desc">Visibilidad total del área de compras: ahorro, cumplimiento, performance de proveedores en tiempo real.</span></div>
  <div class="svc reveal" style="transition-delay:.25s"><span class="svc-num">06</span><span class="svc-name">Procurement as a Service</span><span class="svc-desc">Tu departamento de compras externo. Para empresas sin función de procurement interna.</span></div>
</section>

<div class="mq">
  <div class="mq-inner">
    <span class="f">MALLI</span><span>PROCUREMENT</span><span class="f">MADRID</span><span>ESPAÑA</span><span class="f">EUROPA</span><span>PROCUREMENT</span>&nbsp;&nbsp;&nbsp;&nbsp;
    <span class="f">MALLI</span><span>PROCUREMENT</span><span class="f">MADRID</span><span>ESPAÑA</span><span class="f">EUROPA</span><span>PROCUREMENT</span>
  </div>
</div>

<section class="about" id="nosotros">
  <div class="about-l reveal">
    <div>
      <div class="abt-lbl">Fundador</div>
      <div class="abt-name">Nahuel<br>Pentimalli</div>
      <div class="abt-ttl">Industrial Engineer · MBA · Global Procurement</div>
    </div>
    <div class="exp-list">
      <div class="exp-row"><div class="exp-dot"></div><div><div class="exp-co">Avolta · World Duty Free</div><div class="exp-ro">Global Category Manager EMEA & LATAM<br>€1,600M en ventas anuales · +26% YoY</div></div></div>
      <div class="exp-row"><div class="exp-dot"></div><div><div class="exp-co">Aeropuertos Argentina (CAAP)</div><div class="exp-ro">Procurement Manager · $40M budget<br>7% ahorro YoY · SAP Ariba implementation</div></div></div>
      <div class="exp-row"><div class="exp-dot"></div><div><div class="exp-co">Calm es Simple</div><div class="exp-ro">Procurement Manager LATAM<br>+$1.5M cash flow/mes liberado</div></div></div>
      <div class="exp-row"><div class="exp-dot"></div><div><div class="exp-co">Walmart Argentina ($WMT)</div><div class="exp-ro">Equipment & Services Buyer<br>92 tiendas y centros de distribución</div></div></div>
    </div>
  </div>
  <div class="about-r reveal">
    <p class="big-q">"La mayoría de las empresas no saben cuánto dejan de ganar por no gestionar bien sus compras. Nosotros <em>sí lo sabemos</em>. Y lo convertimos en resultados."</p>
    <p class="abt-body">Malli nació de la convicción de que las herramientas del procurement de primer nivel no son exclusivas de las grandes multinacionales. Con más de ocho años gestionando compras en Walmart, aeropuertos, startups y una de las mayores duty-free del mundo, Nahuel trae ese expertise directamente a empresas medianas y pequeñas en España y Europa.</p>
    <p class="abt-body">El modelo es simple: entramos, diagnosticamos, ejecutamos y medimos. Sin consultoras de 50 personas que facturan presentaciones. Solo trabajo real con impacto real en tu P&L.</p>
  </div>
</section>

<section class="contact" id="contacto">
  <div class="ctbg">MALLI</div>
  <p class="ct-lbl reveal">Empezar</p>
  <h2 class="ct-title reveal">¿Cuánto<br>estás dejando<br><span class="ct-open">escapar?</span></h2>
  <p class="ct-body reveal">Una primera conversación de 30 minutos es suficiente para identificar si hay oportunidades reales en tu empresa. Sin compromiso, sin costo.</p>
  <div class="ct-row reveal">
    <a class="ct-link" href="mailto:nahuel.penti@gmail.com">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M3 8l9 6 9-6M3 8v11a1 1 0 001 1h16a1 1 0 001-1V8M3 8a1 1 0 011-1h16a1 1 0 011 1"/></svg>
      nahuel.penti@gmail.com
    </a>
    <a class="ct-link" href="tel:+34627924459">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-16.73-16.73A2 2 0 015.09 2h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L9.09 9.91a16 16 0 006.99 6.99l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
      +34 627 92 44 59
    </a>
    <a class="ct-link" href="https://linkedin.com/in/nahuel-hern%C3%A1n-pentimalli" target="_blank">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-4 0v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
      LinkedIn
    </a>
  </div>
</section>

<footer>
  <div class="f-logo">M<span>ALLI</span></div>
  <p>Procurement Consulting · Madrid, España · 2025</p>
  <p>Industrial Engineer · MBA · EMEA & LATAM</p>
</footer>

<script>
const cur=document.getElementById('cursor'),ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cur.style.left=mx+'px';cur.style.top=my+'px'});
(function animR(){rx+=(mx-rx)*0.12;ry+=(my-ry)*0.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animR)})();
document.querySelectorAll('a,button').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cur.style.width='6px';cur.style.height='6px';ring.style.width='54px';ring.style.height='54px';ring.style.opacity='0.5'});
  el.addEventListener('mouseleave',()=>{cur.style.width='10px';cur.style.height='10px';ring.style.width='36px';ring.style.height='36px';ring.style.opacity='1'});
});

const obs=new IntersectionObserver(entries=>entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('in');obs.unobserve(e.target)}}),{threshold:0.12});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

const cObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(!e.isIntersecting)return;
    const el=e.target,pre=el.dataset.pre||'',suf=el.dataset.suf||'';
    if(el.dataset.target==='m')return;
    const tgt=+el.dataset.target;
    let t0=null;
    (function step(ts){
      if(!t0)t0=ts;
      const p=Math.min((ts-t0)/1400,1),ease=1-Math.pow(1-p,3),v=Math.round(ease*tgt);
      el.textContent=suf===' años'?pre+v+' años':pre+v+'%';
      if(p<1)requestAnimationFrame(step);
    })(0);
    cObs.unobserve(el);
  })
},{threshold:0.6});
document.querySelectorAll('[data-target]').forEach(c=>cObs.observe(c));
</script>
</body>
</html>
