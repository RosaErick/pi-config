# Configuração do Pi

Configuração global versionada desta máquina.

## Link simbólico

`~/.pi/agent/settings.json` aponta para `/home/erick/Workspace/pi-agent-config/settings.json`.

Credenciais (`auth.json`), catálogo de modelos e sessões permanecem em `~/.pi/agent/`, fora deste repositório.

As skills estão em `/home/erick/Workspace/skills`, referenciadas pelo `settings.json`, e não são copiadas para este repositório.

## Alterações

Depois de editar a configuração, execute `/reload` no Pi ou reinicie-o quando necessário.

```bash
cd ~/Workspace/pi-agent-config
git diff
git add settings.json
git commit -m "Atualiza configuração do Pi"
```

Em outra máquina, ajuste o caminho das skills e crie o link para o local do clone. Preserve qualquer configuração existente antes de substituí-la.
