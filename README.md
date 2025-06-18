<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Extrator de Palavras-chave</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background: #ff66b2; /* Fundo rosa suave */
      color: #fff;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
      box-sizing: border-box;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 20px;
      color: #fff;
      text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
    }

    textarea {
      width: 80%;
      max-width: 600px;
      height: 200px;
      padding: 15px;
      font-size: 18px;
      background-color: #fff;
      color: #333;
      border: 2px solid #ff007f; /* Borda rosa vibrante */
      border-radius: 10px;
      margin-bottom: 20px;
      transition: border-color 0.3s ease;
    }

    textarea:focus {
      border-color: #ff66b2; /* Cor de borda rosa mais suave ao focar */
    }

    button {
      padding: 12px 25px;
      font-size: 18px;
      background-color: #ff007f; /* Rosa forte */
      color: #fff;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
    }

    button:hover {
      background-color: #ff66b2; /* Rosa suave no hover */
      transform: scale(1.05);
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4); /* Sombra mais intensa */
    }

    .resultado {
      margin-top: 30px;
      padding: 20px;
      background-color: #fff;
      border-radius: 10px;
      color: #333;
      width: 80%;
      max-width: 600px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1); /* Sombra suave nos resultados */
    }

    .palavra {
      display: inline-block;
      background: #ff99cc; /* Fundo rosa claro para as palavras */
      color: #ff007f; /* Texto rosa escuro */
      margin: 8px;
      padding: 8px 12px;
      border-radius: 12px;
      font-weight: bold;
      font-size: 1.1em;
      transition: transform 0.3s ease, background-color 0.3s ease, box-shadow 0.3s ease;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    }

    .palavra:hover {
      background-color: #ff66b2; /* Cor de fundo rosa suave no hover */
      transform: scale(1.1);
      color: #fff; /* Cor do texto muda para branco */
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3); /* Sombra mais forte ao passar o mouse */
    }

    .resultado h3 {
      font-size: 1.5em;
      color: #ff007f;
      margin-bottom: 15px;
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
 



