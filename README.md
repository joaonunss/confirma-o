<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Casamento Thayna & João</title>
  <style>
    body {
      font-family: 'Georgia', serif;
      background-color: #fff7f9;
      color: #5e2c40;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #ffdce5;
      text-align: center;
      padding: 50px 20px 30px;
    }

    header h1 {
      font-size: 2.5em;
      margin: 0;
    }

    header p {
      font-size: 1.2em;
      margin-top: 10px;
    }

    .container {
      max-width: 700px;
      margin: 0 auto;
      padding: 30px 20px;
      text-align: center;
    }

    .details {
      margin-top: 20px;
      font-size: 1.1em;
      line-height: 1.8;
    }

    form {
      margin-top: 30px;
    }

    input[type="text"] {
      padding: 10px;
      width: 80%;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 1em;
    }

    button {
      background-color: #d94f70;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      margin-left: 10px;
      cursor: pointer;
      font-weight: bold;
    }

    button:hover {
      background-color: #b63d5a;
    }

    .confirmados {
      margin-top: 40px;
      text-align: left;
    }

    .confirmados h3 {
      text-align: center;
      color: #5e2c40;
    }

    .confirmados ul {
      list-style: none;
      padding: 0;
    }

    .confirmados li {
      background-color: #ffdce5;
      padding: 10px;
      margin: 5px 0;
      border-radius: 5px;
    }

    footer {
      text-align: center;
      font-size: 0.9em;
      color: #aa667a;
      margin-top: 50px;
      padding-bottom: 20px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Thayna & João</h1>
    <p>Com o coração cheio de amor,<br> convidamos você para testemunhar o<br><strong>início da nossa nova jornada</strong>.</p>
  </header>

  <div class="container">
    <div class="details">
      <p><strong>📅 Data:</strong> Sábado, 18 de Outubro de 2025</p>
      <p><strong>⏰ Horário:</strong> 18:00 hrs</p>
      <p><strong>📍 Local:</strong> Churrascaria Tendall Grill - Aricanduva</p>
      <p><strong>📌 Endereço:</strong> Av. Aricanduva, 7997</p>
      <p><strong>🍽️ Rodízio:</strong> R$ 89,90 por pessoa</p>
    </div>

    <!-- Formulário de Confirmação -->
    <form id="confirmForm">
      <input type="text" id="nome" placeholder="Digite seu nome" required>
      <button type="submit">Confirmar Presença</button>
    </form>

    <!-- Lista de confirmados -->
    <div class="confirmados">
      <h3>Lista de Presenças Confirmadas</h3>
      <ul id="listaConfirmados"></ul>
    </div>
  </div>

  <footer>
    Com carinho, Thayna & João ❣️
  </footer>

  <script>
    const form = document.getElementById('confirmForm');
    const lista = document.getElementById('listaConfirmados');

    // Recupera do localStorage se tiver
    let confirmados = JSON.parse(localStorage.getItem('confirmados')) || [];

    // Renderiza a lista ao carregar
    function renderizarLista() {
      lista.innerHTML = '';
      confirmados.forEach(nome => {
        const li = document.createElement('li');
        li.textContent = nome;
        lista.appendChild(li);
      });
    }

    renderizarLista();

    // Ao enviar o formulário
    form.addEventListener('submit', function (e) {
      e.preventDefault();
      const nome = document.getElementById('nome').value.trim();
      if (nome && !confirmados.includes(nome)) {
        confirmados.push(nome);
        localStorage.setItem('confirmados', JSON.stringify(confirmados));
        renderizarLista();
        form.reset();
      }
    });
  </script>

</body>
</html>
