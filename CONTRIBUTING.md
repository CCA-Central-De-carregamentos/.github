# Como contribuir — CCA Central de Carregamentos

Vale para todos os repositórios da organização que não tragam um `CONTRIBUTING.md` próprio. Quando o repositório tiver um `AGENTS.md`, ele traz as regras daquele repositório e vence este arquivo.

## Branches

- `main`: o que está liberado, ou seja, a release. Ninguém commita direto.
- `develop`: a integração. Todo PR entra por ela.
- Branch de trabalho: `<tipo>/<descricao-em-kebab>`, por exemplo `feat/login-motorista` ou `fix/espelho-a4`.

Tipos: `feat` `fix` `chore` `refactor` `docs` `test` `ci` `perf`.

## Commits

`<tipo>(<escopo>): <o que muda, no imperativo>`, por exemplo `fix(ponto): espelho cabe numa folha A4`.

## Pull requests

- O PR vai para a `develop` e usa o template da organização: uma frase de abertura com o que passa a ser verdade no sistema, depois **Mecanismo · Correção · Raio de alcance · Evidência · Rollback** e, quando houver, **Decisão**.
- "Testado localmente" não é evidência. Cole o comando e a saída.
- O CI tem de estar verde (testes, CodeQL e varredura de segredos) antes do review.
- A promoção para a `main` é sempre feita em dois PRs: o release `develop → main` (squash) e, logo em seguida, o back-merge `main → develop` (merge commit).

## Segredos

- Senha, token e chave **nunca** entram no repositório, nem em documentação. Use `.env` fora do versionamento, variável de ambiente ou o cofre da empresa.
- O GitHub bloqueia o push que contém segredo. Se isso acontecer, tire o valor do commit; não peça liberação.
- Arquivos `.env.example` levam só o nome da variável, sem valor.

## Ferramentas

- Node: **pnpm** sempre, nunca npm nem yarn. Um repositório tem um lockfile só.
- Dependências: o Dependabot abre PR semanal para a `develop`, agrupado por ecossistema.

## Segurança

Para relatar uma falha, siga o [SECURITY.md](SECURITY.md). Nunca abra issue pública.
