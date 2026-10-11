<title>Guardianes de la Sonrisa</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Grandstander:wght@700;800;900&family=Nunito:wght@400;600;700;800&display=swap">
<style>
/* Layout: mesa de juego. Barra superior con el camino de niveles, bloque de instrucciones a la izquierda, tablero de cartas que se voltean debajo; fin de nivel y final como ventana encima. */
:root{
  --bg:#E7F3F5; --surface:#FFFFFF; --ink:#10304A; --muted:#48687D;
  --line:#C5DCE4; --line-strong:#9CBFCD;
  --accent:#0B7F73; --accent-deep:#07574F; --accent-ink:#FFFFFF; --accent-soft:#D3F0EB;
  --back:#1F63A0; --back-2:#17507F; --back-edge:#12426B; --back-ink:#FFFFFF; --back-line:rgba(255,255,255,.4);
  --a-bg:#EAF3FF; --a-line:#B2D1F4; --a-ink:#1A4F8B;
  --b-bg:#E4F7F0; --b-line:#A6DEC9; --b-ink:#0B6A55;
  --star:#FFB400; --star-off:#C6D8E0;
  --coral:#EF6363; --gum:#F4929F; --gum-edge:#DF6E7E;
  --dentin:#F0B84B; --dentin-edge:#C48418;
  --tooth:#FFFFFF; --tooth-edge:#A3BAC8; --tooth-shade:#E2EDF3;
  --ok:#1E9E5A; --ok-soft:#BDEBD3; --miss-bg:#FCE3E1;
  --gold:#F5B323; --gold-deep:#C98408;
  --font-display:'Grandstander','Baloo 2','Trebuchet MS',system-ui,sans-serif;
  --font-body:'Nunito','Segoe UI',system-ui,sans-serif;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --bg:#0D2030; --surface:#15324A; --ink:#EAF5F8; --muted:#9DBBCB;
    --line:#2A4B63; --line-strong:#41647D;
    --accent:#3CCDBA; --accent-deep:#1F9A8B; --accent-ink:#06241F; --accent-soft:#12423F;
    --back:#2C77AF; --back-2:#23679A; --back-edge:#1B527E;
    --a-bg:#183B5E; --a-line:#2D5D8F; --a-ink:#BBDAFF;
    --b-bg:#14423A; --b-line:#2A6B5C; --b-ink:#A7EAD4;
    --star:#FFC531; --star-off:#35546A;
    --coral:#FF8080; --gum:#E57D8C; --gum-edge:#C9606E;
    --tooth:#F7FBFD; --tooth-edge:#7E9BAD; --tooth-shade:#D3E2EB;
    --ok:#43D68A; --ok-soft:#1C5A3E; --miss-bg:#4A2630;
    --gold:#FFC83D; --gold-deep:#D9930E;
    color-scheme:dark;
  }
}
:root[data-theme="dark"]{
  --bg:#0D2030; --surface:#15324A; --ink:#EAF5F8; --muted:#9DBBCB;
  --line:#2A4B63; --line-strong:#41647D;
  --accent:#3CCDBA; --accent-deep:#1F9A8B; --accent-ink:#06241F; --accent-soft:#12423F;
  --back:#2C77AF; --back-2:#23679A; --back-edge:#1B527E;
  --a-bg:#183B5E; --a-line:#2D5D8F; --a-ink:#BBDAFF;
  --b-bg:#14423A; --b-line:#2A6B5C; --b-ink:#A7EAD4;
  --star:#FFC531; --star-off:#35546A;
  --coral:#FF8080; --gum:#E57D8C; --gum-edge:#C9606E;
  --tooth:#F7FBFD; --tooth-edge:#7E9BAD; --tooth-shade:#D3E2EB;
  --ok:#43D68A; --ok-soft:#1C5A3E; --miss-bg:#4A2630;
  --gold:#FFC83D; --gold-deep:#D9930E;
  color-scheme:dark;
}
 
*,*::before,*::after{box-sizing:border-box}
body{background:var(--bg);color:var(--ink);font-family:var(--font-body);font-size:16px;line-height:1.5;-webkit-font-smoothing:antialiased}
h1,h2,h3,p,ul,ol{margin:0}
button{font:inherit;color:inherit}
 
.app{max-width:1040px;margin-inline:auto;padding-inline:16px;padding-block:18px 56px;display:flex;flex-direction:column;gap:22px}
 
/* barra superior */
.top{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px 20px}
.brand{display:flex;align-items:center;gap:10px;font-family:var(--font-display);font-weight:800;font-size:1.05rem}
.brand svg{width:22px;height:26px;fill:var(--accent);flex:none}
.path{list-style:none;padding:0;display:flex;gap:6px}
.path li{display:flex;align-items:center;gap:6px;padding:4px 11px 4px 9px;border-radius:999px;border:2px solid transparent;font-weight:800;font-size:.82rem;color:var(--muted)}
.path li svg{width:15px;height:18px;fill:var(--line-strong)}
.path li.now{color:var(--ink);background:var(--surface);border-color:var(--line)}
.path li.now svg,.path li.done svg{fill:var(--accent)}
.path li.done{color:var(--accent)}
.path .w{display:none}
@media (min-width:520px){.path .w{display:inline}}
 
/* pantalla de inicio */
.hero{display:grid;gap:22px;align-items:center;padding-block:8px}
.hero-copy{display:flex;flex-direction:column;align-items:flex-start;gap:16px;min-width:0}
.mascot{order:-1;width:min(132px,38%);height:auto;overflow:visible}
@media (min-width:760px){
  .hero{grid-template-columns:minmax(0,1fr) 260px;gap:48px}
  .mascot{order:0;width:100%}
}
.kicker{font-size:.78rem;font-weight:800;letter-spacing:.14em;text-transform:uppercase;color:var(--accent)}
h1{font-family:var(--font-display);font-weight:900;font-size:clamp(2.3rem,1.3rem + 4.6vw,4.2rem);line-height:1.02;text-wrap:balance}
.lead{font-size:1.08rem;color:var(--muted);max-width:34rem}
.levels{list-style:none;padding:0;display:grid;gap:8px;width:100%;max-width:30rem}
.levels li{display:flex;align-items:center;gap:12px;padding:10px 14px;border-radius:14px;background:var(--surface);border:2px solid var(--line);font-weight:700}
.levels .n{flex:none;display:grid;place-items:center;width:28px;height:28px;border-radius:50%;background:var(--accent-soft);color:var(--accent);font-family:var(--font-display);font-weight:800}
.levels .t{flex:1;min-width:0}
.levels .c{font-size:.8rem;font-weight:700;color:var(--muted);white-space:nowrap}
.how{color:var(--muted);max-width:30rem}
 
.btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;padding:13px 28px;border-radius:999px;border:0;background:var(--accent);color:var(--accent-ink);font-weight:800;font-size:1.05rem;cursor:pointer;box-shadow:0 4px 0 var(--accent-deep);transition:transform .08s,box-shadow .08s}
.btn:hover{filter:brightness(1.06)}
.btn:active{transform:translateY(3px);box-shadow:0 1px 0 var(--accent-deep)}
.btn.ghost{background:transparent;color:var(--ink);border:2px solid var(--line-strong);box-shadow:none;padding:7px 16px;font-size:.88rem}
.btn.ghost:active{transform:none}
.btn:focus-visible,.card:focus-visible{outline:3px solid var(--accent);outline-offset:3px}
 
/* juego */
.levelhead{display:flex;flex-wrap:wrap;align-items:flex-end;justify-content:space-between;gap:14px 24px}
.levelhead .txt{flex:1 1 20rem;min-width:0;display:flex;flex-direction:column;gap:6px}
h2{font-family:var(--font-display);font-weight:900;font-size:clamp(1.8rem,1.2rem + 2.6vw,2.8rem);line-height:1.05;text-wrap:balance}
.meter{display:flex;flex-wrap:wrap;align-items:center;gap:8px}
.chip{padding:6px 14px;border-radius:999px;background:var(--surface);border:2px solid var(--line);font-weight:700;font-size:.9rem}
.chip b{font-variant-numeric:tabular-nums;font-weight:800}
.status{min-height:2.7rem;display:flex;align-items:center;padding:8px 16px;border-radius:14px;background:var(--surface);border:2px solid var(--line);font-weight:700}
.status.good{background:var(--accent-soft);border-color:var(--accent)}
.status.bad{background:var(--miss-bg);border-color:var(--coral)}
 
.board{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));grid-auto-rows:1fr;gap:12px}
@media (min-width:720px){.board.c6{grid-template-columns:repeat(3,minmax(0,1fr));gap:16px}}
@media (min-width:900px){.board.c10{grid-template-columns:repeat(5,minmax(0,1fr));gap:14px}}
 
.card{perspective:1000px;cursor:pointer;min-width:0;-webkit-tap-highlight-color:transparent;border-radius:20px}
.card.just{animation:pop .5s ease}
@keyframes pop{0%{transform:scale(1)}40%{transform:scale(1.06)}100%{transform:scale(1)}}
.inner{position:relative;display:grid;height:100%;min-height:11rem;transform-style:preserve-3d;transition:transform .55s cubic-bezier(.3,.7,.2,1)}
.card.open .inner{transform:rotateY(180deg)}
.card:not(.open):hover .inner{transform:translateY(-4px)}
.face{grid-area:1/1;position:relative;min-width:0;display:flex;flex-direction:column;gap:8px;padding:14px;border-radius:18px;border:2px solid transparent;backface-visibility:hidden;-webkit-backface-visibility:hidden}
.back{align-items:center;justify-content:center;background:linear-gradient(155deg,var(--back),var(--back-2));border-color:var(--back-edge)}
.back::after{content:"";position:absolute;inset:8px;border:2px dashed var(--back-line);border-radius:12px}
.bk{width:46px;height:55px;fill:var(--back-ink);opacity:.92}
.front{transform:rotateY(180deg);overflow-wrap:break-word}
.ka .front{background:var(--a-bg);border-color:var(--a-line)}
.kb .front{background:var(--b-bg);border-color:var(--b-line)}
.card.done .front{border-color:var(--ok);box-shadow:0 0 0 3px var(--ok-soft)}
.card.done .front::after{content:"\2713";position:absolute;top:-10px;right:-10px;width:26px;height:26px;border-radius:50%;display:grid;place-items:center;background:var(--ok);color:#fff;font-weight:800;font-size:.9rem}
.tag{align-self:flex-start;padding:3px 9px;border-radius:999px;font-size:.66rem;font-weight:800;letter-spacing:.12em;text-transform:uppercase}
.ka .tag{background:var(--a-ink);color:var(--a-bg)}
.kb .tag{background:var(--b-ink);color:var(--b-bg)}
.art{display:grid;place-items:center;padding:2px 0}
.art svg{display:block;width:min(100%,124px);height:auto}
.cap{font-weight:800;font-size:.92rem;line-height:1.3}
.note{font-size:.8rem;line-height:1.3;color:var(--muted)}
.ttl{font-family:var(--font-display);font-weight:800;font-size:clamp(1.02rem,.92rem + .5vw,1.25rem);line-height:1.15;text-wrap:balance}
.em{font-size:1.15em}
.bl{padding-left:1.1em;display:grid;gap:5px;font-size:.84rem;line-height:1.4;font-weight:600}
.ka .bl li::marker{color:var(--a-ink)}
.kb .bl li::marker{color:var(--b-ink)}
.bigem{font-size:2.6rem;line-height:1}
.quote{font-family:var(--font-display);font-weight:800;font-size:1.08rem;line-height:1.2}
 
/* dibujo del diente */
.t-fill{fill:var(--tooth)}
.t-outline{fill:none;stroke:var(--tooth-edge);stroke-width:3;stroke-linejoin:round}
.t-shade{fill:var(--tooth-shade)}
.t-gum{fill:var(--gum);stroke:var(--gum-edge);stroke-width:3}
.t-dentin{fill:var(--dentin)}
.t-cut{fill:none;stroke:var(--tooth-edge);stroke-width:3;stroke-linecap:round}
.t-cut.dn{stroke:var(--dentin-edge)}
.t-impact{stroke:var(--coral);fill:none}
 
/* mascota */
.m-cape{fill:var(--coral)}
.m-tooth{fill:var(--tooth);stroke:var(--tooth-edge);stroke-width:3;stroke-linejoin:round}
.m-eye{fill:var(--ink)}
.m-smile{fill:none;stroke:var(--ink);stroke-width:3;stroke-linecap:round}
.m-cheek{fill:var(--gum);opacity:.65}
.m-star{fill:var(--star)}
.mascot{animation:bob 3.2s ease-in-out infinite}
@keyframes bob{50%{transform:translateY(-6px)}}
 
/* ventana de fin de nivel */
.overlay{position:fixed;inset:0;z-index:20;display:grid;place-items:center;padding:16px;overflow:auto;background:rgba(7,24,38,.62)}
.sheet{width:min(100%,460px);display:flex;flex-direction:column;align-items:center;gap:12px;padding:28px 24px 24px;border-radius:26px;background:var(--surface);border:2px solid var(--line);box-shadow:0 18px 50px rgba(0,0,0,.35);text-align:center}
.sheet h2{font-size:clamp(1.9rem,1.4rem + 2vw,2.5rem)}
.ov-text{color:var(--muted);font-weight:700}
.sheet.final .ov-text{color:var(--ink);font-family:var(--font-display);font-weight:800;font-size:1.25rem;line-height:1.2;text-wrap:balance}
.stars{display:flex;gap:6px}
.star{width:40px;height:40px}
.star.on{fill:var(--star)}
.star.off{fill:var(--star-off)}
.stars .star{animation:pop .5s ease both}
.stars .star:nth-child(2){animation-delay:.12s}
.stars .star:nth-child(3){animation-delay:.24s}
.recap{list-style:none;padding:0;width:100%;display:grid;gap:6px;text-align:left}
.recap li{display:flex;align-items:center;justify-content:space-between;gap:10px;padding:6px 12px;border-radius:12px;background:var(--bg);font-weight:700;font-size:.9rem}
.recap .star{width:18px;height:18px;animation:none}
.recap .stars{gap:2px}
.trophy{width:140px;height:auto}
.g-fill{fill:var(--gold)}
.g-deep{fill:var(--gold-deep)}
.g-arm{fill:none;stroke:var(--gold);stroke-width:9;stroke-linecap:round;stroke-linejoin:round}
.g-shine{fill:none;stroke:rgba(255,255,255,.55);stroke-width:5;stroke-linecap:round}
.g-tooth{fill:var(--tooth);stroke:var(--gold-deep);stroke-width:5;stroke-linejoin:round}
.spark{fill:var(--star)}
#confetti{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:30}
 
@media (prefers-reduced-motion: reduce){
  .inner{transition:none}
  .card.just,.stars .star,.mascot{animation:none}
}
</style>
 
<svg width="0" height="0" style="position:absolute" aria-hidden="true" focusable="false">
  <symbol id="glyph" viewBox="0 0 100 120"><path d="M50 8 C38 2 18 4 14 24 C11 40 22 50 24 68 C26 90 28 112 38 112 C47 112 46 86 50 86 C54 86 53 112 62 112 C72 112 74 90 76 68 C78 50 89 40 86 24 C82 4 62 2 50 8 Z"/></symbol>
</svg>
 
<div class="app">
  <header class="top">
    <div class="brand"><svg viewBox="0 0 100 120" aria-hidden="true" focusable="false"><use href="#glyph"/></svg><span>Guardianes de la Sonrisa</span></div>
    <ol class="path" id="path" aria-label="Niveles"></ol>
  </header>
 
  <section id="start" class="hero">
    <div class="hero-copy">
      <p class="kicker">Odontopediatría · Juego de memoria</p>
      <h1>Guardianes de la Sonrisa</h1>
      <p class="lead">Voltea las cartas, encuentra las parejas y aprende qué hacer cuando un diente recibe un golpe.</p>
      <ul class="levels" id="levels"></ul>
      <p class="how">Toca una carta para voltearla. Si encuentras su pareja, las dos se quedan abiertas.</p>
      <button class="btn" id="go" type="button">¡A jugar!</button>
    </div>
    <svg class="mascot" viewBox="-12 0 124 134" role="img" aria-label="Un diente sonriente con capa de superhéroe">
      <path class="m-cape" d="M26 40 C0 66 -6 104 4 126 L50 112 L96 126 C106 104 100 66 74 40 Z"/>
      <path class="m-tooth" d="M50 8 C38 2 18 4 14 24 C11 40 22 50 24 68 C26 90 28 112 38 112 C47 112 46 86 50 86 C54 86 53 112 62 112 C72 112 74 90 76 68 C78 50 89 40 86 24 C82 4 62 2 50 8 Z"/>
      <circle class="m-eye" cx="39" cy="34" r="3.6"/><circle class="m-eye" cx="61" cy="34" r="3.6"/>
      <circle class="m-cheek" cx="31" cy="45" r="4.5"/><circle class="m-cheek" cx="69" cy="45" r="4.5"/>
      <path class="m-smile" d="M40 46 Q50 57 60 46"/>
      <path class="m-star" transform="translate(39 58) scale(.92)" d="M12 2.2l2.95 6.1 6.7.9-4.9 4.7 1.2 6.7L12 17.4l-5.95 3.2 1.2-6.7-4.9-4.7 6.7-.9z"/>
    </svg>
  </section>
 
  <section id="play" hidden>
    <div class="levelhead">
      <div class="txt">
        <p class="kicker" id="kicker"></p>
        <h2 id="ltitle"></h2>
        <p class="lead" id="llead"></p>
      </div>
      <div class="meter">
        <span class="chip">Parejas <b id="s-pairs">0/0</b></span>
        <span class="chip">Intentos <b id="s-tries">0</b></span>
        <button class="btn ghost" id="shuffle" type="button">Barajar de nuevo</button>
      </div>
    </div>
    <p class="status" id="status" role="status" aria-live="polite"></p>
    <div class="board" id="board"></div>
  </section>
</div>
 
<div class="overlay" id="overlay" hidden>
  <div class="sheet" id="sheet" role="dialog" aria-modal="true" aria-labelledby="ov-title">
    <div id="ov-art"></div>
    <h2 id="ov-title"></h2>
    <p class="ov-text" id="ov-text"></p>
    <div id="ov-extra" style="width:100%"></div>
    <button class="btn" id="ov-btn" type="button"></button>
  </div>
</div>
<canvas id="confetti" aria-hidden="true"></canvas>
 
<script>
(function () {
  'use strict';
 
  var LEVELS = [
    {
      title: 'Conoce la lesión',
      lead: 'Une la imagen o la descripción de la lesión con su nombre.',
      tags: { a: 'Imagen', b: 'Nombre' },
      pairs: [
        { id: 'concusion', name: 'Concusión',
          a: { type: 'img', variant: 'concusion', caption: 'Diente completo después de un golpe', note: 'No se observa ninguna parte rota' },
          b: { type: 'text', emoji: '⭐', title: 'Concusión', bullets: ['Es un golpe en el diente.', 'El diente sigue completo.', 'Puede doler o sentirse sensible.', 'No hay pérdida de una parte del diente.'] } },
        { id: 'esmalte', name: 'Fractura de esmalte',
          a: { type: 'img', variant: 'esmalte', caption: 'Falta un pequeño pedacito de la parte blanca del diente' },
          b: { type: 'text', emoji: '⭐', title: 'Fractura de esmalte', bullets: ['Se rompe solamente la capa externa del diente llamada esmalte.', 'El diente puede perder un pequeño fragmento.', 'La parte interna del diente no queda expuesta.'] } },
        { id: 'dentina', name: 'Fractura de esmalte y dentina',
          a: { type: 'img', variant: 'dentina', caption: 'Falta una parte blanca y se observa una zona amarillenta' },
          b: { type: 'text', emoji: '⭐', title: 'Fractura de esmalte y dentina', bullets: ['Se rompe el esmalte y también la dentina.', 'Puede verse una capa amarilla debajo del esmalte.', 'Puede causar más sensibilidad porque la dentina quedó expuesta.'] } }
      ]
    },
    {
      title: 'Cuida el diente',
      lead: 'Une cada lesión con el manejo correcto.',
      tags: { a: 'Lesión', b: 'Qué hacer' },
      pairs: [
        { id: 'concusion', name: 'Concusión',
          a: { type: 'text', emoji: '⭐', title: 'Concusión' },
          b: { type: 'text', emoji: '🩺', title: 'Manejo', bullets: ['Visitar al odontólogo para revisar el diente.', 'Observar si aparece dolor, cambio de color o movilidad.', 'Mantener buena higiene oral.', 'Evitar golpear nuevamente el diente.'] } },
        { id: 'esmalte', name: 'Fractura de esmalte',
          a: { type: 'text', emoji: '⭐', title: 'Fractura de esmalte' },
          b: { type: 'text', emoji: '🩺', title: 'Manejo', bullets: ['Revisar el diente con el odontólogo.', 'Si hay bordes filosos, pueden suavizarse.', 'Puede repararse el pedacito perdido si es necesario.', 'Mantener controles.'] } },
        { id: 'dentina', name: 'Fractura de esmalte y dentina',
          a: { type: 'text', emoji: '⭐', title: 'Fractura de esmalte y dentina' },
          b: { type: 'text', emoji: '🩺', title: 'Manejo', bullets: ['Acudir al odontólogo lo antes posible.', 'Proteger la dentina que quedó expuesta.', 'Restaurar el diente para evitar sensibilidad.', 'Realizar controles para cuidar la salud del diente.'] } }
      ]
    },
    {
      title: '¡Protege tu sonrisa!',
      lead: 'Une cada situación con la acción que cuida tus dientes.',
      tags: { a: 'Situación', b: 'Acción correcta' },
      pairs: [
        { id: 'futbol', name: 'Uso protección',
          a: { type: 'situation', emoji: '⚽', title: '“Voy a jugar fútbol”' },
          b: { type: 'text', emoji: '🛡️', title: 'Uso protección', bullets: ['Utilizar protector bucal en deportes de contacto.', 'Usar casco si el deporte lo requiere.', 'Jugar con cuidado para proteger mis dientes.'] } },
        { id: 'bici', name: 'Me protejo antes de jugar',
          a: { type: 'situation', emoji: '🚲', title: '“Voy a andar en bicicleta”' },
          b: { type: 'text', emoji: '⛑️', title: 'Me protejo antes de jugar', bullets: ['Usar casco.', 'Revisar que la bicicleta sea segura.', 'Evitar jugar en lugares peligrosos.'] } },
        { id: 'paquete', name: 'Mis dientes no son herramientas',
          a: { type: 'situation', emoji: '🍬', title: '“Quiero abrir un paquete con mis dientes”' },
          b: { type: 'text', emoji: '🚫🦷', title: 'Mis dientes no son herramientas', bullets: ['No usar los dientes para abrir objetos.', 'Usarlos solo para comer y sonreír.'] } },
        { id: 'correr', name: 'Juego de forma segura',
          a: { type: 'situation', emoji: '🏃', title: '“Estoy jugando y corro sin mirar”' },
          b: { type: 'text', emoji: '👀', title: 'Juego de forma segura', bullets: ['Prestar atención al lugar donde juego.', 'Evitar empujar o correr cerca de objetos peligrosos.'] } },
        { id: 'cepillo', name: 'Cuido mi sonrisa',
          a: { type: 'situation', emoji: '🪥', title: '“Quiero mantener mis dientes fuertes”' },
          b: { type: 'text', emoji: '✨', title: 'Cuido mi sonrisa', bullets: ['Cepillar mis dientes todos los días.', 'Visitar al odontólogo.', 'Tener hábitos saludables.'] } }
      ]
    }
  ];
 
  var STAR = '<path d="M12 2.2l2.95 6.1 6.7.9-4.9 4.7 1.2 6.7L12 17.4l-5.95 3.2 1.2-6.7-4.9-4.7 6.7-.9z"/>';
  var GLYPH = 'M50 8 C38 2 18 4 14 24 C11 40 22 50 24 68 C26 90 28 112 38 112 C47 112 46 86 50 86 C54 86 53 112 62 112 C72 112 74 90 76 68 C78 50 89 40 86 24 C82 4 62 2 50 8 Z';
  var TOOTH = 'M34 30 H106 V40 C108 70 110 100 106 116 C104 128 90 132 70 132 C50 132 36 128 34 116 C30 100 32 70 34 40 Z';
  var SHADE = 'M94 36 H106 V40 C108 70 110 100 106 116 C103 125 98 128 93 130 C97 100 97 70 94 36 Z';
  var GUM = 'M0 0 H140 V34 H112 C104 34 100 44 70 44 C40 44 36 34 28 34 H0 Z';
  var CHIPS = {
    esmalte: { cut: '80,140 112,100 112,140', line: '80,140 112,100' },
    dentina: { cut: '60,142 114,86 114,142', line: '60,142 114,86', band: '60,142 114,86 105.4,77.7 51.4,133.7' }
  };
  var reduce = !!(window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches);
  var uid = 0;
 
  function $(id) { return document.getElementById(id); }
  function h(tag, cls, text) {
    var e = document.createElement(tag);
    if (cls) e.className = cls;
    if (text != null) e.textContent = text;
    return e;
  }
 
  function toothSVG(variant) {
    var n = ++uid, chip = CHIPS[variant];
    var s = '<svg viewBox="0 0 140 150" aria-hidden="true" focusable="false"><defs><clipPath id="tc' + n + '"><path d="' + TOOTH + '"/></clipPath>';
    if (chip) {
      s += '<mask id="tm' + n + '" maskUnits="userSpaceOnUse" x="0" y="0" width="140" height="150"><rect width="140" height="150" fill="#fff"/><polygon points="' + chip.cut + '" fill="#000"/></mask>';
    }
    s += '</defs><g' + (chip ? ' mask="url(#tm' + n + ')"' : '') + '>';
    s += '<path d="' + TOOTH + '" class="t-fill"/><path d="' + SHADE + '" class="t-shade"/>';
    if (chip && chip.band) {
      s += '<g clip-path="url(#tc' + n + ')"><polygon points="' + chip.band + '" class="t-dentin"/></g>';
    }
    s += '<path d="' + TOOTH + '" class="t-outline"/></g>';
    if (chip) {
      s += '<polyline points="' + chip.line + '" class="t-cut' + (chip.band ? ' dn' : '') + '" clip-path="url(#tc' + n + ')"/>';
    }
    s += '<path d="' + GUM + '" class="t-gum"/>';
    if (variant === 'concusion') {
      s += '<g class="t-impact" stroke-width="5" stroke-linecap="round">' +
        '<line x1="118" y1="64" x2="132" y2="58"/><line x1="121" y1="82" x2="137" y2="82"/><line x1="118" y1="100" x2="132" y2="106"/>' +
        '<line x1="22" y1="64" x2="8" y2="58"/><line x1="19" y1="82" x2="3" y2="82"/><line x1="22" y1="100" x2="8" y2="106"/></g>';
    }
    return s + '</svg>';
  }
 
  function starSvg(on) {
    return '<svg class="star ' + (on ? 'on' : 'off') + '" viewBox="0 0 24 24" aria-hidden="true">' + STAR + '</svg>';
  }
  function starRow(n) {
    var s = '';
    for (var i = 0; i < 3; i++) s += starSvg(i < n);
    return s;
  }
 
  var TROPHY = '<svg class="trophy" viewBox="0 0 160 170" aria-hidden="true" focusable="false">' +
    '<path class="g-arm" d="M38 36 H22 C22 62 32 76 48 80"/><path class="g-arm" d="M122 36 H138 C138 62 128 76 112 80"/>' +
    '<rect class="g-deep" x="70" y="112" width="20" height="26"/><rect class="g-deep" x="46" y="136" width="68" height="18" rx="5"/>' +
    '<path class="g-fill" d="M38 24 H122 V58 C122 92 104 116 80 116 C56 116 38 92 38 58 Z"/>' +
    '<path class="g-shine" d="M50 36 C48 60 54 84 66 98"/>' +
    '<svg x="58" y="36" width="44" height="53" viewBox="0 0 100 120"><path class="g-tooth" d="' + GLYPH + '"/></svg>' +
    '<path class="spark" transform="translate(4 6) scale(.9)" d="M12 2.2l2.95 6.1 6.7.9-4.9 4.7 1.2 6.7L12 17.4l-5.95 3.2 1.2-6.7-4.9-4.7 6.7-.9z"/>' +
    '<path class="spark" transform="translate(128 0) scale(.7)" d="M12 2.2l2.95 6.1 6.7.9-4.9 4.7 1.2 6.7L12 17.4l-5.95 3.2 1.2-6.7-4.9-4.7 6.7-.9z"/>' +
    '<path class="spark" transform="translate(130 112) scale(.8)" d="M12 2.2l2.95 6.1 6.7.9-4.9 4.7 1.2 6.7L12 17.4l-5.95 3.2 1.2-6.7-4.9-4.7 6.7-.9z"/>' +
    '</svg>';
 
  var S = { li: 0, cards: [], first: null, pending: null, timer: null, matched: 0, total: 0, tries: 0, miss: 0, stars: [0, 0, 0], onNext: null };
 
  function shuffle(a) {
    for (var i = a.length - 1; i > 0; i--) {
      var j = Math.floor(Math.random() * (i + 1)), t = a[i]; a[i] = a[j]; a[j] = t;
    }
    return a;
  }
 
  function say(text, mood) {
    var el = $('status');
    el.textContent = text;
    el.className = 'status' + (mood ? ' ' + mood : '');
  }
 
  function renderPath(playing) {
    var ol = $('path');
    ol.innerHTML = '';
    LEVELS.forEach(function (L, i) {
      var li = h('li');
      var state = S.stars[i] > 0 ? 'done' : (playing && i === S.li ? 'now' : '');
      if (state) li.className = state;
      li.setAttribute('aria-label', 'Nivel ' + (i + 1) + ': ' + L.title + (state === 'done' ? ', completado' : state === 'now' ? ', en juego' : ''));
      li.innerHTML = '<svg viewBox="0 0 100 120" aria-hidden="true" focusable="false"><use href="#glyph"/></svg><span><span class="w">Nivel </span>' + (i + 1) + '</span>';
      ol.appendChild(li);
    });
  }
 
  function renderLevelList() {
    var ul = $('levels');
    LEVELS.forEach(function (L, i) {
      var li = h('li');
      li.appendChild(h('span', 'n', String(i + 1)));
      li.appendChild(h('span', 't', L.title));
      li.appendChild(h('span', 'c', L.pairs.length + ' parejas'));
      ul.appendChild(li);
    });
  }
 
  function buildFront(d, tag) {
    var f = h('div', 'face front');
    f.appendChild(h('span', 'tag', tag));
    if (d.type === 'img') {
      var art = h('div', 'art');
      art.innerHTML = toothSVG(d.variant);
      f.appendChild(art);
      f.appendChild(h('p', 'cap', d.caption));
      if (d.note) f.appendChild(h('p', 'note', '(' + d.note + ')'));
    } else if (d.type === 'situation') {
      f.appendChild(h('div', 'bigem', d.emoji));
      f.appendChild(h('p', 'quote', d.title));
    } else {
      var t = h('h3', 'ttl');
      var em = h('span', 'em', d.emoji);
      em.setAttribute('aria-hidden', 'true');
      t.appendChild(em);
      t.appendChild(document.createTextNode(' ' + d.title));
      f.appendChild(t);
      if (d.bullets) {
        var ul = h('ul', 'bl');
        d.bullets.forEach(function (b) { ul.appendChild(h('li', null, b)); });
        f.appendChild(ul);
      }
    }
    return f;
  }
 
  function labelFor(d, tag) {
    if (d.type === 'img') return tag + ': ' + d.caption + (d.note ? ' (' + d.note + ')' : '');
    if (d.type === 'situation') return tag + ': ' + d.title;
    return tag + ': ' + d.title + '. ' + (d.bullets ? d.bullets.join(' ') : '');
  }
 
  function paint(c) {
    c.node.classList.toggle('open', c.open);
    c.node.classList.toggle('done', c.done);
    c.back.setAttribute('aria-hidden', c.open ? 'true' : 'false');
    c.front.setAttribute('aria-hidden', c.open ? 'false' : 'true');
    c.node.setAttribute('aria-label', c.open ? c.label : 'Carta ' + c.n + ', boca abajo');
  }
 
  function updateStats() {
    $('s-pairs').textContent = S.matched + '/' + S.total;
    $('s-tries').textContent = String(S.tries);
  }
 
  function settleMismatch() {
    clearTimeout(S.timer);
    S.timer = null;
    if (S.pending) {
      S.pending.forEach(function (c) { c.open = false; paint(c); });
      S.pending = null;
    }
  }
 
  function flip(c) {
    if (c.open || c.done) return;
    if (S.pending) settleMismatch();
    c.open = true;
    paint(c);
    if (!S.first) {
      S.first = c;
      say('Ahora busca su pareja.');
      return;
    }
    var a = S.first;
    S.first = null;
    S.tries++;
    if (a.pid === c.pid) {
      a.done = c.done = true;
      paint(a); paint(c);
      [a, c].forEach(function (x) {
        x.node.classList.add('just');
        setTimeout(function () { x.node.classList.remove('just'); }, 600);
      });
      S.matched++;
      say('¡Pareja encontrada! ' + c.name, 'good');
      updateStats();
      if (S.matched === S.total) setTimeout(levelDone, 1100);
    } else {
      S.miss++;
      S.pending = [a, c];
      say('No son pareja. Mira bien y prueba otra vez.', 'bad');
      updateStats();
      S.timer = setTimeout(settleMismatch, 1700);
    }
  }
 
  function startLevel(i) {
    settleMismatch();
    hideOverlay();
    S.li = i; S.first = null; S.pending = null; S.matched = 0; S.tries = 0; S.miss = 0;
    var L = LEVELS[i];
    var deck = [];
    L.pairs.forEach(function (p) {
      deck.push({ pid: p.id, side: 'a', data: p.a, tag: L.tags.a, name: p.name });
      deck.push({ pid: p.id, side: 'b', data: p.b, tag: L.tags.b, name: p.name });
    });
    shuffle(deck);
    S.total = L.pairs.length;
    var board = $('board');
    board.innerHTML = '';
    board.className = 'board c' + deck.length;
    S.cards = deck.map(function (cfg, k) {
      var node = h('div', 'card k' + cfg.side);
      node.setAttribute('role', 'button');
      node.tabIndex = 0;
      var inner = h('div', 'inner');
      var back = h('div', 'face back');
      back.innerHTML = '<svg class="bk" viewBox="0 0 100 120" aria-hidden="true" focusable="false"><use href="#glyph"/></svg>';
      var front = buildFront(cfg.data, cfg.tag);
      inner.appendChild(back);
      inner.appendChild(front);
      node.appendChild(inner);
      var c = { pid: cfg.pid, name: cfg.name, n: k + 1, node: node, back: back, front: front, open: false, done: false, label: labelFor(cfg.data, cfg.tag) };
      node.addEventListener('click', function () { flip(c); });
      node.addEventListener('keydown', function (ev) {
        if (ev.key === 'Enter' || ev.key === ' ') { ev.preventDefault(); flip(c); }
      });
      paint(c);
      board.appendChild(node);
      return c;
    });
    $('kicker').textContent = 'Nivel ' + (i + 1) + ' de ' + LEVELS.length;
    $('ltitle').textContent = L.title;
    $('llead').textContent = L.lead;
    say('Voltea dos cartas para empezar.');
    updateStats();
    renderPath(true);
    $('start').hidden = true;
    $('play').hidden = false;
    window.scrollTo(0, 0);
  }
 
  function hideOverlay() {
    $('overlay').hidden = true;
    $('sheet').classList.remove('final');
  }
 
  function showOverlay(o) {
    $('ov-art').innerHTML = o.art || '';
    $('ov-art').className = o.artClass || '';
    $('ov-title').textContent = o.title;
    $('ov-text').textContent = o.text;
    $('ov-extra').innerHTML = o.extra || '';
    $('ov-btn').textContent = o.button;
    $('sheet').classList.toggle('final', !!o.final);
    S.onNext = o.onNext;
    $('overlay').hidden = false;
    $('ov-btn').focus();
  }
 
  function levelDone() {
    var L = LEVELS[S.li], n = S.li + 1;
    var stars = S.miss <= S.total ? 3 : (S.miss <= S.total * 2 ? 2 : 1);
    S.stars[S.li] = stars;
    renderPath(true);
    if (S.li === LEVELS.length - 1) { showFinal(); return; }
    var msg = stars === 3 ? 'Memoria de campeón.' : stars === 2 ? 'Muy bien, casi perfecto.' : 'Lo lograste. Con práctica serás más rápido.';
    var next = LEVELS[S.li + 1];
    showOverlay({
      art: '<div class="stars" aria-label="' + stars + ' de 3 estrellas">' + starRow(stars) + '</div>',
      title: '¡Nivel ' + n + ' completo!',
      text: 'Encontraste las ' + S.total + ' parejas en ' + S.tries + ' intentos. ' + msg,
      button: 'Nivel ' + (n + 1) + ': ' + next.title,
      onNext: function () { startLevel(S.li + 1); }
    });
  }
 
  function showFinal() {
    var total = S.stars.reduce(function (a, b) { return a + b; }, 0);
    var extra = '<ul class="recap">';
    LEVELS.forEach(function (L, i) {
      extra += '<li><span>' + (i + 1) + '. ' + L.title + '</span><span class="stars" aria-label="' + S.stars[i] + ' de 3 estrellas">' + starRow(S.stars[i]) + '</span></li>';
    });
    extra += '</ul>';
    showOverlay({
      art: TROPHY,
      title: '¡Misión cumplida!',
      text: 'Ahora eres un Guardián de la Sonrisa',
      extra: extra,
      button: 'Jugar otra vez',
      final: true,
      onNext: function () { S.stars = [0, 0, 0]; startLevel(0); }
    });
    confetti();
  }
 
  function confetti() {
    if (reduce) return;
    var cv = $('confetti'), ctx = cv.getContext && cv.getContext('2d');
    if (!ctx) return;
    var dpr = Math.min(window.devicePixelRatio || 1, 2), W = window.innerWidth, H = window.innerHeight;
    cv.width = W * dpr; cv.height = H * dpr;
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    var cols = ['#EF6363', '#0E9F8E', '#FFB400', '#3B8BD0', '#F4929F', '#FFFFFF'];
    var ps = [];
    for (var i = 0; i < 150; i++) {
      ps.push({ x: Math.random() * W, y: -20 - Math.random() * H * 0.6, w: 6 + Math.random() * 6, h: 8 + Math.random() * 8,
        vx: -1 + Math.random() * 2, vy: 2 + Math.random() * 3.5, r: Math.random() * 6.28, vr: -0.15 + Math.random() * 0.3,
        c: cols[Math.floor(Math.random() * cols.length)] });
    }
    var t0 = performance.now();
    function tick(t) {
      ctx.clearRect(0, 0, W, H);
      var alive = false;
      ps.forEach(function (p) {
        p.x += p.vx; p.y += p.vy; p.r += p.vr;
        if (p.y < H + 20) alive = true;
        ctx.save(); ctx.translate(p.x, p.y); ctx.rotate(p.r);
        ctx.fillStyle = p.c; ctx.fillRect(-p.w / 2, -p.h / 2, p.w, p.h);
        ctx.restore();
      });
      if (alive && t - t0 < 6000) requestAnimationFrame(tick); else ctx.clearRect(0, 0, W, H);
    }
    requestAnimationFrame(tick);
  }
 
  $('go').addEventListener('click', function () { S.stars = [0, 0, 0]; startLevel(0); });
  $('shuffle').addEventListener('click', function () { startLevel(S.li); });
  $('ov-btn').addEventListener('click', function () { if (S.onNext) S.onNext(); });
  $('overlay').addEventListener('keydown', function (ev) {
    if (ev.key === 'Tab') { ev.preventDefault(); $('ov-btn').focus(); }
  });
 
  renderLevelList();
  renderPath(false);
})();
</script>
