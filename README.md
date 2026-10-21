# JurisFlow IA — MVP 0.1

Sistema web inicial para gestão jurídica. Inclui login/cadastro, escritório isolado por políticas RLS, clientes, processos, demandas Kanban (arrastar e soltar no desktop), agenda em lista e dashboard.

## Instalação
1. Instale Node.js 20 ou superior.
2. Crie um projeto no [Supabase](https://supabase.com/).
3. No SQL Editor do Supabase, execute `supabase/schema.sql` **uma única vez** em um projeto novo. Não rode repetidamente: políticas SQL não têm `if not exists`.
4. Em Authentication > Providers, habilite Email; configure confirmação de e-mail e URLs de redirecionamento para seu domínio.
5. Copie `.env.example` para `.env.local` e preencha URL e **chave pública publishable/anon** do Supabase. Nunca use service_role no navegador.
6. Execute `npm install` e `npm run dev`. Abra `http://localhost:3000`.
7. Cadastre um usuário, confirme o e-mail se solicitado e crie o escritório.
8. Para publicar, conecte o repositório ao [Vercel](https://vercel.com/), configure as duas variáveis de ambiente e ajuste a URL do site no Supabase Auth. Use domínio com HTTPS.

## Segurança e limites
- Políticas RLS aplicadas a clientes, processos, demandas e eventos. O escritório inicial é criado via função autenticada. Nesta versão, não há interface para convidar outros membros.
- Login ocorre no cliente com Supabase Auth. Para produção, recomenda-se SSR com sessão por cookies, proteção adicional de rotas, rate limiting e testes de penetração.
- Exclusões são definitivas; configure backup, retenção e recuperação no Supabase antes de uso real.
- Ainda não inclui documentos/anexos, Google Calendar, Claude, Juiz IA, notificações push, auditoria completa, cálculo de prazos ou PWA instalável. Nenhuma dessas integrações é simulada.
- Agenda mostra registros em lista, não calendário mensal/semanal; a interface é responsiva.
- Esta é uma base de desenvolvimento, não uma plataforma auditada para dados sigilosos reais. Valide segurança e conformidade LGPD antes de usar dados de clientes.

## Próximas etapas
Google OAuth e sincronização com eventos externos, calendários diário/semanal/mensal, documentos privados, histórico/auditoria, controle de permissões por função, PWA com manifest/service worker, testes E2E, backup, alertas e IA com confirmação humana.
