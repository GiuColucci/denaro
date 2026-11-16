# Sprints

As apresentações originais estão em [`apresentacoes/`](apresentacoes/).

## Sprint 1

**Objetivos**

- Modelagem visual das gamificações.
- Integração dos diagnósticos 1 e 2 no n8n.

**Entregas**

- **Mascote do Denaro** em seis poses, para uso nas interações: neutro, acenando com notas voando, apresentando, comemorando, confuso (pontos de interrogação) e triste.
- **Perguntas** dos Diagnósticos Financeiros 1 e 2. Veja [`diagnosticos.md`](diagnosticos.md).
- **Integração no n8n** com WhatsApp. A conversa de teste percorreu os dois diagnósticos, apresentou duas opções de plano, a pessoa escolheu a opção 2 e recebeu dicas e metas semanais. O Denaro também retomou a conversa quando a pessoa voltou a mandar "oi".
- **Fluxo no n8n** e **banco MySQL** com as tabelas `users`, `goals`, `messages_log` e `tips`. Veja [`arquitetura.md`](arquitetura.md) e [`banco-de-dados.md`](banco-de-dados.md).

## Sprint 3

**Objetivo**

- Entregar o MVP.

**Ajustes**

- Integração do n8n com o banco MySQL.
- Solução: demo em Python.

**Entregas**

- **Banco de dados** no Google Sheets, com as abas `usuarios`, `perfil_financeiro`, `metas_financeiras` e `progresso_metas`.
- **Demo em Python** com interface de chat web, Gemini para a conversa e Google Sheets para o armazenamento. A demo percorre os dois diagnósticos, calcula o plano e oferece as opções 1 e 2.

## Próximos passos

- Preencher e usar a aba `progresso_metas` para acompanhar se a pessoa está seguindo a meta.
- Aplicar a gamificação com o mascote nas interações da demo.
- Adicionar ao repositório o código da demo e o export do fluxo n8n.
