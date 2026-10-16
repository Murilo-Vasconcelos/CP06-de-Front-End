# CP06 de Front — Portfólio (Checkpoint 6: Vibecoding)

Repositório de entrega do **Checkpoint 6** de Front-End (FIAP). Ele reúne o **site** e toda a **documentação** pedida na atividade.

**Aluno:** Murilo Gomes

## Entregas da atividade

| Item | O que é | Onde está |
|---|---|---|
| 3.1 | Referências visuais (mínimo 5), com o que foi aproveitado de cada | [docs/01-referencias.md](docs/01-referencias.md) |
| 3.2 | Decisões de identidade visual: paleta (hex e papéis), tipografia, tom e estrutura | [docs/02-identidade-visual.md](docs/02-identidade-visual.md) |
| 3.3 | Prompts utilizados, na ordem e na íntegra | [docs/03-prompts.md](docs/03-prompts.md) |
| 3.4 | Registro de correções (Problema, Prompt de correção, Resultado, Aprendizado) e QA | [docs/04-registro-de-correcoes.md](docs/04-registro-de-correcoes.md) |
| 3.5 | Links do repositório e do deploy, prints e reflexão | [docs/05-resultado-final.md](docs/05-resultado-final.md) |

Os prints usados na documentação ficam em `docs/img/`.

## Sobre o projeto

Portfólio de uma página que conta a trajetória profissional e acadêmica por rolagem. Foi criado em conversa com a IA (Claude), em 5 passos, a partir de referências visuais e de um briefing. O processo completo está documentado nos arquivos acima.

## Créditos

- Logos das skills: [Simple Icons](https://simpleicons.org) (CC0) e [Devicon](https://devicon.dev) (MIT). As marcas pertencem aos seus donos.
- Fontes: Nunito e Oswald (Google Fonts, licença OFL).
- Referências visuais: autores citados em `docs/01-referencias.md`.

---

## O que o site tem

- Cores (preto, cinza e branco), fontes (Nunito e Oswald), tema claro/escuro e PT/EN
- Rolagem suave (Lenis), barra de progresso, cursor personalizado e intro com contador
- Abertura com nome gigante, foto com efeito do mouse e números que contam
- **Jornada:** frase que acende palavra por palavra e linha do tempo que se desenha na rolagem
- **Experiência:** Bozza, com a TV do RH em destaque
- **Projetos:** REVI em destaque (com a equipe e links do LinkedIn), Global Solution, GoGames e TCC, em cards que inclinam com o mouse
- **Skills:** 15 tecnologias com logo, em 4 grupos (linguagens, front-end, dados e nuvem, design)
- **Certificações:** 9 certificados em 4 grupos e faixas infinitas de palavras
- **Marcos** e **Contato** (botões magnéticos)
- Troca de tema com um círculo que se espalha a partir do botão (navegadores com View Transitions)
- Quem usa "reduzir movimento" no sistema vê tudo parado e no lugar
- Prévia de link (imagem ao compartilhar no LinkedIn/WhatsApp), sitemap, robots e hreflang PT/EN
- Link "pular para o conteúdo" e foco visível para quem navega pelo teclado

## O que você precisa preencher

Dados que não mudam de idioma ficam em `data/`:

- `data/profile.ts`: foto (`photo`), e-mail (`links.email`), LinkedIn, GitHub e os números da abertura
- `data/projects.ts`: link do repositório de cada projeto e a equipe do REVI. Quando o resultado do NEXT sair e você puder divulgar o código do REVI, coloque o link em `repo` e o botão "Ver código" aparece
- `data/experience.ts`: ferramentas mostradas na Bozza
- Currículo: salve o PDF em `public/curriculo-murilo.pdf`. Para atualizar, é só trocar o arquivo

## Como funcionam os idiomas

Todo texto do site fica em dois arquivos:

```
app/[lang]/dictionaries/pt.json
app/[lang]/dictionaries/en.json
```

Para mudar ou acrescentar um texto, edite os dois. Se faltar uma chave no
inglês, o TypeScript avisa. O arquivo `proxy.ts` escolhe o idioma na primeira
visita, e o botão PT | EN no topo troca depois.

## Estrutura

```
app/[lang]/     página, layout e dicionários de texto
components/     cabeçalho, botões e animações
components/sections/  Jornada, Experiência, Projetos, Skills, Certificações, Marcos, Contato
data/           projetos, equipe, ferramentas, skills (e logos) e dados do perfil
lib/i18n.ts     lista de idiomas
proxy.ts        escolhe o idioma na primeira visita
public/         currículo em PDF e imagens
