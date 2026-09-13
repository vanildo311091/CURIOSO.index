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
        h.1, p {
            text-align: center;
            padding: 0 20px;
        }
        h1 {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 10px;
        }
        p {
            font-size: 1rem;
            color: #888;
        }
    </style>
</head>
<body>

    <div class="spinner"></div>
    <h1>Atualizando o Android. Não desligue o dispositivo...</h1>
    <p id="percentage">Fazendo alterações: 1%</p>

    <script>
        let percent = 1;
        const textElement = document.getElementById("percentage");

        const interval = setInterval(() => {
            if (percent < 99) {
                percent += Math.floor(Math.random() * 3) + 1;
                if (percent > 99) percent = 99;
                textElement.innerText = `Fazendo alterações: ${percent}%`;
            } else {
                clearInterval(interval);
            }
        }, 1500);

        // Ativa o modo tela cheia ao tocar na tela (necessário em celulares)
        document.body.addEventListener("click", () => {
            if (!document.fullscreenElement) {
                document.documentElement.requestFullscreen().catch(() => {});
            }
        });
    </script>

</body>
</html>
