<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gerador de Prompts: Grok Video</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    /* Estilos extras para os botões e toggles */
    .toggle-checkbox:checked {
      right: 0;
      border-color: #68D391;
    }
    .toggle-checkbox:checked + .toggle-label {
      background-color: #2563EB;
    }
    .toggle-checkbox:checked + .toggle-label .toggle-circle {
      transform: translateX(100%);
    }
  </style>
</head>
<body class="min-h-screen bg-neutral-900 text-neutral-100 p-4 md:p-8 font-sans">
  <div class="max-w-3xl mx-auto space-y-6">
    
    <div class="flex items-center space-x-3 pb-4 border-b border-neutral-800">
      <i data-lucide="wand-2" class="w-8 h-8 text-blue-500"></i>
      <h1 class="text-2xl font-bold">Gerador de Prompts: Grok Video</h1>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div class="space-y-5 bg-neutral-800 p-5 rounded-xl border border-neutral-700">
        
        <div class="space-y-2">
          <label class="flex items-center space-x-2 text-sm font-medium text-neutral-300">
            <i data-lucide="video" class="w-4 h-4"></i>
            <span>Ideia Principal do Vídeo</span>
          </label>
          <textarea id="subject" placeholder="Ex: Um cachorro correndo em um parque futurista cheio de luzes neon..." class="w-full bg-neutral-900 border border-neutral-700 rounded-lg p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none resize-none h-24"></textarea>
        </div>

        <div class="space-y-2">
          <label class="flex items-center space-x-2 text-sm font-medium text-neutral-300">
            <i data-lucide="camera" class="w-4 h-4"></i>
            <span>Estilo de Câmera</span>
          </label>
          <select id="camera" class="w-full bg-neutral-900 border border-neutral-700 rounded-lg p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none">
            <option value="Nenhuma específica">Nenhuma específica</option>
            <option value="Cinematográfica 4K">Cinematográfica 4K</option>
            <option value="Visão de Drone (Aérea)">Visão de Drone (Aérea)</option>
            <option value="Câmera na mão (Handheld)">Câmera na mão (Handheld)</option>
            <option value="Macro (Super close-up)">Macro (Super close-up)</option>
            <option value="Câmera Lenta (Slow Motion)">Câmera Lenta (Slow Motion)</option>
          </select>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <div class="space-y-2">
            <label class="flex items-center space-x-2 text-sm font-medium text-neutral-300">
              <i data-lucide="music" class="w-4 h-4"></i>
              <span>Música</span>
            </label>
            <select id="music" class="w-full bg-neutral-900 border border-neutral-700 rounded-lg p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none">
              <option value="Nenhuma">Nenhuma</option>
              <option value="Épica / Orquestral">Épica / Orquestral</option>
              <option value="Lo-Fi / Relaxante">Lo-Fi / Relaxante</option>
              <option value="Eletrônica / Upbeat">Eletrônica / Upbeat</option>
            </select>
          </div>

          <div class="space-y-2">
            <label class="flex items-center space-x-2 text-sm font-medium text-neutral-300">
              <i data-lucide="mic" class="w-4 h-4"></i>
              <span>Narração (Voz)</span>
            </label>
            <select id="voice" class="w-full bg-neutral-900 border border-neutral-700 rounded-lg p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none">
              <option value="Nenhuma">Nenhuma</option>
              <option value="Voz masculina profunda">Voz masculina profunda</option>
              <option value="Voz feminina suave">Voz feminina suave</option>
              <option value="Voz de documentário">Voz de documentário</option>
            </select>
          </div>
        </div>

        <div class="space-y-4 pt-4 border-t border-neutral-700">
          <div class="space-y-2">
            <label class="flex items-center space-x-2 text-sm font-medium text-neutral-300">
              <i data-lucide="clock" class="w-4 h-4"></i>
              <span>Duração do Vídeo</span>
            </label>
            <select id="duration" class="w-full bg-neutral-900 border border-neutral-700 rounded-lg p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:outline-none">
              <option value="6">6 Segundos</option>
              <option value="10">10 Segundos</option>
            </select>
          </div>

          <div class="flex flex-col gap-3 pt-2">
            <label class="flex items-center space-x-3 cursor-pointer">
              <input type="checkbox" id="extend" class="w-5 h-5 rounded border-neutral-700 bg-neutral-900 text-blue-600 focus:ring-blue-600 focus:ring-offset-neutral-800">
              <span class="text-sm font-medium text-neutral-300">Extender Vídeo (--extend)</span>
            </label>

            <label class="flex items-center space-x-3 cursor-pointer">
              <input type="checkbox" id="singleVideo" class="w-5 h-5 rounded border-neutral-700 bg-neutral-900 text-blue-600 focus:ring-blue-600 focus:ring-offset-neutral-800">
              <span class="text-sm font-medium text-neutral-300">Apenas 1 Vídeo</span>
            </label>
            
            <label class="flex items-center space-x-3 cursor-pointer">
              <input type="checkbox" id="zoomFaceEnd" class="w-5 h-5 rounded border-neutral-700 bg-neutral-900 text-blue-600 focus:ring-blue-600 focus:ring-offset-neutral-800">
              <span class="text-sm font-medium text-neutral-300">Zoom no Rosto no Final</span>
            </label>
          </div>
        </div>

      </div>

      <div class="space-y-4">
        <div class="bg-blue-900/20 border border-blue-500/30 rounded-xl p-5 h-full flex flex-col">
          <h2 class="text-lg font-semibold text-blue-400 mb-4 flex items-center">
            Prompt Gerado
          </h2>
          
          <div id="generatedPrompt" class="flex-1 bg-neutral-900/50 rounded-lg p-4 border border-neutral-800 text-neutral-200 text-sm md:text-base leading-relaxed break-words whitespace-pre-wrap">
            Digite a ideia principal para começar a gerar o prompt.
          </div>

          <button id="copyBtn" class="mt-4 w-full flex items-center justify-center space-x-2 py-3 rounded-lg font-medium transition-all bg-blue-600 hover:bg-blue-700 text-white shadow-lg shadow-blue-900/20">
            <i data-lucide="copy" class="w-5 h-5"></i>
            <span id="copyText">Copiar Prompt</span>
          </button>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Inicializa os ícones
    lucide.createIcons();

    // Pega os elementos
    const subject = document.getElementById('subject');
    const camera = document.getElementById('camera');
    const music = document.getElementById('music');
    const voice = document.getElementById('voice');
    const duration = document.getElementById('duration');
    const extend = document.getElementById('extend');
    const singleVideo = document.getElementById('singleVideo');
    const zoomFaceEnd = document.getElementById('zoomFaceEnd');
    const generatedPrompt = document.getElementById('generatedPrompt');
    const copyBtn = document.getElementById('copyBtn');
    const copyText = document.getElementById('copyText');

    // Função para gerar o prompt
    function gerarPrompt() {
      const subjectVal = subject.value.trim();
      
      if (!subjectVal) {
        generatedPrompt.innerText = 'Digite a ideia principal para começar a gerar o prompt.';
        return;
      }

      let partes = [`Imagine um vídeo: ${subjectVal}.`];

      if (camera.value !== "Nenhuma específica") partes.push(`Estilo de filmagem: ${camera.value}.`);

      let audioParts = [];
      if (music.value !== "Nenhuma") audioParts.push(`trilha sonora ${music.value.toLowerCase()}`);
      if (voice.value !== "Nenhuma") audioParts.push(`narração com ${voice.value.toLowerCase()}`);
      if (audioParts.length > 0) partes.push(`Áudio: ${audioParts.join(' e ')}.`);

      partes.push(`Duração exata: ${duration.value} segundos.`);

      if (extend.checked) partes.push(`--extend`); 
      if (singleVideo.checked) partes.push(`Gerar apenas 1 vídeo (sem variações extras).`);
      if (zoomFaceEnd.checked) partes.push(`Terminar o último frame com um zoom próximo ao rosto do personagem principal para manter a fidelidade na próxima cena.`);

      generatedPrompt.innerText = partes.join(' ');
    }

    // Adiciona os eventos para atualizar o texto na hora
    const inputs = [subject, camera, music, voice, duration, extend, singleVideo, zoomFaceEnd];
    inputs.forEach(input => {
      input.addEventListener('input', gerarPrompt);
      input.addEventListener('change', gerarPrompt);
    });

    // Função de copiar
    copyBtn.addEventListener('click', () => {
      const texto = generatedPrompt.innerText;
      if (texto.includes('Digite a ideia principal')) return;

      navigator.clipboard.writeText(texto).then(() => {
        copyText.innerText = "Copiado!";
        setTimeout(() => { copyText.innerText = "Copiar Prompt"; }, 2000);
      });
    });
  </script>
</body>
</html>
