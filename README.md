<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Extrator de Palavras-chave</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
      background: #ff007f; /* fundo rosa neon */
      color: #fff;
    }
    h1 {
      text-align: center;
      color: #fff;
    }
    textarea {
      width: 100%;
      height: 200px;
      padding: 10px;
      font-size: 16px;
      resize: vertical;
      border: 2px solid #000; /* borda preta */
      background-color: #fff;
      color: #333;
      border-radius: 5px;
      margin-bottom: 20px;
    }
    button {
      padding: 10px 20px;
      margin-top: 10px;
      font-size: 16px;
      background-color: #ff66b2; /* rosa delicado */
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #ff3385; /* rosa mais escuro para o hover */
    }
    .resultado {
      margin-top: 20px;
      padding: 10px;
      background: #fff;
      color: #333;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .palavra {
      display: inline-block;
      background: #ff99cc; /* rosa claro para as palavras */
      margin: 4px;
      padding: 6px 10px;
      border-radius: 6px;
      font-weight: bold;
      color: #ff007f; /* letra em rosa neon */
    }
    .palavra:hover {
      background: #ff66b2; /* rosa delicado no hover */
      color: #fff; /* muda a cor do texto quando passa o mouse */
    }
  </style>
</head>
<body>
  <h1>Extrator de Palavras-chave</h1>
  <textarea id="texto" placeholder="Cole seu texto aqui..."></textarea>
  <br>
  <button onclick="extrairPalavrasChave()">Extrair</button>
  <div class="resultado" id="resultado"></div>

  <script>
    const stopwords = [
      'de', 'a', 'o', 'que', 'e', 'do', 'da', 'em', 'um', 'para', 'com', 'não', 'uma', 'os', 'no', 'se', 'na',
      'por', 'mais', 'as', 'dos', 'como', 'mas', 'foi', 'ao', 'ele', 'das', 'tem', 'isso', 'são', 'sua', 'ou', 'ser',
      'quando', 'muito', 'há', 'nos', 'já', 'está', 'eu', 'também', 'só', 'pelo', 'pela', 'até', 'isso', 'seu', 'sua',
      'me', 'te', 'nos', 'lhe', 'eles', 'elas', 'meu', 'minha', 'teu', 'tua', 'nosso', 'nossa', 'deles', 'delas'
    ];

    function extrairPalavrasChave() {
      const texto = document.getElementById('texto').value.toLowerCase();
      const palavras = texto.match(/\b[\wáéíóúãõç]+\b/g);
      const contagem = {};

      palavras?.forEach(palavra => {
        if (!stopwords.includes(palavra) && palavra.length > 2) {
          contagem[palavra] = (contagem[palavra] || 0) + 1;
        }
      });

      const resultadoDiv = document.getElementById('resultado');
      resultadoDiv.innerHTML = '<h3>Palavras-chave encontradas:</h3>';

      const palavrasOrdenadas = Object.entries(contagem)
        .sort((a, b) => b[1] - a[1])
        .slice(0, 20);

      palavrasOrdenadas.forEach(([palavra, freq]) => {
        const span = document.createElement('span');
        span.className = 'palavra';
        span.textContent = `${palavra} (${freq})`;
        resultadoDiv.appendChild(span);
      });
    }
  </script>
</body>
</html>



