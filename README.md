<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Gerador de Sacadas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 30px;
      background-color: #f5f5f5;
    }
    .controls {
      margin-bottom: 20px;
    }
    select, button {
      padding: 10px 15px;
      font-size: 16px;
      border-radius: 8px;
      border: none;
      margin: 5px;
      cursor: pointer;
    }
    button {
      background-color: #3498db;
      color: white;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #2980b9;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 15px;
      margin-top: 20px;
    }
    .card {
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      padding: 10px;
    }
    .card img {
      width: 100%;
      border-radius: 10px;
    }
  </style>
</head>
<body>

  <h1>Gerador de Sacadas de Casas</h1>

  <div class="controls">
    <label for="categoria">Escolha o estilo:</label>
    <select id="categoria">
      <option value="modern">Moderna</option>
      <option value="rustic">Rústica</option>
      <option value="classic">Clássica</option>
      <option value="minimalist">Minimalista</option>
    </select>
    <button onclick="gerarImagens()">Gerar Imagens</button>
  </div>

  <div class="grid" id="galeria"></div>

  <script>
    function gerarImagens() {
      const galeria = document.getElementById('galeria');
      galeria.innerHTML = ''; // Limpa a galeria
      const categoria = document.getElementById('categoria').value;
      const largura = 600;
      const altura = 400;
      const termos = `balcony,house,${categoria}`;

      for (let i = 0; i < 6; i++) {
        const random = Math.floor(Math.random() * 10000); // número aleatório
        const url = `https://source.unsplash.com/${largura}x${altura}/?${termos}&sig=${random}`;

        const card = document.createElement('div');
        card.className = 'card';

        const img = document.createElement('img');
        img.src = url;
        img.alt = `Sacada ${i+1}`;

        const btnDownload = document.createElement('a');
        btnDownload.href = url;
        btnDownload.download = `sacada_${i+1}.jpg`;
        btnDownload.innerText = 'Baixar';
        btnDownload.style.display = 'inline-block';
        btnDownload.style.marginTop = '10px';
        btnDownload.style.textDecoration = 'none';
        btnDownload.style.color = '#3498db';
        btnDownload.style.fontWeight = 'bold';

        card.appendChild(img);
        card.appendChild(btnDownload);
        galeria.appendChild(card);
      }
    }

    // Gera imagens automaticamente ao abrir
    gerarImagens();
  </script>

</body>
</html>
