# rfc-writer

Plugin de Claude Code que padroniza a escrita e revisão de RFCs / design docs
seguindo um template fixo. Funciona no CLI e na extensão do VS Code (usam a
mesma configuração de plugins).

## O que tem aqui

- `skills/rfc-writer/SKILL.md` — a skill em si: quando ativar, regras de
  redação, checklist de qualidade.
- `skills/rfc-writer/templates/rfc-template.md` — o template que todo RFC
  segue. **Edite este arquivo com o template real do seu time.**
- `commands/rfc-new.md` — comando `/rfc-new`, cria um RFC do zero.
- `commands/rfc-review.md` — comando `/rfc-review`, revisa um RFC existente
  contra o template.

A skill ativa automaticamente quando você pede para "escrever um RFC",
"documentar essa decisão", etc. — não precisa digitar o comando, mas ele
existe para invocação explícita.

## Publicar no GitHub

```bash
cd rfc-writer
git init
git add .
git commit -m "rfc-writer plugin"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/rfc-writer.git
git push -u origin main
```

## Instalar (CLI ou VS Code — é o mesmo comando)

Dentro de uma sessão do Claude Code:

```
/plugin marketplace add SEU-USUARIO/rfc-writer
/plugin install alpheres@rfc-writer
```

No VS Code, `/plugins` abre a mesma interface e lê o mesmo marketplace — não
precisa reinstalar nada separadamente.

## Atualizar depois de mudar algo

```bash
git add .
git commit -m "ajusta template"
git push
```

E em cada máquina onde está instalado:

```
/plugin marketplace update
```

## Testar localmente antes de publicar

Sem precisar do GitHub ainda:

```
/plugin marketplace add ./caminho/para/rfc-writer
/plugin install alpheres@rfc-writer
```
