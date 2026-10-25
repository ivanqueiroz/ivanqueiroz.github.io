# AGENTS.md

Instruções para agentes que trabalham neste repositório. Esta é a fonte única: ferramentas específicas apenas apontam para cá. O estilo de escrita detalhado está em [docs/estilo-de-escrita.md](docs/estilo-de-escrita.md).

## Visão geral

- Blog pessoal de Ivan Queiroz, escrito em pt-BR: https://ivanqueiroz.dev
- Hugo (extended) 0.168.0, com o tema `poison` como submódulo em `themes/poison`.
- Publicado no GitHub Pages pelo workflow `.github/workflows/hugo.yaml`.
- Conteúdo em `content/posts/AAAA/` (posts e TILs) e `content/about/_index.md`.

## Papéis

Papéis são etapas, não ferramentas. Um agente pode assumir mais de um, mas a ordem é fixa: Pesquisador → Redator → Revisor → Publicador.

### Pesquisador

- **Entrada:** tema e perguntas do Ivan.
- **Saída:** antes de qualquer rascunho, uma lista de fontes abertas e lidas, cada uma com o que ela sustenta (ex.: "documentação do Spring Boot: sustenta a versão mínima do Java"). Fato sem fonte aberta fica de fora ou vira TODO.
- **Limites:** não escreve o post. Não afirma o que não leu. Quando existe fonte primária, não usa resumo de terceiro no lugar dela.

### Redator

- **Entrada:** roteiro e anotações do Ivan, mais as fontes aprovadas pelo Pesquisador. Só atua quando o Ivan pedir.
- **Saída:** rascunho completo, criado com `hugo new` (ver [Formatos](#formatos)), com `draft: true`.
- **Limites:** escreve no estilo do Ivan (ver `docs/estilo-de-escrita.md`) e só com o que ele forneceu. Não inventa experiência nem opinião em 1ª pessoa. Não publica.

### Revisor

- **Entrada:** rascunho ou branch com o post.
- **Saída:** lista de problemas (ortografia, gramática, estilo, consistência, links, TODOs pendentes) e as correções feitas em posts novos. Também lista o que não conseguiu checar.
- **Limites:** é sempre a última etapa antes de qualquer PR. Corrige sem trocar o jeito de dizer do Ivan. Em posts já publicados, só aponta problemas (regra f).

### Publicador

- **Entrada:** post revisado.
- **Saída:** front matter conferido, build de validação sem erros, branch novo e PR para `main` com a descrição do que mudou e dos TODOs pendentes.
- **Limites:** não faz merge, não faz push na `main`, não dispara deploy. O merge na `main` dispara o workflow de publicação, então essa decisão é do Ivan.

## Regras de conteúdo

a) **Draft.** Todo rascunho nasce com `draft: true`. O agente nunca publica, nunca faz merge e nunca dispara deploy.

b) **Fontes.** Cite só o que foi aberto e lido. Prefira fontes primárias (docs oficiais, especificação, repositório, paper). Os links vão na seção `## Fontes`, no fim do texto. Nunca invente URL, citação, versão ou número. O que não puder verificar não é afirmado e recebe `<!-- TODO(ivan): verificar -->`. Para fatos que mudam (versões, preços, APIs), registre a data de consulta.

c) **Experiência própria.** Nunca invente experiência ou opinião em 1ª pessoa. Use só o que o Ivan deu no roteiro ou nas anotações. Onde faltar, deixe `<!-- TODO(ivan): sua experiência aqui -->`. O aviso de uso de IA fica a critério do Ivan: o agente não o adiciona por conta própria.

d) **Código.** Todo exemplo é compilado ou executado antes de entrar no post, e as versões usadas são declaradas no texto (ex.: "testado com Java 21 e Spring Boot 3.5"). Se não for possível rodar, avise em vez de incluir o código.

e) **Ortografia.** pt-BR pelo Acordo Ortográfico (ex.: "ideia", sem acento). Corrija grafia, acentuação, concordância, pontuação e crase sem trocar o jeito de dizer do Ivan. Rode `hunspell -d pt_BR -l < arquivo.md` quando o dicionário existir; confirme antes com `hunspell -d pt_BR -l` num texto de teste. Sem dicionário, faça revisão manual e avise no PR.
   **Estado em 2026-10-25:** o dicionário pt_BR não está instalado (`hunspell -d pt_BR -l` falha). No Arch ele vem do AUR: `yay -S hunspell-pt-br`, que exige `sudo`, então o agente não instala e pede ao Ivan. Até isso mudar, a revisão é manual.

f) **Posts publicados.** O Revisor só aponta problemas em posts já publicados e nunca edita sozinho, porque mexer altera o histórico e as URLs. Edição só com autorização explícita do Ivan.

## Formatos

**Post longo** (1.000-4.000 palavras)

- Archetype: `archetypes/post.md`. Criação: `hugo new --kind post posts/AAAA/AAAA-MM-DD-slug.md`.
- Abre com gancho ou epígrafe. Seções com `##`, subseções com `###`. Termina com `## Concluindo` e `## Fontes`.

**TIL** (300-500 palavras)

- Archetype: `archetypes/til.md`. Criação: `hugo new --kind til posts/AAAA/AAAA-MM-DD-slug.md`.
- Vai direto ao ponto, com um exemplo. Termina com `## Fontes`.
- Pendente de confirmação pelo Ivan: se TILs ficam em `posts/` ou em outra seção. Não há TIL publicado no repositório ainda.

## Regras do projeto

**Hugo e build**

- Versão esperada: 0.168.0 (extended). Confirme com `hugo version`, porque o `hugo` do PATH pode ser outra versão. O binário do mise fica em `~/.local/share/mise/installs/hugo-extended/0.168.0/hugo`.
- Build de validação, com saída fora do repositório: `hugo --gc --minify -d "$(mktemp -d)"`.
- O build local é obrigatório antes do PR. O workflow só roda em push para `main`, então o PR não é validado no CI.
- O build mostra avisos de `deprecated` (ex.: `languageCode` em `hugo.toml`). Eles já existem; não corrija sem pedido.

**Tema e layouts**

- Não mexa em `themes/poison` (submódulo). Customize só em `layouts/` ou `assets/`.
- Shortcodes disponíveis: `kotlin`, `iframe`, `sub`, `sup` (em `layouts/shortcodes/`), além de `ref` do próprio Hugo. Detalhes e uso no guia de estilo.

**Criar post**

- Sempre via `hugo new` com o archetype certo. Não copie um post antigo como base.
- Front matter completo: `title`, `description` (1-2 frases, ~150 caracteres), `date`, `tags` (minúsculas, lista inline), `categories` (lista inline) e `draft`.

**URLs**

- A URL vem do caminho do arquivo: `content/posts/2026/2026-10-25-slug.md` vira `/posts/2026/2026-10-25-slug/`. Renomear um arquivo publicado muda a URL.
- Não mude URLs existentes. Posts antigos têm o campo `url:` no front matter; não mexa nele.
- O Giscus usa o pathname como chave de comentários (`hugo.toml`, `mapping = "pathname"`). Mudar a URL de um post separa os comentários dele.
- Imagens de posts novos em `static/images/AAAA/MM/DD/` (padrão de 2024), referenciadas com caminho absoluto (`/images/AAAA/MM/DD/arquivo.png`).

**Git**

- Branch e PR para toda mudança. Nunca faça push direto na `main`.
- A `main` está travada e exige review. Merge é decisão do Ivan.
- Commits em inglês, no padrão convencional: `feat:`, `fix:`, `docs:`, `chore:`.
- O working tree pode ser compartilhado com outros agentes. Não troque de branch e não faça commit se a tarefa disser para não fazer.

**Checagens antes do PR**

- `grep -rn "TODO(ivan)" content/`: lista os TODOs pendentes. Eles vão no corpo do PR.
- Build de validação sem erros (comando acima).

## Limites

- Sem credenciais (tokens, chaves, `.env`), nem no repositório nem em comandos.
- Não publica, não faz merge e não dispara deploy.
- Não altera posts antigos sem autorização explícita.
- Não envia rascunhos para serviços externos sem pedido.
