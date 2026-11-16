# Arquitetura

O Denaro teve duas implementações. A primeira foi um fluxo no n8n (Sprint 1 em diante). A segunda é a demo em Python para o MVP (Sprint 3).

## Fluxo no n8n

```
WhatsApp ──POST──▶ Webhook ──▶ Dados ──▶ Insert/Update (MySQL) ──▶ Switch
                                                                       │
                          ┌────────────────────────────────────────────┤
                          ▼                                            ▼
                 Teste diagnóstico 1                          Teste diagnóstico (2)
                 (AI Agent + Gemini + Redis)                  (AI Agent + Gemini + Redis)
                          │                                            │
                  Send Seen / Send Text                        Send Seen / Send Text
                          │                                    Insert/Update (MySQL)
                  Insert/Update (MySQL)
                          │
                      AI Agent (plano)
                          │
                  Send Seen / Send Text
```

Os nós, na ordem:

1. **Webhook (POST):** recebe cada mensagem do WhatsApp.
2. **Dados:** normaliza o payload (sessão, chat, nome, mensagem).
3. **Insert or update (MySQL):** grava o usuário (upsert).
4. **Switch (modo regras):** decide em qual etapa da conversa a pessoa está e roteia para o agente certo.
5. **Agentes "Teste diagnóstico":** cada um é um AI Agent com modelo **Google Gemini** e memória no **Redis**, que conduz as perguntas do diagnóstico.
6. **Send Seen / Send Text:** marca a mensagem como vista e responde pelo WhatsApp.
7. **AI Agent final:** com o diagnóstico completo, monta o plano financeiro.

O *system message* do agente define o papel: um assistente financeiro que ajuda pessoas indisciplinadas com suas finanças, dando dicas e conselhos.

### Ajuste da Sprint 3

A integração com o n8n foi ajustada para conversar com o banco MySQL. A demo em Python entrou como solução para o MVP.

## Demo em Python (MVP)

Uma interface de chat web, chamada "Denaro, seu assistente financeiro pessoal", com rodapé *Powered by Google Gemini · Armazenado em Google Sheets*.

- A conversa segue o roteiro dos diagnósticos 1 e 2.
- Algumas perguntas pedem resposta de opções fechadas, como "sim, não ou parcial".
- Ao final de cada etapa o Denaro confirma que os dados foram salvos e segue para a próxima.
- Os dados ficam em um Google Sheets chamado **Denaro Database**. Veja [`banco-de-dados.md`](banco-de-dados.md).
