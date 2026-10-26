# Decisões técnicas e de produto

Registro das principais decisões tomadas no desenvolvimento do FocusFlow. Cada uma traz o contexto, as opções consideradas e a escolha feita.

## 1. Sair do protótipo no Lovable para um projeto em React

**Contexto:** o FocusFlow começou como protótipo no Lovable, útil para testar a ideia, mas limitado para contas, sincronização e testes.

**Opções:** continuar no Lovable ou levar o projeto para React e TypeScript.

**Escolha:** React 18 com TypeScript estrito e Vite, para ter controle sobre a estrutura, os testes e a publicação.

## 2. Isolar o player de música em outro endereço

**Contexto:** a música toca pelos players oficiais do YouTube e do Spotify, que carregam scripts de terceiros.

**Opções:** carregar os players dentro do app ou isolá-los em um site separado.

**Escolha:** player isolado em outro endereço, conversando com o app só por mensagens com a origem conferida. Assim, os scripts de terceiros não têm acesso aos dados do app.

## 3. Proteger os dados com Row Level Security e testar com duas contas

**Contexto:** com contas e sincronização, cada pessoa precisa ver apenas os próprios dados.

**Opções:** controlar o acesso só no app ou aplicar regras no banco.

**Escolha:** Row Level Security no Postgres do Supabase. As regras foram testadas no Supabase real com duas contas temporárias, para confirmar que uma conta não acessa os dados da outra.

## 4. Trocar o n8n por pg_cron

**Contexto:** o protótipo previa o n8n para agendar os avisos por e-mail.

**Opções:** manter um serviço externo de automação ou agendar dentro do próprio Supabase.

**Escolha:** pg_cron chamando Edge Functions. Menos um serviço para manter e configurar, com o agendamento junto do banco.

## 5. Substituir a loja de itens por cenas que evoluem sozinhas

**Contexto:** o protótipo chegou a ter loja, inventário, moedas e 126 itens de decoração.

**Opções:** manter o sistema de loja ou simplificar a gamificação.

**Escolha:** cinco cenas completas que evoluem conforme os ciclos de foco. O app ficou mais leve, mais fácil de manter e mais coerente com a proposta de foco.

## 6. Não chamar de pronto o que só passou em teste simulado

**Contexto:** várias integrações (Google Agenda, e-mails, exclusão de conta) foram testadas com serviços simulados.

**Escolha:** separar no README o que foi testado em navegador real do que está pronto no código, mas ainda sem teste real.
