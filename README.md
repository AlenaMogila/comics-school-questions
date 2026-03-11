<!DOCTYPE html>
<html lang="ru" class="h-full">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Почтовый ящик вопросов · олдскул</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Special+Elite&family=IBM+Plex+Mono:wght@400;600&display=swap" rel="stylesheet">
  <style>
    /* ч/б олдскульная эстетика, никаких эмодзи, всё линейное */
    body {
      background: #f0f0f0;
      font-family: 'IBM Plex Mono', monospace;
      filter: grayscale(100%);
    }
    .font-old {
      font-family: 'Special Elite', cursive;
    }
    .font-mono {
      font-family: 'IBM Plex Mono', monospace;
    }
    /* комикс-панели в стиле старых газет */
    .comic-panel-old {
      border: 3px solid #111;
      background: #ffffff;
      box-shadow: 6px 6px 0 #222;
      image-rendering: crisp-edges;
    }
    /* линейные человечки (стик-фигуры) через CSS */
    .stick-figure {
      position: relative;
      width: 36px;
      height: 72px;
      display: inline-block;
    }
    .stick-figure .head {
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 20px;
      height: 20px;
      border: 2px solid #111;
      border-radius: 50%;
      background: white;
    }
    .stick-figure .body {
      position: absolute;
      top: 20px;
      left: 50%;
      width: 2px;
      height: 30px;
      background: #111;
      transform: translateX(-50%);
    }
    .stick-figure .arm-left {
      position: absolute;
      top: 28px;
      left: 35%;
      width: 14px;
      height: 2px;
      background: #111;
      transform: rotate(-30deg);
      transform-origin: right;
    }
    .stick-figure .arm-right {
      position: absolute;
      top: 28px;
      right: 35%;
      width: 14px;
      height: 2px;
      background: #111;
      transform: rotate(30deg);
      transform-origin: left;
    }
    .stick-figure .leg-left {
      position: absolute;
      top: 50px;
      left: 44%;
      width: 14px;
      height: 2px;
      background: #111;
      transform: rotate(-20deg);
      transform-origin: right;
    }
    .stick-figure .leg-right {
      position: absolute;
      top: 50px;
      right: 44%;
      width: 14px;
      height: 2px;
      background: #111;
      transform: rotate(20deg);
      transform-origin: left;
    }
    /* учительский вариант (юбка/брюки не принципиально — просто линии) */
    .stick-figure.teacher .body {
      height: 32px;
    }
    .stick-figure.teacher .arm-left, .stick-figure.teacher .arm-right {
      top: 26px;
    }
    /* доска / ч/б элементы */
    .old-blackboard {
      background: #222;
      border: 4px solid #111;
      color: #eee;
      font-family: 'Special Elite', monospace;
      text-transform: uppercase;
      letter-spacing: 1px;
    }
    .speech-bubble-old {
      position: relative;
      background: white;
      border: 2px solid #111;
      padding: 10px 14px;
      font-size: 0.9rem;
      font-family: 'IBM Plex Mono', monospace;
      box-shadow: 3px 3px 0 #111;
    }
    .speech-bubble-old::after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 20px;
      width: 0;
      height: 0;
      border-left: 10px solid transparent;
      border-right: 10px solid transparent;
      border-top: 10px solid #111;
    }
    .thought-cloud-old {
      background: white;
      border: 2px solid #111;
      border-radius: 40% 40% 40% 40% / 40% 40% 40% 40%;
      padding: 6px 12px;
      font-size: 0.75rem;
      box-shadow: 3px 3px 0 #111;
    }
    /* простой ящик */
    .mailbox-old {
      background: #ddd;
      border: 3px solid #111;
      width: 120px;
      height: 90px;
      position: relative;
      box-shadow: 4px 4px 0 #111;
    }
    .mailbox-old .slot {
      width: 70px;
      height: 12px;
      background: #111;
      margin: 10px auto 8px;
    }
    .mailbox-old .label {
      background: white;
      border: 2px solid #111;
      padding: 4px 6px;
      font-size: 0.7rem;
      font-weight: bold;
      text-transform: uppercase;
      display: inline-block;
      margin: 0 auto;
    }
    /* навигационные точки строго ч/б */
    .panel-dot-old {
      width: 14px;
      height: 14px;
      border: 2px solid #111;
      background: white;
      transition: 0.1s;
    }
    .panel-dot-old.active {
      background: #111;
    }
    /* кнопки ч/б */
    .btn-old {
      background: white;
      border: 2px solid #111;
      color: #111;
      font-weight: bold;
      padding: 8px 16px;
      box-shadow: 3px 3px 0 #111;
      transition: 0.1s;
    }
    .btn-old:hover:not(:disabled) {
      background: #eee;
      box-shadow: 2px 2px 0 #111;
      transform: translate(1px,1px);
    }
    .btn-old:disabled {
      opacity: 0.3;
      border-color: #777;
      box-shadow: none;
    }
    .paper-old {
      background: white;
      border: 2px solid #111;
      width: 40px;
      height: 50px;
      transform: rotate(2deg);
      box-shadow: 2px 2px 0 #111;
    }
  </style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
</head>
<body class="h-full font-mono bg-gray-100">

<div id="app-container" class="h-full overflow-auto bg-white" style="background: #f0f0f0;">
  
  <!-- шапка строгая -->
  <header class="text-center py-8 px-4 border-b-4 border-black bg-white">
    <h1 id="main-title" class="font-old text-5xl md:text-6xl font-bold text-black uppercase tracking-wide">📬 почтовый ящик вопросов</h1>
    <p id="subtitle-text" class="mt-3 text-black border-t-2 border-black inline-block px-6 pt-2 text-sm uppercase tracking-widest">Окружающий мир · 2 класс</p>
  </header>

  <!-- панель навигации ч/б -->
  <div class="flex justify-center items-center gap-6 my-6">
    <button id="prev-btn" class="btn-old px-5 py-2 text-sm uppercase tracking-wide" disabled>← назад</button>
    <div class="flex gap-3">
      <button class="panel-dot-old active" data-panel="0"></button>
      <button class="panel-dot-old" data-panel="1"></button>
      <button class="panel-dot-old" data-panel="2"></button>
      <button class="panel-dot-old" data-panel="3"></button>
    </div>
    <button id="next-btn" class="btn-old px-5 py-2 text-sm uppercase tracking-wide">далее →</button>
  </div>

  <!-- комикс панели -->
  <main class="max-w-4xl mx-auto px-4 pb-12">

    <!-- ПАНЕЛЬ 1: Шквал вопросов -->
    <div id="panel-0" class="comic-panel-old p-5 mb-8">
      <div class="text-left mb-4 ml-2 border-b-2 border-black inline-block pr-8">
        <span class="font-old text-sm uppercase tracking-widest bg-white px-3">кадр 1 · шквал вопросов</span>
      </div>
      <div class="relative min-h-[300px] bg-gray-50 border-2 border-black p-3">
        <!-- доска -->
        <div class="absolute top-3 left-1/2 -translate-x-1/2 w-44 h-20 bg-black border-2 border-white text-white flex items-center justify-center font-old text-sm">ОКР. МИР</div>
        <!-- учитель (стик) -->
        <div class="absolute bottom-8 left-1/2 -translate-x-1/2">
          <div class="stick-figure teacher">
            <div class="head"></div>
            <div class="body"></div>
            <div class="arm-left"></div>
            <div class="arm-right"></div>
            <div class="leg-left"></div>
            <div class="leg-right"></div>
          </div>
          <!-- речевое облако -->
          <div class="speech-bubble-old absolute -top-16 left-1/2 -translate-x-1/2 w-48 text-center text-xs">
            По одному! Я не успеваю…
          </div>
        </div>
        <!-- ученики-стики с мыслями -->
        <div class="absolute bottom-4 left-4">
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div><div class="leg-left"></div><div class="leg-right"></div></div>
          <div class="thought-cloud-old absolute -top-12 left-0 whitespace-nowrap">почему трава зелёная?</div>
        </div>
        <div class="absolute bottom-4 left-28">
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div><div class="leg-left"></div><div class="leg-right"></div></div>
          <div class="thought-cloud-old absolute -top-14 left-0 whitespace-nowrap">куда уходит солнце?</div>
        </div>
        <div class="absolute bottom-4 right-28">
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div><div class="leg-left"></div><div class="leg-right"></div></div>
          <div class="thought-cloud-old absolute -top-12 right-0 whitespace-nowrap">откуда дождик?</div>
        </div>
        <div class="absolute bottom-4 right-4">
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div><div class="leg-left"></div><div class="leg-right"></div></div>
          <div class="thought-cloud-old absolute -top-14 right-0 whitespace-nowrap">почему небо голубое?</div>
        </div>
      </div>
    </div>

    <!-- ПАНЕЛЬ 2: Гениальная идея -->
    <div id="panel-1" class="comic-panel-old p-5 mb-8 hidden">
      <div class="text-left mb-4 ml-2 border-b-2 border-black inline-block pr-8">
        <span class="font-old text-sm uppercase tracking-widest bg-white px-3">кадр 2 · гениальная идея</span>
      </div>
      <div class="relative min-h-[300px] bg-gray-50 border-2 border-black p-3">
        <!-- доска с Д/З -->
        <div class="absolute top-3 left-1/2 -translate-x-1/2 w-48 h-24 bg-black border-2 border-white text-white flex flex-col items-center justify-center font-old">
          <span class="text-xl">Д/З</span>
          <span class="text-xs">найти ответ на вопрос</span>
        </div>
        <!-- учитель -->
        <div class="absolute bottom-8 left-1/4">
          <div class="stick-figure teacher">
            <div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div><div class="leg-left"></div><div class="leg-right"></div>
          </div>
          <div class="speech-bubble-old absolute -top-20 left-8 w-56 text-xs">
            Записывайте вопросы на листочки. Д/з — найти самый интересный ответ!
          </div>
        </div>
        <!-- стопка бумаги -->
        <div class="absolute bottom-12 right-8">
          <div class="paper-old absolute rotate-3"></div>
          <div class="paper-old absolute -top-2 left-1 -rotate-2"></div>
          <div class="paper-old absolute -top-4 left-2 rotate-6"></div>
          <span class="absolute top-0 left-6 text-xs font-bold">вопросы</span>
        </div>
        <!-- довольные ученики (стики) -->
        <div class="absolute bottom-4 right-1/4 flex gap-3">
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
        </div>
        <!-- лампочка просто линиями (без эмодзи) -->
        <div class="absolute top-4 right-4 text-4xl font-old opacity-50">⚡︎</div>
      </div>
    </div>

    <!-- ПАНЕЛЬ 3: Неожиданный подарок (почтовый ящик) -->
    <div id="panel-2" class="comic-panel-old p-5 mb-8 hidden">
      <div class="text-left mb-4 ml-2 border-b-2 border-black inline-block pr-8">
        <span class="font-old text-sm uppercase tracking-widest bg-white px-3">кадр 3 · подарок</span>
      </div>
      <div class="relative min-h-[300px] bg-gray-50 border-2 border-black p-3">
        <!-- солнце линиями: просто круг с лучами -->
        <div class="absolute top-2 right-6 w-12 h-12 border-2 border-black rounded-full"></div>
        <div class="absolute top-2 right-6 w-16 h-16 border border-black rounded-full opacity-30"></div>
        <!-- девочка с рюкзаком (стик, рюкзак квадратик) -->
        <div class="absolute bottom-8 left-8">
          <div class="stick-figure"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div><div class="leg-left"></div><div class="leg-right"></div></div>
          <div class="absolute -top-2 -right-6 w-7 h-8 border-2 border-black bg-white"></div> <!-- рюкзак -->
        </div>
        <!-- почтовый ящик handmade -->
        <div class="absolute bottom-12 left-1/2 -translate-x-1/2">
          <div class="mailbox-old">
            <div class="slot"></div>
            <div class="label font-old text-[0.6rem]">ПОЧТА ВОПРОСОВ</div>
            <div class="absolute -top-3 -left-2 text-xl">⌂</div>
            <div class="absolute -bottom-2 right-2 text-xl">⌂</div>
          </div>
        </div>
        <!-- реплика девочки -->
        <div class="absolute top-20 left-4 max-w-[160px] speech-bubble-old text-xs">
          Чтобы вопросы не терялись! Как настоящий ящик.
        </div>
        <!-- учитель в удивлении -->
        <div class="absolute bottom-8 right-8">
          <div class="stick-figure teacher">
            <div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right" style="transform:rotate(60deg);"></div><div class="leg-left"></div><div class="leg-right"></div>
          </div>
          <div class="absolute -top-6 left-3 text-xl">!</div>
        </div>
      </div>
    </div>

    <!-- ПАНЕЛЬ 4: Рождение традиции -->
    <div id="panel-3" class="comic-panel-old p-5 mb-8 hidden">
      <div class="text-left mb-4 ml-2 border-b-2 border-black inline-block pr-8">
        <span class="font-old text-sm uppercase tracking-widest bg-white px-3">кадр 4 · традиция</span>
      </div>
      <div class="relative min-h-[340px] bg-gray-50 border-2 border-black p-3">
        <!-- ящик на стене -->
        <div class="absolute top-6 right-10">
          <div class="mailbox-old scale-90">
            <div class="slot"></div>
            <div class="label font-old text-[0.55rem]">ПОЧТА ВОПРОСОВ</div>
          </div>
          <!-- летящие бумажки -->
          <div class="paper-old absolute -top-4 -left-6 w-7 h-9 rotate-12"></div>
          <div class="paper-old absolute -top-2 left-6 w-7 h-9 -rotate-12"></div>
        </div>
        <!-- дверной косяк справа (просто линия) -->
        <div class="absolute top-0 right-0 w-1 h-full bg-black"></div>
        <!-- шеренга детей слева снизу -->
        <div class="absolute bottom-16 left-4 right-32 flex justify-around">
          <div class="stick-figure scale-90"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
          <div class="stick-figure scale-90"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
          <div class="stick-figure scale-90"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
          <div class="stick-figure scale-90"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
        </div>
        <!-- бумажки в руках (линии) -->
        <div class="absolute bottom-28 left-16 w-5 h-6 border-2 border-black rotate-6"></div>
        <div class="absolute bottom-32 left-40 w-5 h-6 border-2 border-black -rotate-3"></div>
        <!-- учитель кивает -->
        <div class="absolute bottom-16 left-8">
          <div class="stick-figure teacher"><div class="head"></div><div class="body"></div><div class="arm-left"></div><div class="arm-right"></div></div>
          <div class="absolute -bottom-4 left-2 text-lg">👍</div>
        </div>
        <!-- итоговая подпись строго -->
        <div class="absolute bottom-2 left-4 right-4 bg-white border-2 border-black p-2 text-center text-xs uppercase tracking-wide">
          ✦ так во 2 «б» появилась традиция: собирать вопросы в ящик ✦<br>умение спросить — половина ответа
        </div>
      </div>
    </div>
  </main>

  <!-- футер в стиле old school -->
  <footer class="border-t-4 border-black bg-white py-6 text-center uppercase text-sm tracking-widest">
    <p class="font-old text-xl mb-2">? спрашивай, думай, открывай ?</p>
    <p class="text-xs border-t border-black pt-2 inline-block px-6">комикс для юных исследователей · всё ч/б</p>
  </footer>
</div>

<!-- навигационный скрипт (минимум) -->
<script>
  let currentPanel = 0;
  const totalPanels = 4;

  function updatePanels() {
    for (let i = 0; i < totalPanels; i++) {
      const p = document.getElementById(`panel-${i}`);
      if (p) p.classList.toggle('hidden', i !== currentPanel);
    }
    document.getElementById('prev-btn').disabled = currentPanel === 0;
    document.getElementById('next-btn').disabled = currentPanel === totalPanels - 1;
    
    document.querySelectorAll('.panel-dot-old').forEach((dot, idx) => {
      dot.classList.toggle('active', idx === currentPanel);
    });
  }

  document.getElementById('prev-btn').addEventListener('click', () => {
    if (currentPanel > 0) { currentPanel--; updatePanels(); }
  });
  document.getElementById('next-btn').addEventListener('click', () => {
    if (currentPanel < totalPanels-1) { currentPanel++; updatePanels(); }
  });
  document.querySelectorAll('.panel-dot-old').forEach((dot, idx) => {
    dot.addEventListener('click', () => {
      currentPanel = idx;
      updatePanels();
    });
  });
  document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowLeft' && currentPanel > 0) { currentPanel--; updatePanels(); }
    if (e.key === 'ArrowRight' && currentPanel < totalPanels-1) { currentPanel++; updatePanels(); }
  });
  updatePanels();

  // заглушка SDK, чтобы не ломалось (можно доработать под ч/б, но это необязательно)
  window.elementSdk = window.elementSdk || { init: () => {} };
  if (window.elementSdk) {
    window.elementSdk.init({
      defaultConfig: {},
      onConfigChange: (c) => {},
      mapToCapabilities: () => ({}),
      mapToEditPanelValues: () => new Map()
    });
  }
</script>
<!-- убран скрипт Cloudflare, лишний -->
</body>
</html>
