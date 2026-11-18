# LiveKit auto-hospedado, com toda a mídia passando pelo SFU e sem TURN na 1.0

- **Data**: 2026-11-18
- **Status**: Aceito

## Contexto

O RustCord precisa de voz, tela e câmera entre 2 e 10 pessoas no Windows, em redes domésticas diferentes e atrás de NAT/CGNAT. O servidor é a VPS que já existe: Hostinger KVM1, com 1 vCPU e 4 GB de RAM, dividida com outros apps. Nela, as portas 80 e 443 pertencem ao Caddy, atrás do proxy do Cloudflare, e o UFW só libera a 443 para as faixas de IP do Cloudflare. O Cloudflare não repassa mídia em UDP.

## Decisão

Usamos o **LiveKit server auto-hospedado** nessa VPS como SFU. **Toda a mídia passa pelo SFU**, inclusive numa DM com 2 pessoas, e os clientes nunca se conectam diretamente entre si. A sinalização entra por `rustcord.fassi.dev`, via Caddy e Cloudflare. A mídia vai direto para o IP da VPS, por portas próprias: **7882/udp**, com **7881/tcp** de reserva. Não existe **TURN** na 1.0.

Pelo SFU, quem compartilha envia o vídeo uma vez só, seja qual for o número de Espectadores. DM e Grupo usam o mesmo caminho. O IP de cada Participante fica escondido dos outros, e a conexão funciona atrás de NAT porque todo cliente fala com um IP público. O Discord adota o mesmo desenho pelos mesmos motivos.

## Opções descartadas

- **P2P em malha**: quem compartilha enviaria uma cópia do vídeo para cada Participante, e DM e Grupo teriam caminhos diferentes.
- **LiveKit Cloud**: depende da cota de um terceiro, e o conteúdo das telas sairia da nossa infraestrutura.
- **SFU próprio em Rust** (str0m, webrtc-rs): seriam semanas reconstruindo controle de banda e repasse de pacotes que o LiveKit já resolve.
- **TURN/TLS na 443**: conflita com o Caddy e com o proxy do Cloudflare que já ocupam essa porta.

## Consequências

- O servidor passa a depender do LiveKit (Go) e o cliente, do SDK Rust do LiveKit (libwebrtc).
- A VPS é ponto único de falha e soma um salto à latência (~8 ms até ela).
- Quem estiver numa rede que bloqueia UDP e portas fora do padrão (corporativa, de faculdade) não conecta. O remédio é acrescentar TURN/TLS num hostname fora do proxy do Cloudflare, registrado num ADR novo.
- O IP da VPS fica visível para os clientes. Ele já é público por causa das portas do RustDesk.
- O UFW precisa liberar 7881/tcp e 7882/udp para qualquer origem.
