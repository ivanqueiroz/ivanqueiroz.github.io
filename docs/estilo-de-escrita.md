# Guia de estilo de escrita

Guia para escrever posts no tom do Ivan Queiroz. Serve de referência para o Redator e o Revisor (ver [AGENTS.md](../AGENTS.md)).

Derivado em 2026-10-25 a partir dos 32 posts em `content/posts/` e de `content/about/_index.md`. Peso maior para o post de 2024 e para os de 2012 a 2022, que servem para as constantes. **O post de 2025 (`content/posts/2025/`) foi criado por um agente de IA** (confirmado pelo Ivan em 2026-10-25): ele não é referência de voz, e o que o guia cita dele serve só como contraexemplo ou para estrutura. Com pouco material recente, a amostra é pequena: tudo que for inferência fraca está marcado com um `<!-- TODO(ivan): ... -->`. Melhorar este guia, principalmente a voz, é uma tarefa futura.

Este guia descreve o que os posts fazem. Ele não é uma lista de regras para o agente inventar texto no mesmo molde.

## 1. Tom e voz

- **1ª pessoa, com ressalva.** O autor fala como quem relata a própria experiência: "eu" aparece como palavra em 13 dos 32 posts (contagem por grep). Quando a afirmação é pessoal, ela vem com um qualificador: "inclusive eu, após alguma pesquisa e experimentação" (2025).
- **Dirige-se ao leitor com "você".** Aparece em cerca de 23 linhas dos posts. No fechamento de 2025, usa "leitor" explicitamente.
- **Explica para quem está aprendendo.** Diz o que vai ou não vai cobrir: "Não vou aprofundar na matemática" (`content/posts/2022/2022-05-21-tempo-complexidade-algoritmo.md:27`).
- **Pouco entusiasmo de marketing.** A exclamação aparece em vários posts de 2019-2020 (15 linhas só em `content/posts/2019/2019-05-27-historia-java.md`) e raramente nos recentes (2 linhas em 2025). Os recentes são mais formais que os de 2019-2020 ("Este artigo tem como objetivo mostrar...").
- **Sobre (`content/about/_index.md`).** Frases diretas, em primeira pessoa, sem gíria: "Sou engenheiro de software." (linha 6). Use como referência para a voz da apresentação, não para posts.
- <!-- TODO(ivan): confirmar o grau de formalidade desejado para posts novos (2024 mais formal; 2019-2020 mais coloquial). -->

## 2. Estrutura típica

### Abertura

Três padrões aparecem:

1. **Contexto pessoal ou anedota** (2024, linha 18): o autor conta como surgiu a ideia.
2. **Escopo do texto** (2020, linha 14; 2025, linha 10): primeiro o que o post cobre, depois a reflexão. Ex.: "Neste artigo, compartilho minhas impressões e aprendizados ao revisitar o Kotlin" (2025, linha 10).
3. **Pergunta direta** (2022, linha 11): "O que é notação big-O?".

Antes de a abertura, costuma haver a **epígrafe** (ver abaixo).

### Epígrafe

- Bloco de citação com a frase e, na linha seguinte, a atribuição após `-- `, com ou sem itálico no nome (`-- Andrew Carnegie`, `-- _Sun Microsystems_`). Aparece em posts de 2017 a 2025.
- <!-- TODO(ivan): as epígrafes existentes não foram verificadas por mim. Ao usar epígrafe, verificar o texto e o autor antes (AGENTS.md, regra b). -->
- Formato da citação: aspas duplas (`"..."`) ou tipográficas (`“...”`), sem padrão único.

### Títulos

- `##` para seções principais, `###` para subseções. Os posts de 2019-2020 usam `#` no corpo; evite, porque o título já vem do front matter.
- **Caixa dos títulos:** mistura. Em 2022 e 2024 são frases (`## O que é o big-O?`, `## Uma aplicação Kanban para desktop`). Em 2019 há os dois (`## Morre o Star7 e nasce o Java` e `## Grandes Evoluções`). O post de 2025 usa Title Case (`## O Que Mudou no Kotlin (e no Ecossistema) nos Últimos 3 Anos?`), mas ele foi criado por IA. **Decisão do Ivan:** frases sucintas que expressam a ideia do artigo, em caixa de frase (só a primeira palavra e nomes próprios em maiúscula), sem Title Case.
- Títulos com dois-pontos (`## Primeira dica: ...`, em 2021; `### Avanços em Frameworks: Ktor e Spring Boot`, em 2025) aparecem em alguns posts. Não aparecem nos de 2024.

### Fechamento

- **Recentes (2024, 2025):** parágrafos de recapitulação, sem assinatura. "Esse artigo mostrou como configurar uma aplicação..." (2024, linha 329). O de 2025 convida a comentar: "Se você, leitor, também passou por uma experiência semelhante [...] adoraria ouvir sua história." (linha 184).
- **Antigos (2012-2022):** assinatura do tipo "Um forte abraço e até a próxima." Não aparece em 2024 nem em 2025.
- **Decisão do Ivan:** a assinatura "Um forte abraço e até a próxima." pode ser mantida. Ela vai como último parágrafo da `## Conclusão`, antes da seção Fontes, como nos posts antigos.

### Seção Fontes

- Vem no fim, depois da conclusão. Os nomes variam: `## Fontes` (2017-2024), `## Referências` (2025), `## Créditos` (2017, quando o post tem código no GitHub).
- Ver [seção 8](#8-links-e-fontes).
- **Decisão do Ivan:** o título final é `## Conclusão`, seguido de `## Fontes`. Os posts antigos têm variações (`## Finalizando`, `## Concluindo`); não replique.

## 3. Ritmo e tamanho de parágrafos

- **Quebra de linha.** A premissa de quebrar o markdown em torno de 120 colunas vale só para os posts de 2019-2022, e mesmo assim com exceções (há linhas de até 206 colunas em `2019-05-27-historia-java.md`). Os posts de 2024 e 2025 têm cada parágrafo numa linha só: o de 2025 tem linhas de até 1.260 caracteres. Recomendação: um parágrafo por linha, como nos recentes. <!-- TODO(ivan): confirmar. -->
- **Tamanho dos parágrafos (contagem aproximada, sem listas nem código):** 2024 tem ~37 palavras por parágrafo; 2025, ~73. Nos posts de 2019-2022, a média varia de ~23 a ~95 (o de comandos Git, cheio de listas e código, não entra bem nessa conta).
- **Frases:** médias a longas, com orações encadeadas por vírgula e "que", "onde", "mas". Frases curtas ficam para transições ("Aqui uma observação:", "Agora vamos implementar...").
- **Parágrafo de código:** um parágrafo de contexto antes do bloco. Nos recentes, a frase introdutória termina em dois-pontos: "Como a aplicação será desktop não será necessário subir uma aplicação web, então podemos ajustar a configuração no `application.properties`:" (2024, linha 76).

## 4. Vocabulário e construções recorrentes

Construções observadas (contagem aproximada por grep, por linha):

- **Apresentação do texto:** "Nesse artigo" (7 linhas), "Neste artigo" (2), "Este artigo tem como objetivo" (2024).
- **Ressalva de escopo:** "Não vou aprofundar...", "Não foi objetivo mostrar detalhes..." (2024, linha 329).
- **Apontar algo no código:** "Aqui uma observação:" (2024, linha 122); "Coloquei aqui apenas o início da classe" (2024, linha 256).
- **Conectores:** "Além disso" (9 linhas), "Aqui" (8), "Basicamente" (5). Aparecem em vários posts.
- **Expressões de expectativa:** "Espero que..." (6 linhas, 2017-2021), como em "Espero que seja útil".
- **Palavras que aparecem muito:** "ecossistema" (12 linhas), "é fundamental" (3), "robusto" (4).
- **Primeira pessoa do plural em tutorial:** "vamos" para guiar o passo a passo ("Agora vamos implementar..." em 2024).
- **Expressões que só aparecem no post de 2025 (evitar, ver seção 9):** "Não há como subestimar", "não mediram esforços", "é como reencontrar um velho amigo", "trunfo".

## 5. Termos em inglês

- Termos técnicos ficam em inglês quando são o nome oficial: `framework`, `starter`, `data classes`, `extension functions`, `coroutines`, `streaming`, `drag and drop`. Não traduza: o post de 2024 traduziu "beans" e "Spring" de forma errada (ver seção 9).
- Itálico no primeiro uso de um termo em inglês aparece em 2020 (`*streaming*`) e 2024 (`_starter_`, `_views_`). Em 2025 não há itálico para eles. Não havia padrão único. **Decisão do Ivan:** sempre itálico (`*termo*`) em termos em inglês, a cada uso no texto corrido. Identificadores, classes e comandos continuam em crase, sem itálico.
- Identificadores, classes, métodos e comandos vão em crase: `` `runApplication` ``, `` `@Scheduled` ``, `` `application.properties` ``.

## 6. Listas

- **Bullets:** o post de 2025 usa `*` com três espaços (`*   **Melhorias:** texto`); o de 2024 usa `- `. Escolha uma e mantenha no post.
- **Item com rótulo:** `**Rótulo:** explicação`, com dois-pontos dentro do negrito ou fora. Aparece nos dois posts recentes.
- **Passo a passo:** lista numerada (`1.`, `2.`), como na seção de configuração de 2024.
- **Tamanho:** 3 a 6 itens. Listas longas viram seção própria. <!-- TODO(ivan): confirmar; é uma leitura das listas, não uma contagem. -->

## 7. Código e shortcodes

**Blocos de código.** Use cerca com a linguagem: ```` ```java ````, ```` ```kotlin ````, ```` ```xml ````. O post de 2024 usou ```` ```terminal ```` para uma linha de `application.properties`. <!-- TODO(ivan): confirmar a linguagem para arquivos .properties. -->

**Versões no texto.** Declare a versão junto do código, como em 2024, linha 70: "Estou utilizando o Java 17 para esse projeto, mas acredito que não teria problema utilizar uma versão mais recente." O AGENTS.md exige isso (regra d).

**Shortcodes** (definidos em `layouts/shortcodes/`):

| Shortcode | Uso no repositório | Como usar |
|---|---|---|
| `kotlin` | 5 blocos em 2022 (`content/posts/2022/2022-05-21-tempo-complexidade-algoritmo.md`) | `{{< kotlin >}}...{{< /kotlin >}}`. Só com `kotlinplay: true` no front matter, porque é ele que carrega o Kotlin Playground (`layouts/partials/head/head.html`). Para os outros posts, use cerca ```` ```kotlin ````. |
| `sup` | 13 vezes em 2024 (notas numeradas) | `{{< sup "1" >}}`. O número corresponde à posição do item na seção Fontes. |
| `ref` | 7 vezes em 2015-2020 (links internos) | `[texto]({{< ref "posts/2020/2020-06-14-conceitos-kafka" >}})`. Os exemplos usam caminhos com e sem `/` inicial e com e sem `.md`; use o formato sem extensão e sem `/` inicial, e confira o link no build local. <!-- TODO(ivan): confirmar a convenção de caminho do ref. -->
| `sub` | não usado em nenhum post | Definido em `layouts/shortcodes/sub.html`. Se precisar, teste no build antes. |
| `iframe` | não usado em nenhum post | Definido em `layouts/shortcodes/iframe.html` (`width="100%" height="150"`). Se precisar, teste no build antes. |

**Imagens.** `![texto alternativo](/images/AAAA/MM/DD/arquivo.png)`, com os arquivos em `static/images/`. O padrão de 2024 é `AAAA/MM/DD`; os posts de 2015-2017 usam `AAAAMMDD` e 2022 usa só `AAAA`. Use o de 2024.

## 8. Links e fontes

- Link inline em markdown: `[texto](https://...)`. Sem espaço entre `]` e `(`. O post de 2024 tem um link quebrado por espaço (linha 54).
- **Notas no texto:** 2024 usa `{{< sup >}}` com número. Uma marca por afirmação que precisa de fonte, e o número bate com a lista de Fontes. <!-- TODO(ivan): confirmar, porque 2024 repete os números sem regra clara. -->
- **Seção Fontes:** lista numerada, com o nome da fonte como link: `1. [Openjfx.io](https://openjfx.io/)` (2024, linha 333). Os posts de 2025 usam uma lista por organização, com "Nome: URL". Ambos são aceitos. Prefira fontes primárias (AGENTS.md, regra b).

## 9. O que evitar

### Padrões de texto genérico ausentes dos posts

Verificados com grep em todos os posts: zero ocorrências de "Em um mundo", "No cenário atual", "guia abrangente", "Neste guia", "Ao longo deste", "Ao final deste", "É importante ressaltar", "Em conclusão", "Em suma", "Portanto", "Desta forma", "fascinante", "uau", "Dica:", "Nota:", "**Dica", e emojis. O travessão "—" não aparece em nenhum post. O "–" aparece em três linhas, todas de 2024 e 2025. <!-- TODO(ivan): confirmar o travessão; a regra aqui é inferida só da ausência nos posts. -->

### Frases que só aparecem no post de 2025

"Não há como subestimar", "não mediram esforços", "é como reencontrar um velho amigo", "trunfo". Estão no post de 2025 e em nenhum dos posts de 2012-2022. Não use como padrão. O Ivan confirmou que esse post foi criado por um agente de IA; por isso as frases genéricas não representam a voz dele. A revisão desse post fica para depois.

### Erros que não devem ser copiados

- "an" no lugar de "a" (2024, linhas 52 e 56): "an aplicação", "an existência", "an implementação".
- Tradução errada de termos: "grãos e as dependências do verão" (2024, linha 50), onde o sentido era Spring beans.
- Grafias erradas: "listerner" (2024, linha 180), "Aplication" (2024, linha 141), "esté" (2024, linha 325), "Concluíndo" (2019-04-26).
- Pergunta com erro: "Para quer serve?" (2022, linha 11).

## 10. Exemplos reais

Trechos curtos, com o arquivo e a linha de origem. Use como referência de voz, não para copiar.

1. **Abertura com anedota.** `content/posts/2024/2024-01-27-conectando-o-poder-do-spring-boot-à-experiência-visual-do-javafx-um-guia-completo.md:18`:
   > Durante as minhas férias comecei a organizar alguns projetos pessoais e veio na minha mente como seria criar uma aplicação de controle de tarefas que utilizasse Kanban.

2. **Escopo do texto.** `content/posts/2020/2020-06-14-conceitos-kafka.md:14`:
   > Nesse artigo irei escrever sobre esse novo aprendizado e minhas impressões sobre o Kafka

3. **Versão declarada junto do código.** `content/posts/2024/2024-01-27-conectando-o-poder-do-spring-boot-à-experiência-visual-do-javafx-um-guia-completo.md:70`:
   > Estou utilizando o Java 17 para esse projeto, mas acredito que não teria problema utilizar uma versão mais recente.

4. **Experiência pessoal com ressalva.** *(post de 2025, criado por IA: serve só como estrutura, não como voz)* `content/posts/2025/2025-05-23-retornando-kotlin-apos-tres-anos.md:114` (dentro de um item de lista):
   > muitos desenvolvedores (inclusive eu, após alguma pesquisa e experimentação) optam por usar classes regulares (`class`) para entidades JPA

5. **Ressalva de escopo.** `content/posts/2022/2022-05-21-tempo-complexidade-algoritmo.md:27`:
   > Não vou aprofundar na matemática, mas a complexidade pode ser definida como uma função numérica *T(n)*

6. **Recapitulação no fechamento.** `content/posts/2024/2024-01-27-conectando-o-poder-do-spring-boot-à-experiência-visual-do-javafx-um-guia-completo.md:329`:
   > Esse artigo mostrou como configurar uma aplicação para unir o JavaFX com o Spring Boot, permitindo que o desenvolvimento desktop possa usufruir dos recursos de um dos frameworks mais utilizados no mercado, [...]

7. **Fontes numeradas.** `content/posts/2024/2024-01-27-conectando-o-poder-do-spring-boot-à-experiência-visual-do-javafx-um-guia-completo.md:333`:
   > 1. [Openjfx.io](https://openjfx.io/)

8. **Convite ao leitor no fechamento.** *(post de 2025, criado por IA: serve só como estrutura, não como voz)* `content/posts/2025/2025-05-23-retornando-kotlin-apos-tres-anos.md:184`:
   > Se você, leitor, também passou por uma experiência semelhante – seja retornando ao Kotlin após um hiato ou revisitando qualquer outra tecnologia depois de um tempo – adoraria ouvir sua história.

## 11. Checklist de revisão

Antes de abrir o PR, confira:

- [ ] `draft: true` no front matter, e o arquivo foi criado com `hugo new`.
- [ ] `title`, `description` (1-2 frases, ~150 caracteres), `date`, `tags` (minúsculas, lista inline), `categories` e `draft` preenchidos.
- [ ] Post longo: 1.000-4.000 palavras, termina com `## Conclusão` (com a assinatura "Um forte abraço e até a próxima.") e `## Fontes`. TIL: 300-500 palavras, um exemplo, termina com `## Fontes`.
- [ ] Títulos em `##` e `###`, sem `#` no corpo.
- [ ] Epígrafe (se houver) com autor e texto verificados.
- [ ] Cada afirmação factual tem fonte aberta e lida, com link na seção Fontes. Nenhuma URL, versão ou número inventado.
- [ ] Experiência em 1ª pessoa só com o que o Ivan forneceu. Lacunas marcadas com `<!-- TODO(ivan): sua experiência aqui -->`.
- [ ] Todo código compilou ou rodou, com as versões declaradas no texto. Código que não rodou não entrou.
- [ ] Ortografia em pt-BR pelo Acordo Ortográfico. `hunspell` rodado como no AGENTS.md (regra e), com a leitura manual feita depois; falsos positivos de termos em inglês descartados.
- [ ] Nenhuma frase da seção 9 entrou no texto.
- [ ] Parágrafos e listas no padrão da seção 3 e 6.
- [ ] Shortcodes usados como na seção 7.
- [ ] Nenhum TODO(ivan) sem registro no PR: `grep -rn "TODO(ivan)" content/`.
- [ ] URL do arquivo não mudou em relação a posts existentes (AGENTS.md, bloco URLs).
