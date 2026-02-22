# Site Profissional Bike Elétrica + Painel Admin

## Como usar
1. Extraia o ZIP
2. Abra o arquivo index.html para ver o site
3. Abra admin.html para acessar o painel administrativo

## Funções
- Página principal profissional
- Botão WhatsApp integrado
- Painel administrativo local (salva no navegador)
- Fácil de personalizar

## Contato configurado
WhatsApp: (62) 99994-5175

## Hospedagem
Pode ser hospedado em:
- GitHub Pages
- Hostinger
- Netlify
- Qualquer servidor comum

## Desenvolvido por ChatGPT
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Painel Administrativo - Login</title>
<style>
body{font-family:Arial;background:#111;color:#fff;margin:0}
.container{max-width:400px;margin:80px auto;background:#1e1e1e;padding:25px;border-radius:8px}
h1{text-align:center}
input,textarea{width:100%;padding:10px;margin:10px 0;border:none;border-radius:5px}
button{width:100%;padding:12px;background:#25d366;color:#fff;border:none;border-radius:6px;font-size:16px;font-weight:bold}
.panel{display:none;max-width:700px;margin:40px auto;background:#1e1e1e;padding:25px;border-radius:8px}
.logout{background:#e74c3c;margin-top:10px}
</style>
</head>
<body>

<div class="container" id="login">
  <h1>Login Admin</h1>
  <input id="user" placeholder="Usuário">
  <input id="pass" type="password" placeholder="Senha">
  <button onclick="login()">Entrar</button>
</div>

<div class="panel" id="panel">
  <h1>Painel Administrativo</h1>

  <label>Título do Site</label>
  <input id="titulo">

  <label>Descrição do Site</label>
  <textarea id="descricao"></textarea>

  <button onclick="salvar()">Salvar Alterações</button>
  <button class="logout" onclick="logout()">Sair</button>
</div>

<script>
const USER = "admin";
const PASS = "1234";

function login(){
  const u = document.getElementById("user").value;
  const p = document.getElementById("pass").value;

  if(u === USER && p === PASS){
    localStorage.setItem("logado","true");
    abrirPainel();
  } else {
    alert("Usuário ou senha incorretos!");
  }
}

function abrirPainel(){
  document.getElementById("login").style.display="none";
  document.getElementById("panel").style.display="block";

  const dados = JSON.parse(localStorage.getItem("siteDados"));
  if(dados){
    document.getElementById("titulo").value = dados.titulo || "";
    document.getElementById("descricao").value = dados.descricao || "";
  }
}

function salvar(){
  const dados = {
    titulo: document.getElementById("titulo").value,
    descricao: document.getElementById("descricao").value
  }
  localStorage.setItem("siteDados", JSON.stringify(dados));
  alert("Dados salvos com sucesso!");
}

function logout(){
  localStorage.removeItem("logado");
  location.reload();
}

if(localStorage.getItem("logado") === "true"){
  abrirPainel();
}
</script>

</body>
</html>
