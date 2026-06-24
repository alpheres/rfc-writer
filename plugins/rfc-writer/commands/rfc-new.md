---
description: Cria um novo RFC a partir do template, perguntando o necessário antes de escrever.
---

Use a skill rfc-writer para criar um novo RFC.

1. Se o usuário não disse o título/tema, pergunte.
2. Pergunte o que falta de essencial (problema, escopo, público) — no máximo
   2-3 perguntas, só o que não foi dito.
3. Gere o documento completo seguindo `skills/rfc-writer/templates/rfc-template.md`,
   sem pular nenhuma seção.
4. Rode o checklist final da skill antes de mostrar o resultado.
5. Salve o arquivo como `RFC-XXXX-titulo-em-kebab-case.md` (pergunte o número
   da RFC se o usuário não informar e não houver convenção óbvia no repo).
