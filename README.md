<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atualizando o sistema...</title>
    <style>
        body {
            background-color: #000;
            color: #fff;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
            user-select: none;
            text-align: center;
        }
        .spinner {
            width: 50px;
            height: 50px;
            border: 5px solid rgba(255, 255, 255, 0.2);
            border-top: 5px solid #fff;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-bottom: 25px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        h1 {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 10px;
            padding: 0 20px;
        }
        p {
            font-size: 1rem;
            color: #888;
        }
        #troll-screen {
            display: none;
            font-size: 2.5rem;
            color: #00ff00;
            font-weight: bold;
            padding: 20px;
        }
    </style>
</head>
<body>

    <div id="update-container">
        <div class="spinner"></div>
        <h1 id="main-title">Atualizando o Android. Não desligue o dispositivo...</h1>
        <p id="percentage">Fazendo alterações: 1%</p>
    </div>

    <div id="troll-screen">
        😂 PEGADINHA DO MALANDRO! SEU CELULAR ESTÁ ÓTIMO! 😂
    </div>

    <script>
        let percent = 1;
        const textElement = document.getElementById("percentage");
        const mainTitle = document.getElementById("main-title");
        const updateContainer = document.getElementById("update-container");
        const trollScreen = document.getElementById("troll-screen");

        const frases = [
            "Apagando o histórico de navegação...",
            "Roubando suas figurinhas do WhatsApp...",
            "Baixando mais memória RAM...",
            "Quase lá, confia...",
            "Limpando a bagunça que você deixou..."
        ];

        const interval = setInterval(() => {
            if (percent < 100) {
                percent += Math.floor(Math.random() * 4) + 1;
                if (percent > 100) percent = 100;
                
                textElement.innerText = `Fazendo alterações: ${percent}%`;

                // Muda o texto principal em alguns pontos para zoar mais
                if (percent === 30) mainTitle.innerText = frases[0];
                if (percent === 50) mainTitle.innerText = frases[1];
                if (percent === 70) mainTitle.innerText = frases[2];
                if (percent === 90) mainTitle.innerText = frases[3];
                if (percent === 99) mainTitle.innerText = frases[4];

            } else {
                clearInterval(interval);
                // Esconde a tela de atualização e mostra a surpresa
                updateContainer.style.display = "none";
                trollScreen.style.display = "block";
            }
        }, 1200);

        // Ativa tela cheia ao tocar
        document.body.addEventListener("click", () => {
            if (!document.fullscreenElement) {
                document.documentElement.requestFullscreen().catch(() => {});
            }
        });
    </script>

</body>
</html>
