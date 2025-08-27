<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Algo especial...</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: #ff99cc; /* fundo rosa suave */
      overflow: hidden; /* impede scroll */
    }

    .container {
      background: rgba(255, 192, 203, 0.9);
      padding: 30px;
      border-radius: 25px;
      text-align: center;
      box-shadow: 0 0 25px rgba(255, 0, 100, 0.7);
      max-width: 500px;
      animation: pulse 3s infinite;
      position: relative;
      z-index: 2;
    }

    @keyframes pulse {
      0% { box-shadow: 0 0 15px rgba(255, 0, 100, 0.5); }
      50% { box-shadow: 0 0 40px rgba(255, 0, 100, 1); }
      100% { box-shadow: 0 0 15px rgba(255, 0, 100, 0.5); }
    }

    h1 {
      color: #ff0055;
      font-size: 1.8rem;
      margin-bottom: 20px;
    }

    button {
      font-size: 1rem;
      padding: 10px 20px;
      margin: 10px;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      transition: 0.3s;
    }

    #sim {
      background: #ff3366;
      color: white;
      box-shadow: 0 0 10px #ff6699;
    }

    #sim:hover {
      background: #ff6699;
      transform: scale(1.1);
    }

    #nao {
      background: #000 ;
      color: white;
      position: absolute;
    }

    .mensagem {
      display: none;
      margin-top: 20px;
      padding: 20px;
      background: #fff0f5;
      border: 2px solid #ff6699;
      border-radius: 20px;
      font-size: 1.2rem;
      color: #cc0066;
      font-style: italic;
      font-weight: bold;
      box-shadow: 0 0 15px rgba(255, 100, 150, 0.7);
      animation: aparecer 1.5s ease forwards;
    }

    @keyframes aparecer {
      from { opacity: 0; transform: scale(0.5); }
      to { opacity: 1; transform: scale(1); }
    }

    /* Animação de subir */
    .subir {
      position: fixed;
      bottom: 0;
      font-size: 2rem;
      animation: subir 4s linear forwards;
      z-index: 1;
    }

    @keyframes subir {
      from { transform: translateY(0) rotate(0deg); opacity: 1; }
      to { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Sophia, você aceita namorar comigo? 💖</h1>
    <button id="sim">Sim</button>
    <button id="nao">Não</button>
    <div class="mensagem" id="mensagem">
     Sabia que iria aceitar minha menina (Você não tinha muita escolha mesmo akakakakak), Enfim meu bem, Prometo te honrar, proteger, alegrar, compreender, e acima de tudo te apoiar, você é a garota mais importante em toda a minha vida e também meu maior presente, <b><i>Eu te amo minha borboletinha!</i></b>
    </div>
  </div>

  <script>
    const nao = document.getElementById("nao");
    const sim = document.getElementById("sim");
    const mensagem = document.getElementById("mensagem");

    // Botão "Não" foge do clique
    nao.addEventListener("mouseover", () => {
      const x = Math.floor(Math.random() * (window.innerWidth - nao.offsetWidth));
      const y = Math.floor(Math.random() * (window.innerHeight - nao.offsetHeight));
      nao.style.left = x + "px";
      nao.style.top = y + "px";
    });

    // Exibe mensagem e inicia animação de corações e borboletas
    sim.addEventListener("click", () => {
      mensagem.style.display = "block";
      nao.style.display = "none";

      setInterval(criarElemento, 600);
    });

    // Função para criar elementos alternando coração e borboleta
    function criarElemento() {
      const elementos = ["💖", "💗", "💞", "💝", "🦋"]; // corações brilhantes + borboleta
      const escolha = elementos[Math.floor(Math.random() * elementos.length)];

      const el = document.createElement("div");
      el.classList.add("subir");
      el.style.left = Math.random() * window.innerWidth + "px";
      el.innerHTML = escolha;

      document.body.appendChild(el);

      setTimeout(() => el.remove(), 4000);
    }
  </script>
</body>
</html>
