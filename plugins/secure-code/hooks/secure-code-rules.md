# SECURE CODE MODE ACTIVE

Você DEVE aplicar os princípios abaixo em TODO código que escrever ou modificar nesta sessão. Não são opcionais — são requisitos de segurança.

## Princípios obrigatórios

### 1. Input validation (Trust boundary)
- NUNCA confie em dados que vêm de fora (request body, query params, headers, cookies, variáveis de ambiente controladas pelo usuário, dados de banco que vieram de input externo).
- Valide tipo, formato, tamanho e range de TODA entrada antes de usar.
- Use allowlists, não blocklists. Rejeite por padrão.

### 2. Injection prevention
- **SQL**: use sempre queries parametrizadas / prepared statements. NUNCA concatene strings em queries.
- **Command injection**: NUNCA passe input do usuário para `exec`, `system`, `child_process.exec`, `os.system`, `subprocess.shell=True` ou equivalentes. Use arrays de argumentos (`execFile`, `subprocess.run([...])`) quando necessário.
- **XSS**: escape toda saída renderizada em HTML. Use os mecanismos nativos do framework (React JSX auto-escape, template engines com auto-escape). NUNCA use `dangerouslySetInnerHTML`, `innerHTML`, `v-html` com dados não sanitizados.
- **Path traversal**: valide e normalize paths. NUNCA concatene input do usuário em caminhos de arquivo sem sanitizar.
- **LDAP/NoSQL/Template injection**: aplique o mesmo princípio — parametrize, nunca concatene.

### 3. Authentication & Authorization
- Autenticação em toda rota que não seja explicitamente pública.
- Verificação de autorização (permissões, roles, ownership) em toda operação que acesse ou modifique dados. Não confie apenas na autenticação.
- Tokens/sessões: use libs estabelecidas, não implemente crypto própria. Use `httpOnly`, `secure`, `sameSite` em cookies.
- NUNCA exponha credenciais, tokens ou secrets em logs, respostas de API, ou código client-side.

### 4. Data protection
- Senhas: hash com bcrypt/scrypt/argon2 + salt. NUNCA armazene em texto plano ou MD5/SHA sem salt.
- Dados sensíveis (PII, cartão, saúde): criptografe at rest e in transit. Use TLS. Minimize coleta e retenção.
- Logs: NUNCA logue senhas, tokens, números de cartão, ou PII sem mascarar.
- Respostas de erro: NUNCA retorne stack traces, queries SQL, ou detalhes internos ao usuário final. Use mensagens genéricas e logue o detalhe internamente.

### 5. Secure defaults
- CORS: configure origins explícitas. NUNCA use `*` em produção com credenciais.
- Headers de segurança: `Content-Security-Policy`, `X-Content-Type-Options: nosniff`, `Strict-Transport-Security`.
- Rate limiting em endpoints de autenticação e APIs públicas.
- CSRF protection em formulários que mudam estado.

### 6. Dependencies & supply chain
- Não adicione dependências desnecessárias. Cada dependência é superfície de ataque.
- Quando adicionar, prefira libs bem mantidas com poucos sub-dependencies.
- NUNCA fixe versão em range que inclui minor/patch sem lock file.

### 7. Secrets management
- NUNCA hardcode secrets, API keys, passwords, connection strings no código.
- Use variáveis de ambiente ou vault/secret manager.
- Verifique que `.env`, credenciais e chaves privadas estão no `.gitignore`.

### 8. Error handling seguro
- Capture erros para não vazar informação interna.
- Falhe de forma segura: na dúvida, negue acesso / rejeite a operação.
- Não silencie erros de segurança (auth failures, permission denials) — logue-os.

## Como aplicar

- Ao escrever código novo: aplique todos os princípios relevantes automaticamente.
- Ao modificar código existente: se notar uma violação no código que está tocando, corrija-a junto com a mudança.
- Se o contexto não permitir aplicar um princípio (ex.: projeto sem framework de auth), sinalize ao usuário: "⚠️ SEGURANÇA: [descrição do gap]".
- Priorize: injection prevention e auth são os mais críticos. Um SQL injection em produção é pior que um header faltando.
