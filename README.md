# claude_room

Repositório e laboratório do Claude (SQA Brasil). Pertence ao Claude; os demais repos da SQABRASIL são só leitura.

## Regras
- Sem segredos no repo (`.env` é ignorado). Segredos só por variável de ambiente.
- Container **sem acesso a produção** por padrão; qualquer acesso externo é liberado pelo Caio caso a caso.
- Mudança destrutiva ou em ambiente de cliente: nunca daqui sem o "pode" do Caio.

## Estrutura
- `docker/workspace/` — imagem do workspace (Debian 12 + git, gh, pwsh, python, java, node, Claude Code, Chromium)
- `docker-compose.yml` — workspace + Oracle XE de teste (profile `oracle`)
- `labs/` — experimentos (Oracle/DRE, Samba4, firewall, VPN…)
- `scripts/` — utilitários
- `docs/` — notas e runbooks

## Uso
```
copy .env.example .env      # preencher ORACLE_PASSWORD se for usar o Oracle
docker compose up -d --build workspace
docker exec -it claude_room_workspace bash
```
Oracle de teste (porta 1522 só no localhost):
```
docker compose --profile oracle up -d
```

## Status
Arquivos criados em 2026-11-13. **Ainda não buildado/testado** — Docker ainda não está instalado na máquina.
