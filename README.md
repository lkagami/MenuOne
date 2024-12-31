# MenuOne
## System that integrates food orders in a single space.

1. Funcionalidades principais:

Gestão de pedidos: Receber, visualizar e atualizar status dos pedidos.

Integração com WhatsApp e iFood:
- Para WhatsApp: API do WhatsApp Business (ou Webhooks).
- Para iFood: API oficial (caso o restaurante tenha acesso).

Dashboard:
- Exibir pedidos ativos, finalizados e cancelados.
- Filtrar por canais (WhatsApp/iFood).
- Atualizar status de um pedido.
  
Notificações: 
- Alertas para novos pedidos.
  
Autenticação:
- Controle de acesso para gerentes e funcionários.
  
2. Estrutura do Projeto
Backend (NestJS)

Autenticação:
- Módulos de autenticação do NestJS com JWT para gerenciar login e permissões.

Pedidos:
- Módulo para gerenciar pedidos com operações CRUD.
- Lógica para integração com APIs externas (WhatsApp e iFood).
  
WebSocket para Notificações:
- Gateway WebSocket para notificações em tempo real.
  
Banco de Dados:
- TypeORM para gerenciar o banco de dados (MongoDB - não relacional).
  
Estrutura das tabelas: 
- Users;
- Orders;
- Channels (ex.: WhatsApp, iFood);
  
Serviços de Integração:
Configure serviços específicos para cada canal:
WhatsApp: 
- Usar a API oficial para receber mensagens e responder.
iFood:
- Criar hooks para monitorar pedidos recebidos.
  
Frontend (ReactJS)
Bibliotecas principais:
React Router: 
- Para navegação entre páginas.
React Query:
- Gerenciar estados e chamadas de API.
Material-UI:
- Para componentes visuais do dashboard.
  
Páginas principais:
Login: 
- Autenticação de usuários.
Dashboard:
- Exibir pedidos de todos os canais.
Detalhes do Pedido:
- Página para visualizar/editar informações de um pedido.
WebSocket:
- Socket.IO para conectar-se ao back-end e receber notificações em tempo real.
  
4. Fluxo de Dados
Recepção de Pedidos:
- O back-end recebe os pedidos de APIs externas (WhatsApp/iFood).
- Armazena no banco de dados e envia notificações para o front-end via WebSocket.
  
Visualização e Atualização:
- O front-end consome APIs REST do back-end para listar e atualizar os pedidos.
- Alterações são propagadas em tempo real com WebSocket.
