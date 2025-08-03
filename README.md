<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Rifa Online - Caroni Digital</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
      color: #333;
    }
    header {
      background: #4caf50;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      padding: 20px;
      max-width: 800px;
      margin: auto;
      background: white;
      border-radius: 10px;
    }
    .prize-img {
      width: 100%;
      max-height: 300px;
      object-fit: cover;
      border-radius: 10px;
    }
    .numbers {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 20px;
    }
    .number {
      width: 60px;
      height: 60px;
      background: #ddd;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
      cursor: pointer;
      font-weight: bold;
    }
    .number.selected {
      background: #4caf50;
      color: white;
    }
    .buy-button {
      margin-top: 20px;
      background: #4caf50;
      color: white;
      padding: 15px;
      border: none;
      width: 100%;
      font-size: 18px;
      cursor: pointer;
      border-radius: 8px;
    }
    .buy-button:hover {
      background: #45a049;
    }
  </style>
</head>
<body>

  <header>
    <h1>Rifa Online</h1>
    <p>Concorra a um <strong>PRÊMIO INCRÍVEL</strong> com apenas R$ 5,00!</p>
  </header>

  <div class="container">
    <img src="https://via.placeholder.com/800x300.png?text=PRÊMIO+DA+RIFA" alt="Prêmio" class="prize-img">
    
    <h2>Escolha seu(s) número(s):</h2>
    <div class="numbers" id="numbersContainer"></div>

    <button class="buy-button" onclick="buyNumbers()">Finalizar Compra via WhatsApp</button>
  </div>

  <!-- Botão flutuante WhatsApp -->
  <a href="https://wa.me/551497312602?text=Olá!%20Quero%20comprar%20números%20da%20rifa." style="position:fixed;bottom:20px;right:20px;background:#25d366;padding:15px;border-radius:50%;color:white;text-decoration:none;font-size:24px;" target="_blank">💬</a>

  <script>
    const numbersContainer = document.getElementById('numbersContainer');
    const selectedNumbers = [];

    for (let i = 1; i <= 50; i++) {
      const numDiv = document.createElement('div');
      numDiv.textContent = i;
      numDiv.classList.add('number');
      numDiv.addEventListener('click', () => {
        if (numDiv.classList.contains('selected')) {
          numDiv.classList.remove('selected');
          selectedNumbers.splice(selectedNumbers.indexOf(i), 1);
        } else {
          numDiv.classList.add('selected');
          selectedNumbers.push(i);
        }
      });
      numbersContainer.appendChild(numDiv);
    }

    function buyNumbers() {
      if (selectedNumbers.length === 0) {
        alert('Selecione ao menos 1 número.');
        return;
      }
      const mensagem = `Olá! Quero comprar os seguintes números da rifa: ${selectedNumbers.join(', ')}.`;
      const numero = "551497312602";
      const url = `https://wa.me/${numero}?text=${encodeURIComponent(mensagem)}`;
      window.open(url, '_blank');
    }
  </script>

</body>
</html>
