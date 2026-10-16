# 3.2 Decisões de identidade visual

## Conceito

Um portfólio de quem está começando na área, mas quer mostrar **constância de aprendizado**. Por isso o visual é sóbrio, limpo e sem enfeite que distraia da trajetória. A decisão de partida foi: **100% preto, cinza e branco**, sem cor de destaque.

## Paleta de cores

O site tem dois temas (escuro e claro), e as cores se invertem entre eles. Os valores abaixo são os do arquivo `app/globals.css`.

| Cor | Hex | Papel no tema escuro | Papel no tema claro |
|---|---|---|---|
| Preto | `#121212` | Fundo da página | Texto principal e botões preenchidos |
| Branco gelo | `#f5f5f5` | Texto principal e botões preenchidos | Fundo da página |
| Cinza médio | `#a6a6a6` | Texto secundário (descrições, legendas) | não usado (baixo contraste sobre claro) |
| Cinza escuro | `#5c5c5c` | não usado | Texto secundário |
| Grafite | `#1c1c1c` | Fundo dos cards | não usado |
| Branco | `#ffffff` | não usado | Fundo dos cards |
| Linhas | `rgba(245,245,245,.16)` / `rgba(18,18,18,.14)` | Bordas finas e divisores | Bordas finas e divisores |

**Por que combinam com o conceito:**
- Preto, cinza e branco deixam o conteúdo (projetos, datas, certificações) como protagonista.
- Sem cor de destaque, o "destaque" é feito com **inversão** (botão que vira preto no branco e vice-versa), **contorno** (o sobrenome só com traço) e **sublinhado**. Isso mantém tudo dentro da paleta e dá um ar de editorial.
- A paleta vem da referência 02 (Dribbble), adaptada para ter também a versão clara.

**Acessibilidade (contraste calculado, mínimo recomendado 4,5:1):**

| Combinação | Contraste |
|---|---|
| `#f5f5f5` sobre `#121212` | 17,2:1 |
| `#a6a6a6` sobre `#121212` | 7,7:1 |
| `#121212` sobre `#f5f5f5` | 17,2:1 |
| `#5c5c5c` sobre `#f5f5f5` | 6,1:1 |

O cinza do texto secundário no tema claro é `#5c5c5c` e não o `#a6a6a6` da referência, porque `#a6a6a6` sobre fundo claro tem só 2,2:1 e fica difícil de ler. Essa foi uma decisão consciente de adaptar a referência.

## Tipografia

| Uso | Fonte | Sensação que queria transmitir |
|---|---|---|
| Textos corridos, botões, descrições | **Nunito** | Legível e amigável, combina com o tom descontraído |
| Títulos, nome gigante, rótulos, números, texto vertical | **Oswald** | Condensada e forte, dá o impacto "editorial" aos títulos em maiúsculas |

As duas fontes vieram da referência 02 e são gratuitas no Google Fonts. Oswald em caixa alta com espaçamento largo nos rótulos (`JORNADA`, `01 /`) cria uma hierarquia clara sem precisar de cor.

## Tom e personalidade

- **Descontraído, direto e honesto.** Escrito em primeira pessoa. Exemplo: "Eu não nasci sabendo programar. Fui aprendendo um curso, um projeto e um erro de cada vez, e não parei mais."
- **Sem desespero e sem citar vagas ou empresas-alvo.** O site mostra evolução e constância e deixa o recrutador concluir.
- **Moderno e minimalista no layout:** muito espaço em branco, bordas finas, cantos bem arredondados, números grandes.
- **Dinâmico:** animações pensadas para guiar a leitura (a linha do tempo se desenha, o texto acende), com respeito a quem pede "reduzir movimento" no sistema.
- **Inglês escrito como falante nativo** (não tradução automática): os dois idiomas têm textos próprios, em `pt.json` e `en.json`.

## Estrutura da página e por quê

A página é única e se percorre rolando, como uma história (decisão minha: "a ordem que o visitante vai escrolando e vai seguindo meio que uma história").

| # | Seção | Por que existe |
|---|---|---|
| — | **Intro e Abertura** | Primeira impressão: quem sou, o que estudo e números de constância |
| 01 | **Jornada** | Conta a evolução de 2023 até hoje em ordem cronológica: é o coração do objetivo (provar constância) |
| 02 | **Experiência** | Mostra trabalho real (Bozza), com a TV do RH em destaque |
| 03 | **Projetos** | Prova prática: REVI em destaque (com equipe), Global Solution, GoGames e TCC, cada um com "minha parte" e "o que aprendi" |
| 04 | **Skills** | Responde rápido "o que ele sabe?", com o logo de cada tecnologia |
| 05 | **Certificações** | Mostra o hábito de estudar, agrupado por tema |
| 06 | **Marcos** | Eventos e momentos (NEXT 2026, Jovi Mobile, Talent Summit) |
| 07 | **Contato** | Fecha com chamada para conversar, currículo em PDF, LinkedIn, GitHub e e-mail |

**Recursos de apoio:** troca de tema claro/escuro, botão PT/EN, menu de seções, barra de progresso de rolagem e currículo em PDF para baixar.
