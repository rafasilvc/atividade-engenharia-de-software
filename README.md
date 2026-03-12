# atividade-engenharia-de-software
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Linha do Tempo da Engenharia de Software</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="style.css">
</head>
<body class="bg-slate-50 py-12">
    <main id="app" class="max-w-3xl mx-auto px-6">
    </main>
    <script src="script.js"></script>
</body>
</html>
.card {
    background: white;
    border-radius: 12px;
    border: 1px solid #e2e8f0;
    transition: all 0.3s ease;
}
.card:hover {
    box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1);
    transform: translateY(-2px);
}
.btn-toggle {
    background-color: #f8fafc;
    transition: background 0.2s;
}
.btn-toggle:hover {
    background-color: #f1f5f9;
}
.hidden { display: none; }
const marcos = [
    {
        ano: "1970s",
        marco: "Modelo Cascata (Waterfall)",
        contexto: "Surgiu para trazer disciplina, organização e previsibilidade ao processo de desenvolvimento de sistemas, estruturando as etapas de forma sequencial.",
        desafio: "Dificuldade em lidar com mudanças durante o projeto, o que frequentemente gerava retrabalho, atrasos nos prazos e entregas que não atendiam totalmente às expectativas do cliente."
    },
    {
        ano: "2001",
        marco: "Manifesto Ágil",
        contexto: "Criado por um grupo de desenvolvedores para priorizar colaboração entre pessoas, comunicação constante e adaptação a mudanças, tornando o desenvolvimento de software mais flexível e centrado no cliente.",
        desafio: "Resolver problemas comuns dos modelos tradicionais, como falta de comunicação entre equipe e cliente, mudanças difíceis durante o projeto e entregas que não atendiam totalmente às expectativas do usuário."
    },
    {
        ano: "2010s",
        marco: "DevOps e Integração Contínua",
        contexto: "Surgiram para aproximar as equipes de desenvolvimento (Dev) e operações (Ops), automatizando processos de build, teste e implantação. Esse movimento também ampliou o uso de ferramentas de controle de versão como Git, facilitando o trabalho colaborativo e a entrega contínua de software.",
        desafio: "Reduzir problemas como versionamento confuso, conflitos de código entre desenvolvedores e ausência de testes automatizados, que frequentemente geravam falhas na integração e atrasos nas entregas."
    }
];

function renderizarLinhaDoTempo() {
    const app = document.getElementById('app');
    app.innerHTML = `
        <h1 class="text-4xl font-extrabold text-slate-900 mb-10 text-center">Linha do Tempo da Engenharia</h1>
        <div class="space-y-6">
            ${marcos.map((m, index) => `
                <div class="card overflow-hidden">
                    <button onclick="toggleDetails(${index})" class="w-full p-6 text-left btn-toggle">
                        <span class="text-xs font-bold text-blue-600 uppercase tracking-widest">${m.ano}</span>
                        <h2 class="text-xl font-bold text-slate-800">${m.marco}</h2>
                        <span id="icon-${index}" class="block text-slate-400 text-sm mt-2 font-medium">Ver detalhes ▼</span>
                    </button>
                    <div id="details-${index}" class="hidden p-6 border-t border-slate-100 bg-white">
                        <div class="mb-4">
                            <h4 class="font-bold text-slate-900 text-sm uppercase mb-1">Contexto</h4>
                            <p class="text-slate-600 leading-relaxed">${m.contexto}</p>
                        </div>
                        <div class="bg-red-50 p-4 rounded-lg border border-red-100">
                            <h4 class="font-bold text-red-800 text-sm uppercase mb-1">Desafio Real</h4>
                            <p class="text-red-700 leading-relaxed">${m.desafio}</p>
                        </div>
                    </div>
                </div>
            `).join('')}
        </div>
    `;
}

window.toggleDetails = function(index) {
    const element = document.getElementById(`details-${index}`);
    const icon = document.getElementById(`icon-${index}`);
    element.classList.toggle('hidden');
    icon.innerText = element.classList.contains('hidden') ? 'Ver detalhes ▼' : 'Ocultar detalhes ▲';
};

renderizarLinhaDoTempo();
