---
name: secure-code
description: "Ativa automaticamente via hook em toda sessão. Força validação de segurança arquitetural e princípios OWASP em todo código gerado. Também pode ser invocado manualmente para reforçar as regras ou verificar se estão ativas."
---

# Secure Code

Este plugin está ativo automaticamente via hook de sessão. As regras de
segurança em `hooks/secure-code-rules.md` são injetadas no início de toda
sessão.

Se invocado manualmente, confirme ao usuário que o modo está ativo e
relembre os princípios sendo aplicados.
