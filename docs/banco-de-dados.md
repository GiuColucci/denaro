# Banco de dados

## Sprint 1: MySQL (`denaro_db`)

Usado pelo fluxo n8n.

| Tabela | Conteúdo |
| --- | --- |
| `users` | Usuários do WhatsApp |
| `goals` | Metas financeiras |
| `messages_log` | Registro das mensagens |
| `tips` | Dicas financeiras |

A tabela `tips` tem as colunas `id`, `tag`, `persona` e `dica`. As dicas são agrupadas por tag (economia, motivação, controle) e por persona (conservador, moderado, arrojado, geral). Exemplos de dicas: reservar 10% da renda todo mês, o desafio das 52 semanas, anotar todos os gastos por 30 dias.

## Sprint 3: Google Sheets (**Denaro Database**)

Usado pela demo em Python. A planilha tem quatro abas.

### `usuarios`

| Coluna | Descrição |
| --- | --- |
| `id` | Identificador do usuário |
| `nome` | Nome |
| `telefone` | Telefone |
| `email` | E-mail |
| `criado_em` | Data e hora de criação |

### `perfil_financeiro`

Respostas do Diagnóstico 1.

| Coluna | Descrição |
| --- | --- |
| `id` | Identificador do registro |
| `usuario_id` | Referência a `usuarios.id` |
| `telefone` | Telefone |
| `ganho_mensal` | Ganho por mês |
| `despesas_mensais` | Despesas por mês |
| `tem_controle_dinheiro` | `sim`, `não` ou `parcial` |
| `buscou_aprender_financas` | `sim`, `não` ou `um_pouco` |
| `maior_dificuldade_economizar` | Texto livre |
| `expectativa_denaro` | Texto livre |
| `criado_em` | Data e hora de criação |

### `metas_financeiras`

Respostas do Diagnóstico 2.

| Coluna | Descrição |
| --- | --- |
| `id` | Identificador da meta |
| `usuario_id` | Referência a `usuarios.id` |
| `telefone` | Telefone |
| `objetivo` | Objetivo (por exemplo, comprar um tablet) |
| `prazo_meses` | Prazo em meses |
| `valor_meta` | Valor total da meta |
| `valor_reservado` | Valor já guardado |
| `plano_escolhido` | Plano escolhido (opção 1 ou 2) |
| `status` | Por exemplo, `ativa` |
| `criado_em` | Data e hora de criação |

### `progresso_metas`

Acompanhamento da meta. A aba existe com as colunas definidas, mas ainda sem registros.

| Coluna | Descrição |
| --- | --- |
| `id` | Identificador |
| `telefone` | Telefone |
| `seguindo_meta` | Se a pessoa está seguindo a meta |
| `observacao` | Observação |
| `data_registro` | Data do registro |

## Relacionamento

```
usuarios 1 ──── N perfil_financeiro
usuarios 1 ──── N metas_financeiras
metas_financeiras 1 ──── N progresso_metas
```

O vínculo entre `progresso_metas` e a meta ainda não está definido na planilha: a aba tem `telefone`, mas não um `meta_id`.
