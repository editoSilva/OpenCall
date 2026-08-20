# OpenCall

Infraestrutura e videochamada.

## Docker + Docker Compose

Orquestração de todos os serviços.

- **Jitsi self-hosted** (imagens oficiais `jitsi/web`, `jitsi/prosody`, `jitsi/jicofo`, `jitsi/jvb`) — sinalização (XMPP/Prosody), foco de conferência (Jicofo) e roteamento de mídia (JVB)
- **Coturn** — servidor TURN/STUN próprio, para garantir conectividade em qualquer rede
- **WebRTC** — protocolo de mídia (áudio/vídeo) usado pelo Jitsi por baixo dos panos
- **ICE/STUN/TURN** — negociação de conectividade entre peers atrás de NAT
- **Let's Encrypt (certbot)** — certificados TLS para o domínio do Jitsi e do TURN

## Backend (sua API)

- **Node.js**
- **Fastify** — framework HTTP para criar salas e gerar credenciais TURN
- **TypeScript** — tipagem em toda a API e no código do frontend
- **JWT** — autenticação de moderador, API com o `AUTH_TYPE=jwt` do Jitsi

## Frontend

- **React**

## Segurança e controle de acesso

- **Prosody `mod_muc_lobby_rooms`** — lobby/aprovação de entrada (já embutido, sem serviço extra)
