---
title: "{{ replace (replaceRE "^[0-9]{4}-[0-9]{2}-[0-9]{2}-" "" .Name) "-" " " | title }}"  # TODO(ivan): revisar o título
description: ""  # TODO(ivan): 1-2 frases, ~150 caracteres
date: {{ .Date }}
tags: [ ]  # minúsculas, lista inline
categories: [ ]
draft: true  # só o Ivan remove; o agente nunca publica
---

<!-- Formato: post longo, 1.000-4.000 palavras. Guia de estilo: docs/estilo-de-escrita.md -->

<!-- Abertura: gancho ou epígrafe. Epígrafe só com autor verificado; sem epígrafe, abra com o gancho. -->
<!-- TODO(ivan): abertura (gancho, anedota ou epígrafe) -->

## Contexto

<!-- TODO(ivan): por que este assunto, em 1-2 parágrafos -->

## Desenvolvimento

### Subtópico

<!-- Código: compilar/executar antes e declarar as versões no texto (ex.: "testado com Java 21 e Spring Boot 3.5"). -->
<!-- Se não puder rodar, avisar em vez de incluir. -->

## Conclusão

<!-- TODO(ivan): sua experiência aqui -->

Um forte abraço e até a próxima.

## Fontes

<!-- Só fontes abertas e lidas, preferir primárias. Data de consulta para fatos que mudam (versões). -->
1. <!-- TODO(ivan): verificar --> título, URL e data de consulta
