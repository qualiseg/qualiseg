## Hi there 👋

<!--
**qualiseg/qualiseg** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
--><form action="enviar.php" method="POST">
  <label for="nome">Nome</label>
  <input type="text" id="nome" name="nome" required>

  <label for="email">E-mail</label>
  <input type="email" id="email" name="email" required>

  <label for="mensagem">Mensagem</label>
  <textarea id="mensagem" name="mensagem" rows="4" required></textarea>

  <button type="submit">Enviar Pedido</button>
</form>
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $nome = htmlspecialchars($_POST['nome']);
    $email = htmlspecialchars($_POST['email']);
    $mensagem = htmlspecialchars($_POST['mensagem']);

    $to = "seuemail@empresa.com"; // coloque aqui seu e-mail
    $subject = "Novo pedido de orçamento - $nome";
    $body = "Nome: $nome\nE-mail: $email\n\nMensagem:\n$mensagem";
    $headers = "From: $email";

    if (mail($to, $subject, $body, $headers)) {
        echo "Pedido enviado com sucesso!";
    } else {
        echo "Erro ao enviar. Tente novamente.";
    }
}
?>
<form id="orcamentoForm">
  <label for="nome">Nome</label>
  <input type="text" id="nome" name="nome" required>

  <label for="email">E-mail</label>
  <input type="email" id="email" name="email" required>

  <label for="mensagem">Mensagem</label>
  <textarea id="mensagem" name="mensagem" rows="4" required></textarea>

  <button type="submit">Enviar Pedido</button>
</form>

<script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
<script>
  emailjs.init("SEU_USER_ID");

  document.getElementById("orcamentoForm").addEventListener("submit", function(event) {
    event.preventDefault();

    emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID", this)
      .then(() => {
        alert("Pedido enviado com sucesso!");
        document.getElementById("orcamentoForm").reset();
      }, (error) => {
        alert("Erro ao enviar: " + JSON.stringify(error));
      });
  });
</script>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Monitoramento 24H</title>
  <style>
    body { margin: 0; font-family: Arial, sans-serif; background: #f7f7f7; color: #333; }
    header { background: #1e3a8a; color: white; padding: 1rem 2rem; display: flex; justify-content: space-between; align-items: center; }
    header nav a { margin-left: 1rem; color: white; text-decoration: none; }
    header nav a:hover { text-decoration: underline; }
    .hero { background: #1e40af; color: white; text-align: center; padding: 5rem 2rem; }
    .hero h2 { font-size: 2.5rem; margin-bottom: 1rem; }
    .hero p { font-size: 1.2rem; margin-bottom: 2rem; }
    .hero a button { background: #facc15; color: black; padding: 1rem 2rem; border: none; border-radius: 50px; font-weight: bold; cursor: pointer; }
    .hero a button:hover { background: #eab308; }
    .servicos { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.5rem; padding: 4rem 2rem; max-width: 1100px; margin: auto; }
    .card { background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
    .card h3 { margin-bottom: .5rem; }
    .orcamento { background: #e5e7eb; padding: 4rem 2rem; }
    .orcamento form { background: white; padding: 2rem; border-radius: 12px; max-width: 500px; margin: auto; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
    .orcamento label { display: block; margin-bottom: .5rem; font-weight: bold; }
    .orcamento input, .orcamento textarea { width: 100%; padding: .8rem; margin-bottom: 1rem; border: 1px solid #ccc; border-radius: 8px; }
    .orcamento button { background: #1d4ed8; color: white; padding: 1rem; border: none; border-radius: 8px; font-weight: bold; width: 100%; cursor: pointer; }
    .orcamento button:hover { background: #1e40af; }
    footer { background: #1e3a8a; color: white; text-align: center; padding: 1rem; margin-top: 2rem; }
  </style>
</head>
<body>

  <header>
    <h1>Monitoramento 24H</h1>
    <nav>
      <a href="#inicio">Início</a>
      <a href="#servicos">Serviços</a>
      <a href="#orcamento">Orçamento</a>
    </nav>
  </header>

  <section id="inicio" class="hero">
    <h2>Segurança e Monitoramento 24 horas</h2>
    <p>Proteção para sua empresa e residência com tecnologia de ponta.</p>
    <a href="#orcamento"><button>Solicitar Orçamento</button></a>
  </section>

  <section id="servicos" class="servicos">
    <div class="card">
      <h3>Monitoramento 24H</h3>
      <p>Acompanhamento em tempo real da sua residência ou empresa.</p>
    </div>
    <div class="card">
      <h3>Instalação de Câmeras</h3>
      <p>Câmeras de alta definição com acesso remoto.</p>
    </div>
    <div class="card">
      <h3>Alarmes e Sensores</h3>
      <p>Segurança completa com sensores de movimento e alarmes inteligentes.</p>
    </div>
  </section>

  <section id="orcamento" class="orcamento">
    <h2 style="text-align:center; margin-bottom: 1.5rem;">Solicite um Orçamento</h2>
    <form id="orcamentoForm">
      <label for="nome">Nome</label>
      <input type="text" id="nome" name="nome" required>

      <label for="email">E-mail</label>
      <input type="email" id="email" name="email" required>

      <label for="mensagem">Mensagem</label>
      <textarea id="mensagem" name="mensagem" rows="4" required></textarea>

      <button type="submit">Enviar Pedido</button>
    </form>
  </section>

  <footer>
    <p>© 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- EmailJS Script -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function() {
      emailjs.init("SEU_USER_ID"); // substitua pelo seu User ID
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(event) {
      event.preventDefault();

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID", this)
        .then(() => {
          alert("Pedido enviado com sucesso!");
          document.getElementById("orcamentoForm").reset();
        }, (error) => {
          alert("Erro ao enviar: " + JSON.stringify(error));
        });
    });
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Monitoramento 24H</title>
  <style>
    body { margin: 0; font-family: Arial, sans-serif; background: #f7f7f7; color: #333; }
    header { background: #1e3a8a; color: white; padding: 1rem 2rem; display: flex; justify-content: space-between; align-items: center; }
    header nav a { margin-left: 1rem; color: white; text-decoration: none; }
    header nav a:hover { text-decoration: underline; }
    .hero { background: #1e40af; color: white; text-align: center; padding: 5rem 2rem; }
    .hero h2 { font-size: 2.5rem; margin-bottom: 1rem; }
    .hero p { font-size: 1.2rem; margin-bottom: 2rem; }
    .hero a button { background: #facc15; color: black; padding: 1rem 2rem; border: none; border-radius: 50px; font-weight: bold; cursor: pointer; }
    .hero a button:hover { background: #eab308; }
    .servicos { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.5rem; padding: 4rem 2rem; max-width: 1100px; margin: auto; }
    .card { background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
    .card h3 { margin-bottom: .5rem; }
    .orcamento { background: #e5e7eb; padding: 4rem 2rem; }
    .orcamento form { background: white; padding: 2rem; border-radius: 12px; max-width: 500px; margin: auto; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
    .orcamento label { display: block; margin-bottom: .5rem; font-weight: bold; }
    .orcamento input, .orcamento textarea { width: 100%; padding: .8rem; margin-bottom: 1rem; border: 1px solid #ccc; border-radius: 8px; }
    .orcamento button { background: #1d4ed8; color: white; padding: 1rem; border: none; border-radius: 8px; font-weight: bold; width: 100%; cursor: pointer; }
    .orcamento button:hover { background: #1e40af; }
    footer { background: #1e3a8a; color: white; text-align: center; padding: 1rem; margin-top: 2rem; }
  </style>
</head>
<body>

  <header>
    <h1>Monitoramento 24H</h1>
    <nav>
      <a href="#inicio">Início</a>
      <a href="#servicos">Serviços</a>
      <a href="#orcamento">Orçamento</a>
    </nav>
  </header>

  <section id="inicio" class="hero">
    <h2>Segurança e Monitoramento 24 horas</h2>
    <p>Proteção para sua empresa e residência com tecnologia de ponta.</p>
    <a href="#orcamento"><button>Solicitar Orçamento</button></a>
  </section>

  <section id="servicos" class="servicos">
    <div class="card">
      <h3>Monitoramento 24H</h3>
      <p>Acompanhamento em tempo real da sua residência ou empresa.</p>
    </div>
    <div class="card">
      <h3>Instalação de Câmeras</h3>
      <p>Câmeras de alta definição com acesso remoto.</p>
    </div>
    <div class="card">
      <h3>Alarmes e Sensores</h3>
      <p>Segurança completa com sensores de movimento e alarmes inteligentes.</p>
    </div>
  </section>

  <section id="orcamento" class="orcamento">
    <h2 style="text-align:center; margin-bottom: 1.5rem;">Solicite um Orçamento</h2>
    <form id="orcamentoForm">
      <label for="from_name">Nome</label>
      <input type="text" id="from_name" name="from_name" required>

      <label for="reply_to">E-mail</label>
      <input type="email" id="reply_to" name="reply_to" required>

      <label for="message">Mensagem</label>
      <textarea id="message" name="message" rows="4" required></textarea>

      <button type="submit">Enviar Pedido</button>
    </form>
  </section>

  <footer>
    <p>© 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- EmailJS Script -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function() {
      emailjs.init("SEU_USER_ID"); // substitua pelo seu User ID
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(event) {
      event.preventDefault();

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID", this)
        .then(() => {
          alert("Pedido enviado com sucesso!");
          document.getElementById("orcamentoForm").reset();
        }, (error) => {
          alert("Erro ao enviar: " + JSON.stringify(error));
        });
    });
  </script>
</body>
</html>
Novo pedido de orçamento - {{from_name}}
📌 Você recebeu um novo pedido de orçamento!

👤 Nome: {{from_name}}
📧 E-mail: {{reply_to}}

📝 Mensagem:
{{message}}

---
Este e-mail foi enviado automaticamente pelo site de Monitoramento 24H.
Recebemos seu pedido de orçamento - Monitoramento 24H
Olá {{from_name}},

Obrigado por entrar em contato com a Monitoramento 24H! ✅

Recebemos sua solicitação de orçamento com a seguinte mensagem:
---
{{message}}
---

Nossa equipe entrará em contato com você em breve através do e-mail {{reply_to}}.

Atenciosamente,  
Equipe Monitoramento 24H
document.getElementById("orcamentoForm").addEventListener("submit", function(event) {
  event.preventDefault();

  // Envia para você
  emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID", this)
    .then(() => {
      // Envia auto-reply para o cliente
      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_AUTO_REPLY_ID", this);

      alert("Pedido enviado com sucesso! Você receberá uma confirmação por e-mail.");
      document.getElementById("orcamentoForm").reset();
    }, (error) => {
      alert("Erro ao enviar: " + JSON.stringify(error));
    });
});
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Monitoramento 24H</title>
  <style>
    body { margin: 0; font-family: Arial, sans-serif; background: #f7f7f7; color: #333; }
    header { background: #1e3a8a; color: white; padding: 1rem 2rem; display: flex; justify-content: space-between; align-items: center; }
    header nav a { margin-left: 1rem; color: white; text-decoration: none; }
    header nav a:hover { text-decoration: underline; }
    .hero { background: #1e40af; color: white; text-align: center; padding: 5rem 2rem; }
    .hero h2 { font-size: 2.5rem; margin-bottom: 1rem; }
    .hero p { font-size: 1.2rem; margin-bottom: 2rem; }
    .hero a button { background: #facc15; color: black; padding: 1rem 2rem; border: none; border-radius: 50px; font-weight: bold; cursor: pointer; }
    .hero a button:hover { background: #eab308; }
    .servicos { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.5rem; padding: 4rem 2rem; max-width: 1100px; margin: auto; }
    .card { background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
    .card h3 { margin-bottom: .5rem; }
    .orcamento { background: #e5e7eb; padding: 4rem 2rem; }
    .orcamento form { background: white; padding: 2rem; border-radius: 12px; max-width: 500px; margin: auto; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
    .orcamento label { display: block; margin-bottom: .5rem; font-weight: bold; }
    .orcamento input, .orcamento textarea { width: 100%; padding: .8rem; margin-bottom: 1rem; border: 1px solid #ccc; border-radius: 8px; }
    .orcamento button { background: #1d4ed8; color: white; padding: 1rem; border: none; border-radius: 8px; font-weight: bold; width: 100%; cursor: pointer; }
    .orcamento button:hover { background: #1e40af; }
    footer { background: #1e3a8a; color: white; text-align: center; padding: 1rem; margin-top: 2rem; }
  </style>
</head>
<body>

  <header>
    <h1>Monitoramento 24H</h1>
    <nav>
      <a href="#inicio">Início</a>
      <a href="#servicos">Serviços</a>
      <a href="#orcamento">Orçamento</a>
    </nav>
  </header>

  <section id="inicio" class="hero">
    <h2>Segurança e Monitoramento 24 horas</h2>
    <p>Proteção para sua empresa e residência com tecnologia de ponta.</p>
    <a href="#orcamento"><button>Solicitar Orçamento</button></a>
  </section>

  <section id="servicos" class="servicos">
    <div class="card">
      <h3>Monitoramento 24H</h3>
      <p>Acompanhamento em tempo real da sua residência ou empresa.</p>
    </div>
    <div class="card">
      <h3>Instalação de Câmeras</h3>
      <p>Câmeras de alta definição com acesso remoto.</p>
    </div>
    <div class="card">
      <h3>Alarmes e Sensores</h3>
      <p>Segurança completa com sensores de movimento e alarmes inteligentes.</p>
    </div>
  </section>

  <section id="orcamento" class="orcamento">
    <h2 style="text-align:center; margin-bottom: 1.5rem;">Solicite um Orçamento</h2>
    <form id="orcamentoForm">
      <label for="from_name">Nome</label>
      <input type="text" id="from_name" name="from_name" required>

      <label for="reply_to">E-mail</label>
      <input type="email" id="reply_to" name="reply_to" required>

      <label for="message">Mensagem</label>
      <textarea id="message" name="message" rows="4" required></textarea>

      <button type="submit">Enviar Pedido</button>
    </form>
  </section>

  <footer>
    <p>© 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- EmailJS Script -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function() {
      emailjs.init("SEU_USER_ID"); // substitua pelo seu User ID
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(event) {
      event.preventDefault();

      // Envia o pedido para você
      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID", this)
        .then(() => {
          // Envia a resposta automática para o cliente
          emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_AUTO_REPLY_ID", this);

          alert("Pedido enviado com sucesso! Você receberá uma confirmação por e-mail.");
          document.getElementById("orcamentoForm").reset();
        }, (error) => {
          alert("Erro ao enviar: " + JSON.stringify(error));
        });
    });
  </script>
</body>
</html>📌 Novo pedido de orçamento - {{from_name}}
Você recebeu um novo pedido de orçamento no site Monitoramento 24H 🚨

👤 Nome: {{from_name}}
📧 E-mail: {{reply_to}}

📝 Mensagem:
{{message}}

---
Este e-mail foi enviado automaticamente pelo formulário do site.
✅ Recebemos seu pedido de orçamento - Monitoramento 24H
Olá {{from_name}},

Obrigado por entrar em contato com a Monitoramento 24H! 🔐

Recebemos sua solicitação com a seguinte mensagem:
---
{{message}}
---

📌 Em breve nossa equipe retornará no e-mail: {{reply_to}}

Atenciosamente,  
Equipe Monitoramento 24H
📌 Novo pedido de orçamento - {{from_name}}
<div style="font-family: Arial, sans-serif; max-width: 600px; margin: auto; background: #f9f9f9; padding: 20px; border-radius: 10px; border: 1px solid #ddd;">
  <div style="text-align: center; margin-bottom: 20px;">
    <img src="URL_DA_SUA_LOGO" alt="Monitoramento 24H" style="max-width: 150px;">
    <h2 style="color: #1e3a8a;">Novo Pedido de Orçamento 🚨</h2>
  </div>

  <p><strong>👤 Nome:</strong> {{from_name}}</p>
  <p><strong>📧 E-mail:</strong> {{reply_to}}</p>
  <p><strong>📝 Mensagem:</strong></p>
  <div style="background: #fff; padding: 15px; border-radius: 8px; border: 1px solid #ddd; margin-bottom: 20px;">
    {{message}}
  </div>

  <hr>
  <p style="font-size: 12px; color: #666; text-align: center;">
    Este e-mail foi enviado automaticamente pelo site <strong>Monitoramento 24H</strong>.
  </p>
</div>✅ Recebemos seu pedido de orçamento - Monitoramento 24H
<div style="font-family: Arial, sans-serif; max-width: 600px; margin: auto; background: #f9f9f9; padding: 20px; border-radius: 10px; border: 1px solid #ddd;">
  <div style="text-align: center; margin-bottom: 20px;">
    <img src="URL_DA_SUA_LOGO" alt="Monitoramento 24H" style="max-width: 150px;">
    <h2 style="color: #16a34a;">Pedido de Orçamento Recebido ✅</h2>
  </div>

  <p>Olá <strong>{{from_name}}</strong>,</p>
  <p>Obrigado por entrar em contato com a <strong>Monitoramento 24H</strong>! 🔐</p>

  <p>Recebemos sua mensagem:</p>
  <div style="background: #fff; padding: 15px; border-radius: 8px; border: 1px solid #ddd; margin-bottom: 20px;">
    {{message}}
  </div>

  <p>📌 Em breve nossa equipe retornará no e-mail: <strong>{{reply_to}}</strong></p>

  <p style="margin-top: 30px;">Atenciosamente,<br><strong>Equipe Monitoramento 24H</strong></p>

  <hr>
  <p style="font-size: 12px; color: #666; text-align: center;">
    Este e-mail foi enviado automaticamente pelo site <strong>Monitoramento 24H</strong>.
  </p>
</div>🚨 Novo pedido de orçamento - {{from_name}}
<div style="font-family: Arial, sans-serif; max-width: 650px; margin: auto; background: #fff4f4; padding: 20px; border-radius: 12px; border: 2px solid #dc2626;">
  <div style="text-align: center; margin-bottom: 20px;">
    <img src="URL_DA_SUA_LOGO" alt="Monitoramento 24H" style="max-width: 150px; margin-bottom: 10px;">
    <h2 style="color: #dc2626; margin: 0;">🚨 Novo Pedido de Orçamento</h2>
  </div>

  <p><strong>👤 Nome:</strong> {{from_name}}</p>
  <p><strong>📧 E-mail:</strong> {{reply_to}}</p>
  <p><strong>📝 Mensagem:</strong></p>
  <div style="background: #fff; padding: 15px; border-radius: 8px; border: 1px solid #f87171; margin-bottom: 20px;">
    {{message}}
  </div>

  <p style="color: #b91c1c; font-size: 14px;"><strong>Atenção:</strong> Responda esse cliente o mais rápido possível.</p>

  <hr style="margin: 20px 0; border: none; border-top: 1px solid #fca5a5;">
  <p style="font-size: 12px; color: #666; text-align: center;">
    Este e-mail foi enviado automaticamente pelo site <strong>Monitoramento 24H</strong>.
  </p>
</div>
✅ Recebemos seu pedido de orçamento - Monitoramento 24H
<div style="font-family: Arial, sans-serif; max-width: 650px; margin: auto; background: #f0fdf4; padding: 20px; border-radius: 12px; border: 2px solid #16a34a;">
  <div style="text-align: center; margin-bottom: 20px;">
    <img src="URL_DA_SUA_LOGO" alt="Monitoramento 24H" style="max-width: 150px; margin-bottom: 10px;">
    <h2 style="color: #15803d; margin: 0;">✅ Pedido Recebido com Sucesso</h2>
  </div>

  <p>Olá <strong>{{from_name}}</strong>,</p>
  <p>Obrigado por entrar em contato com a <strong>Monitoramento 24H</strong>! 🔐</p>

  <p>Recebemos sua mensagem:</p>
  <div style="background: #fff; padding: 15px; border-radius: 8px; border: 1px solid #86efac; margin-bottom: 20px;">
    {{message}}
  </div>

  <p>📌 Em breve nossa equipe retornará no e-mail: <strong>{{reply_to}}</strong></p>

  <p style="margin-top: 30px;">Atenciosamente,<br><strong>Equipe Monitoramento 24H</strong></p>

  <hr style="margin: 20px 0; border: none; border-top: 1px solid #bbf7d0;">
  <p style="font-size: 12px; color: #666; text-align: center;">
    Este e-mail foi enviado automaticamente pelo site <strong>Monitoramento 24H</strong>.
  </p>
</div>
🚨 Novo pedido de orçamento - {{from_name}}
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Novo Pedido de Orçamento</title>
</head>
<body style="margin:0; padding:0; font-family: Arial, sans-serif; background-color:#f9fafb;">
  <table align="center" width="100%" cellspacing="0" cellpadding="0" style="max-width:650px; margin:auto; background:#fff4f4; border:2px solid #dc2626; border-radius:12px;">
    <tr>
      <td style="text-align:center; padding:20px;">
        <img src="URL_DA_SUA_LOGO" alt="Monitoramento 24H" style="max-width:150px; margin-bottom:10px;">
        <h2 style="color:#dc2626; margin:0;">🚨 Novo Pedido de Orçamento</h2>
      </td>
    </tr>
    <tr>
      <td style="padding:20px;">
        <p><strong>👤 Nome:</strong> {{from_name}}</p>
        <p><strong>📧 E-mail:</strong> {{reply_to}}</p>
        <p><strong>📝 Mensagem:</strong></p>
        <table width="100%" style="background:#fff; border:1px solid #f87171; border-radius:8px; margin:15px 0;">
          <tr>
            <td style="padding:15px; color:#333;">{{message}}</td>
          </tr>
        </table>
        <p style="color:#b91c1c; font-size:14px;"><strong>Atenção:</strong> Responda esse cliente o mais rápido possível.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:center; font-size:12px; color:#666; padding:15px; border-top:1px solid #fca5a5;">
        Este e-mail foi enviado automaticamente pelo site <strong>Monitoramento 24H</strong>.
      </td>
    </tr>
  </table>
</body>
</html>
✅ Recebemos seu pedido de orçamento - Monitoramento 24H
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Confirmação de Orçamento</title>
</head>
<body style="margin:0; padding:0; font-family: Arial, sans-serif; background-color:#f9fafb;">
  <table align="center" width="100%" cellspacing="0" cellpadding="0" style="max-width:650px; margin:auto; background:#f0fdf4; border:2px solid #16a34a; border-radius:12px;">
    <tr>
      <td style="text-align:center; padding:20px;">
        <img src="URL_DA_SUA_LOGO" alt="Monitoramento 24H" style="max-width:150px; margin-bottom:10px;">
        <h2 style="color:#15803d; margin:0;">✅ Pedido Recebido com Sucesso</h2>
      </td>
    </tr>
    <tr>
      <td style="padding:20px; color:#333;">
        <p>Olá <strong>{{from_name}}</strong>,</p>
        <p>Obrigado por entrar em contato com a <strong>Monitoramento 24H</strong>! 🔐</p>
        <p>Recebemos sua mensagem:</p>
        <table width="100%" style="background:#fff; border:1px solid #86efac; border-radius:8px; margin:15px 0;">
          <tr>
            <td style="padding:15px;">{{message}}</td>
          </tr>
        </table>
        <p>📌 Em breve nossa equipe retornará no e-mail: <strong>{{reply_to}}</strong></p>
        <p style="margin-top:30px;">Atenciosamente,<br><strong>Equipe Monitoramento 24H</strong></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:center; font-size:12px; color:#666; padding:15px; border-top:1px solid #bbf7d0;">
        Este e-mail foi enviado automaticamente pelo site <strong>Monitoramento 24H</strong>.
      </td>
    </tr>
  </table>
</body>
</html><!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f3f4f6; }
    header { background:#1e3a8a; color:white; text-align:center; padding:20px; }
    nav { background:#111827; padding:10px; text-align:center; }
    nav a { color:white; margin:0 15px; text-decoration:none; font-weight:bold; }
    section { padding:40px 20px; max-width:800px; margin:auto; background:white; margin-top:20px; border-radius:12px; box-shadow:0 2px 10px rgba(0,0,0,0.1); }
    form input, form textarea { width:100%; padding:12px; margin:8px 0; border:1px solid #ccc; border-radius:8px; }
    form button { background:#1e3a8a; color:white; padding:12px; border:none; border-radius:8px; cursor:pointer; font-size:16px; font-weight:bold; }
    form button:hover { background:#2563eb; }
    footer { background:#111827; color:white; text-align:center; padding:15px; margin-top:30px; }
  </style>
</head>
<body>
  <header>
    <h1>Monitoramento 24H</h1>
    <p>Segurança e tranquilidade 24 horas por dia</p>
  </header>

  <nav>
    <a href="#sobre">Sobre Nós</a>
    <a href="#servicos">Serviços</a>
    <a href="#orcamento">Solicitar Orçamento</a>
  </nav>

  <section id="sobre">
    <h2>Sobre Nós</h2>
    <p>Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
  </section>

  <section id="servicos">
    <h2>Nossos Serviços</h2>
    <ul>
      <li>Monitoramento de alarmes</li>
      <li>Rastreamento de veículos</li>
      <li>CFTV - Câmeras de segurança</li>
      <li>Equipe de pronta resposta</li>
    </ul>
  </section>

  <section id="orcamento">
    <h2>Solicite um Orçamento</h2>
    <form id="orcamentoForm">
      <input type="text" name="from_name" placeholder="Seu nome" required>
      <input type="email" name="reply_to" placeholder="Seu e-mail" required>
      <textarea name="message" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      <button type="submit">Enviar</button>
    </form>
    <p id="statusMsg" style="margin-top:10px; font-weight:bold;"></p>
  </section>

  <footer>
    <p>&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      // Enviar para você (orçamento)
      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          // Enviar resposta automática para cliente
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

  <!-- Header -->
  <header class="bg-primary text-white text-center py-4">
    <h1 class="mb-1">Monitoramento 24H</h1>
    <p class="mb-0">Segurança e tranquilidade 24 horas por dia</p>
  </header>

  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
      <a class="navbar-brand" href="#">Monitoramento</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu" aria-controls="menu" aria-expanded="false" aria-label="Menu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#servicos">Serviços</a></li>
          <li class="nav-item"><a class="nav-link" href="#orcamento">Orçamento</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Sobre -->
  <section id="sobre" class="container my-5">
    <div class="text-center">
      <h2>Sobre Nós</h2>
      <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="container my-5">
    <div class="text-center">
      <h2>Nossos Serviços</h2>
    </div>
    <div class="row mt-4">
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🔔 Monitoramento de Alarmes</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚗 Rastreamento de Veículos</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🎥 Câmeras de Segurança (CFTV)</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚓 Equipe de Pronta Resposta</h5>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="container my-5">
    <div class="text-center">
      <h2>Solicite um Orçamento</h2>
      <p class="text-muted">Preencha o formulário abaixo e entraremos em contato com você.</p>
    </div>
    <form id="orcamentoForm" class="p-4 shadow rounded bg-light mt-3">
      <div class="mb-3">
        <label class="form-label">Nome</label>
        <input type="text" name="from_name" class="form-control" placeholder="Seu nome" required>
      </div>
      <div class="mb-3">
        <label class="form-label">E-mail</label>
        <input type="email" name="reply_to" class="form-control" placeholder="Seu e-mail" required>
      </div>
      <div class="mb-3">
        <label class="form-label">Mensagem</label>
        <textarea name="message" class="form-control" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      </div>
      <button type="submit" class="btn btn-primary w-100">Enviar Orçamento</button>
      <p id="statusMsg" class="mt-3 fw-bold"></p>
    </form>
  </section>

  <!-- Footer -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      // Envia para você (orçamento)
      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          // Envia resposta automática para o cliente
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    .carousel-item img {
      height: 500px;
      object-fit: cover;
    }
  </style>
</head>
<body>

  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand fw-bold" href="#">Monitoramento 24H</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu" aria-controls="menu" aria-expanded="false" aria-label="Menu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#servicos">Serviços</a></li>
          <li class="nav-item"><a class="nav-link" href="#orcamento">Orçamento</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Carousel -->
  <div id="bannerCarousel" class="carousel slide mt-5" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="https://source.unsplash.com/1200x500/?security,camera" class="d-block w-100" alt="Segurança 24H">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Monitoramento 24 Horas</h3>
          <p>Sua segurança em boas mãos, dia e noite.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?cctv,building" class="d-block w-100" alt="Câmeras de Segurança">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>CFTV e Alarmes</h3>
          <p>Tecnologia avançada para proteger sua residência ou empresa.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?security,team" class="d-block w-100" alt="Equipe de Pronta Resposta">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Equipe de Pronta Resposta</h3>
          <p>Intervenção rápida em caso de emergência.</p>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#bannerCarousel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#bannerCarousel" data-bs-slide="next">
      <span class="carousel-control-next-icon"></span>
    </button>
  </div>

  <!-- Sobre -->
  <section id="sobre" class="container my-5">
    <div class="text-center">
      <h2>Sobre Nós</h2>
      <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="container my-5">
    <div class="text-center">
      <h2>Nossos Serviços</h2>
    </div>
    <div class="row mt-4">
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🔔 Monitoramento de Alarmes</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚗 Rastreamento de Veículos</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🎥 Câmeras de Segurança (CFTV)</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚓 Equipe de Pronta Resposta</h5>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="container my-5">
    <div class="text-center">
      <h2>Solicite um Orçamento</h2>
      <p class="text-muted">Preencha o formulário abaixo e entraremos em contato com você.</p>
    </div>
    <form id="orcamentoForm" class="p-4 shadow rounded bg-light mt-3">
      <div class="mb-3">
        <label class="form-label">Nome</label>
        <input type="text" name="from_name" class="form-control" placeholder="Seu nome" required>
      </div>
      <div class="mb-3">
        <label class="form-label">E-mail</label>
        <input type="email" name="reply_to" class="form-control" placeholder="Seu e-mail" required>
      </div>
      <div class="mb-3">
        <label class="form-label">Mensagem</label>
        <textarea name="message" class="form-control" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      </div>
      <button type="submit" class="btn btn-primary w-100">Enviar Orçamento</button>
      <p id="statusMsg" class="mt-3 fw-bold"></p>
    </form>
  </section>

  <!-- Footer -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      // Envia para você (orçamento)
      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          // Envia resposta automática para o cliente
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    .carousel-item img {
      height: 500px;
      object-fit: cover;
    }
    /* Botão WhatsApp */
    .whatsapp-float {
      position: fixed;
      width: 60px;
      height: 60px;
      bottom: 20px;
      right: 20px;
      background-color: #25d366;
      color: #fff;
      border-radius: 50%;
      text-align: center;
      font-size: 30px;
      box-shadow: 2px 2px 8px rgba(0,0,0,0.3);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.2s;
    }
    .whatsapp-float:hover {
      transform: scale(1.1);
      color: #fff;
    }
  </style>
  <!-- Ícones -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
</head>
<body>

  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand fw-bold" href="#">Monitoramento 24H</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu" aria-controls="menu" aria-expanded="false" aria-label="Menu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#servicos">Serviços</a></li>
          <li class="nav-item"><a class="nav-link" href="#orcamento">Orçamento</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Carousel -->
  <div id="bannerCarousel" class="carousel slide mt-5" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="https://source.unsplash.com/1200x500/?security,camera" class="d-block w-100" alt="Segurança 24H">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Monitoramento 24 Horas</h3>
          <p>Sua segurança em boas mãos, dia e noite.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?cctv,building" class="d-block w-100" alt="Câmeras de Segurança">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>CFTV e Alarmes</h3>
          <p>Tecnologia avançada para proteger sua residência ou empresa.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?security,team" class="d-block w-100" alt="Equipe de Pronta Resposta">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Equipe de Pronta Resposta</h3>
          <p>Intervenção rápida em caso de emergência.</p>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#bannerCarousel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#bannerCarousel" data-bs-slide="next">
      <span class="carousel-control-next-icon"></span>
    </button>
  </div>

  <!-- Sobre -->
  <section id="sobre" class="container my-5">
    <div class="text-center">
      <h2>Sobre Nós</h2>
      <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="container my-5">
    <div class="text-center">
      <h2>Nossos Serviços</h2>
    </div>
    <div class="row mt-4">
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🔔 Monitoramento de Alarmes</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚗 Rastreamento de Veículos</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🎥 Câmeras de Segurança (CFTV)</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚓 Equipe de Pronta Resposta</h5>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="container my-5">
    <div class="text-center">
      <h2>Solicite um Orçamento</h2>
      <p class="text-muted">Preencha o formulário abaixo e entraremos em contato com você.</p>
    </div>
    <form id="orcamentoForm" class="p-4 shadow rounded bg-light mt-3">
      <div class="mb-3">
        <label class="form-label">Nome</label>
        <input type="text" name="from_name" class="form-control" placeholder="Seu nome" required>
      </div>
      <div class="mb-3">
        <label class="form-label">E-mail</label>
        <input type="email" name="reply_to" class="form-control" placeholder="Seu e-mail" required>
      </div>
      <div class="mb-3">
        <label class="form-label">Mensagem</label>
        <textarea name="message" class="form-control" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      </div>
      <button type="submit" class="btn btn-primary w-100">Enviar Orçamento</button>
      <p id="statusMsg" class="mt-3 fw-bold"></p>
    </form>
  </section>

  <!-- Footer -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Botão WhatsApp -->
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     class="whatsapp-float" target="_blank">
    <i class="fab fa-whatsapp"></i>
  </a>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<section id="sobre" class="container my-5">
  <div class="text-center">
    <h2>Sobre Nós</h2>
    <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
  </div>

  <!-- Google Maps -->
  <div class="mt-4">
    <iframe 
      src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3656.510403190348!2d-46.6333091850213!3d-23.5880164846696!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94ce59c7b1b1b1%3A0x123456789abcdef!2sSua%20Empresa%20Aqui!5e0!3m2!1spt-BR!2sbr!4v1700000000000!5m2!1spt-BR!2sbr" 
      width="100%" 
      height="350" 
      style="border:0; border-radius:12px;" 
      allowfullscreen="" 
      loading="lazy" 
      referrerpolicy="no-referrer-when-downgrade">
    </iframe>
  </div>
</section>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    .carousel-item img {
      height: 500px;
      object-fit: cover;
    }
    /* Botão WhatsApp */
    .whatsapp-float {
      position: fixed;
      width: 60px;
      height: 60px;
      bottom: 20px;
      right: 20px;
      background-color: #25d366;
      color: #fff;
      border-radius: 50%;
      text-align: center;
      font-size: 30px;
      box-shadow: 2px 2px 8px rgba(0,0,0,0.3);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.2s;
    }
    .whatsapp-float:hover {
      transform: scale(1.1);
      color: #fff;
    }
  </style>
  <!-- Ícones -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
</head>
<body>

  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand fw-bold" href="#">Monitoramento 24H</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu" aria-controls="menu" aria-expanded="false" aria-label="Menu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#servicos">Serviços</a></li>
          <li class="nav-item"><a class="nav-link" href="#orcamento">Orçamento</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Carousel -->
  <div id="bannerCarousel" class="carousel slide mt-5" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="https://source.unsplash.com/1200x500/?security,camera" class="d-block w-100" alt="Segurança 24H">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Monitoramento 24 Horas</h3>
          <p>Sua segurança em boas mãos, dia e noite.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?cctv,building" class="d-block w-100" alt="Câmeras de Segurança">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>CFTV e Alarmes</h3>
          <p>Tecnologia avançada para proteger sua residência ou empresa.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?security,team" class="d-block w-100" alt="Equipe de Pronta Resposta">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Equipe de Pronta Resposta</h3>
          <p>Intervenção rápida em caso de emergência.</p>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#bannerCarousel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#bannerCarousel" data-bs-slide="next">
      <span class="carousel-control-next-icon"></span>
    </button>
  </div>

  <!-- Sobre -->
  <section id="sobre" class="container my-5">
    <div class="text-center">
      <h2>Sobre Nós</h2>
      <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
    </div>

    <!-- Google Maps -->
    <div class="mt-4">
      <iframe 
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3656.510403190348!2d-46.6333091850213!3d-23.5880164846696!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94ce59c7b1b1b1%3A0x123456789abcdef!2sSua%20Empresa%20Aqui!5e0!3m2!1spt-BR!2sbr!4v1700000000000!5m2!1spt-BR!2sbr" 
        width="100%" 
        height="350" 
        style="border:0; border-radius:12px;" 
        allowfullscreen="" 
        loading="lazy" 
        referrerpolicy="no-referrer-when-downgrade">
      </iframe>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="container my-5">
    <div class="text-center">
      <h2>Nossos Serviços</h2>
    </div>
    <div class="row mt-4">
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🔔 Monitoramento de Alarmes</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚗 Rastreamento de Veículos</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🎥 Câmeras de Segurança (CFTV)</h5>
          </div>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm">
          <div class="card-body text-center">
            <h5 class="card-title">🚓 Equipe de Pronta Resposta</h5>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="container my-5">
    <div class="text-center">
      <h2>Solicite um Orçamento</h2>
      <p class="text-muted">Preencha o formulário abaixo e entraremos em contato com você.</p>
    </div>
    <form id="orcamentoForm" class="p-4 shadow rounded bg-light mt-3">
      <div class="mb-3">
        <label class="form-label">Nome</label>
        <input type="text" name="from_name" class="form-control" placeholder="Seu nome" required>
      </div>
      <div class="mb-3">
        <label class="form-label">E-mail</label>
        <input type="email" name="reply_to" class="form-control" placeholder="Seu e-mail" required>
      </div>
      <div class="mb-3">
        <label class="form-label">Mensagem</label>
        <textarea name="message" class="form-control" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      </div>
      <button type="submit" class="btn btn-primary w-100">Enviar Orçamento</button>
      <p id="statusMsg" class="mt-3 fw-bold"></p>
    </form>
  </section>

  <!-- Footer -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Botão WhatsApp -->
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     class="whatsapp-float" target="_blank">
    <i class="fab fa-whatsapp"></i>
  </a>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<!-- Depoimentos -->
<section id="depoimentos" class="container my-5">
  <div class="text-center">
    <h2>O que nossos clientes dizem</h2>
    <p class="text-muted">A satisfação dos clientes é a nossa melhor propaganda.</p>
  </div>

  <div class="row mt-4">
    <div class="col-md-4 mb-4">
      <div class="card shadow-sm h-100">
        <div class="card-body text-center">
          <img src="https://randomuser.me/api/portraits/men/32.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 1">
          <h5 class="card-title">Carlos Silva</h5>
          <p class="text-warning">★★★★★</p>
          <p class="card-text">"Excelente atendimento e rapidez na instalação. Agora me sinto muito mais seguro em casa."</p>
        </div>
      </div>
    </div>

    <div class="col-md-4 mb-4">
      <div class="card shadow-sm h-100">
        <div class="card-body text-center">
          <img src="https://randomuser.me/api/portraits/women/44.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 2">
          <h5 class="card-title">Mariana Souza</h5>
          <p class="text-warning">★★★★★</p>
          <p class="card-text">"Serviço de monitoramento impecável! Sempre atenciosos e prontos para ajudar."</p>
        </div>
      </div>
    </div>

    <div class="col-md-4 mb-4">
      <div class="card shadow-sm h-100">
        <div class="card-body text-center">
          <img src="https://randomuser.me/api/portraits/men/12.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 3">
          <h5 class="card-title">João Pereira</h5>
          <p class="text-warning">★★★★★</p>
          <p class="card-text">"Equipe muito profissional, sistema confiável e suporte técnico excelente."</p>
        </div>
      </div>
    </div>
  </div>
</section>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    .carousel-item img {
      height: 500px;
      object-fit: cover;
    }
    /* Botão WhatsApp */
    .whatsapp-float {
      position: fixed;
      width: 60px;
      height: 60px;
      bottom: 20px;
      right: 20px;
      background-color: #25d366;
      color: #fff;
      border-radius: 50%;
      text-align: center;
      font-size: 30px;
      box-shadow: 2px 2px 8px rgba(0,0,0,0.3);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.2s;
    }
    .whatsapp-float:hover {
      transform: scale(1.1);
      color: #fff;
    }
  </style>
  <!-- Ícones -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
</head>
<body>

  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand fw-bold" href="#">Monitoramento 24H</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu" aria-controls="menu" aria-expanded="false" aria-label="Menu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#servicos">Serviços</a></li>
          <li class="nav-item"><a class="nav-link" href="#depoimentos">Depoimentos</a></li>
          <li class="nav-item"><a class="nav-link" href="#orcamento">Orçamento</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Carousel -->
  <div id="bannerCarousel" class="carousel slide mt-5" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="https://source.unsplash.com/1200x500/?security,camera" class="d-block w-100" alt="Segurança 24H">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Monitoramento 24 Horas</h3>
          <p>Sua segurança em boas mãos, dia e noite.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?cctv,building" class="d-block w-100" alt="Câmeras de Segurança">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>CFTV e Alarmes</h3>
          <p>Tecnologia avançada para proteger sua residência ou empresa.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?security,team" class="d-block w-100" alt="Equipe de Pronta Resposta">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Equipe de Pronta Resposta</h3>
          <p>Intervenção rápida em caso de emergência.</p>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#bannerCarousel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#bannerCarousel" data-bs-slide="next">
      <span class="carousel-control-next-icon"></span>
    </button>
  </div>

  <!-- Sobre -->
  <section id="sobre" class="container my-5">
    <div class="text-center">
      <h2>Sobre Nós</h2>
      <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
    </div>
    <div class="mt-4">
      <iframe 
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3656.510403190348!2d-46.6333091850213!3d-23.5880164846696!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94ce59c7b1b1b1%3A0x123456789abcdef!2sSua%20Empresa%20Aqui!5e0!3m2!1spt-BR!2sbr!4v1700000000000!5m2!1spt-BR!2sbr" 
        width="100%" 
        height="350" 
        style="border:0; border-radius:12px;" 
        allowfullscreen="" 
        loading="lazy">
      </iframe>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="container my-5">
    <div class="text-center">
      <h2>Nossos Serviços</h2>
    </div>
    <div class="row mt-4">
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🔔 Monitoramento de Alarmes</h5>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🚗 Rastreamento de Veículos</h5>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🎥 Câmeras de Segurança (CFTV)</h5>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🚓 Equipe de Pronta Resposta</h5>
        </div>
      </div>
    </div>
  </section>

  <!-- Depoimentos -->
  <section id="depoimentos" class="container my-5">
    <div class="text-center">
      <h2>O que nossos clientes dizem</h2>
      <p class="text-muted">A satisfação dos clientes é a nossa melhor propaganda.</p>
    </div>
    <div class="row mt-4">
      <div class="col-md-4 mb-4">
        <div class="card shadow-sm h-100 text-center p-4">
          <img src="https://randomuser.me/api/portraits/men/32.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 1">
          <h5 class="card-title">Carlos Silva</h5>
          <p class="text-warning">★★★★★</p>
          <p>"Excelente atendimento e rapidez na instalação. Agora me sinto muito mais seguro em casa."</p>
        </div>
      </div>
      <div class="col-md-4 mb-4">
        <div class="card shadow-sm h-100 text-center p-4">
          <img src="https://randomuser.me/api/portraits/women/44.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 2">
          <h5 class="card-title">Mariana Souza</h5>
          <p class="text-warning">★★★★★</p>
          <p>"Serviço de monitoramento impecável! Sempre atenciosos e prontos para ajudar."</p>
        </div>
      </div>
      <div class="col-md-4 mb-4">
        <div class="card shadow-sm h-100 text-center p-4">
          <img src="https://randomuser.me/api/portraits/men/12.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 3">
          <h5 class="card-title">João Pereira</h5>
          <p class="text-warning">★★★★★</p>
          <p>"Equipe muito profissional, sistema confiável e suporte técnico excelente."</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="container my-5">
    <div class="text-center">
      <h2>Solicite um Orçamento</h2>
      <p class="text-muted">Preencha o formulário abaixo e entraremos em contato com você.</p>
    </div>
    <form id="orcamentoForm" class="p-4 shadow rounded bg-light mt-3">
      <div class="mb-3">
        <label class="form-label">Nome</label>
        <input type="text" name="from_name" class="form-control" placeholder="Seu nome" required>
      </div>
      <div class="mb-3">
        <label class="form-label">E-mail</label>
        <input type="email" name="reply_to" class="form-control" placeholder="Seu e-mail" required>
      </div>
      <div class="mb-3">
        <label class="form-label">Mensagem</label>
        <textarea name="message" class="form-control" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      </div>
      <button type="submit" class="btn btn-primary w-100">Enviar Orçamento</button>
      <p id="statusMsg" class="mt-3 fw-bold"></p>
    </form>
  </section>

  <!-- Footer -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Botão WhatsApp -->
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     class="whatsapp-float" target="_blank">
    <i class="fab fa-whatsapp"></i>
  </a>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<!-- FAQ -->
<section id="faq" class="container my-5">
  <div class="text-center mb-4">
    <h2>Perguntas Frequentes</h2>
    <p class="text-muted">Tire suas principais dúvidas sobre nossos serviços.</p>
  </div>

  <div class="accordion" id="faqAccordion">

    <div class="accordion-item">
      <h2 class="accordion-header" id="faq1">
        <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta1" aria-expanded="true" aria-controls="pergunta1">
          O monitoramento funciona 24 horas por dia?
        </button>
      </h2>
      <div id="pergunta1" class="accordion-collapse collapse show" aria-labelledby="faq1" data-bs-parent="#faqAccordion">
        <div class="accordion-body">
          Sim! Nossa central de monitoramento funciona todos os dias, 24 horas, sem interrupções.
        </div>
      </div>
    </div>

    <div class="accordion-item">
      <h2 class="accordion-header" id="faq2">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta2" aria-expanded="false" aria-controls="pergunta2">
          Posso acessar as câmeras pelo celular?
        </button>
      </h2>
      <div id="pergunta2" class="accordion-collapse collapse" aria-labelledby="faq2" data-bs-parent="#faqAccordion">
        <div class="accordion-body">
          Sim, você pode acompanhar as imagens em tempo real pelo nosso aplicativo no celular, tablet ou computador.
        </div>
      </div>
    </div>

    <div class="accordion-item">
      <h2 class="accordion-header" id="faq3">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta3" aria-expanded="false" aria-controls="pergunta3">
          Qual é o prazo para instalação?
        </button>
      </h2>
      <div id="pergunta3" class="accordion-collapse collapse" aria-labelledby="faq3" data-bs-parent="#faqAccordion">
        <div class="accordion-body">
          O prazo médio de instalação varia de 24 a 72 horas após a assinatura do contrato, dependendo do tamanho do projeto.
        </div>
      </div>
    </div>

    <div class="accordion-item">
      <h2 class="accordion-header" id="faq4">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta4" aria-expanded="false" aria-controls="pergunta4">
          A empresa oferece suporte técnico?
        </button>
      </h2>
      <div id="pergunta4" class="accordion-collapse collapse" aria-labelledby="faq4" data-bs-parent="#faqAccordion">
        <div class="accordion-body">
          Sim! Temos suporte técnico especializado, disponível para auxiliar sempre que necessário.
        </div>
      </div>
    </div>

  </div>
</section>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    .carousel-item img {
      height: 500px;
      object-fit: cover;
    }
    /* Botão WhatsApp */
    .whatsapp-float {
      position: fixed;
      width: 60px;
      height: 60px;
      bottom: 20px;
      right: 20px;
      background-color: #25d366;
      color: #fff;
      border-radius: 50%;
      text-align: center;
      font-size: 30px;
      box-shadow: 2px 2px 8px rgba(0,0,0,0.3);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.2s;
    }
    .whatsapp-float:hover {
      transform: scale(1.1);
      color: #fff;
    }
  </style>
  <!-- Ícones -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
</head>
<body>

  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand fw-bold" href="#">Monitoramento 24H</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu" aria-controls="menu" aria-expanded="false" aria-label="Menu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#servicos">Serviços</a></li>
          <li class="nav-item"><a class="nav-link" href="#depoimentos">Depoimentos</a></li>
          <li class="nav-item"><a class="nav-link" href="#faq">FAQ</a></li>
          <li class="nav-item"><a class="nav-link" href="#orcamento">Orçamento</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Carousel -->
  <div id="bannerCarousel" class="carousel slide mt-5" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="https://source.unsplash.com/1200x500/?security,camera" class="d-block w-100" alt="Segurança 24H">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Monitoramento 24 Horas</h3>
          <p>Sua segurança em boas mãos, dia e noite.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?cctv,building" class="d-block w-100" alt="Câmeras de Segurança">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>CFTV e Alarmes</h3>
          <p>Tecnologia avançada para proteger sua residência ou empresa.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img src="https://source.unsplash.com/1200x500/?security,team" class="d-block w-100" alt="Equipe de Pronta Resposta">
        <div class="carousel-caption d-none d-md-block bg-dark bg-opacity-50 rounded p-3">
          <h3>Equipe de Pronta Resposta</h3>
          <p>Intervenção rápida em caso de emergência.</p>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#bannerCarousel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#bannerCarousel" data-bs-slide="next">
      <span class="carousel-control-next-icon"></span>
    </button>
  </div>

  <!-- Sobre -->
  <section id="sobre" class="container my-5">
    <div class="text-center">
      <h2>Sobre Nós</h2>
      <p class="lead">Somos uma empresa especializada em monitoramento 24 horas, oferecendo soluções modernas de segurança para residências e empresas.</p>
    </div>
    <div class="mt-4">
      <iframe 
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3656.510403190348!2d-46.6333091850213!3d-23.5880164846696!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94ce59c7b1b1b1%3A0x123456789abcdef!2sSua%20Empresa%20Aqui!5e0!3m2!1spt-BR!2sbr!4v1700000000000!5m2!1spt-BR!2sbr" 
        width="100%" 
        height="350" 
        style="border:0; border-radius:12px;" 
        allowfullscreen="" 
        loading="lazy">
      </iframe>
    </div>
  </section>

  <!-- Serviços -->
  <section id="servicos" class="container my-5">
    <div class="text-center">
      <h2>Nossos Serviços</h2>
    </div>
    <div class="row mt-4">
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🔔 Monitoramento de Alarmes</h5>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🚗 Rastreamento de Veículos</h5>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🎥 Câmeras de Segurança (CFTV)</h5>
        </div>
      </div>
      <div class="col-md-3 col-sm-6 mb-4">
        <div class="card h-100 shadow-sm text-center p-3">
          <h5>🚓 Equipe de Pronta Resposta</h5>
        </div>
      </div>
    </div>
  </section>

  <!-- Depoimentos -->
  <section id="depoimentos" class="container my-5">
    <div class="text-center">
      <h2>O que nossos clientes dizem</h2>
      <p class="text-muted">A satisfação dos clientes é a nossa melhor propaganda.</p>
    </div>
    <div class="row mt-4">
      <div class="col-md-4 mb-4">
        <div class="card shadow-sm h-100 text-center p-4">
          <img src="https://randomuser.me/api/portraits/men/32.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 1">
          <h5 class="card-title">Carlos Silva</h5>
          <p class="text-warning">★★★★★</p>
          <p>"Excelente atendimento e rapidez na instalação. Agora me sinto muito mais seguro em casa."</p>
        </div>
      </div>
      <div class="col-md-4 mb-4">
        <div class="card shadow-sm h-100 text-center p-4">
          <img src="https://randomuser.me/api/portraits/women/44.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 2">
          <h5 class="card-title">Mariana Souza</h5>
          <p class="text-warning">★★★★★</p>
          <p>"Serviço de monitoramento impecável! Sempre atenciosos e prontos para ajudar."</p>
        </div>
      </div>
      <div class="col-md-4 mb-4">
        <div class="card shadow-sm h-100 text-center p-4">
          <img src="https://randomuser.me/api/portraits/men/12.jpg" class="rounded-circle mb-3" width="80" height="80" alt="Cliente 3">
          <h5 class="card-title">João Pereira</h5>
          <p class="text-warning">★★★★★</p>
          <p>"Equipe muito profissional, sistema confiável e suporte técnico excelente."</p>
        </div>
      </div>
    </div>
  </section>

  <!-- FAQ -->
  <section id="faq" class="container my-5">
    <div class="text-center mb-4">
      <h2>Perguntas Frequentes</h2>
      <p class="text-muted">Tire suas principais dúvidas sobre nossos serviços.</p>
    </div>

    <div class="accordion" id="faqAccordion">

      <div class="accordion-item">
        <h2 class="accordion-header" id="faq1">
          <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta1" aria-expanded="true" aria-controls="pergunta1">
            O monitoramento funciona 24 horas por dia?
          </button>
        </h2>
        <div id="pergunta1" class="accordion-collapse collapse show" aria-labelledby="faq1" data-bs-parent="#faqAccordion">
          <div class="accordion-body">
            Sim! Nossa central de monitoramento funciona todos os dias, 24 horas, sem interrupções.
          </div>
        </div>
      </div>

      <div class="accordion-item">
        <h2 class="accordion-header" id="faq2">
          <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta2" aria-expanded="false" aria-controls="pergunta2">
            Posso acessar as câmeras pelo celular?
          </button>
        </h2>
        <div id="pergunta2" class="accordion-collapse collapse" aria-labelledby="faq2" data-bs-parent="#faqAccordion">
          <div class="accordion-body">
            Sim, você pode acompanhar as imagens em tempo real pelo nosso aplicativo no celular, tablet ou computador.
          </div>
        </div>
      </div>

      <div class="accordion-item">
        <h2 class="accordion-header" id="faq3">
          <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta3" aria-expanded="false" aria-controls="pergunta3">
            Qual é o prazo para instalação?
          </button>
        </h2>
        <div id="pergunta3" class="accordion-collapse collapse" aria-labelledby="faq3" data-bs-parent="#faqAccordion">
          <div class="accordion-body">
            O prazo médio de instalação varia de 24 a 72 horas após a assinatura do contrato, dependendo do tamanho do projeto.
          </div>
        </div>
      </div>

      <div class="accordion-item">
        <h2 class="accordion-header" id="faq4">
          <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#pergunta4" aria-expanded="false" aria-controls="pergunta4">
            A empresa oferece suporte técnico?
          </button>
        </h2>
        <div id="pergunta4" class="accordion-collapse collapse" aria-labelledby="faq4" data-bs-parent="#faqAccordion">
          <div class="accordion-body">
            Sim! Temos suporte técnico especializado, disponível para auxiliar sempre que necessário.
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- Orçamento -->
  <section id="orcamento" class="container my-5">
    <div class="text-center">
      <h2>Solicite um Orçamento</h2>
      <p class="text-muted">Preencha o formulário abaixo e entraremos em contato com você.</p>
    </div>
    <form id="orcamentoForm" class="p-4 shadow rounded bg-light mt-3">
      <div class="mb-3">
        <label class="form-label">Nome</label>
        <input type="text" name="from_name" class="form-control" placeholder="Seu nome" required>
      </div>
      <div class="mb-3">
        <label class="form-label">E-mail</label>
        <input type="email" name="reply_to" class="form-control" placeholder="Seu e-mail" required>
      </div>
      <div class="mb-3">
        <label class="form-label">Mensagem</label>
        <textarea name="message" class="form-control" rows="5" placeholder="Descreva sua necessidade..." required></textarea>
      </div>
      <button type="submit" class="btn btn-primary w-100">Enviar Orçamento</button>
      <p id="statusMsg" class="mt-3 fw-bold"></p>
    </form>
  </section>

  <!-- Footer -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Botão WhatsApp -->
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     class="whatsapp-float" target="_blank">
    <i class="fab fa-whatsapp"></i>
  </a>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html><!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Monitoramento 24H</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <!-- Ícones -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

  <style>
    .carousel-item img {
      height: 500px;
      object-fit: cover;
    }

    /* Botão WhatsApp */
    .whatsapp-float {
      position: fixed;
      width: 60px;
      height: 60px;
      bottom: 80px; /* ajustado para não cobrir o menu fixo */
      right: 20px;
      background-color: #25d366;
      color: #fff;
      border-radius: 50%;
      text-align: center;
      font-size: 30px;
      box-shadow: 2px 2px 8px rgba(0,0,0,0.3);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.2s;
    }
    .whatsapp-float:hover {
      transform: scale(1.1);
      color: #fff;
    }

    /* Menu fixo rodapé */
    .footer-menu {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background: #212529;
      display: flex;
      justify-content: space-around;
      padding: 10px 0;
      z-index: 999;
    }
    .footer-menu a {
      color: #fff;
      text-align: center;
      font-size: 12px;
      flex-grow: 1;
    }
    .footer-menu a i {
      display: block;
      font-size: 20px;
      margin-bottom: 3px;
    }
    .footer-menu a:hover {
      color: #0d6efd;
    }
  </style>
</head>
<body>

  <!-- (Mantém o mesmo conteúdo anterior: Navbar, Carousel, Sobre, Serviços, Depoimentos, FAQ, Orçamento, Footer institucional etc.) -->

  <!-- Footer Institucional -->
  <footer class="bg-dark text-white text-center py-3 mt-5">
    <p class="mb-0">&copy; 2025 Monitoramento 24H - Todos os direitos reservados.</p>
  </footer>

  <!-- Botão WhatsApp -->
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     class="whatsapp-float" target="_blank">
    <i class="fab fa-whatsapp"></i>
  </a>

  <!-- Menu fixo rodapé -->
  <div class="footer-menu">
    <a href="#bannerCarousel"><i class="fas fa-home"></i> Início</a>
    <a href="#servicos"><i class="fas fa-shield-alt"></i> Serviços</a>
    <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i> Orçamento</a>
    <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank"><i class="fab fa-whatsapp"></i> WhatsApp</a>
    <a href="#faq"><i class="fas fa-question-circle"></i> FAQ</a>
  </div>

  <!-- Bootstrap JS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <!-- EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("SEU_PUBLIC_KEY"); // Substitua pela sua Public Key
    })();

    document.getElementById("orcamentoForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const statusMsg = document.getElementById("statusMsg");

      emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_ORCAMENTO", this)
        .then(function() {
          return emailjs.sendForm("SEU_SERVICE_ID", "SEU_TEMPLATE_ID_REPLY", document.getElementById("orcamentoForm"));
        })
        .then(function() {
          statusMsg.style.color = "green";
          statusMsg.textContent = "✅ Orçamento enviado com sucesso! Em breve entraremos em contato.";
          document.getElementById("orcamentoForm").reset();
        }, function(error) {
          statusMsg.style.color = "red";
          statusMsg.textContent = "❌ Ocorreu um erro ao enviar. Tente novamente.";
          console.error("Erro:", error);
        });
    });
  </script>
</body>
</html>
<!-- Menu fixo rodapé -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i> Início</a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i> Serviços</a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i> Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank">
    <i class="fab fa-whatsapp"></i> WhatsApp
  </a>
  <a href="tel:+5511999999999">
    <i class="fas fa-phone-alt"></i> Ligar
  </a>
  <a href="#faq"><i class="fas fa-question-circle"></i> FAQ</a>
</div>
<a href="tel:+5511999999999">
<!-- Menu fixo rodapé -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i> Início</a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i> Serviços</a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i> Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank">
    <i class="fab fa-whatsapp"></i> WhatsApp
  </a>
  <a href="tel:+5511999999999">
    <i class="fas fa-phone-alt"></i> Ligar
  </a>
  <a href="mailto:contato@suaempresa.com">
    <i class="fas fa-envelope"></i> E-mail
  </a>
  <a href="#faq"><i class="fas fa-question-circle"></i> FAQ</a>
</div>
<a href="mailto:contato@suaempresa.com">
<!-- Menu fixo rodapé -->
<div class="footer-menu">
  <a href="#bannerCarousel">
    <i class="fas fa-home"></i> 
    <span class="d-none d-md-block">Início</span>
  </a>
  <a href="#servicos">
    <i class="fas fa-shield-alt"></i> 
    <span class="d-none d-md-block">Serviços</span>
  </a>
  <a href="#orcamento">
    <i class="fas fa-file-invoice-dollar"></i> 
    <span class="d-none d-md-block">Orçamento</span>
  </a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank">
    <i class="fab fa-whatsapp"></i> 
    <span class="d-none d-md-block">WhatsApp</span>
  </a>
  <a href="tel:+5511999999999">
    <i class="fas fa-phone-alt"></i> 
    <span class="d-none d-md-block">Ligar</span>
  </a>
  <a href="mailto:contato@suaempresa.com">
    <i class="fas fa-envelope"></i> 
    <span class="d-none d-md-block">E-mail</span>
  </a>
  <a href="#faq">
    <i class="fas fa-question-circle"></i> 
    <span class="d-none d-md-block">FAQ</span>
  </a>
</div>
<style>
  .footer-menu a.active {
    color: #0d6efd; /* azul destaque */
  }
  .footer-menu a.active i {
    transform: scale(1.2);
    transition: transform 0.2s;
  }
</style>
<script>
  // Ativar item do menu ao rolar a página
  const sections = document.querySelectorAll("section, header, footer");
  const navLinks = document.querySelectorAll(".footer-menu a");

  window.addEventListener("scroll", () => {
    let current = "";

    sections.forEach(section => {
      const sectionTop = section.offsetTop - 150;
      const sectionHeight = section.clientHeight;
      if (scrollY >= sectionTop && scrollY < sectionTop + sectionHeight) {
        current = section.getAttribute("id");
      }
    });

    navLinks.forEach(link => {
      link.classList.remove("active");
      if (link.getAttribute("href").includes(current)) {
        link.classList.add("active");
      }
    });
  });
</script>
<style>
  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
  }

  /* Bolha animada */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }

  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque ativo */
  .footer-menu a.active {
    color: #0d6efd;
  }
  .footer-menu a.active i {
    transform: scale(1.2);
    transition: transform 0.2s;
  }
</style>
<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Ícone ativo com shake */
  .footer-menu a.active {
    color: #0d6efd;
  }
  .footer-menu a.active i {
    animation: shake 0.6s ease-in-out infinite;
  }
</style>
<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque azul ativo (desktop e mobile) */
  .footer-menu a.active {
    color: #0d6efd;
  }

  /* Shake apenas no mobile */
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }
</style>
<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque azul ativo (desktop e mobile) */
  .footer-menu a.active {
    color: #0d6efd;
  }

  /* Shake apenas no mobile */
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }

  /* Badge de notificação no WhatsApp */
  .footer-menu a.whatsapp {
    position: relative;
  }
  .footer-menu a.whatsapp::after {
    content: "";
    position: absolute;
    top: 2px;
    right: 30%;
    width: 10px;
    height: 10px;
    background: red;
    border-radius: 50%;
    border: 2px solid #212529; /* contorno para destacar */
  }
</style>
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span class="d-none d-md-block">Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span class="d-none d-md-block">Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span class="d-none d-md-block">Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i><span class="d-none d-md-block">WhatsApp</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span class="d-none d-md-block">Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span class="d-none d-md-block">E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span class="d-none d-md-block">FAQ</span></a>
</div>
<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  /* Animação blink para o badge */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque azul ativo (desktop e mobile) */
  .footer-menu a.active {
    color: #0d6efd;
  }

  /* Shake apenas no mobile */
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }

  /* Badge de notificação no WhatsApp */
  .footer-menu a.whatsapp {
    position: relative;
  }
  .footer-menu a.whatsapp::after {
    content: "";
    position: absolute;
    top: 2px;
    right: 30%;
    width: 10px;
    height: 10px;
    background: red;
    border-radius: 50%;
    border: 2px solid #212529; /* contorno para destacar */
    animation: blink 1s infinite; /* pisca suavemente */
  }
</style>
<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  /* Animação blink para o badge */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque azul ativo (desktop e mobile) */
  .footer-menu a.active {
    color: #0d6efd;
  }

  /* Shake apenas no mobile */
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }

  /* Badge de notificação no WhatsApp */
  .footer-menu a.whatsapp {
    position: relative;
  }
  .footer-menu a.whatsapp::after {
    content: "1"; /* número da notificação */
    position: absolute;
    top: 0px;
    right: 28%;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529; /* contorno para destacar */
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite; /* pisca suavemente */
  }
</style>
<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  /* Animação blink para o badge */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque azul ativo (desktop e mobile) */
  .footer-menu a.active {
    color: #0d6efd;
  }

  /* Shake apenas no mobile */
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }

  /* Badge de notificação no WhatsApp */
  .footer-menu a.whatsapp {
    position: relative;
  }
  .footer-menu a.whatsapp .badge {
    position: absolute;
    top: 0px;
    right: 28%;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529; /* contorno para destacar */
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite; /* pisca suavemente */
  }
</style>
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span class="d-none d-md-block">Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span class="d-none d-md-block">Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span class="d-none d-md-block">Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i>
    <span class="d-none d-md-block">WhatsApp</span>
    <span class="badge">1</span> <!-- Badge dinâmico -->
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span class="d-none d-md-block">Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span class="d-none d-md-block">E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span class="d-none d-md-block">FAQ</span></a>
</div>
<script>
  // Seleciona o badge
  const badge = document.querySelector(".footer-menu .whatsapp .badge");

  // Simulação: atualiza o número de mensagens a cada 5 segundos
  let mensagens = 1;
  setInterval(() => {
    mensagens++;
    badge.textContent = mensagens; // atualiza o número no badge
  }, 5000);

  // Para zerar quando o usuário clicar no WhatsApp
  document.querySelector(".footer-menu .whatsapp").addEventListener("click", () => {
    mensagens = 0;
    badge.textContent = mensagens;
  });
</script>
<script>
  // Seleciona o badge
  const badge = document.querySelector(".footer-menu .whatsapp .badge");

  // Agora começa em 3 mensagens
  let mensagens = 3;
  badge.textContent = mensagens;

  // Simulação: atualiza o número de mensagens a cada 5 segundos
  setInterval(() => {
    mensagens++;
    badge.textContent = mensagens; // atualiza o número no badge
  }, 5000);

  // Para zerar quando o usuário clicar no WhatsApp
  document.querySelector(".footer-menu .whatsapp").addEventListener("click", () => {
    mensagens = 0;
    badge.textContent = mensagens;
  });
</script>
<script>
  // Seleciona o badge
  const badge = document.querySelector(".footer-menu .whatsapp .badge");

  // Agora começa em 3 mensagens
  let mensagens = 3;
  badge.textContent = mensagens;

  // Simulação: atualiza o número de mensagens a cada 5 segundos
  setInterval(() => {
    // Número aleatório entre 1 e 3
    const incremento = Math.floor(Math.random() * 3) + 1;
    mensagens += incremento;
    badge.textContent = mensagens; // atualiza o número no badge
  }, 5000);

  // Para zerar quando o usuário clicar no WhatsApp
  document.querySelector(".footer-menu .whatsapp").addEventListener("click", () => {
    mensagens = 0;
    badge.textContent = mensagens;
  });
</script>
<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  /* Animação shake */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }

  /* Animação blink para o badge */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }

  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }

  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }

  /* Bolha azul no hover */
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }

  /* Texto escondido no mobile */
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu a span {
      display: block;
    }
  }

  /* Destaque azul ativo */
  .footer-menu a.active {
    color: #0d6efd;
  }

  /* Shake no mobile */
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }

  /* Badge do WhatsApp */
  .footer-menu a.whatsapp {
    position: relative;
  }
  .footer-menu a.whatsapp .badge {
    position: absolute;
    top: 0px;
    right: 28%;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529;
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite;
  }
</style>

<!-- Rodapé -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i>
    <span>WhatsApp</span>
    <span class="badge">3</span> <!-- Badge inicial -->
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- Script do contador dinâmico -->
<script>
  const badge = document.querySelector(".footer-menu .whatsapp .badge");

  // Começa em 3 mensagens
  let mensagens = 3;
  badge.textContent = mensagens;

  // Aumenta de forma aleatória (+1, +2 ou +3) a cada 5 segundos
  setInterval(() => {
    const incremento = Math.floor(Math.random() * 3) + 1;
    mensagens += incremento;
    badge.textContent = mensagens;
  }, 5000);

  // Zera quando o usuário clicar no WhatsApp
  document.querySelector(".footer-menu .whatsapp").addEventListener("click", () => {
    mensagens = 0;
    badge.textContent = mensagens;
  });
</script>
<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  /* Navbar Desktop */
  .navbar-desktop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #212529;
    padding: 12px 20px;
    display: flex;
    justify-content: center;
    gap: 30px;
    z-index: 1000;
  }
  .navbar-desktop a {
    color: #fff;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    position: relative;
    transition: color 0.3s;
  }
  .navbar-desktop a:hover {
    color: #0d6efd;
  }
  .navbar-desktop a.active {
    color: #0d6efd;
  }
  /* Efeito linha embaixo ao passar o mouse */
  .navbar-desktop a::after {
    content: "";
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: #0d6efd;
    transition: width 0.3s;
  }
  .navbar-desktop a:hover::after {
    width: 100%;
  }

  /* Oculta navbar no mobile */
  @media (max-width: 767px) {
    .navbar-desktop {
      display: none;
    }
  }

  /* Footer Mobile */
  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }
  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }
  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu {
      display: none; /* Esconde footer no desktop */
    }
  }
  /* Shake no mobile */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }
  /* Badge WhatsApp */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }
  .footer-menu a.whatsapp {
    position: relative;
  }
  .footer-menu a.whatsapp .badge {
    position: absolute;
    top: 0px;
    right: 28%;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529;
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite;
  }
</style>

<!-- Navbar Desktop -->
<div class="navbar-desktop">
  <a href="#bannerCarousel" class="active">Início</a>
  <a href="#servicos">Serviços</a>
  <a href="#orcamento">Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank">WhatsApp</a>
  <a href="tel:+5511999999999">Ligar</a>
  <a href="mailto:contato@suaempresa.com">E-mail</a>
  <a href="#faq">FAQ</a>
</div>

<!-- Footer Mobile -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i>
    <span>WhatsApp</span>
    <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- Script Contador Dinâmico -->
<script>
  const badge = document.querySelector(".footer-menu .whatsapp .badge");

  // Começa em 3
  let mensagens = 3;
  badge.textContent = mensagens;

  // Incremento aleatório a cada 5s
  setInterval(() => {
    const incremento = Math.floor(Math.random() * 3) + 1;
    mensagens += incremento;
    badge.textContent = mensagens;
  }, 5000);

  // Zera ao clicar no WhatsApp
  document.querySelector(".footer-menu .whatsapp").addEventListener("click", () => {
    mensagens = 0;
    badge.textContent = mensagens;
  });
</script>
<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  /* Navbar Desktop */
  .navbar-desktop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #212529;
    padding: 12px 20px;
    display: flex;
    justify-content: center;
    gap: 30px;
    z-index: 1000;
  }
  .navbar-desktop a {
    color: #fff;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    position: relative;
    transition: color 0.3s;
  }
  .navbar-desktop a:hover {
    color: #0d6efd;
  }
  .navbar-desktop a.active {
    color: #0d6efd;
  }
  /* Linha azul ao hover */
  .navbar-desktop a::after {
    content: "";
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: #0d6efd;
    transition: width 0.3s;
  }
  .navbar-desktop a:hover::after {
    width: 100%;
  }

  /* Oculta navbar no mobile */
  @media (max-width: 767px) {
    .navbar-desktop {
      display: none;
    }
  }

  /* Footer Mobile */
  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }
  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }
  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }
  .footer-menu a span {
    display: none;
  }
  @media (min-width: 768px) {
    .footer-menu {
      display: none; /* Esconde footer no desktop */
    }
  }

  /* Shake no mobile */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }
  @media (max-width: 767px) {
    .footer-menu a.active i {
      animation: shake 0.6s ease-in-out infinite;
    }
  }

  /* Badge do WhatsApp (navbar + footer) */
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }
  .whatsapp {
    position: relative;
  }
  .whatsapp .badge {
    position: absolute;
    top: -6px;
    right: -12px;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529;
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite;
  }
  /* Ajuste do badge no footer */
  .footer-menu .whatsapp .badge {
    top: 0px;
    right: 28%;
  }
</style>

<!-- Navbar Desktop -->
<div class="navbar-desktop">
  <a href="#bannerCarousel" class="active">Início</a>
  <a href="#servicos">Serviços</a>
  <a href="#orcamento">Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     target="_blank" class="whatsapp">
    WhatsApp <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999">Ligar</a>
  <a href="mailto:contato@suaempresa.com">E-mail</a>
  <a href="#faq">FAQ</a>
</div>

<!-- Footer Mobile -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." 
     target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i>
    <span>WhatsApp</span>
    <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- Script Contador Dinâmico -->
<script>
  const badges = document.querySelectorAll(".whatsapp .badge");

  // Começa em 3
  let mensagens = 3;
  badges.forEach(b => b.textContent = mensagens);

  // Incremento aleatório a cada 5s
  setInterval(() => {
    const incremento = Math.floor(Math.random() * 3) + 1;
    mensagens += incremento;
    badges.forEach(b => b.textContent = mensagens);
  }, 5000);

  // Zera ao clicar no WhatsApp
  document.querySelectorAll(".whatsapp").forEach(btn => {
    btn.addEventListener("click", () => {
      mensagens = 0;
      badges.forEach(b => b.textContent = mensagens);
    });
  });
</script>
<section id="orcamento" style="padding: 60px 20px; background: #f8f9fa;">
  <div style="max-width: 700px; margin: auto; background: #fff; padding: 30px; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
    <h2 style="text-align: center; color: #212529; margin-bottom: 20px;">
      Solicite um Orçamento
    </h2>
    <p style="text-align: center; margin-bottom: 30px; color: #555;">
      Preencha o formulário abaixo e retornaremos o mais rápido possível.
    </p>
    <form id="formOrcamento">
      <div style="margin-bottom: 15px;">
        <label>Nome *</label>
        <input type="text" name="nome" required style="width:100%; padding:10px; border:1px solid #ddd; border-radius:8px;">
      </div>
      <div style="margin-bottom: 15px;">
        <label>E-mail *</label>
        <input type="email" name="email" required style="width:100%; padding:10px; border:1px solid #ddd; border-radius:8px;">
      </div>
      <div style="margin-bottom: 15px;">
        <label>Telefone *</label>
        <input type="tel" name="telefone" required style="width:100%; padding:10px; border:1px solid #ddd; border-radius:8px;">
      </div>
      <div style="margin-bottom: 15px;">
        <label>Serviço Desejado *</label>
        <select name="servico" required style="width:100%; padding:10px; border:1px solid #ddd; border-radius:8px;">
          <option value="">Selecione...</option>
          <option value="Monitoramento 24h">Monitoramento 24h</option>
          <option value="Câmeras de Segurança">Câmeras de Segurança</option>
          <option value="Alarmes">Alarmes</option>
          <option value="Controle de Acesso">Controle de Acesso</option>
        </select>
      </div>
      <div style="margin-bottom: 15px;">
        <label>Mensagem</label>
        <textarea name="mensagem" rows="4" style="width:100%; padding:10px; border:1px solid #ddd; border-radius:8px;"></textarea>
      </div>
      <div style="display:flex; gap:10px; justify-content:center; margin-top:20px;">
        <button type="button" onclick="enviarWhatsApp()" style="flex:1; padding:12px; background:#25D366; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer;">
          <i class="fab fa-whatsapp"></i> Enviar WhatsApp
        </button>
        <button type="button" onclick="enviarEmail()" style="flex:1; padding:12px; background:#0d6efd; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer;">
          <i class="fas fa-envelope"></i> Enviar E-mail
        </button>
      </div>
    </form>
  </div>
</section>

<script>
  function getDadosFormulario() {
    const form = document.getElementById("formOrcamento");
    const nome = form.nome.value;
    const email = form.email.value;
    const telefone = form.telefone.value;
    const servico = form.servico.value;
    const mensagem = form.mensagem.value;

    return { nome, email, telefone, servico, mensagem };
  }

  function enviarWhatsApp() {
    const { nome, email, telefone, servico, mensagem } = getDadosFormulario();
    const texto = `*Novo Orçamento*%0A
    📌 Nome: ${nome}%0A
    📧 E-mail: ${email}%0A
    📱 Telefone: ${telefone}%0A
    🛠 Serviço: ${servico}%0A
    💬 Mensagem: ${mensagem}`;

    window.open(`https://wa.me/5511999999999?text=${texto}`, "_blank");
  }

  function enviarEmail() {
    const { nome, email, telefone, servico, mensagem } = getDadosFormulario();
    const assunto = "Solicitação de Orçamento";
    const corpo = `Novo Orçamento:%0A
    Nome: ${nome}%0A
    E-mail: ${email}%0A
    Telefone: ${telefone}%0A
    Serviço: ${servico}%0A
    Mensagem: ${mensagem}`;

    window.location.href = `mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;
  }
</script>
Nome | E-mail | Telefone | Serviço | Mensagem | Data/Hora
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var dados = JSON.parse(e.postData.contents);

  sheet.appendRow([
    dados.nome,
    dados.email,
    dados.telefone,
    dados.servico,
    dados.mensagem,
    new Date()
  ]);

  return ContentService.createTextOutput("Sucesso");
}
<div style="display:flex; gap:10px; justify-content:center; margin-top:20px;">
  <button type="button" onclick="enviarWhatsApp()" style="flex:1; padding:12px; background:#25D366; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer;">
    <i class="fab fa-whatsapp"></i> Enviar WhatsApp
  </button>
  <button type="button" onclick="enviarEmail()" style="flex:1; padding:12px; background:#0d6efd; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer;">
    <i class="fas fa-envelope"></i> Enviar E-mail
  </button>
  <button type="button" onclick="enviarSheets()" style="flex:1; padding:12px; background:#198754; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer;">
    <i class="fas fa-table"></i> Salvar na Planilha
  </button>
</div>

<script>
  const SCRIPT_URL = "COLE_AQUI_SUA_URL_DO_APPS_SCRIPT";

  function getDadosFormulario() {
    const form = document.getElementById("formOrcamento");
    return {
      nome: form.nome.value,
      email: form.email.value,
      telefone: form.telefone.value,
      servico: form.servico.value,
      mensagem: form.mensagem.value
    };
  }

  function enviarSheets() {
    const dados = getDadosFormulario();

    fetch(SCRIPT_URL, {
      method: "POST",
      body: JSON.stringify(dados),
      headers: { "Content-Type": "application/json" }
    })
    .then(res => res.text())
    .then(res => alert("Orçamento salvo com sucesso na planilha!"))
    .catch(err => alert("Erro ao salvar: " + err));
  }
</script>
<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  /* ---------------- Navbar Desktop ---------------- */
  .navbar-desktop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #212529;
    padding: 12px 20px;
    display: flex;
    justify-content: center;
    gap: 30px;
    z-index: 1000;
  }
  .navbar-desktop a {
    color: #fff;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    position: relative;
    transition: color 0.3s;
  }
  .navbar-desktop a:hover { color: #0d6efd; }
  .navbar-desktop a.active { color: #0d6efd; }
  .navbar-desktop a::after {
    content: "";
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: #0d6efd;
    transition: width 0.3s;
  }
  .navbar-desktop a:hover::after { width: 100%; }
  @media (max-width: 767px) { .navbar-desktop { display: none; } }

  /* ---------------- Footer Mobile ---------------- */
  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }
  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }
  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }
  .footer-menu a span { display: none; }
  @media (min-width: 768px) { .footer-menu { display: none; } }

  /* ---------------- Shake no mobile ---------------- */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }
  @media (max-width: 767px) {
    .footer-menu a.active i { animation: shake 0.6s ease-in-out infinite; }
  }

  /* ---------------- Badge WhatsApp ---------------- */
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }
  .whatsapp { position: relative; }
  .whatsapp .badge {
    position: absolute;
    top: -6px;
    right: -12px;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529;
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite;
  }
  .footer-menu .whatsapp .badge {
    top: 0px;
    right: 28%;
  }

  /* ---------------- Formulário Orçamento ---------------- */
  #orcamento { padding: 60px 20px; background: #f8f9fa; }
  #orcamento form { max-width:700px; margin:auto; background:#fff; padding:30px; border-radius:12px; box-shadow:0 4px 15px rgba(0,0,0,0.1); }
  #orcamento h2 { text-align:center; color:#212529; margin-bottom:20px; }
  #orcamento p { text-align:center; margin-bottom:30px; color:#555; }
  #orcamento input, #orcamento select, #orcamento textarea {
    width:100%; padding:10px; border:1px solid #ddd; border-radius:8px; margin-bottom:15px;
  }
  #orcamento button { flex:1; padding:12px; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer; }
  .btn-whatsapp { background:#25D366; }
  .btn-email { background:#0d6efd; }
  .btn-sheets { background:#198754; }
  .btn-container { display:flex; gap:10px; justify-content:center; margin-top:20px; flex-wrap:wrap; }
</style>

<!-- ---------------- Navbar Desktop ---------------- -->
<div class="navbar-desktop">
  <a href="#bannerCarousel" class="active">Início</a>
  <a href="#servicos">Serviços</a>
  <a href="#orcamento">Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    WhatsApp <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999">Ligar</a>
  <a href="mailto:contato@suaempresa.com">E-mail</a>
  <a href="#faq">FAQ</a>
</div>

<!-- ---------------- Footer Mobile ---------------- -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- ---------------- Formulário Orçamento ---------------- -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>
    <input type="text" name="nome" placeholder="Nome *" required>
    <input type="email" name="email" placeholder="E-mail *" required>
    <input type="tel" name="telefone" placeholder="Telefone *" required>
    <select name="servico" required>
      <option value="">Selecione o serviço...</option>
      <option value="Monitoramento 24h">Monitoramento 24h</option>
      <option value="Câmeras de Segurança">Câmeras de Segurança</option>
      <option value="Alarmes">Alarmes</option>
      <option value="Controle de Acesso">Controle de Acesso</option>
    </select>
    <textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea>

    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> Enviar WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> Enviar E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Salvar na Planilha</button>
    </div>
  </form>
</section>

<!-- ---------------- Script Dinâmico ---------------- -->
<script>
  const SCRIPT_URL = "COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; // URL do Google Apps Script
  const badges = document.querySelectorAll(".whatsapp .badge");
  let mensagens = 3;
  badges.forEach(b => b.textContent = mensagens);

  setInterval(() => {
    const incremento = Math.floor(Math.random() * 3) + 1;
    mensagens += incremento;
    badges.forEach(b => b.textContent = mensagens);
  }, 5000);

  document.querySelectorAll(".whatsapp").forEach(btn => {
    btn.addEventListener("click", () => {
      mensagens = 0;
      badges.forEach(b => b.textContent = mensagens);
    });
  });

  function getDadosFormulario() {
    const form = document.getElementById("formOrcamento");
    return {
      nome: form.nome.value,
      email: form.email.value,
      telefone: form.telefone.value,
      servico: form.servico.value,
      mensagem: form.mensagem.value
    };
  }

  function enviarWhatsApp() {
    const { nome, email, telefone, servico, mensagem } = getDadosFormulario();
    const texto = `*Novo Orçamento*%0A📌 Nome: ${nome}%0A📧 E-mail: ${email}%0A📱 Telefone: ${telefone}%0A🛠 Serviço: ${servico}%0A💬 Mensagem: ${mensagem}`;
    window.open(`https://wa.me/5511999999999?text=${texto}`, "_blank");
  }

  function enviarEmail() {
    const { nome, email, telefone, servico, mensagem } = getDadosFormulario();
    const assunto = "Solicitação de Orçamento";
    const corpo = `Novo Orçamento:%0ANome: ${nome}%0AE-mail: ${email}%0ATelefone: ${telefone}%0AServiço: ${servico}%0AMensagem: ${mensagem}`;
    window.location.href = `mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;
  }

  function enviarSheets() {
    const dados = getDadosFormulario();
    fetch(SCRIPT_URL, {
      method: "POST",
      body: JSON.stringify(dados),
      headers: { "Content-Type": "application/json" }
    })
    .then(res => res.text())
    .then(res => alert("Orçamento salvo com sucesso na planilha!"))
    .catch(err => alert("Erro ao salvar: " + err));
  }
</script>
<!-- Botão Voltar ao Topo -->
<button id="btnTopo" title="Voltar ao Topo" style="
  position: fixed;
  bottom: 80px;
  right: 20px;
  display: none;
  z-index: 999;
  background: #0d6efd;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 22px;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  transition: background 0.3s;
">↑</button>

<style>
  #btnTopo:hover {
    background: #025ce2;
  }
</style>

<script>
  const btnTopo = document.getElementById("btnTopo");

  // Mostra o botão quando rolar 200px
  window.onscroll = function() {
    if (document.body.scrollTop > 200 || document.documentElement.scrollTop > 200) {
      btnTopo.style.display = "block";
    } else {
      btnTopo.style.display = "none";
    }
  };

  // Ao clicar, volta suavemente ao topo
  btnTopo.addEventListener("click", () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  });
</script>
<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  /* ---------------- Navbar Desktop ---------------- */
  .navbar-desktop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #212529;
    padding: 12px 20px;
    display: flex;
    justify-content: center;
    gap: 30px;
    z-index: 1000;
  }
  .navbar-desktop a {
    color: #fff;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    position: relative;
    transition: color 0.3s;
  }
  .navbar-desktop a:hover { color: #0d6efd; }
  .navbar-desktop a.active { color: #0d6efd; }
  .navbar-desktop a::after {
    content: "";
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: #0d6efd;
    transition: width 0.3s;
  }
  .navbar-desktop a:hover::after { width: 100%; }
  @media (max-width: 767px) { .navbar-desktop { display: none; } }

  /* ---------------- Footer Mobile ---------------- */
  .footer-menu {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background: #212529;
    display: flex;
    justify-content: space-around;
    padding: 10px 0;
    z-index: 999;
  }
  .footer-menu a {
    color: #fff;
    text-align: center;
    font-size: 12px;
    flex-grow: 1;
    position: relative;
    padding: 5px 0;
  }
  .footer-menu a i {
    display: block;
    font-size: 20px;
    margin-bottom: 3px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s;
  }
  .footer-menu a::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 40px;
    height: 40px;
    background: #0d6efd;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.3s ease;
    z-index: 1;
    opacity: 0.15;
  }
  .footer-menu a:hover::before,
  .footer-menu a:focus::before {
    transform: translate(-50%, -50%) scale(1);
  }
  .footer-menu a span { display: none; }
  @media (min-width: 768px) { .footer-menu { display: none; } }

  /* ---------------- Shake no mobile ---------------- */
  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-2px); }
    50% { transform: translateX(2px); }
    75% { transform: translateX(-2px); }
    100% { transform: translateX(0); }
  }
  @media (max-width: 767px) {
    .footer-menu a.active i { animation: shake 0.6s ease-in-out infinite; }
  }

  /* ---------------- Badge WhatsApp ---------------- */
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }
  .whatsapp { position: relative; }
  .whatsapp .badge {
    position: absolute;
    top: -6px;
    right: -12px;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: red;
    color: white;
    font-size: 10px;
    font-weight: bold;
    border-radius: 50%;
    border: 2px solid #212529;
    text-align: center;
    line-height: 14px;
    animation: blink 1s infinite;
  }
  .footer-menu .whatsapp .badge {
    top: 0px;
    right: 28%;
  }

  /* ---------------- Formulário Orçamento ---------------- */
  #orcamento { padding: 60px 20px; background: #f8f9fa; }
  #orcamento form { max-width:700px; margin:auto; background:#fff; padding:30px; border-radius:12px; box-shadow:0 4px 15px rgba(0,0,0,0.1); }
  #orcamento h2 { text-align:center; color:#212529; margin-bottom:20px; }
  #orcamento p { text-align:center; margin-bottom:30px; color:#555; }
  #orcamento input, #orcamento select, #orcamento textarea {
    width:100%; padding:10px; border:1px solid #ddd; border-radius:8px; margin-bottom:15px;
  }
  #orcamento button { flex:1; padding:12px; color:white; border:none; border-radius:8px; font-size:16px; cursor:pointer; }
  .btn-whatsapp { background:#25D366; }
  .btn-email { background:#0d6efd; }
  .btn-sheets { background:#198754; }
  .btn-container { display:flex; gap:10px; justify-content:center; margin-top:20px; flex-wrap:wrap; }

  /* ---------------- Botão Voltar ao Topo ---------------- */
  #btnTopo {
    position: fixed;
    bottom: 80px;
    right: 20px;
    display: none;
    z-index: 999;
    background: #0d6efd;
    color: white;
    border: none;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    font-size: 22px;
    cursor: pointer;
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    transition: background 0.3s;
  }
  #btnTopo:hover { background: #025ce2; }
</style>

<!-- ---------------- Navbar Desktop ---------------- -->
<div class="navbar-desktop">
  <a href="#bannerCarousel" class="active">Início</a>
  <a href="#servicos">Serviços</a>
  <a href="#orcamento">Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    WhatsApp <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999">Ligar</a>
  <a href="mailto:contato@suaempresa.com">E-mail</a>
  <a href="#faq">FAQ</a>
</div>

<!-- ---------------- Footer Mobile ---------------- -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- ---------------- Formulário Orçamento ---------------- -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>
    <input type="text" name="nome" placeholder="Nome *" required>
    <input type="email" name="email" placeholder="E-mail *" required>
    <input type="tel" name="telefone" placeholder="Telefone *" required>
    <select name="servico" required>
      <option value="">Selecione o serviço...</option>
      <option value="Monitoramento 24h">Monitoramento 24h</option>
      <option value="Câmeras de Segurança">Câmeras de Segurança</option>
      <option value="Alarmes">Alarmes</option>
      <option value="Controle de Acesso">Controle de Acesso</option>
    </select>
    <textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea>

    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> Enviar WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> Enviar E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Salvar na Planilha</button>
    </div>
  </form>
</section>

<!-- ---------------- Botão Voltar ao Topo ---------------- -->
<button id="btnTopo" title="Voltar ao Topo">↑</button>

<!-- ---------------- Script Dinâmico ---------------- -->
<script>
  const SCRIPT_URL = "COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; // URL do Google Apps Script
  const badges = document.querySelectorAll(".whatsapp .badge");
  let mensagens = 3;
  badges.forEach(b => b.textContent = mensagens);

  setInterval(() => {
    const incremento = Math.floor(Math.random() * 3) + 1;
    mensagens += incremento;
    badges.forEach(b => b.textContent = mensagens);
  }, 5000);

  document.querySelectorAll(".whatsapp").forEach(btn => {
    btn.addEventListener("click", () => {
      mensagens = 0;
      badges.forEach(b => b.textContent = mensagens);
    });
  });

  function getDadosFormulario() {
    const form = document.getElementById("formOrcamento");
    return {
      nome: form.nome.value,
      email: form.email.value,
      telefone: form.telefone.value,
      servico: form.servico.value,
      mensagem: form.mensagem.value
    };
  }

  function enviarWhatsApp() {
    const { nome, email, telefone, servico, mensagem } = getDadosFormulario();
    const texto = `*Novo Orçamento*%0A📌 Nome: ${nome}%0A📧 E-mail: ${email}%0A📱 Telefone: ${telefone}%0A🛠 Serviço: ${servico}%0A💬 Mensagem: ${mensagem}`;
    window.open(`https://wa.me/5511999999999?text=${texto}`, "_blank");
  }

  function enviarEmail() {
    const { nome, email, telefone, servico, mensagem } = getDadosFormulario();
    const assunto = "Solicitação de Orçamento";
    const corpo = `Novo Orçamento:%0ANome: ${nome}%0AE-mail: ${email}%0ATelefone: ${telefone}%0AServiço: ${servico}%0AMensagem: ${mensagem}`;
    window.location.href = `mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;
  }

  function enviarSheets() {
    const dados = getDadosFormulario();
    fetch(SCRIPT_URL, {
      method: "POST",
      body: JSON.stringify(dados),
      headers: { "Content-Type": "application/json" }
    })
    .then(res => res.text())
    .then(res => alert("Orçamento salvo com sucesso na planilha!"))
    .catch(err => alert("Erro ao salvar: " + err));
  }

  // ---------------- Botão Voltar ao Topo ----------------
  const btnTopo = document.getElementById("btnTopo");
  window.onscroll = function() {
    if (document.body.scrollTop > 200 || document.documentElement.scrollTop > 200) {
      btnTopo.style.display = "block";
    } else {
      btnTopo.style.display = "none";
    }
  };
  btnTopo.addEventListener("click", () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  });
</script>
<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  /* ---------------- Cores da Marca ---------------- */
  :root {
    --primary: #0d6efd;
    --secondary: #198754;
    --success: #25D366;
    --bg-light: #f8f9fa;
    --text-dark: #212529;
  }

  body { font-family: 'Segoe UI', sans-serif; margin:0; background: var(--bg-light); color: var(--text-dark); }

  /* ---------------- Navbar Desktop ---------------- */
  .navbar-desktop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #212529;
    padding: 14px 20px;
    display: flex;
    justify-content: center;
    gap: 30px;
    z-index: 1000;
    box-shadow: 0 3px 10px rgba(0,0,0,0.2);
  }
  .navbar-desktop a {
    color: #fff;
    font-size: 15px;
    font-weight: 500;
    text-decoration: none;
    position: relative;
    padding: 5px 0;
    transition: color 0.3s;
  }
  .navbar-desktop a:hover { color: var(--primary); }
  .navbar-desktop a.active { color: var(--primary); }
  .navbar-desktop a::after {
    content:"";
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 3px;
    background: var(--primary);
    transition: width 0.3s;
    border-radius: 2px;
  }
  .navbar-desktop a:hover::after { width: 100%; }
  @media (max-width:767px) { .navbar-desktop { display:none; } }

  /* ---------------- Footer Mobile ---------------- */
  .footer-menu {
    position: fixed;
    bottom:0;
    left:0;
    width:100%;
    background:#212529;
    display:flex;
    justify-content:space-around;
    padding:10px 0;
    z-index:999;
    box-shadow: 0 -3px 10px rgba(0,0,0,0.2);
  }
  .footer-menu a {
    color:#fff;
    text-align:center;
    font-size:12px;
    flex-grow:1;
    position:relative;
    padding:5px 0;
  }
  .footer-menu a i {
    display:block;
    font-size:22px;
    margin-bottom:3px;
    transition: transform 0.2s;
  }
  .footer-menu a:hover i { transform: scale(1.2); }
  .footer-menu a span { display:none; }
  @media (min-width:768px) { .footer-menu { display:none; } }

  /* ---------------- Badge WhatsApp ---------------- */
  @keyframes blink {0%,100%{opacity:1}50%{opacity:0}}
  .whatsapp { position: relative; }
  .whatsapp .badge {
    position: absolute;
    top:-6px;
    right:-12px;
    min-width:16px;
    height:16px;
    padding:0 4px;
    background:red;
    color:white;
    font-size:10px;
    font-weight:bold;
    border-radius:50%;
    border:2px solid #212529;
    text-align:center;
    line-height:14px;
    animation: blink 1s infinite;
  }
  .footer-menu .whatsapp .badge { top:0; right:28%; }

  /* ---------------- Formulário Orçamento ---------------- */
  #orcamento {
    padding:80px 20px 120px 20px;
    background: var(--bg-light);
  }
  #orcamento form {
    max-width:700px;
    margin:auto;
    background:#fff;
    padding:40px 30px;
    border-radius:16px;
    box-shadow:0 6px 20px rgba(0,0,0,0.15);
    transition: transform 0.3s;
  }
  #orcamento form:hover { transform: translateY(-3px); }
  #orcamento h2 { text-align:center; margin-bottom:15px; font-size:28px; color:var(--text-dark); }
  #orcamento p { text-align:center; margin-bottom:30px; color:#555; }

  #orcamento .input-group {
    position: relative;
    margin-bottom:20px;
  }
  #orcamento .input-group i {
    position: absolute;
    top:50%;
    left:12px;
    transform:translateY(-50%);
    color:#888;
  }
  #orcamento input, #orcamento select, #orcamento textarea {
    width:100%;
    padding:12px 12px 12px 40px;
    border:1px solid #ddd;
    border-radius:10px;
    transition:border 0.3s, box-shadow 0.3s;
    font-size:15px;
  }
  #orcamento input:focus, #orcamento select:focus, #orcamento textarea:focus {
    border-color: var(--primary);
    box-shadow:0 0 6px rgba(13,110,253,0.3);
    outline:none;
  }
  .btn-container { display:flex; gap:15px; justify-content:center; margin-top:20px; flex-wrap:wrap; }
  .btn-container button {
    flex:1;
    padding:14px;
    color:white;
    border:none;
    border-radius:10px;
    font-size:16px;
    cursor:pointer;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .btn-container button:hover { transform: translateY(-2px); box-shadow:0 4px 10px rgba(0,0,0,0.2); }
  .btn-whatsapp { background: var(--success); }
  .btn-email { background: var(--primary); }
  .btn-sheets { background: var(--secondary); }

  /* ---------------- Botão Voltar ao Topo ---------------- */
  #btnTopo {
    position: fixed;
    bottom: 90px;
    right: 20px;
    display: none;
    z-index: 999;
    background: var(--primary);
    color:white;
    border:none;
    border-radius:50%;
    width:50px;
    height:50px;
    font-size:24px;
    cursor:pointer;
    box-shadow:0 4px 12px rgba(0,0,0,0.3);
    transition: background 0.3s, transform 0.2s;
  }
  #btnTopo:hover { background: #025ce2; transform: scale(1.1); }
</style>

<!-- ---------------- Navbar Desktop ---------------- -->
<div class="navbar-desktop">
  <a href="#bannerCarousel" class="active">Início</a>
  <a href="#servicos">Serviços</a>
  <a href="#orcamento">Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i> WhatsApp <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i> Ligar</a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i> E-mail</a>
  <a href="#faq"><i class="fas fa-question-circle"></i> FAQ</a>
</div>

<!-- ---------------- Footer Mobile ---------------- -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- ---------------- Formulário Orçamento ---------------- -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>

    <div class="input-group"><i class="fas fa-user"></i><input type="text" name="nome" placeholder="Nome *" required></div>
    <div class="input-group"><i class="fas fa-envelope"></i><input type="email" name="email" placeholder="E-mail *" required></div>
    <div class="input-group"><i class="fas fa-phone-alt"></i><input type="tel" name="telefone" placeholder="Telefone *" required></div>
    <div class="input-group"><i class="fas fa-cogs"></i>
      <select name="servico" required>
        <option value="">Selecione o serviço...</option>
        <option value="Monitoramento 24h">Monitoramento 24h</option>
        <option value="Câmeras de Segurança">Câmeras de Segurança</option>
        <option value="Alarmes">Alarmes</option>
        <option value="Controle de Acesso">Controle de Acesso</option>
      </select>
    </div>
    <div class="input-group"><i class="fas fa-comment"></i><textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea></div>

    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Planilha</button>
    </div>
  </form>
</section>

<!-- ---------------- Botão Voltar ao Topo ---------------- -->
<button id="btnTopo" title="Voltar ao Topo">↑</button>

<!-- ---------------- Script Dinâmico ---------------- -->
<script>
  const SCRIPT_URL = "COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; // Google Apps Script
  const badges = document.querySelectorAll(".whatsapp .badge");
  let mensagens = 3;
  badges.forEach(b=>b.textContent=mensagens);

  setInterval(()=>{
    const inc=Math.floor(Math.random()*3)+1;
    mensagens+=inc;
    badges.forEach(b=>b.textContent=mensagens);
  },5000);

  document.querySelectorAll(".whatsapp").forEach(btn=>{
    btn.addEventListener("click",()=>{
      mensagens=0;
      badges.forEach(b=>b.textContent=mensagens);
    });
  });

  function getDadosFormulario(){
    const f=document.getElementById("formOrcamento");
    return {nome:f.nome.value,email:f.email.value,telefone:f.telefone.value,servico:f.servico.value,mensagem:f.mensagem.value};
  }

  function enviarWhatsApp(){
    const d=getDadosFormulario();
    const txt=`*Novo Orçamento*%0A📌 Nome: ${d.nome}%0A📧 E-mail: ${d.email}%0A📱 Telefone: ${d.telefone}%0A🛠 Serviço: ${d.servico}%0A💬 Mensagem: ${d.mensagem}`;
    window.open(`https://wa.me/5511999999999?text=${txt}`,"_blank");
  }

  function enviarEmail(){
    const d=getDadosFormulario();
    const assunto="Solicitação de Orçamento";
    const corpo=`Novo Orçamento:%0ANome: ${d.nome}%0AE-mail: ${d.email}%0ATelefone: ${d.telefone}%0AServiço: ${d.servico}%0AMensagem: ${d.mensagem}`;
    window.location.href=`mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;
  }

  function enviarSheets(){
    const d=getDadosFormulario();
    fetch(SCRIPT_URL,{method:"POST",body:JSON.stringify(d),headers:{"Content-Type":"application/json"}})
    .then(res=>res.text()).then(res=>alert("Orçamento salvo com sucesso na planilha!"))
    .catch(err=>alert("Erro ao salvar: "+err));
  }

  // Voltar ao Topo
  const btnTopo=document.getElementById("btnTopo");
  window.onscroll=function(){
    if(document.body.scrollTop>200||document.documentElement.scrollTop>200){btnTopo.style.display="block";}
    else{btnTopo.style.display="none";}
  };
  btnTopo.addEventListener("click",()=>{window.scrollTo({top:0,behavior:'smooth'});});
</script>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Empresa de Monitoramento 24h</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  :root {
    --primary: #0d6efd;
    --secondary: #198754;
    --success: #25D366;
    --bg-light: #f8f9fa;
    --text-dark: #212529;
  }
  body { font-family: 'Segoe UI', sans-serif; margin:0; background: var(--bg-light); color: var(--text-dark); }

  /* Navbar Desktop */
  .navbar-desktop {
    position: fixed; top:0; left:0; width:100%; background:#212529; padding:14px 20px;
    display:flex; justify-content:center; gap:30px; z-index:1000; box-shadow:0 3px 10px rgba(0,0,0,0.2);
  }
  .navbar-desktop a { color:#fff; font-size:15px; font-weight:500; text-decoration:none; position:relative; padding:5px 0; transition:color 0.3s; }
  .navbar-desktop a:hover, .navbar-desktop a.active { color: var(--primary); }
  .navbar-desktop a::after { content:""; position:absolute; bottom:-5px; left:0; width:0; height:3px; background: var(--primary); transition:width 0.3s; border-radius:2px; }
  .navbar-desktop a:hover::after, .navbar-desktop a.active::after { width:100%; }
  @media(max-width:767px){ .navbar-desktop{display:none;} }

  /* Footer Mobile */
  .footer-menu {
    position: fixed; bottom:0; left:0; width:100%; background:#212529;
    display:flex; justify-content:space-around; padding:10px 0; z-index:999; box-shadow:0 -3px 10px rgba(0,0,0,0.2);
  }
  .footer-menu a { color:#fff; text-align:center; font-size:12px; flex-grow:1; position:relative; padding:5px 0; }
  .footer-menu a i { display:block; font-size:22px; margin-bottom:3px; transition:transform 0.2s; }
  .footer-menu a:hover i { transform: scale(1.2); }
  .footer-menu a span { display:none; }
  @media(min-width:768px){ .footer-menu{display:none;} }

  /* Badge WhatsApp */
  @keyframes blink {0%,100%{opacity:1}50%{opacity:0}}
  .whatsapp { position: relative; }
  .whatsapp .badge {
    position:absolute; top:-6px; right:-12px; min-width:16px; height:16px; padding:0 4px;
    background:red; color:white; font-size:10px; font-weight:bold; border-radius:50%;
    border:2px solid #212529; text-align:center; line-height:14px; animation:blink 1s infinite;
  }
  .footer-menu .whatsapp .badge { top:0; right:28%; }

  /* Formulário Orçamento */
  #orcamento { padding:80px 20px 120px 20px; background: var(--bg-light); }
  #orcamento form { max-width:700px; margin:auto; background:#fff; padding:40px 30px; border-radius:16px; box-shadow:0 6px 20px rgba(0,0,0,0.15); transition:transform 0.3s; }
  #orcamento form:hover { transform:translateY(-3px); }
  #orcamento h2 { text-align:center; margin-bottom:15px; font-size:28px; color:var(--text-dark); }
  #orcamento p { text-align:center; margin-bottom:30px; color:#555; }
  .input-group { position: relative; margin-bottom:20px; }
  .input-group i { position:absolute; top:50%; left:12px; transform:translateY(-50%); color:#888; }
  #orcamento input, #orcamento select, #orcamento textarea {
    width:100%; padding:12px 12px 12px 40px; border:1px solid #ddd; border-radius:10px; transition:border 0.3s, box-shadow 0.3s; font-size:15px;
  }
  #orcamento input:focus, #orcamento select:focus, #orcamento textarea:focus {
    border-color: var(--primary); box-shadow:0 0 6px rgba(13,110,253,0.3); outline:none;
  }
  .btn-container { display:flex; gap:15px; justify-content:center; margin-top:20px; flex-wrap:wrap; }
  .btn-container button { flex:1; padding:14px; color:white; border:none; border-radius:10px; font-size:16px; cursor:pointer; transition:transform 0.2s, box-shadow 0.2s; }
  .btn-container button:hover { transform:translateY(-2px); box-shadow:0 4px 10px rgba(0,0,0,0.2); }
  .btn-whatsapp { background: var(--success); }
  .btn-email { background: var(--primary); }
  .btn-sheets { background: var(--secondary); }

  /* Botão Voltar ao Topo */
  #btnTopo {
    position: fixed; bottom:90px; right:20px; display:none; z-index:999; background:var(--primary); color:white;
    border:none; border-radius:50%; width:50px; height:50px; font-size:24px; cursor:pointer; box-shadow:0 4px 12px rgba(0,0,0,0.3);
    transition: background 0.3s, transform 0.2s;
  }
  #btnTopo:hover { background:#025ce2; transform:scale(1.1); }
</style>
</head>
<body>

<!-- Navbar Desktop -->
<div class="navbar-desktop">
  <a href="#bannerCarousel" class="active">Início</a>
  <a href="#servicos">Serviços</a>
  <a href="#orcamento">Orçamento</a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i> WhatsApp <span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i> Ligar</a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i> E-mail</a>
  <a href="#faq"><i class="fas fa-question-circle"></i> FAQ</a>
</div>

<!-- Footer Mobile -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp">
    <i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span>
  </a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
  <a href="#faq"><i class="fas fa-question-circle"></i><span>FAQ</span></a>
</div>

<!-- Formulário Orçamento -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>

    <div class="input-group"><i class="fas fa-user"></i><input type="text" name="nome" placeholder="Nome *" required></div>
    <div class="input-group"><i class="fas fa-envelope"></i><input type="email" name="email" placeholder="E-mail *" required></div>
    <div class="input-group"><i class="fas fa-phone-alt"></i><input type="tel" name="telefone" placeholder="Telefone *" required></div>
    <div class="input-group"><i class="fas fa-cogs"></i>
      <select name="servico" required>
        <option value="">Selecione o serviço...</option>
        <option value="Monitoramento 24h">Monitoramento 24h</option>
        <option value="Câmeras de Segurança">Câmeras de Segurança</option>
        <option value="Alarmes">Alarmes</option>
        <option value="Controle de Acesso">Controle de Acesso</option>
      </select>
    </div>
    <div class="input-group"><i class="fas fa-comment"></i><textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea></div>

    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Planilha</button>
    </div>
  </form>
</section>

<!-- Botão Voltar ao Topo -->
<button id="btnTopo" title="Voltar ao Topo">↑</button>

<!-- Script Dinâmico -->
<script>
const SCRIPT_URL="COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; // Google Apps Script
const badges=document.querySelectorAll(".whatsapp .badge");
let mensagens=3;
badges.forEach(b=>b.textContent=mensagens);
setInterval(()=>{
  const inc=Math.floor(Math.random()*3)+1;
  mensagens+=inc;
  badges.forEach(b=>b.textContent=mensagens);
},5000);
document.querySelectorAll(".whatsapp").forEach(btn=>{btn.addEventListener("click",()=>{mensagens=0; badges.forEach(b=>b.textContent=mensagens);});});

function getDadosFormulario(){
  const f=document.getElementById("formOrcamento");
  return {nome:f.nome.value,email:f.email.value,telefone:f.telefone.value,servico:f.servico.value,mensagem:f.mensagem.value};
}

function enviarWhatsApp(){
  const d=getDadosFormulario();
  const txt=`*Novo Orçamento*%0A📌 Nome: ${d.nome}%0A📧 E-mail: ${d.email}%0A📱 Telefone: ${d.telefone}%0A🛠 Serviço: ${d.servico}%0A💬 Mensagem: ${d.mensagem}`;
  window.open(`https://wa.me/5511999999999?text=${txt}`,"_blank");
}

function enviarEmail(){
  const d=getDadosFormulario();
  const assunto="Solicitação de Orçamento";
  const corpo=`Novo Orçamento:%0ANome: ${d.nome}%0AE-mail: ${d.email}%0ATelefone: ${d.telefone}%0AServiço: ${d.servico}%0AMensagem: ${d.mensagem}`;
  window.location.href=`mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;
}

function enviarSheets(){
  const d=getDadosFormulario();
  fetch(SCRIPT_URL,{method:"POST",body:JSON.stringify(d),headers:{"Content-Type":"application/json"}})
  .then(res=>res.text()).then(res=>alert("Orçamento salvo com sucesso na planilha!"))
  .catch(err=>alert("Erro ao salvar: "+err));
}

// Botão Voltar ao Topo
const btnTopo=document.getElementById("btnTopo");
window.onscroll=function(){
  if(document.body.scrollTop>200||document.documentElement.scrollTop>200){btnTopo.style.display="block";}
  else{btnTopo.style.display="none";}
};
btnTopo.addEventListener("click",()=>{window.scrollTo({top:0,behavior:'smooth'});});
</script>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Monitoramento 24h - Sua Empresa</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
:root {
  --primary:#0d6efd; --secondary:#198754; --success:#25D366;
  --bg-light:#f8f9fa; --text-dark:#212529; --accent:#f1f1f1;
}
body{margin:0;font-family:'Segoe UI',sans-serif;background:var(--bg-light);color:var(--text-dark);}
/* ---------------- Banner ---------------- */
#bannerCarousel{
  height:400px;
  background:url('https://images.unsplash.com/photo-1601582581264-f3a204ae1586?auto=format&fit=crop&w=1950&q=80') center/cover no-repeat;
  display:flex;align-items:center;justify-content:center;color:white;text-align:center;
}
#bannerCarousel h1{font-size:42px;text-shadow:2px 2px 6px rgba(0,0,0,0.6);}
#bannerCarousel p{font-size:20px;text-shadow:1px 1px 4px rgba(0,0,0,0.5);}
/* ---------------- Navbar Desktop ---------------- */
.navbar-desktop{position:fixed;top:0;left:0;width:100%;background:#212529;display:flex;align-items:center;justify-content:space-between;padding:10px 20px;z-index:1000;box-shadow:0 3px 10px rgba(0,0,0,0.2);}
.navbar-desktop .logo{height:40px;}
.navbar-desktop nav{display:flex;gap:25px;}
.navbar-desktop a{color:#fff;text-decoration:none;font-weight:500;position:relative;transition:color 0.3s;}
.navbar-desktop a:hover, .navbar-desktop a.active{color:var(--primary);}
.navbar-desktop a::after{content:"";position:absolute;bottom:-5px;left:0;width:0;height:3px;background:var(--primary);transition:width 0.3s;border-radius:2px;}
.navbar-desktop a:hover::after,.navbar-desktop a.active::after{width:100%;}
@media(max-width:767px){.navbar-desktop{display:none;}}
/* ---------------- Footer Mobile ---------------- */
.footer-menu{position:fixed;bottom:0;left:0;width:100%;background:#212529;display:flex;justify-content:space-around;padding:10px 0;z-index:999;box-shadow:0 -3px 10px rgba(0,0,0,0.2);}
.footer-menu a{color:#fff;text-align:center;font-size:12px;flex-grow:1;position:relative;padding:5px 0;}
.footer-menu a i{display:block;font-size:22px;margin-bottom:3px;transition:transform 0.2s;}
.footer-menu a:hover i{transform:scale(1.2);}
.footer-menu a span{display:none;}
@media(min-width:768px){.footer-menu{display:none;}}
/* ---------------- Badge WhatsApp ---------------- */
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.whatsapp{position:relative;}
.whatsapp .badge{position:absolute;top:-6px;right:-12px;min-width:16px;height:16px;padding:0 4px;background:red;color:white;font-size:10px;font-weight:bold;border-radius:50%;border:2px solid #212529;text-align:center;line-height:14px;animation:blink 1s infinite;}
.footer-menu .whatsapp .badge{top:0;right:28%;}
/* ---------------- Seção Serviços ---------------- */
#servicos{padding:80px 20px;text-align:center;background:var(--accent);}
#servicos h2{font-size:32px;margin-bottom:40px;}
.servico-box{display:flex;flex-direction:column;align-items:center;gap:15px;background:white;padding:25px;border-radius:16px;box-shadow:0 4px 12px rgba(0,0,0,0.1);transition:transform 0.3s;}
.servico-box:hover{transform:translateY(-5px);}
.servico-box i{font-size:36px;color:var(--primary);}
/* ---------------- Formulário Orçamento ---------------- */
#orcamento{padding:80px 20px 120px 20px;background:var(--bg-light);}
#orcamento form{max-width:700px;margin:auto;background:#fff;padding:40px 30px;border-radius:16px;box-shadow:0 6px 20px rgba(0,0,0,0.15);transition:transform 0.3s;}
#orcamento form:hover{transform:translateY(-3px);}
#orcamento h2{text-align:center;margin-bottom:15px;font-size:28px;}
#orcamento p{text-align:center;margin-bottom:30px;color:#555;}
.input-group{position:relative;margin-bottom:20px;}
.input-group i{position:absolute;top:50%;left:12px;transform:translateY(-50%);color:#888;}
#orcamento input,#orcamento select,#orcamento textarea{width:100%;padding:12px 12px 12px 40px;border:1px solid #ddd;border-radius:10px;transition:border 0.3s,box-shadow 0.3s;font-size:15px;}
#orcamento input:focus,#orcamento select:focus,#orcamento textarea:focus{border-color:var(--primary);box-shadow:0 0 6px rgba(13,110,253,0.3);outline:none;}
.btn-container{display:flex;gap:15px;justify-content:center;margin-top:20px;flex-wrap:wrap;}
.btn-container button{flex:1;padding:14px;color:white;border:none;border-radius:10px;font-size:16px;cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;}
.btn-container button:hover{transform:translateY(-2px);box-shadow:0 4px 10px rgba(0,0,0,0.2);}
.btn-whatsapp{background:var(--success);}
.btn-email{background:var(--primary);}
.btn-sheets{background:var(--secondary);}
/* Botão Voltar ao Topo */
#btnTopo{position:fixed;bottom:90px;right:20px;display:none;z-index:999;background:var(--primary);color:white;border:none;border-radius:50%;width:50px;height:50px;font-size:24px;cursor:pointer;box-shadow:0 4px 12px rgba(0,0,0,0.3);transition:background 0.3s,transform 0.2s;}
#btnTopo:hover{background:#025ce2;transform:scale(1.1);}
</style>
</head>
<body>

<!-- Banner -->
<section id="bannerCarousel">
  <div>
    <h1>Segurança 24h para Sua Empresa</h1>
    <p>Monitoramento confiável, ágil e moderno</p>
  </div>
</section>

<!-- Navbar Desktop -->
<div class="navbar-desktop">
  <img src="https://via.placeholder.com/150x40?text=Logo" alt="Logo" class="logo">
  <nav>
    <a href="#bannerCarousel" class="active">Início</a>
    <a href="#servicos">Serviços</a>
    <a href="#orcamento">Orçamento</a>
    <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp <span class="badge">3</span></a>
    <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i> Ligar</a>
    <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i> E-mail</a>
  </nav>
</div>

<!-- Seção Serviços -->
<section id="servicos">
  <h2>Nossos Serviços</h2>
  <div style="display:flex;gap:20px;flex-wrap:wrap;justify-content:center;">
    <div class="servico-box"><i class="fas fa-video"></i><h3>Monitoramento 24h</h3></div>
    <div class="servico-box"><i class="fas fa-camera"></i><h3>Câmeras de Segurança</h3></div>
    <div class="servico-box"><i class="fas fa-bell"></i><h3>Alarmes</h3></div>
    <div class="servico-box"><i class="fas fa-key"></i><h3>Controle de Acesso</h3></div>
  </div>
</section>

<!-- Formulário Orçamento -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>
    <div class="input-group"><i class="fas fa-user"></i><input type="text" name="nome" placeholder="Nome *" required></div>
    <div class="input-group"><i class="fas fa-envelope"></i><input type="email" name="email" placeholder="E-mail *" required></div>
    <div class="input-group"><i class="fas fa-phone-alt"></i><input type="tel" name="telefone" placeholder="Telefone *" required></div>
    <div class="input-group"><i class="fas fa-cogs"></i>
      <select name="servico" required>
        <option value="">Selecione o serviço...</option>
        <option value="Monitoramento 24h">Monitoramento 24h</option>
        <option value="Câmeras de Segurança">Câmeras de Segurança</option>
        <option value="Alarmes">Alarmes</option>
        <option value="Controle de Acesso">Controle de Acesso</option>
      </select>
    </div>
    <div class="input-group"><i class="fas fa-comment"></i><textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea></div>
    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Planilha</button>
    </div>
  </form>
</section>

<!-- Footer Mobile -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp"><i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span></a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
</div>

<!-- Botão Voltar ao Topo -->
<button id="btnTopo" title="Voltar ao Topo">↑</button>

<script>
// Configurações
const SCRIPT_URL="COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; 
const badges=document.querySelectorAll(".whatsapp .badge");
let mensagens=3;
badges.forEach(b=>b.textContent=mensagens);
setInterval(()=>{
  const inc=Math.floor(Math.random()*3)+1; mensagens+=inc; badges.forEach(b=>b.textContent=mensagens);
},5000);
document.querySelectorAll(".whatsapp").forEach(btn=>{btn.addEventListener("click",()=>{mensagens=0; badges.forEach(b=>b.textContent=mensagens);});});

// Formulário
function getDadosFormulario(){const f=document.getElementById("formOrcamento"); return {nome:f.nome.value,email:f.email.value,telefone:f.telefone.value,servico:f.servico.value,mensagem:f.mensagem.value};}
function enviarWhatsApp(){const d=getDadosFormulario(); const txt=`*Novo Orçamento*%0A📌 Nome: ${d.nome}%0A📧 E-mail: ${d.email}%0A📱 Telefone: ${d.telefone}%0A🛠 Serviço: ${d.servico}%0A💬 Mensagem: ${d.mensagem}`; window.open(`https://wa.me/5511999999999?text=${txt}`,"_blank");}
function enviarEmail(){const d=getDadosFormulario(); const assunto="Solicitação de Orçamento"; const corpo=`Novo Orçamento:%0ANome: ${d.nome}%0AE-mail: ${d.email}%0ATelefone: ${d.telefone}%0AServiço: ${d.servico}%0AMensagem: ${d.mensagem}`; window.location.href=`mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;}
function enviarSheets(){const d=getDadosFormulario(); fetch(SCRIPT_URL,{method:"POST",body:JSON.stringify(d),headers:{"Content-Type":"application/json"}}).then(res=>res.text()).then(res=>alert("Orçamento salvo com sucesso na planilha!")).catch(err=>alert("Erro ao salvar: "+err));}

// Voltar ao Topo
const btnTopo=document.getElementById("btnTopo");
window.onscroll=function(){if(document.body.scrollTop>200||document.documentElement.scrollTop>200){btnTopo.style.display="block";}else{btnTopo.style.display="none";}};
btnTopo.addEventListener("click",()=>{window.scrollTo({top:0,behavior:'smooth'});});
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Monitoramento 24h - Sua Empresa</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
:root {
  --primary:#001f3f; /* azul marinho */
  --secondary:#C0C0C0; /* prata */
  --success:#25D366;
  --bg-light:#f8f9fa;
  --text-dark:#212529;
  --accent:#e6e6e6;
}
body{margin:0;font-family:'Segoe UI',sans-serif;background:var(--bg-light);color:var(--text-dark);}
/* ---------------- Banner ---------------- */
#bannerCarousel{
  height:400px;
  background:url('https://images.unsplash.com/photo-1601582581264-f3a204ae1586?auto=format&fit=crop&w=1950&q=80') center/cover no-repeat;
  display:flex;align-items:center;justify-content:center;color:white;text-align:center;
}
#bannerCarousel h1{font-size:42px;text-shadow:2px 2px 6px rgba(0,0,0,0.6);}
#bannerCarousel p{font-size:20px;text-shadow:1px 1px 4px rgba(0,0,0,0.5);}

/* ---------------- Navbar Desktop ---------------- */
.navbar-desktop{position:fixed;top:0;left:0;width:100%;background:var(--primary);display:flex;align-items:center;justify-content:space-between;padding:10px 20px;z-index:1000;box-shadow:0 3px 10px rgba(0,0,0,0.2);}
.navbar-desktop .logo{height:40px;}
.navbar-desktop nav{display:flex;gap:25px;}
.navbar-desktop a{color:var(--secondary);text-decoration:none;font-weight:500;position:relative;transition:color 0.3s;}
.navbar-desktop a:hover, .navbar-desktop a.active{color:white;}
.navbar-desktop a::after{content:"";position:absolute;bottom:-5px;left:0;width:0;height:3px;background:white;transition:width 0.3s;border-radius:2px;}
.navbar-desktop a:hover::after,.navbar-desktop a.active::after{width:100%;}
@media(max-width:767px){.navbar-desktop{display:none;}}

/* Footer Mobile */
.footer-menu{position:fixed;bottom:0;left:0;width:100%;background:var(--primary);display:flex;justify-content:space-around;padding:10px 0;z-index:999;box-shadow:0 -3px 10px rgba(0,0,0,0.2);}
.footer-menu a{color:var(--secondary);text-align:center;font-size:12px;flex-grow:1;position:relative;padding:5px 0;}
.footer-menu a i{display:block;font-size:22px;margin-bottom:3px;transition:transform 0.2s;}
.footer-menu a:hover i{transform:scale(1.2);}
.footer-menu a span{display:none;}
@media(min-width:768px){.footer-menu{display:none;}}

/* Badge WhatsApp */
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.whatsapp{position:relative;}
.whatsapp .badge{position:absolute;top:-6px;right:-12px;min-width:16px;height:16px;padding:0 4px;background:red;color:white;font-size:10px;font-weight:bold;border-radius:50%;border:2px solid var(--primary);text-align:center;line-height:14px;animation:blink 1s infinite;}
.footer-menu .whatsapp .badge{top:0;right:28%;}

/* Seção Serviços */
#servicos{padding:80px 20px;text-align:center;background:var(--accent);}
#servicos h2{font-size:32px;margin-bottom:40px;color:var(--primary);}
.servico-box{display:flex;flex-direction:column;align-items:center;gap:15px;background:white;padding:25px;border-radius:16px;box-shadow:0 4px 12px rgba(0,0,0,0.1);transition:transform 0.3s;}
.servico-box:hover{transform:translateY(-5px);}
.servico-box i{font-size:36px;color:var(--primary);}
.servico-box h3{color:var(--primary);}

/* Formulário Orçamento */
#orcamento{padding:80px 20px 120px 20px;background:var(--bg-light);}
#orcamento form{max-width:700px;margin:auto;background:#fff;padding:40px 30px;border-radius:16px;box-shadow:0 6px 20px rgba(0,0,0,0.15);transition:transform 0.3s;}
#orcamento form:hover{transform:translateY(-3px);}
#orcamento h2{text-align:center;margin-bottom:15px;font-size:28px;color:var(--primary);}
#orcamento p{text-align:center;margin-bottom:30px;color:var(--text-dark);}
.input-group{position:relative;margin-bottom:20px;}
.input-group i{position:absolute;top:50%;left:12px;transform:translateY(-50%);color:#888;}
#orcamento input,#orcamento select,#orcamento textarea{width:100%;padding:12px 12px 12px 40px;border:1px solid #ddd;border-radius:10px;transition:border 0.3s,box-shadow 0.3s;font-size:15px;}
#orcamento input:focus,#orcamento select:focus,#orcamento textarea:focus{border-color:var(--primary);box-shadow:0 0 6px rgba(0,0,0,0.3);outline:none;}
.btn-container{display:flex;gap:15px;justify-content:center;margin-top:20px;flex-wrap:wrap;}
.btn-container button{flex:1;padding:14px;color:white;border:none;border-radius:10px;font-size:16px;cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;}
.btn-container button:hover{transform:translateY(-2px);box-shadow:0 4px 10px rgba(0,0,0,0.2);}
.btn-whatsapp{background:#25D366;}
.btn-email{background:var(--primary);}
.btn-sheets{background:var(--secondary);}

/* Botão Voltar ao Topo */
#btnTopo{position:fixed;bottom:90px;right:20px;display:none;z-index:999;background:var(--primary);color:white;border:none;border-radius:50%;width:50px;height:50px;font-size:24px;cursor:pointer;box-shadow:0 4px 12px rgba(0,0,0,0.3);transition:background 0.3s,transform 0.2s;}
#btnTopo:hover{background:#000033;transform:scale(1.1);}
</style>
</head>
<body>

<!-- Banner -->
<section id="bannerCarousel">
  <div>
    <h1>Segurança 24h para Sua Empresa</h1>
    <p>Monitoramento confiável, ágil e moderno</p>
  </div>
</section>

<!-- Navbar Desktop -->
<div class="navbar-desktop">
  <img src="https://via.placeholder.com/150x40?text=Logo" alt="Logo" class="logo">
  <nav>
    <a href="#bannerCarousel" class="active">Início</a>
    <a href="#servicos">Serviços</a>
    <a href="#orcamento">Orçamento</a>
    <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp <span class="badge">3</span></a>
    <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i> Ligar</a>
    <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i> E-mail</a>
  </nav>
</div>

<!-- Seção Serviços -->
<section id="servicos">
  <h2>Nossos Serviços</h2>
  <div style="display:flex;gap:20px;flex-wrap:wrap;justify-content:center;">
    <div class="servico-box"><i class="fas fa-video"></i><h3>Monitoramento 24h</h3></div>
    <div class="servico-box"><i class="fas fa-camera"></i><h3>Câmeras de Segurança</h3></div>
    <div class="servico-box"><i class="fas fa-bell"></i><h3>Alarmes</h3></div>
    <div class="servico-box"><i class="fas fa-key"></i><h3>Controle de Acesso</h3></div>
  </div>
</section>

<!-- Formulário Orçamento -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>
    <div class="input-group"><i class="fas fa-user"></i><input type="text" name="nome" placeholder="Nome *" required></div>
    <div class="input-group"><i class="fas fa-envelope"></i><input type="email" name="email" placeholder="E-mail *" required></div>
    <div class="input-group"><i class="fas fa-phone-alt"></i><input type="tel" name="telefone" placeholder="Telefone *" required></div>
    <div class="input-group"><i class="fas fa-cogs"></i>
      <select name="servico" required>
        <option value="">Selecione o serviço...</option>
        <option value="Monitoramento 24h">Monitoramento 24h</option>
        <option value="Câmeras de Segurança">Câmeras de Segurança</option>
        <option value="Alarmes">Alarmes</option>
        <option value="Controle de Acesso">Controle de Acesso</option>
      </select>
    </div>
    <div class="input-group"><i class="fas fa-comment"></i><textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea></div>
    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Planilha</button>
    </div>
  </form>
</section>

<!-- Footer Mobile -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp"><i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span></a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
</div>

<!-- Botão Voltar ao Topo -->
<button id="btnTopo" title="Voltar ao Topo">↑</button>

<script>
const SCRIPT_URL="COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; 
const badges=document.querySelectorAll(".whatsapp .badge");
let mensagens=3;
badges.forEach(b=>b.textContent=mensagens);
setInterval(()=>{const inc=Math.floor(Math.random()*3)+1; mensagens+=inc; badges.forEach(b=>b.textContent=mensagens);},5000);
document.querySelectorAll(".whatsapp").forEach(btn=>{btn.addEventListener("click",()=>{mensagens=0; badges.forEach(b=>b.textContent=mensagens);});});
function getDadosFormulario(){const f=document.getElementById("formOrcamento"); return {nome:f.nome.value,email:f.email.value,telefone:f.telefone.value,servico:f.servico.value,mensagem:f.mensagem.value};}
function enviarWhatsApp(){const d=getDadosFormulario(); const txt=`*Novo Orçamento*%0A📌 Nome: ${d.nome}%0A📧 E-mail: ${d.email}%0A📱 Telefone: ${d.telefone}%0A🛠 Serviço: ${d.servico}%0A💬 Mensagem: ${d.mensagem}`; window.open(`https://wa.me/5511999999999?text=${txt}`,"_blank");}
function enviarEmail(){const d=getDadosFormulario(); const assunto="Solicitação de Orçamento"; const corpo=`Novo Orçamento:%0ANome: ${d.nome}%0AE-mail: ${d.email}%0ATelefone: ${d.telefone}%0AServiço: ${d.servico}%0AMensagem: ${d.mensagem}`; window.location.href=`mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;}
function enviarSheets(){const d=getDadosFormulario(); fetch(SCRIPT_URL,{method:"POST",body:JSON.stringify(d),headers:{"Content-Type":"application/json"}}).then(res=>res.text()).then(res=>alert("Orçamento salvo com sucesso na planilha!")).catch(err=>alert("Erro ao salvar: "+err));}
const btnTopo=document.getElementById("btnTopo");
window.onscroll=function(){if(document.body.scrollTop>200||document.documentElement.scrollTop>200){btnTopo.style.display="block";}else{btnTopo.style.display="none";}};
btnTopo.addEventListener("click",()=>{window.scrollTo({top:0,behavior:'smooth'});});
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Monitoramento 24h - Sua Empresa</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
:root {
  --primary:#001f3f; /* azul marinho */
  --secondary:#C0C0C0; /* prata */
  --success:#25D366;
  --bg-light:#f8f9fa;
  --text-dark:#212529;
  --accent:#e6e6e6;
}
body{margin:0;font-family:'Segoe UI',sans-serif;background:var(--bg-light);color:var(--text-dark);}

/* Banner */
#bannerCarousel{
  height:450px;
  background:url('https://images.unsplash.com/photo-1601582581264-f3a204ae1586?auto=format&fit=crop&w=1950&q=80') center/cover no-repeat;
  display:flex;align-items:center;justify-content:center;color:white;text-align:center;
}
#bannerCarousel h1{font-size:46px;text-shadow:2px 2px 6px rgba(0,0,0,0.6);}
#bannerCarousel p{font-size:22px;text-shadow:1px 1px 4px rgba(0,0,0,0.5);}

/* Navbar Desktop */
.navbar-desktop{position:fixed;top:0;left:0;width:100%;background:var(--primary);display:flex;align-items:center;justify-content:space-between;padding:10px 20px;z-index:1000;box-shadow:0 3px 10px rgba(0,0,0,0.2);}
.navbar-desktop .logo{height:50px;}
.navbar-desktop nav{display:flex;gap:25px;}
.navbar-desktop a{color:var(--secondary);text-decoration:none;font-weight:500;position:relative;transition:color 0.3s;}
.navbar-desktop a:hover, .navbar-desktop a.active{color:white;}
.navbar-desktop a::after{content:"";position:absolute;bottom:-5px;left:0;width:0;height:3px;background:white;transition:width 0.3s;border-radius:2px;}
.navbar-desktop a:hover::after,.navbar-desktop a.active::after{width:100%;}
@media(max-width:767px){.navbar-desktop{display:none;}}

/* Footer Mobile */
.footer-menu{position:fixed;bottom:0;left:0;width:100%;background:var(--primary);display:flex;justify-content:space-around;padding:10px 0;z-index:999;box-shadow:0 -3px 10px rgba(0,0,0,0.2);}
.footer-menu a{color:var(--secondary);text-align:center;font-size:12px;flex-grow:1;position:relative;padding:5px 0;}
.footer-menu a i{display:block;font-size:22px;margin-bottom:3px;transition:transform 0.2s;}
.footer-menu a:hover i{transform:scale(1.2);}
.footer-menu a span{display:none;}
@media(min-width:768px){.footer-menu{display:none;}}

/* Badge WhatsApp */
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.whatsapp{position:relative;}
.whatsapp .badge{position:absolute;top:-6px;right:-12px;min-width:16px;height:16px;padding:0 4px;background:red;color:white;font-size:10px;font-weight:bold;border-radius:50%;border:2px solid var(--primary);text-align:center;line-height:14px;animation:blink 1s infinite;}
.footer-menu .whatsapp .badge{top:0;right:28%;}

/* Seção Serviços */
#servicos{padding:80px 20px;text-align:center;background:var(--accent);}
#servicos h2{font-size:34px;margin-bottom:40px;color:var(--primary);}
.servico-box{display:flex;flex-direction:column;align-items:center;gap:15px;background:white;padding:25px;border-radius:16px;box-shadow:0 4px 12px rgba(0,0,0,0.1);transition:transform 0.3s;}
.servico-box:hover{transform:translateY(-5px);}
.servico-box i{font-size:36px;color:var(--primary);}
.servico-box h3{color:var(--primary);}

/* Formulário Orçamento */
#orcamento{padding:80px 20px 120px 20px;background:var(--bg-light);}
#orcamento form{max-width:700px;margin:auto;background:#fff;padding:40px 30px;border-radius:16px;box-shadow:0 6px 20px rgba(0,0,0,0.15);transition:transform 0.3s;}
#orcamento form:hover{transform:translateY(-3px);}
#orcamento h2{text-align:center;margin-bottom:15px;font-size:30px;color:var(--primary);}
#orcamento p{text-align:center;margin-bottom:30px;color:var(--text-dark);}
.input-group{position:relative;margin-bottom:20px;}
.input-group i{position:absolute;top:50%;left:12px;transform:translateY(-50%);color:#888;}
#orcamento input,#orcamento select,#orcamento textarea{width:100%;padding:12px 12px 12px 40px;border:1px solid #ddd;border-radius:10px;transition:border 0.3s,box-shadow 0.3s;font-size:15px;}
#orcamento input:focus,#orcamento select:focus,#orcamento textarea:focus{border-color:var(--primary);box-shadow:0 0 6px rgba(0,0,0,0.3);outline:none;}
.btn-container{display:flex;gap:15px;justify-content:center;margin-top:20px;flex-wrap:wrap;}
.btn-container button{flex:1;padding:14px;color:white;border:none;border-radius:10px;font-size:16px;cursor:pointer;transition:transform 0.2s,box-shadow 0.2s;}
.btn-container button:hover{transform:translateY(-2px);box-shadow:0 4px 10px rgba(0,0,0,0.2);}
.btn-whatsapp{background:#25D366;}
.btn-email{background:var(--primary);}
.btn-sheets{background:var(--secondary);}

/* Botão Voltar ao Topo */
#btnTopo{position:fixed;bottom:90px;right:20px;display:none;z-index:999;background:var(--primary);color:white;border:none;border-radius:50%;width:50px;height:50px;font-size:24px;cursor:pointer;box-shadow:0 4px 12px rgba(0,0,0,0.3);transition:background 0.3s,transform 0.2s;}
#btnTopo:hover{background:#000033;transform:scale(1.1);}
</style>
</head>
<body>

<!-- Banner -->
<section id="bannerCarousel">
  <div>
    <h1>Segurança 24h para Sua Empresa</h1>
    <p>Monitoramento confiável, ágil e moderno</p>
  </div>
</section>

<!-- Navbar Desktop -->
<div class="navbar-desktop">
  <img src="https://via.placeholder.com/150x50?text=Sua+Logo" alt="Logo" class="logo">
  <nav>
    <a href="#bannerCarousel" class="active">Início</a>
    <a href="#servicos">Serviços</a>
    <a href="#orcamento">Orçamento</a>
    <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp <span class="badge">3</span></a>
    <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i> Ligar</a>
    <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i> E-mail</a>
  </nav>
</div>

<!-- Seção Serviços -->
<section id="servicos">
  <h2>Nossos Serviços</h2>
  <div style="display:flex;gap:20px;flex-wrap:wrap;justify-content:center;">
    <div class="servico-box"><i class="fas fa-video"></i><h3>Monitoramento 24h</h3></div>
    <div class="servico-box"><i class="fas fa-camera"></i><h3>Câmeras de Segurança</h3></div>
    <div class="servico-box"><i class="fas fa-bell"></i><h3>Alarmes</h3></div>
    <div class="servico-box"><i class="fas fa-key"></i><h3>Controle de Acesso</h3></div>
  </div>
</section>

<!-- Formulário Orçamento -->
<section id="orcamento">
  <form id="formOrcamento">
    <h2>Solicite um Orçamento</h2>
    <p>Preencha o formulário abaixo e retornaremos o mais rápido possível.</p>
    <div class="input-group"><i class="fas fa-user"></i><input type="text" name="nome" placeholder="Nome *" required></div>
    <div class="input-group"><i class="fas fa-envelope"></i><input type="email" name="email" placeholder="E-mail *" required></div>
    <div class="input-group"><i class="fas fa-phone-alt"></i><input type="tel" name="telefone" placeholder="Telefone *" required></div>
    <div class="input-group"><i class="fas fa-cogs"></i>
      <select name="servico" required>
        <option value="">Selecione o serviço...</option>
        <option value="Monitoramento 24h">Monitoramento 24h</option>
        <option value="Câmeras de Segurança">Câmeras de Segurança</option>
        <option value="Alarmes">Alarmes</option>
        <option value="Controle de Acesso">Controle de Acesso</option>
      </select>
    </div>
    <div class="input-group"><i class="fas fa-comment"></i><textarea name="mensagem" rows="4" placeholder="Mensagem"></textarea></div>
    <div class="btn-container">
      <button type="button" onclick="enviarWhatsApp()" class="btn-whatsapp"><i class="fab fa-whatsapp"></i> WhatsApp</button>
      <button type="button" onclick="enviarEmail()" class="btn-email"><i class="fas fa-envelope"></i> E-mail</button>
      <button type="button" onclick="enviarSheets()" class="btn-sheets"><i class="fas fa-table"></i> Planilha</button>
    </div>
  </form>
</section>

<!-- Footer Mobile -->
<div class="footer-menu">
  <a href="#bannerCarousel"><i class="fas fa-home"></i><span>Início</span></a>
  <a href="#servicos"><i class="fas fa-shield-alt"></i><span>Serviços</span></a>
  <a href="#orcamento"><i class="fas fa-file-invoice-dollar"></i><span>Orçamento</span></a>
  <a href="https://wa.me/5511999999999?text=Olá! Gostaria de saber mais sobre os serviços de monitoramento." target="_blank" class="whatsapp"><i class="fab fa-whatsapp"></i><span>WhatsApp</span><span class="badge">3</span></a>
  <a href="tel:+5511999999999"><i class="fas fa-phone-alt"></i><span>Ligar</span></a>
  <a href="mailto:contato@suaempresa.com"><i class="fas fa-envelope"></i><span>E-mail</span></a>
</div>

<!-- Botão Voltar ao Topo -->
<button id="btnTopo" title="Voltar ao Topo">↑</button>

<script>
const SCRIPT_URL="COLE_AQUI_SUA_URL_DO_APPS_SCRIPT"; 
const badges=document.querySelectorAll(".whatsapp .badge");
let mensagens=3;
badges.forEach(b=>b.textContent=mensagens);
setInterval(()=>{const inc=Math.floor(Math.random()*3)+1; mensagens+=inc; badges.forEach(b=>b.textContent=mensagens);},5000);
document.querySelectorAll(".whatsapp").forEach(btn=>{btn.addEventListener("click",()=>{mensagens=0; badges.forEach(b=>b.textContent=mensagens);});});
function getDadosFormulario(){const f=document.getElementById("formOrcamento"); return {nome:f.nome.value,email:f.email.value,telefone:f.telefone.value,servico:f.servico.value,mensagem:f.mensagem.value};}
function enviarWhatsApp(){const d=getDadosFormulario(); const txt=`*Novo Orçamento*%0A📌 Nome: ${d.nome}%0A📧 E-mail: ${d.email}%0A📱 Telefone: ${d.telefone}%0A🛠 Serviço: ${d.servico}%0A💬 Mensagem: ${d.mensagem}`; window.open(`https://wa.me/5511999999999?text=${txt}`,"_blank");}
function enviarEmail(){const d=getDadosFormulario(); const assunto="Solicitação de Orçamento"; const corpo=`Novo Orçamento:%0ANome: ${d.nome}%0AE-mail: ${d.email}%0ATelefone: ${d.telefone}%0AServiço: ${d.servico}%0AMensagem: ${d.mensagem}`; window.location.href=`mailto:contato@suaempresa.com?subject=${assunto}&body=${corpo}`;}
function enviarSheets(){const d=getDadosFormulario(); fetch(SCRIPT_URL,{method:"POST",body:JSON.stringify(d),headers:{"Content-Type":"application/json"}}).then(res=>res.text()).then(res=>alert("Orçamento salvo com sucesso na planilha!")).catch(err=>alert("Erro ao salvar: "+err));}
const btnTopo=document.getElementById("btnTopo");
window.onscroll=function(){if(document.body.scrollTop>200||document.documentElement.scrollTop>200){btnTopo.style.display="block";}else{btnTopo.style.display="none";}};
btnTopo.addEventListener("click",()=>{window.scrollTo({top:0,behavior:'smooth'});});
</script>

</body>
</html>






