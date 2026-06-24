---
name: rfc-writer
description: "Use sempre que o usuário pedir para escrever, criar, estruturar, preencher ou revisar um RFC, design doc, ou proposta técnica. Também ativa se o usuário mencionar 'RFC', 'design doc' ou pedir para documentar uma decisão técnica/arquitetural. Garante que o documento segue o template e o padrão de qualidade da empresa."
---

# RFC Writer

Você está ajudando a escrever ou revisar um RFC. Siga este processo.

## 1. Antes de escrever

Se faltar informação essencial, pergunte objetivamente (no máximo 2-3 perguntas)
antes de gerar o documento. Informação essencial = problema que o RFC resolve,
escopo (o que está dentro/fora) e quem é o público (time, empresa toda, etc).
Não pergunte o que já foi dito na conversa.

## 2. Estrutura obrigatória

Todo RFC criado por esta skill segue exatamente o template em
`templates/rfc-template.md`. Não pule seções, não invente seções novas, não troque
a ordem. Se uma seção não se aplica, escreva "Não aplicável" e explique por quê
em uma linha — nunca delete a seção.

## 3. Regras de redação

- Seja direto. Frases curtas. Sem enchimento ("é importante notar que...").
- Toda decisão precisa de um porquê. "Vamos usar Postgres" sem justificativa não
  é aceitável; "Vamos usar Postgres porque já é o padrão do time e evita operar
  um banco novo" é.
- Alternativas consideradas precisam ser reais, não espantalhos. Se há só uma
  opção viável, diga isso e explique por que as outras foram descartadas.
- Riscos e trade-offs nunca podem ser omitidos. Um RFC sem riscos listados é
  sinal de que não foram pensados, não de que não existem.
- Quantifique sempre que possível (latência, custo, esforço em dias/semanas)
  em vez de adjetivos ("rápido", "caro").

## 4. Checklist final (rode antes de entregar)

- [ ] Todas as seções do template estão presentes e preenchidas
- [ ] O problema está descrito antes da solução
- [ ] Existe pelo menos uma alternativa considerada e descartada, com motivo
- [ ] Riscos/trade-offs estão explícitos
- [ ] Existe critério de sucesso (como saber se isso funcionou)
- [ ] Sem jargão não explicado, sem seção vazia, sem prosa enrolada

## 5. Modo revisão

Se o usuário colar um RFC já escrito (em vez de pedir para criar um novo),
não reescreva do zero. Rode o checklist acima contra o documento e devolva
uma lista do que falta ou está fraco, seção por seção. Só reescreva o trecho
se o usuário pedir explicitamente.

## Referências

- Template completo: `templates/rfc-template.md`
- Exemplos de RFCs aprovados: pasta `examples/` (adicione os seus aqui para a
  skill aprender o tom certo)
