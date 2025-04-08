<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nosso Amor</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #fff0f5;
      margin: 0;
      padding: 20px;
      text-align: center;
    }
    h1 {
      color: #d63384;
    }
    .event {
      background: #ffffff;
      border-radius: 20px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      padding: 20px;
      margin: 20px auto;
      max-width: 400px;
    }
    .event-title {
      font-size: 1.4em;
      color: #6f42c1;
    }
    .event-subtitle {
      font-size: 1em;
      color: #555;
      margin-top: 5px;
      margin-bottom: 10px;
    }
    .event-date {
      color: #888;
    }
    .timer {
      margin-top: 10px;
      font-weight: bold;
      font-size: 1.2em;
    }
    .summary {
      margin-top: 40px;
      padding: 20px;
      background-color: #ffe6f0;
      border-radius: 20px;
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    .summary p {
      font-size: 1.1em;
      color: #444;
      margin: 10px 0;
    }
  </style>
</head>
<body>
  <h1>Nosso Amor em Cada Momento</h1>

  <div id="events"></div>
  <div class="summary" id="summary"></div>

  <script>
    const events = [
      { date: '2023-03-07', title: '🌧️☂️', subtitle: 'Caroninha na chuva' },
      { date: '2023-03-08', title: 'Não veio hoje?', subtitle: 'Primeira troca de mensagens' },
      { date: '2023-04-22', title: 'John Wick', subtitle: 'Primeiro encontro' },
      { date: '2023-05-05', title: '🙈😋', subtitle: 'Primeira visita em casa' },
      { date: '2023-05-18', title: 'Pedido de namoro', subtitle: 'Oficialização' },
      { date: '2023-06-03', title: '🏖️👩‍❤️‍👨', subtitle: 'Primeira viagem juntos' },
      { date: '2023-06-06', title: '💍👩‍❤️‍👨', subtitle: 'Começamos a usar alianças' },
      { date: '2023-10-13', title: '🏖️👩‍❤️‍👨', subtitle: 'Segunda viagem juntos' },
      { date: '2024-01-14', title: '🏠👩‍❤️‍👨', subtitle: 'Começamos a morar juntos' },
      { date: '2024-06-01', title: '🏖️🏃🏻🏃🏻‍♀️👩‍❤️‍👨', subtitle: 'Terceira viagem juntos' }
    ];

    function calcTimeAgo(dateStr) {
      const now = new Date();
      const past = new Date(dateStr);
      const diff = now - past;
      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((diff / (1000 * 60)) % 60);
      const seconds = Math.floor((diff / 1000) % 60);
      return `${days} dias, ${hours} horas, ${minutes} minutos e ${seconds} segundos atrás`;
    }

    const container = document.getElementById('events');
    events.forEach((event, index) => {
      const div = document.createElement('div');
      div.className = 'event';
      div.innerHTML = `
        <div class="event-title">${event.title}</div>
        <div class="event-subtitle">${event.subtitle}</div>
        <div class="event-date">${new Date(event.date).toLocaleDateString()}</div>
        <div class="timer" id="timer-${event.date}">${calcTimeAgo(event.date)}</div>
      `;
      container.appendChild(div);

      // Insere casamento após a terceira viagem juntos
      if (event.date === '2024-06-01') {
        const casamentoDiv = document.createElement('div');
        casamentoDiv.className = 'event';
        casamentoDiv.innerHTML = `
          <div class="event-title">💒👰🤵</div>
          <div class="event-subtitle">Nosso casamento</div>
          <div class="event-date">18/06/2025</div>
          <div class="timer" id="casamento-timer"></div>
        `;
        container.appendChild(casamentoDiv);
      }
    });

    function updateCasamentoTimer() {
      const casamento = new Date('2025-06-18T00:00:00');
      const agora = new Date();
      const el = document.getElementById('casamento-timer');
      if (!el) return;

      if (
        agora.getFullYear() === casamento.getFullYear() &&
        agora.getMonth() === casamento.getMonth() &&
        agora.getDate() === casamento.getDate()
      ) {
        el.textContent = '✨ É hoje! ✨';
      } else if (agora < casamento) {
        const diff = casamento - agora;
        const dias = Math.floor(diff / (1000 * 60 * 60 * 24));
        const horas = Math.floor((diff / (1000 * 60 * 60)) % 24);
        const minutos = Math.floor((diff / (1000 * 60)) % 60);
        const segundos = Math.floor((diff / 1000) % 60);
        el.textContent = `Faltam ${dias} dias, ${horas} horas, ${minutos} minutos e ${segundos} segundos para o nosso casamento 💖`;
      } else {
        el.textContent = calcTimeAgo('2025-06-18');
      }
    }

    setInterval(() => {
      events.forEach(event => {
        const el = document.getElementById(`timer-${event.date}`);
        if (el) el.textContent = calcTimeAgo(event.date);
      });
      updateCasamentoTimer();
    }, 1000);

    function showSummary() {
      const startDate = new Date('2023-03-07');
      const now = new Date();

function countOcurrences(day, month) {
  let count = 0;
  const start = new Date('2023-03-07');
  const end = new Date();
  for (let year = start.getFullYear(); year <= end.getFullYear(); year++) {
    const birthday = new Date(year, month, day);
    if (birthday >= start && birthday <= end) count++;
  }
  return count;
}

const aniversariosLucas = countOcurrences(18, 11); // 18 de dezembro
const aniversariosEla = countOcurrences(9, 9);     // 9 de outubro


      let anos = now.getFullYear() - startDate.getFullYear();
      let meses = now.getMonth() - startDate.getMonth();
      if (meses < 0) {
        anos--;
        meses += 12;
      }

      const summary = document.getElementById('summary');
      summary.innerHTML = `
        <p>🎂 Já vivemos <strong>${aniversariosLucas}</strong> aniversários meus juntos</p>
        <p>🎉 Já vivemos <strong>${aniversariosEla}</strong> aniversários seus juntos</p>
        <p>💞 Estamos fazendo parte da vida um do outro há <strong>${anos} anos e ${meses} mês(es)</strong></p>
      `;
    }

    showSummary();
    updateCasamentoTimer();
  </script>
</body>
</html>
