# Cliente nativo em Rust com egui, em vez de webview

- **Data**: 2026-11-18
- **Status**: Aceito

## Contexto

O RustCord fica aberto o dia todo: na bandeja enquanto se trabalha e em Chamada durante partidas de LoL. O objetivo do projeto é pesar muito menos que o Discord, que é um app Electron. As metas são ≤150 MB de RAM em Chamada compartilhando, ≤40 MB na bandeja e queda menor que 5% no FPS do jogo. O peso desse tipo de app vem do runtime do navegador e do caminho de mídia, não do tamanho do binário.

## Decisão

O cliente é **nativo em Rust**, com interface em **egui**. A mídia passa pelo **SDK Rust do LiveKit** (libwebrtc, que já inclui cancelamento de eco, buffer de rede e controle de banda), e a captura de janela e de tela usa a **Windows.Graphics.Capture**. A compilação usa o toolchain **MSVC**, porque o cancelamento de eco do libwebrtc não compila no `windows-gnu`, como mostra o código do Zed.

O Zed, editor nativo em Rust, faz voz e compartilhamento de tela no Windows com esse mesmo SDK. É o precedente mais próximo do que queremos.

## Opções descartadas

- **Tauri + SDK JS do LiveKit**: o WebView2 roda processos do Chromium e o consumo de RAM fica perto do de uma aba de navegador. É o **plano B** se a integração nativa travar ou se a RAM passar de ~250 MB no teste.
- **Electron**: é justamente o peso que o projeto quer evitar.
- **WebRTC em Rust puro** (str0m, webrtc-rs): exigiria montar à mão cancelamento de eco, buffer de rede e controle de banda. O áudio é a parte em que menos podemos errar.

## Consequências

- O vídeo recebido e toda a interface são desenhados por nós. Não existe DOM nem CSS.
- Entrada de texto, emojis e acessibilidade ficam mais pobres que na web e precisam de cuidado próprio.
- O egui precisa redesenhar só quando há evento. Sem isso, a meta de CPU parada não se cumpre.
- O binário cresce dezenas de MB por causa do libwebrtc. O ganho está na RAM, não no tamanho do arquivo.
- Se a codificação por hardware não estiver disponível pelo SDK no Windows, a saída é codificar H.264 por Media Foundation e publicar o vídeo já codificado.
