# Alexandre Reeberg de Mello · ARM Consulting

Site pessoal e portfólio de Alexandre Reeberg de Mello, com foco em dar segurança a empresas que querem contratar a **ARM Consulting** (consultoria em Inteligência Artificial). Reúne as ofertas de consultoria, a pesquisa de pós-doutorado em governança e ciclo de vida da IA, palestras, currículo e trajetória.

- **Idiomas:** inglês por padrão, com versão completa em português em `/pt/`.
- **Design:** sistema de design **Kauri** (papel, fotocópia e retalhos de estampa de cera), com tema claro e escuro que segue a preferência do sistema.
- **Tecnologia:** Jekyll estático, publicado pelo GitHub Pages. Sem dependências de JavaScript.
- **Endereço:** `https://areeberg.github.io/alexandre.github.io/` (repositório de projeto; veja [Publicação](#publicação)).

## Páginas

| Página | Inglês | Português | Conteúdo |
| --- | --- | --- | --- |
| Início | `/` | `/pt/` | Abertura da ARM, números da carreira, as 3 ofertas, palestras recentes e parcerias |
| Consultoria | `/consulting/` | `/pt/consultoria/` | Ofertas com público e entregáveis, método de portões de decisão, casos, trajetória e FAQ |
| Pesquisa | `/research/` | `/pt/pesquisa/` | Pós-doutorado (UFSC e Halmstad University), métricas do Google Scholar, publicações, relatórios do GPAI e patentes |
| Palestras | `/talks/` | `/pt/palestras/` | Palestras e workshops, com link para gravação quando houver |
| Currículo | `/cv/` | `/pt/curriculo/` | CV completo, com botão para imprimir ou salvar em PDF |
| Sobre | `/about/` | `/pt/sobre/` | Biografia, foto, experiência e formação |

O rodapé de todas as páginas traz os contatos (e-mail, LinkedIn, Instagram, Google Scholar, ORCID), a razão social e o CNPJ da ARM.

## Como editar o conteúdo

Quase todo o texto fica em arquivos YAML em `_data/`, com os campos `en` e `pt` lado a lado. Para atualizar o site, edite esses arquivos; o HTML não precisa mudar.

| Arquivo | O que controla |
| --- | --- |
| `_data/offers.yml` | As 3 ofertas da ARM (título, para quem é, entregáveis) e a lista "também fazemos" |
| `_data/cases.yml` | Casos de clientes (desafio, o que foi feito e, opcionais, `result` e `quote` com depoimento) e startups apoiadas |
| `_data/faq.yml` | Perguntas frequentes da página de consultoria |
| `_data/talks.yml` | Palestras e workshops. `date` no formato `AAAA-MM`, `status` (`upcoming` ou `delivered`) e `video` opcional |
| `_data/publications.yml` | Métricas do Google Scholar (atualizar à mão), artigos, relatórios e patentes |
| `_data/cv.yml` | Currículo: resumo, destaques, experiência com tópicos, formação, competências e idiomas |
| `_data/experience.yml` e `_data/education.yml` | Linha do tempo resumida da página Sobre |
| `_data/links.yml` | E-mail, redes, Scholar, ORCID e dados da empresa (razão social e CNPJ) |
| `_data/ui.yml` | Rótulos da interface por idioma (menu, botões) |

Exemplos comuns:

- **Nova palestra:** acrescente um item no topo de `_data/talks.yml`, com os blocos `en` e `pt`. Ela aparece na página de palestras, na home (se estiver entre as duas mais recentes) e no currículo.
- **Depoimento de cliente:** em `_data/cases.yml`, preencha `quote: { text: "...", author: "Nome", role: "Cargo, Empresa" }` dentro de `en` e `pt` do caso.
- **Métricas do Scholar:** atualize `metrics` em `_data/publications.yml`, incluindo as datas `as_of_en` e `as_of_pt`.

## Estrutura do código

```
_config.yml            Título, URL, baseurl e ordem do menu (nav_refs)
_layouts/default.html  Layout único: <head> com SEO, Open Graph e dados estruturados (JSON-LD)
_includes/
  cabecalho.html       Menu e troca de idioma (liga as páginas pelo campo "ref")
  rodape.html          Contato, redes, razão social e CNPJ
  pg-*.html            Conteúdo de cada página, escrito uma vez para os dois idiomas
  palestra.html        Cartão de palestra reutilizado
assets/css/kauri.css   Tokens e componentes do Kauri, layout do site e estilos de impressão
assets/fonts/          Fontes do Kauri (Abril Fatface, Archivo, Caveat, Rye, UnifrakturMaguntia, Monoton)
assets/img/            Retrato (original e recortado) e imagem de compartilhamento og.png
*.html, pt/*.html      Páginas: só front matter (lang, ref, permalink) e o include correspondente
```

Cada página existe em dois arquivos com o mesmo `ref` e `lang` diferente (por exemplo, `consulting.html` e `pt/consultoria.html`). O menu e o botão EN/PT usam o `ref` para achar a versão equivalente. Para criar uma página nova: escreva o include em `_includes/pg-<nome>.html`, crie os dois arquivos de página, adicione o `ref` em `nav_refs` no `_config.yml` e o rótulo em `_data/ui.yml`.

## Rodar localmente

Requer Ruby e Bundler.

```bash
bundle install
bundle exec jekyll serve
```

O site abre em `http://localhost:4000/alexandre.github.io/` (por causa do `baseurl`).

## Publicação

O GitHub Pages publica a branch padrão. Como o repositório é de projeto (`areeberg/alexandre.github.io`), o `_config.yml` usa `baseurl: "/alexandre.github.io"`. Ao configurar um domínio próprio, troque para `baseurl: ""`, ajuste `url` e adicione o arquivo `CNAME`.

## Pendências

- [ ] Depoimentos de clientes nos casos (`_data/cases.yml`).
- [ ] Corrigir no LinkedIn a data da ARM Consultoria, que aparece encerrada.
- [ ] Link de agendamento (Calendly ou Google Agenda) no lugar do "Agendar uma conversa", que hoje leva ao e-mail.
- [ ] Domínio e e-mail próprios.
- [ ] Rodar o build real do Jekyll antes de publicar (o site foi conferido numa renderização aproximada).
- [ ] Remover `gulpfile.js` e `package.json`, que sobraram do tema antigo e apontam para um SCSS que não existe mais.

## Licença

O código herdado do tema original está sob a GNU General Public License v3.0 (veja `LICENSE`). Textos, fotos e dados pessoais são de Alexandre Reeberg de Mello.
