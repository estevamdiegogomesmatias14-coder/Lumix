<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Lumix</title>
<style>
*{box-sizing:border-box}body{margin:0;background:#05040a;color:#fff;font-family:Arial,sans-serif}.app{max-width:430px;margin:auto;height:100vh;display:flex;flex-direction:column;background:linear-gradient(#160d28,#05040a);overflow:hidden}header{padding:18px 20px;border-bottom:1px solid #30213f;font-weight:bold;letter-spacing:3px;font-size:22px}main{flex:1;overflow:auto;padding:20px 16px}.hero{width:230px;height:270px;margin:0 auto 15px;border:2px solid #8b4cff;border-radius:26px;overflow:hidden;box-shadow:0 0 35px #5420a055}.hero img{width:100%;height:100%;object-fit:cover;object-position:center top;display:block}h1{text-align:center;font-size:27px;margin:7px}.sub{text-align:center;color:#bbb;margin-bottom:18px}.msg{display:flex;margin:10px 0}.user{justify-content:flex-end}.bubble{max-width:84%;padding:12px 15px;border-radius:18px;background:#191521;white-space:pre-wrap;line-height:1.4}.user .bubble{background:#713fe0}.status{font-size:12px;color:#aaa;text-align:center;margin:8px}.typing{opacity:.7}form{display:flex;gap:8px;padding:12px;border-top:1px solid #29202f}input{flex:1;background:#15111c;color:#fff;border:1px solid #8b4cff;border-radius:24px;padding:14px;outline:none}button{border:0;border-radius:50%;background:#7b43ef;color:#fff;width:50px;font-size:22px}nav{display:flex;justify-content:space-around;padding:12px;border-top:1px solid #29202f;color:#aaa}
</style>
</head>
<body>
<div class="app"><header>LUMIX</header><main id="chat"><div class="hero"><img src="/personagem.png" alt="Personagem do Lumix"></div><h1>Olá, eu sou o Lumix</h1><div class="sub">IA real conectada ao modelo da OpenAI.</div></main>
<form id="form"><input id="input" placeholder="Digite sua pergunta..." autocomplete="off"><button aria-label="Enviar">➤</button></form><nav>⌂ Início　 💬 Conversa　 ⚙ Configurações</nav></div>
<script>
const chat=document.getElementById('chat'),input=document.getElementById('input'),form=document.getElementById('form');
const sessionId=localStorage.getItem('lumix_session')||crypto.randomUUID(); localStorage.setItem('lumix_session',sessionId);
function add(t,c){const r=document.createElement('div');r.className='msg '+c;const b=document.createElement('div');b.className='bubble';b.textContent=t;r.appendChild(b);chat.appendChild(r);chat.scrollTop=chat.scrollHeight;return r}
form.addEventListener('submit',async e=>{e.preventDefault();const q=input.value.trim();if(!q)return;add(q,'user');input.value='';input.disabled=true;const loading=add('Pensando...','ai typing');try{const r=await fetch('/api/chat',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({message:q,sessionId})});const d=await r.json();loading.remove();add(d.reply||'Não consegui responder agora.','ai')}catch(err){loading.remove();add('Não consegui conectar ao servidor. Verifique se o servidor está ligado.','ai')}finally{input.disabled=false;input.focus()}});
</script>
</body></html>
