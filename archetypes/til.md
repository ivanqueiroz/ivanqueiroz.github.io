---
title: "{{ replace (replaceRE "^[0-9]{4}-[0-9]{2}-[0-9]{2}-" "" .Name) "-" " " | title }}"  # TODO(ivan): revisar o título
description: ""  # TODO(ivan): 1-2 frases, ~150 caracteres
date: {{ .Date }}
tags: [ ]  # minúsculas, lista inline
categories: [ ]
draft: true  # só o Ivan remove; o agente nunca publica
---

<!-- Formato: TIL, 300-500 palavras. Vai direto ao ponto e tem um exemplo. Sem "Conclusão". -->
<!-- Guia de estilo: docs/estilo-de-escrita.md -->

<!-- TODO(ivan): o problema ou a dúvida, em 1-2 frases, sem preâmbulo -->

## Exemplo

<!-- Código: compilar/executar antes e declarar as versões no texto. Se não puder rodar, avisar em vez de incluir. -->

<!-- TODO(ivan): explicação curta do que o exemplo mostra (opcional: "Por que funciona") -->

## Fontes

1. <!-- TODO(ivan): verificar --> título, URL e data de consulta
