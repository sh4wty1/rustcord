# RustCord

App fechado de conversa por voz, vídeo, compartilhamento de tela e texto para um círculo pequeno de amigos convidados. Existe para substituir o Discord nesse grupo, de forma leve e sem excesso.

## Pessoas

**Usuário**:
Pessoa com acesso ao RustCord. Só existe se o Administrador a criar.
_Evitar_: conta, user, membro (fora de um Grupo)

**Administrador**:
Quem opera a instância do RustCord: cria Usuários e Convites e reseta senhas.
_Evitar_: admin do grupo, dono (ver **Dono**)

**@username**:
Identificador único do Usuário, definido pelo Administrador. Usado para entrar no app e para enviar Pedidos de amizade.
_Evitar_: login, nome de usuário, handle

**Nome de exibição**:
Nome livre que o Usuário escolhe e que os outros veem.
_Evitar_: apelido, nickname, display name

**Perfil**:
Nome de exibição, Avatar e Bio de um Usuário.
_Evitar_: conta, cadastro

**Avatar**:
Imagem que representa um Usuário ou um Grupo.
_Evitar_: foto de perfil, ícone

**Bio**:
Texto curto do Perfil em que o Usuário fala de si.
_Evitar_: descrição, sobre

**Convite**:
Código de uso único e com validade, entregue pelo Administrador junto com o @username, que permite ao Usuário criar a própria senha no primeiro acesso.
_Evitar_: token, link de convite, código de acesso

**Pedido de amizade**:
Solicitação de um Usuário a outro, feita pelo @username, que vira Amizade quando aceita.
_Evitar_: convite (ver **Convite**), solicitação

**Amigo**:
Usuário com quem existe uma Amizade aceita. Só Amigos abrem DMs e entram juntos em Grupos.
_Evitar_: contato

## Conversas

**Conversa**:
Lugar onde Usuários trocam Mensagens e fazem Chamadas. É sempre uma DM ou um Grupo.
_Evitar_: sala, canal, chat

**DM**:
Conversa entre exatamente dois Usuários. Os membros de uma DM nunca mudam. Chamar uma terceira pessoa cria um Grupo novo, e a DM continua intacta.
_Evitar_: chat direto, privado, mensagem direta

**Grupo**:
Conversa criada para três ou mais Usuários, com nome, Avatar e Dono. Continua sendo Grupo mesmo que membros saiam.
_Evitar_: sala, group DM, servidor

**Dono**:
Membro do Grupo que pode remover outros membros. No início é quem criou o Grupo. Se ele sai, o membro mais antigo passa a ser o Dono.
_Evitar_: admin, criador, moderador

**Mensagem**:
Texto ou imagem colada que um Usuário envia numa Conversa. Só o autor pode editar ou apagar.
_Evitar_: post, chat

**Servidor**:
Termo reservado para uma futura comunidade com canais. Ainda não tem definição.
_Evitar_: usar "servidor" para Grupo

## Chamadas

**Chamada**:
Sessão ao vivo de voz e vídeo dentro de uma Conversa. Cada Usuário está em no máximo uma Chamada por vez.
_Evitar_: call, ligação, sala de voz

**Participante**:
Usuário que está numa Chamada.
_Evitar_: membro, ouvinte

**Compartilhamento**:
Transmissão de uma janela ou da tela inteira de um Participante, na Chamada. Cada Participante tem no máximo um Compartilhamento ativo.
_Evitar_: stream, transmissão, screen share, live

**Modo Texto**:
Modo de Compartilhamento que prioriza nitidez em vez de fluidez, para terminal, código e logs.
_Evitar_: modo estático, modo qualidade

**Modo Movimento**:
Modo de Compartilhamento que prioriza fluidez em vez de nitidez, para jogos e vídeo.
_Evitar_: modo jogo, modo performance

**Espectador**:
Participante que escolheu assistir a um Compartilhamento. Quem não escolhe não recebe aquele vídeo.
_Evitar_: viewer, plateia

**Câmera**:
Vídeo da webcam de um Participante, na Chamada.
_Evitar_: webcam, vídeo

**Mutar**:
Parar de enviar o próprio microfone na Chamada.
_Evitar_: silenciar

**Ensurdecer**:
Parar de ouvir a Chamada. Quem ensurdece também fica mutado.
_Evitar_: mutar saída, mutar som

## Presença

**Status**:
Disponibilidade do Usuário: Online, Ausente, Não perturbe ou Offline.
_Evitar_: presença (como sinônimo), situação

**Ausente**:
Status que entra sozinho quando um Usuário Online passa um período sem usar o computador.
_Evitar_: inativo, idle

**Não perturbe**:
Status escolhido pelo Usuário que silencia notificações e toques de Chamada.
_Evitar_: ocupado, DND

**Atividade**:
O que o Usuário está fazendo agora, independente do Status. Por enquanto só existe "em Chamada" numa Conversa.
_Evitar_: status (ver **Status**)
