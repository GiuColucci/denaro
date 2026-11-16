# Denaro 💸

> **A solução dos seus problemas (financeiros)!**

Denaro é um assistente financeiro pessoal conversacional. Ele conversa com a pessoa, faz um diagnóstico rápido da situação financeira dela, ajuda a definir uma meta de curto prazo e monta opções de plano para alcançá-la.

O nome vem do *denarius*, a moeda romana. Por isso o mascote é uma nota de dinheiro com coroa de louros e gravata-borboleta.

## O problema

Muita gente não sabe quanto ganha, quanto gasta nem para onde o dinheiro vai. Falta controle e conhecimento, e quem tenta economizar tem dificuldade de manter a constância. O Denaro ataca isso de forma simples: uma conversa guiada, sem planilha para preencher e sem curso para fazer.

## Como funciona

A conversa tem duas etapas e termina com um plano.

1. **Diagnóstico Financeiro 1: entender o perfil.** Ganhos, despesas, sensação de controle, conhecimento sobre finanças, maior dificuldade para economizar e expectativa em relação ao Denaro.
2. **Diagnóstico Financeiro 2: definir a meta.** Objetivo de curto prazo, prazo desejado e valor já reservado.
3. **Plano.** O Denaro calcula quanto falta e oferece opções, como uma **rápida** (poupar mais por mês, atingir antes) e uma **equilibrada** (ritmo mais leve e constante). A pessoa escolhe uma, e o Denaro sugere ferramentas (planilha, apps, lembretes) e metas semanais para manter a motivação.

Exemplo da primeira versão, com o objetivo de juntar R$ 8.000 em 6 meses para uma reforma, já tendo R$ 1.500:

| Opção | Depósito mensal |
| --- | --- |
| Foco na rapidez | R$ 1.083,33 |
| Foco no equilíbrio | R$ 800,00 |

Veja as perguntas completas em [`docs/diagnosticos.md`](docs/diagnosticos.md).

## Evolução do projeto

| Sprint | Objetivo | Entrega |
| --- | --- | --- |
| 1 | Modelagem visual das gamificações; integração dos diagnósticos 1 e 2 no n8n | Mascote em várias expressões; fluxo no n8n com WhatsApp, Gemini, Redis e MySQL |
| 3 | Entregar o MVP | Demo em Python com chat web, Gemini e Google Sheets |

Detalhes em [`docs/sprints.md`](docs/sprints.md).

## Tecnologias

| Camada | Sprint 1 (fluxo n8n) | Sprint 3 (demo em Python) |
| --- | --- | --- |
| Interface | WhatsApp | Chat web |
| Orquestração | n8n (webhook + switch) | Python |
| IA | Google Gemini | Google Gemini |
| Memória da conversa | Redis | n/d |
| Armazenamento | MySQL | Google Sheets |

A arquitetura está em [`docs/arquitetura.md`](docs/arquitetura.md) e o modelo de dados em [`docs/banco-de-dados.md`](docs/banco-de-dados.md).

## Identidade visual

- Paleta: verde-floresta escuro, verde vivo e verde-claro, com detalhes em amarelo (coroa de louros e luvas do mascote).
- Mascote: nota de dinheiro com coroa de louros e gravata vermelha. Aparece feliz, acenando, apresentando, comemorando, confuso e triste, ligado às situações da conversa. Esse é o ponto de partida da gamificação.

## Estrutura do repositório

```
denaro/
├── README.md
└── docs/
    ├── arquitetura.md
    ├── banco-de-dados.md
    ├── diagnosticos.md
    ├── sprints.md
    └── apresentacoes/
        ├── Sprint1_Denaro.pdf
        └── Sprint3_Denaro.pdf
```

## Equipe

Bernardo Santoni, Ichiro Sakai, Giulia Colucci, Pedro Vitral e Yasmin Sandes.

## Status

MVP em desenvolvimento. O código da demo em Python e o export do fluxo n8n ainda não estão neste repositório. A documentação aqui foi escrita a partir das apresentações das Sprints 1 e 3.
