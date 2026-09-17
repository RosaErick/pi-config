# Configuração global do Pi

`~/.pi/agent` é um link simbólico para `/home/erick/Workspace/pi-agent-config`.
Assim, inclusive gravações que substituem arquivos atomicamente chegam ao repositório.

## O que pode ser versionado

- `settings.json`: preferências, modelos selecionados, fontes de recursos e lista de packages.
- `keybindings.json`: atalhos.
- `AGENTS.md`, `AGENTS.override.md`, `CLAUDE.md`, `SYSTEM.md`, `APPEND_SYSTEM.md`: instruções globais.
- `extensions/`, `skills/`, `prompts/`, `themes/`: recursos próprios.
- `package.json` e lockfiles da raiz: dependências de recursos próprios, se necessários.

Diretórios vazios não são registrados pelo Git. A configuração de projetos (`.pi/` dentro de cada projeto) deve ser versionada no respectivo projeto.
As skills externas em `/home/erick/Workspace/skills` continuam no repositório próprio; aqui fica somente sua referência.

## Dados privados e gerados

A política de `.gitignore` permite explicitamente as configurações conhecidas e ignora novos arquivos na raiz por padrão.
Credenciais, sessões, catálogo/cache de modelos, decisões de confiança, packages baixados (`npm/` e `git/`) e dependências não são versionados.
`models.json` também fica excluído por poder conter chaves e headers sensíveis; revise e crie um exemplo sanitizado separadamente se precisar compartilhar provedores customizados.

Os dados preexistentes foram preservados fisicamente em `~/.pi/agent-local/`, com permissão 0700:

- `auth.json`
- `models-store.json`
- `sessions/`

O diretório do Pi contém links ignorados para esses itens. Não apague `~/.pi/agent-local/`: ele contém dados ativos, não um backup.
Outros arquivos de estado criados futuramente podem ficar no diretório do repositório, mas são ignorados pela política padrão.

**Limite de segurança:** `.gitignore` não detecta segredos dentro de arquivos permitidos nem impede `git add -f`. Não grave tokens, senhas, URLs autenticadas ou informações privadas em settings, instruções ou código versionado. Use variáveis de ambiente/armazenamento de credenciais. Revise o diff antes de cada commit e antes de publicar.

## Packages

`pi install` global registra a fonte em `settings.json`; os arquivos baixados ficam ignorados. Fixe versões npm ou refs Git para maior reprodutibilidade. Uma atualização sem mudança na referência configurada pode não gerar diff.
O Pi pode instalar packages ausentes ao iniciar; revise as fontes antes de usar este repositório em outra máquina.
Instalações com `-l` pertencem ao projeto e não entram neste repositório.

## Fluxo de versionamento

Não há commit ou push automático:

```bash
cd ~/Workspace/pi-agent-config
git status --short
git diff
# Revise os arquivos novos também antes de adicioná-los.
git add .
git diff --cached
git commit -m "Atualiza configuração do Pi"
```

Após mudanças manuais, use `/reload` no Pi ou reinicie-o quando necessário.

## Outra máquina

Clone o repositório, ajuste caminhos locais no `settings.json` e preserve o diretório `~/.pi/agent` existente antes de substituí-lo por um link para o clone. Faça login novamente; credenciais e histórico não acompanham o Git. As fontes externas de skills precisam estar disponíveis separadamente.
