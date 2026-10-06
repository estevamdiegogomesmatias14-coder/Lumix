# Lumix IA

Protótipo web do Lumix com interface de chat, autoria preservada e backend seguro para conexão com uma API de IA.

## Rodar
1. Instale Node.js 20+.
2. No terminal, entre nesta pasta e rode `npm install`.
3. Defina a variável `OPENAI_API_KEY` no servidor.
4. Opcionalmente defina `OPENAI_MODEL`.
5. Rode `npm start` e abra `http://localhost:3000`.

A chave de API fica no servidor e não é colocada no navegador.

## Publicar
Publique este projeto em um serviço que rode Node.js (por exemplo, um host de aplicações web), configure `OPENAI_API_KEY` como variável secreta e use `npm start` como comando de inicialização. Depois disso, o endereço público poderá ser compartilhado.
