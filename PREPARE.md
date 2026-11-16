# PREPARADO PARA SUBIR (Hugo Rodriguez)

Tests 13/13, agente probado offline (leaderboard + cards generados). Nombre npm 'skill-audit' verificado libre.

## 1. Clonar y probar
    git clone https://github.com/hugororo2003/skill-audit && cd skill-audit
    npm test
    node agent.js --config config.example.json --no-publish   # offline, 4 skills locales
    node agent.js --top 10 --no-publish                        # online: anthropics + addyosmani

## 2. Publicar npm
    npm publish

## 3. Publicar en ClawHub
    clawhub skill publish .

## 4. Leaderboard vivo
    export GITHUB_TOKEN=<PAT con repo> PUBLISH_REPO=hugororo2003/skill-audit
    node agent.js --top 20          # publica a gh-pages
    # activar Pages (una vez): curl -X POST -H "Authorization: token $GITHUB_TOKEN" \
    #   https://api.github.com/repos/hugororo2003/skill-audit/pages \
    #   -d '{"source":{"branch":"gh-pages","path":"/"}}'
    # → https://hugororo2003.github.io/skill-audit/

## 5. Dejarlo vivo en la Pi (opcional)
    node agent.js --watch 360 --top 20   # cada 6h, re-audita solo lo cambiado

## Tras publicar (lo hago yo si quieres)
- Auditar top-50 ClawHub + PR con el leaderboard
- Post LinkedIn: "mi agente ahora audita las skills de otros agentes" + enlace al leaderboard
