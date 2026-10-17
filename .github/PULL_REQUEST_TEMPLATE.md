<!--
  Padrão de PR da CCA (o detalhe está no repositório interno de processo)
  Cinco seções fixas + ## Decisão, condicional. Nenhuma das fixas é opcional;
  a que não se aplica leva uma linha dizendo por quê.

  A régua: o diff já conta o que mudou. O PR registra o que passou a ser VERDADE
  sobre o sistema. Antes de escrever, responda duas perguntas:
    1. Qual invariante passa a valer?
    2. O que essa escolha impede depois?

  "Testado localmente" não é evidência e não passa no review.
-->

<!-- Uma frase: que propriedade do sistema passa a valer. Não a atividade, não "este PR".
     efeito:     "Lançamento sem unidade resolvida passa a devolver 422."
     propriedade: "Nenhum lançamento entra no banco sem unidade resolvida — a unidade 1
                   deixa de ser destino de fallback."   <- esta é a régua -->

## Mecanismo

<!-- Por que o sistema se comportava assim, no nível do código ou do dado.
     Cite arquivo:linha e cole o trecho. Reclamação de usuário é contexto, não mecanismo.
     Feche nomeando a CLASSE do defeito (fallback silencioso, guarda que existe e não roda,
     escrita sem recorte por tenant, contrato assumido e não verificado) — classe nomeada
     é o que permite achar o mesmo defeito nos outros lugares onde ele mora. -->

## Decisão

<!-- CONDICIONAL. Entra se, e só se, o PR faz uma destas três:
       1. muda um contrato (schema lido por terceiro, payload do app, arquivo entregue a banco);
       2. cria ou dispensa uma invariante;
       3. é irreversível (mão única).
     Não faz nenhuma? APAGUE esta seção — seção de enfeite também é recusa.

     Quando entra, leva as três: a regra que passa a valer (uma frase testável);
     a ALTERNATIVA DESCARTADA e o que ela custaria (sem isso é preferência, não decisão);
     e o que a escolha fecha — dívida assumida com vencimento declarado. -->

## Correção

<!-- O que mudou e por que é a mudança mínima suficiente.
     Ordem obrigatória de aplicação (migração, sincronizador, espelho), numerada.
     Havendo ## Decisão acima, não repita a justificativa aqui. -->

## Raio de alcance

<!-- Rotas, tabelas, unidades, empresas, ambientes, jobs, contratos consumidos por terceiros.
     E a metade que salva o reviewer: o que explicitamente NÃO muda.
     Escrita em banco: declarar o recorte por tenant (empresa_id / unidade_id).
     Nomeie a fronteira que NÃO acompanha o deploy: o app instalado nos aparelhos, uma rotina agendada
     em outro servidor, o arquivo que o banco lê. Componente que não recompila é onde a mudança vira incidente. -->

## Evidência

<!-- Comando e saída, literais. Vale mais que a contagem de testes: a prova de que a
     invariante nova não pode ser violada — a tentativa que antes gravava, agora recusada.
     Sem execução possível: "Sem execução: alteração exclusivamente textual em <arquivo>." -->

```
$
```

## Rollback

<!-- Abra classificando a porta:
       mão dupla  — `git revert` restaura o estado anterior e ninguém percebe.
       mão única  — o revert do código NÃO desfaz o efeito: dado escrito, migração
                    destrutiva, arquivo entregue a terceiro, sequência consumida.
                    Aqui o rollback é um PROCEDIMENTO, escrito por inteiro, com a ordem.
     Dizer "mão dupla" onde há dado escrito para um deploy que podia seguir. -->

---
<!-- Gere com: tools/pr-assinatura.sh  — não escreva o rodapé à mão. -->
