<!doctype html>
<html lang="ru" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Почтовый ящик вопросов</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&amp;family=Nunito:wght@400;600;700&amp;display=swap" rel="stylesheet">
  <style>
    .font-handwritten { font-family: 'Caveat', cursive; }
    .font-body { font-family: 'Nunito', sans-serif; }
    
    .comic-panel {
      border: 4px solid #2d3748;
      border-radius: 12px;
      box-shadow: 6px 6px 0 #2d3748;
      transition: all 0.3s ease;
    }
    
    .comic-panel:hover {
      transform: translateY(-4px);
      box-shadow: 8px 10px 0 #2d3748;
    }
    
    .speech-bubble {
      position: relative;
      background: white;
      border: 3px solid #2d3748;
      border-radius: 20px;
      padding: 12px 16px;
    }
    
    .speech-bubble::after {
      content: '';
      position: absolute;
      bottom: -15px;
      left: 30px;
      border-width: 15px 10px 0;
      border-style: solid;
      border-color: #2d3748 transparent transparent;
    }
    
    .speech-bubble::before {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 32px;
      border-width: 12px 8px 0;
      border-style: solid;
      border-color: white transparent transparent;
      z-index: 1;
    }
    
    .thought-cloud {
      background: white;
      border: 2px solid #2d3748;
      border-radius: 50%;
      padding: 8px 12px;
      font-size: 0.85rem;
      box-shadow: 2px 2px 0 #2d3748;
    }
    
    .panel-nav-btn {
      transition: all 0.2s ease;
    }
    
    .panel-nav-btn:hover:not(:disabled) {
      transform: scale(1.1);
    }
    
    .panel-nav-btn:disabled {
      opacity: 0.4;
      cursor: not-allowed;
    }
    
    .mailbox-slot {
      animation: wiggle 2s ease-in-out infinite;
    }
    
    @keyframes wiggle {
      0%, 100% { transform: rotate(-2deg); }
      50% { transform: rotate(2deg); }
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }
    
    .float-animation {
      animation: float 3s ease-in-out infinite;
    }
    
    .paper-note {
      transform: rotate(-3deg);
      animation: paper-float 4s ease-in-out infinite;
    }
    
    @keyframes paper-float {
      0%, 100% { transform: rotate(-3deg) translateY(0); }
      50% { transform: rotate(-1deg) translateY(-5px); }
    }
  </style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full font-body">
  <div id="app-container" class="h-full overflow-auto" style="background: linear-gradient(135deg, #fef3c7 0%, #fde68a 50%, #fcd34d 100%);"><!-- Header -->
   <header class="text-center py-6 px-4">
    <div class="inline-block relative">
     <h1 id="main-title" class="font-handwritten text-5xl md:text-6xl font-bold text-gray-800 relative z-10">📬 Почтовый ящик вопросов</h1>
     <div class="absolute -bottom-2 left-0 right-0 h-4 bg-yellow-300 -z-0 transform -rotate-1 rounded"></div>
    </div>
    <p id="subtitle-text" class="mt-4 text-lg text-gray-700 font-semibold">Проект для урока окружающего мира, 2 класс</p>
   </header><!-- Panel Navigation -->
   <div class="flex justify-center items-center gap-4 mb-6 px-4"><button id="prev-btn" class="panel-nav-btn bg-orange-500 hover:bg-orange-600 text-white font-bold py-2 px-4 rounded-full shadow-lg disabled:bg-gray-400" disabled> ← Назад </button>
    <div class="flex gap-2"><button class="panel-dot w-4 h-4 rounded-full bg-orange-500 border-2 border-gray-800 transition-all" data-panel="0"></button> <button class="panel-dot w-4 h-4 rounded-full bg-white border-2 border-gray-800 transition-all" data-panel="1"></button> <button class="panel-dot w-4 h-4 rounded-full bg-white border-2 border-gray-800 transition-all" data-panel="2"></button> <button class="panel-dot w-4 h-4 rounded-full bg-white border-2 border-gray-800 transition-all" data-panel="3"></button>
    </div><button id="next-btn" class="panel-nav-btn bg-orange-500 hover:bg-orange-600 text-white font-bold py-2 px-4 rounded-full shadow-lg"> Далее → </button>
   </div><!-- Comic Panels Container -->
   <main class="max-w-4xl mx-auto px-4 pb-8"><!-- Panel 1: Шквал вопросов -->
    <div id="panel-0" class="comic-panel bg-sky-100 p-6 mb-8">
     <div class="text-center mb-4"><span class="inline-block bg-red-500 text-white font-bold px-4 py-1 rounded-full text-sm transform -rotate-2"> Кадр 1: Шквал вопросов </span>
     </div><!-- Scene -->
     <div class="relative min-h-[320px] bg-gradient-to-b from-green-100 to-green-200 rounded-lg p-4 overflow-hidden"><!-- Blackboard -->
      <div class="absolute top-4 left-1/2 -translate-x-1/2 w-48 h-24 bg-green-800 rounded border-4 border-yellow-700 flex items-center justify-center"><span class="text-white font-handwritten text-xl">Окружающий мир</span>
      </div><!-- Teacher -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 text-center">
       <div class="text-6xl mb-2">
        👩‍🏫
       </div>
       <div class="speech-bubble text-sm font-semibold text-gray-800 max-w-[200px]">
        Ребята, по одному! Я не успеваю отвечать!
       </div>
      </div><!-- Students with thought bubbles -->
      <div class="absolute bottom-4 left-4">
       <div class="text-4xl">
        🙋‍♂️
       </div>
       <div class="thought-cloud absolute -top-12 left-0 float-animation" style="animation-delay: 0s;">
        Почему трава зеленая?
       </div>
      </div>
      <div class="absolute bottom-4 left-24">
       <div class="text-4xl">
        🙋‍♀️
       </div>
       <div class="thought-cloud absolute -top-16 left-0 float-animation" style="animation-delay: 0.5s;">
        Куда уходит солнце?
       </div>
      </div>
      <div class="absolute bottom-4 right-24">
       <div class="text-4xl">
        🙋‍♂️
       </div>
       <div class="thought-cloud absolute -top-12 right-0 float-animation" style="animation-delay: 1s;">
        Откуда берется дождик?
       </div>
      </div>
      <div class="absolute bottom-4 right-4">
       <div class="text-4xl">
        🙋‍♀️
       </div>
       <div class="thought-cloud absolute -top-16 right-0 float-animation" style="animation-delay: 1.5s;">
        Почему небо голубое?
       </div>
      </div>
     </div>
    </div><!-- Panel 2: Гениальная идея -->
    <div id="panel-1" class="comic-panel bg-pink-100 p-6 mb-8 hidden">
     <div class="text-center mb-4"><span class="inline-block bg-purple-500 text-white font-bold px-4 py-1 rounded-full text-sm transform rotate-1"> Кадр 2: Гениальная идея </span>
     </div>
     <div class="relative min-h-[320px] bg-gradient-to-b from-amber-50 to-amber-100 rounded-lg p-4 overflow-hidden"><!-- Blackboard with D/Z -->
      <div class="absolute top-4 left-1/2 -translate-x-1/2 w-56 h-28 bg-green-800 rounded border-4 border-yellow-700 flex flex-col items-center justify-center"><span class="text-yellow-300 font-handwritten text-3xl font-bold">Д/З</span> <span class="text-white font-handwritten text-sm mt-1">Найти ответ на вопрос!</span>
      </div><!-- Teacher with papers -->
      <div class="absolute bottom-8 left-1/4 text-center">
       <div class="text-6xl">
        👩‍🏫
       </div>
       <div class="speech-bubble text-sm font-semibold text-gray-800 max-w-[280px] ml-16">
        А давайте сделаем так: все свои вопросы вы будете записывать на листочки. Домашнее задание — выбрать самый интересный вопрос и найти на него ответ!
       </div>
      </div><!-- Stack of papers -->
      <div class="absolute bottom-16 right-8">
       <div class="relative">
        <div class="w-20 h-24 bg-white border-2 border-gray-400 rounded shadow-md transform rotate-3"></div>
        <div class="w-20 h-24 bg-yellow-100 border-2 border-gray-400 rounded shadow-md absolute top-1 left-1 transform -rotate-2"></div>
        <div class="w-20 h-24 bg-pink-100 border-2 border-gray-400 rounded shadow-md absolute top-2 left-2 transform rotate-1"></div><span class="absolute top-8 left-4 font-handwritten text-gray-600 text-sm">Вопросы</span>
       </div>
      </div><!-- Happy students -->
      <div class="absolute bottom-4 right-1/4 flex gap-2">
       <div class="text-3xl">
        😊
       </div>
       <div class="text-3xl">
        🤩
       </div>
       <div class="text-3xl">
        😃
       </div>
      </div><!-- Light bulb idea -->
      <div class="absolute top-4 right-8 text-5xl float-animation">
       💡
      </div>
     </div>
    </div><!-- Panel 3: Неожиданный подарок -->
    <div id="panel-2" class="comic-panel bg-lime-100 p-6 mb-8 hidden">
     <div class="text-center mb-4"><span class="inline-block bg-green-500 text-white font-bold px-4 py-1 rounded-full text-sm transform -rotate-1"> Кадр 3: Неожиданный подарок </span>
     </div>
     <div class="relative min-h-[320px] bg-gradient-to-b from-blue-50 to-blue-100 rounded-lg p-4 overflow-hidden"><!-- Morning sun -->
      <div class="absolute top-2 right-4 text-5xl">
       🌅
      </div><!-- Girl with big backpack -->
      <div class="absolute bottom-8 left-8 text-center">
       <div class="text-6xl">
        👧
       </div>
       <div class="absolute -top-4 -right-8 text-4xl">
        🎒
       </div>
      </div><!-- Handmade mailbox -->
      <div class="absolute bottom-12 left-1/2 -translate-x-1/2 mailbox-slot">
       <div class="relative">
        <div class="w-36 h-28 bg-gradient-to-br from-red-400 to-pink-400 rounded-lg border-4 border-red-600 shadow-lg flex flex-col items-center justify-center"><!-- Slot -->
         <div class="w-24 h-3 bg-gray-800 rounded mb-2"></div><!-- Label -->
         <div class="bg-yellow-200 px-3 py-1 rounded border-2 border-yellow-500 transform -rotate-2"><span class="font-handwritten text-lg font-bold text-purple-700">ПОЧТА ВОПРОСОВ</span>
         </div><!-- Decorations -->
         <div class="absolute -top-2 -left-2 text-2xl">
          ⭐
         </div>
         <div class="absolute -top-2 -right-2 text-2xl">
          🌟
         </div>
         <div class="absolute -bottom-2 left-4 text-xl">
          ❤️
         </div>
         <div class="absolute -bottom-2 right-4 text-xl">
          💛
         </div>
        </div>
       </div>
      </div><!-- Speech bubble -->
      <div class="absolute top-20 left-4 max-w-[200px]">
       <div class="speech-bubble text-sm font-semibold text-gray-800">
        А это, чтобы вопросы не терялись! Как настоящий почтовый ящик!
       </div>
      </div><!-- Teacher reacting -->
      <div class="absolute bottom-8 right-8 text-center">
       <div class="text-5xl">
        😮
       </div>
       <div class="text-3xl mt-1">
        👩‍🏫
       </div>
       <div class="text-xl mt-1">
        ❤️
       </div>
      </div>
     </div>
    </div><!-- Panel 4: Рождение традиции -->
    <div id="panel-3" class="comic-panel bg-violet-100 p-6 mb-8 hidden">
     <div class="text-center mb-4"><span class="inline-block bg-indigo-500 text-white font-bold px-4 py-1 rounded-full text-sm transform rotate-1"> Кадр 4: Рождение традиции </span>
     </div>
     <div class="relative min-h-[360px] bg-gradient-to-b from-orange-50 to-yellow-100 rounded-lg p-4 overflow-hidden"><!-- Mailbox on wall -->
      <div class="absolute top-4 right-8">
       <div class="w-28 h-24 bg-gradient-to-br from-red-400 to-pink-400 rounded-lg border-4 border-red-600 shadow-lg flex flex-col items-center justify-center">
        <div class="w-20 h-3 bg-gray-800 rounded mb-1"></div>
        <div class="bg-yellow-200 px-2 py-0.5 rounded border border-yellow-500"><span class="font-handwritten text-xs font-bold text-purple-700">ПОЧТА ВОПРОСОВ</span>
        </div>
       </div><!-- Papers going in -->
       <div class="paper-note absolute -top-4 -left-4 w-8 h-10 bg-white border border-gray-300 rounded shadow transform rotate-12"></div>
       <div class="paper-note absolute -top-2 left-8 w-8 h-10 bg-yellow-100 border border-gray-300 rounded shadow transform -rotate-6" style="animation-delay: 0.5s;"></div>
      </div><!-- Door frame suggestion -->
      <div class="absolute top-0 right-0 w-4 h-full bg-yellow-700 rounded-l"></div><!-- Line of children -->
      <div class="absolute bottom-20 left-4 right-20 flex justify-around">
       <div class="text-4xl transform hover:scale-110 transition-transform cursor-pointer">
        🧒
       </div>
       <div class="text-4xl transform hover:scale-110 transition-transform cursor-pointer">
        👧
       </div>
       <div class="text-4xl transform hover:scale-110 transition-transform cursor-pointer">
        👦
       </div>
       <div class="text-4xl transform hover:scale-110 transition-transform cursor-pointer">
        👧
       </div>
       <div class="text-4xl transform hover:scale-110 transition-transform cursor-pointer">
        🧒
       </div>
      </div><!-- Folded papers in hands -->
      <div class="absolute bottom-28 left-8 text-xl paper-note">
       📝
      </div>
      <div class="absolute bottom-32 left-28 text-xl paper-note" style="animation-delay: 0.3s;">
       📝
      </div>
      <div class="absolute bottom-30 right-40 text-xl paper-note" style="animation-delay: 0.6s;">
       📝
      </div><!-- Teacher nodding -->
      <div class="absolute bottom-16 left-8 text-center">
       <div class="text-5xl">
        👩‍🏫
       </div>
       <div class="text-2xl">
        😊👍
       </div>
      </div><!-- Author's note -->
      <div class="absolute bottom-2 left-4 right-4 bg-white/80 backdrop-blur rounded-lg p-3 border-2 border-gray-300">
       <p class="text-sm text-gray-700 italic text-center"><span class="font-bold">✨ Так в 2 "Б" появилась традиция</span> собирать вопросы в волшебный ящик. <br>
        Ведь умение спросить — это половина ответа! 📚💫</p>
      </div>
     </div>
    </div>
   </main><!-- Footer -->
   <footer class="text-center py-6 px-4 bg-gradient-to-r from-orange-200 to-yellow-200 border-t-4 border-orange-400">
    <p class="font-handwritten text-2xl text-gray-700 mb-3">🌟 Спрашивай, думай, открывай! 🌟</p>
    <p class="text-sm text-gray-600">Комикс создан с любовью для юных исследователей</p>
   </footer>
  </div>
  <script>
    const defaultConfig = {
      comic_title: '📬 Почтовый ящик вопросов',
      subtitle: 'Проект для урока окружающего мира, 2 класс',
      background_color: '#fef3c7',
      text_color: '#1f2937',
      accent_color: '#f97316',
      panel_bg_color: '#e0f2fe',
      button_color: '#f97316',
      font_family: 'Nunito',
      font_size: 16
    };

    let currentPanel = 0;
    const totalPanels = 4;

    function updatePanelVisibility() {
      for (let i = 0; i < totalPanels; i++) {
        const panel = document.getElementById(`panel-${i}`);
        if (panel) {
          panel.classList.toggle('hidden', i !== currentPanel);
        }
      }
      
      document.getElementById('prev-btn').disabled = currentPanel === 0;
      document.getElementById('next-btn').disabled = currentPanel === totalPanels - 1;
      
      document.querySelectorAll('.panel-dot').forEach((dot, index) => {
        dot.classList.toggle('bg-orange-500', index === currentPanel);
        dot.classList.toggle('bg-white', index !== currentPanel);
      });
    }

    function navigatePanel(direction) {
      const newPanel = currentPanel + direction;
      if (newPanel >= 0 && newPanel < totalPanels) {
        currentPanel = newPanel;
        updatePanelVisibility();
      }
    }

    document.getElementById('prev-btn').addEventListener('click', () => navigatePanel(-1));
    document.getElementById('next-btn').addEventListener('click', () => navigatePanel(1));

    document.querySelectorAll('.panel-dot').forEach(dot => {
      dot.addEventListener('click', (e) => {
        currentPanel = parseInt(e.target.dataset.panel);
        updatePanelVisibility();
      });
    });

    document.addEventListener('keydown', (e) => {
      if (e.key === 'ArrowLeft') navigatePanel(-1);
      if (e.key === 'ArrowRight') navigatePanel(1);
    });

    async function onConfigChange(config) {
      const title = document.getElementById('main-title');
      const subtitle = document.getElementById('subtitle-text');
      const container = document.getElementById('app-container');
      
      if (title) {
        title.textContent = config.comic_title || defaultConfig.comic_title;
        title.style.color = config.text_color || defaultConfig.text_color;
      }
      
      if (subtitle) {
        subtitle.textContent = config.subtitle || defaultConfig.subtitle;
        subtitle.style.color = config.text_color || defaultConfig.text_color;
      }

      const customFont = config.font_family || defaultConfig.font_family;
      document.querySelectorAll('.font-body').forEach(el => {
        el.style.fontFamily = `${customFont}, sans-serif`;
      });

      const baseSize = config.font_size || defaultConfig.font_size;
      if (subtitle) subtitle.style.fontSize = `${baseSize * 1.125}px`;

      document.querySelectorAll('.panel-nav-btn:not(:disabled)').forEach(btn => {
        btn.style.backgroundColor = config.button_color || defaultConfig.button_color;
      });

      document.querySelectorAll('.panel-dot').forEach((dot, index) => {
        if (index === currentPanel) {
          dot.style.backgroundColor = config.accent_color || defaultConfig.accent_color;
        }
      });
    }

    function mapToCapabilities(config) {
      return {
        recolorables: [
          {
            get: () => config.background_color || defaultConfig.background_color,
            set: (value) => { config.background_color = value; window.elementSdk.setConfig({ background_color: value }); }
          },
          {
            get: () => config.panel_bg_color || defaultConfig.panel_bg_color,
            set: (value) => { config.panel_bg_color = value; window.elementSdk.setConfig({ panel_bg_color: value }); }
          },
          {
            get: () => config.text_color || defaultConfig.text_color,
            set: (value) => { config.text_color = value; window.elementSdk.setConfig({ text_color: value }); }
          },
          {
            get: () => config.accent_color || defaultConfig.accent_color,
            set: (value) => { config.accent_color = value; window.elementSdk.setConfig({ accent_color: value }); }
          },
          {
            get: () => config.button_color || defaultConfig.button_color,
            set: (value) => { config.button_color = value; window.elementSdk.setConfig({ button_color: value }); }
          }
        ],
        borderables: [],
        fontEditable: {
          get: () => config.font_family || defaultConfig.font_family,
          set: (value) => { config.font_family = value; window.elementSdk.setConfig({ font_family: value }); }
        },
        fontSizeable: {
          get: () => config.font_size || defaultConfig.font_size,
          set: (value) => { config.font_size = value; window.elementSdk.setConfig({ font_size: value }); }
        }
      };
    }

    function mapToEditPanelValues(config) {
      return new Map([
        ['comic_title', config.comic_title || defaultConfig.comic_title],
        ['subtitle', config.subtitle || defaultConfig.subtitle]
      ]);
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }

    updatePanelVisibility();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9da50130e138dd6d',t:'MTc3MzE3Mzg2NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
