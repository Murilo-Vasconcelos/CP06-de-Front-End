# 3.4 Registro de correções

Este registro tem **três partes**, para ficar claro quem achou cada problema:

- **Parte A:** rodadas em que **eu** reportei algo ou corrigi a conversa (cada uma tem o prompt real, em `03-prompts.md`).
- **Parte B:** problemas que a **IA** encontrou e corrigiu sozinha ao validar o código a cada passo (não houve prompt meu).
- **Parte C:** o **QA completo** feito no final, com navegador automatizado, e o checklist de QA manual.

> Observação honesta: na maior parte do processo eu aprovei as entregas de primeira. Em vez de inventar problemas, registro os que existiram de verdade. Os aprendizados valem para o próximo prompt inicial.

---

## Parte A: rodadas conduzidas por mim

### Rodada 1: mensagem enviada com erros e cortada
| Campo | Registro |
|---|---|
| **Problema** | Minha resposta à Etapa 1 foi enviada com erros de digitação ("surprienda", "costancia"), sem o item 3 (empresas-alvo) e a mensagem seguinte saiu cortada (só a letra "e"). |
| **Prompt de correção** | Reenviei o bloco completo e corrigido (Ajuste 3 em `03-prompts.md`). |
| **Resultado** | Resolveu totalmente. |
| **Aprendizado** | Reler e colar a mensagem inteira antes de enviar, e reunir todo o contexto (objetivo, empresas-alvo, tom) já no prompt inicial. |

### Rodada 2: posicionamento do perfil
| Campo | Registro |
|---|---|
| **Problema** | O conteúdo que a IA leu dos meus repositórios me posicionava como futuro dev backend Java. Isso limita a leitura do recrutador. |
| **Prompt de correção** | "Não precisa citar que eu quero ser dev backend de java, porque limita muito isso, quero que os recrutadores vejam e pensam que eu quero entrar no mundo de desenvolvimento de software" (Ajuste 5). |
| **Resultado** | Resolveu totalmente: o título virou "Estudante de Engenharia de Software" e o site não cita backend como objetivo. Java aparece apenas como uma das skills. |
| **Aprendizado** | Dizer no prompt inicial **qual posicionamento quero** e o que não quero citar. |

### Rodada 3: cores e nível de animação
| Campo | Registro |
|---|---|
| **Problema** | A IA perguntou se eu queria uma cor de destaque e eu ainda não tinha deixado claro o nível de animação que esperava. |
| **Prompt de correção** | "Quero que seja 100% preto, cinza e branco" e "eu quero que o site tenha uma animação bem dinâmica e interativa [...]" com o link do landonorris.com (Ajuste 7). |
| **Resultado** | Resolveu totalmente: sem cor de destaque e com um plano de animações implementado nos passos 2 a 4. |
| **Aprendizado** | Colocar a restrição de cores e o nível de animação, com a referência, no prompt inicial. Isso teria economizado uma rodada. |

### Rodada 4: avisos no `npm install`
| Campo | Registro |
|---|---|
| **Problema** | Ao rodar `npm install` apareceram um aviso de pacote antigo (`eslint@9.39.5 deprecated`) e "5 high severity vulnerabilities". Fiquei sem saber se havia algo errado. Print: [rodada-04-npm-install.png](img/processo/rodada-04-npm-install.png). |
| **Prompt de correção** | "Eu rodei o npm install e apareceu isso aqui:" (Ajuste 9). |
| **Resultado** | Esclarecido, sem correção necessária: eram avisos de ferramentas de desenvolvimento que não vão para o site publicado. |
| **Aprendizado** | Pedir no prompt que a IA já avise **quais mensagens são esperadas** no terminal e quais indicam erro. |

### Rodada 5: tela sem o botão de tema
| Campo | Registro |
|---|---|
| **Problema** | O primeiro print do site no navegador não mostrava o botão de tema e depois mandei a imagem errada. Prints: [primeira tela](img/processo/rodada-05a-primeira-tela-sem-botao.png), [tema escuro](img/processo/rodada-05b-tema-escuro.png), [tema claro](img/processo/rodada-05c-tema-claro.png). |
| **Prompt de correção** | "Mandei errado a imagem, apareceu essa imagem aqui:" (Ajuste 11), seguido do print do tema claro (Ajuste 12). |
| **Resultado** | Resolveu totalmente: não era defeito. O botão aparece quando a página termina de carregar, e o print inicial foi tirado antes. |
| **Aprendizado** | Esperar o carregamento e **clicar nos botões** antes de reportar um problema (a própria atividade pede QA completo). |

---

## Parte B: problemas encontrados pela IA durante a construção

Sem prompt meu. Registro aqui porque fazem parte do processo e mostram o que a IA errou.

| # | Problema | Como foi corrigido | Resultado | Aprendizado |
|---|---|---|---|---|
| B1 | O botão de tema falhava no lint do projeto (`react-hooks/set-state-in-effect`): o código original atualizava estado dentro de um efeito. | Troca por `useSyncExternalStore`, que também evita diferença entre servidor e navegador. | Resolveu totalmente | Pedir que o código rode o lint antes de entregar |
| B2 | Tipos antigos em cache (`.next/types`) davam erro depois de mover arquivos de pasta. | Limpar o cache e regenerar os tipos. | Resolveu totalmente | Mudar a estrutura de pastas uma vez só, no começo |
| B3 | A intro (contador) poderia piscar de novo a cada recarregamento. | Um script no início da página marca "intro já vista" na sessão e a cortina nem aparece. | Resolveu totalmente | Descrever no prompt o comportamento da intro em visitas repetidas |
| B4 | A IA não consegue baixar as fontes do Google no ambiente dela. | O build foi validado sem as fontes e **eu confirmei no meu computador** que Nunito e Oswald carregam. | Resolveu totalmente (com minha confirmação) | Dizer o que a IA não consegue testar |
| B5 | O arquivo de cache do TypeScript (`tsbuildinfo`) foi parar no .zip. | Removido e o .zip foi refeito. | Resolveu totalmente | Pedir lista do que entra no pacote |
| B6 | Na Jornada, o sublinhado das palavras destacadas pegava também o espaço depois da palavra. | O espaço foi movido para fora do trecho sublinhado. | Resolveu totalmente | Revisar detalhes visuais com captura de tela |
| B7 | O título "Vamos conversar?" passava um pouco da margem direita em tela larga. | Tamanho máximo reduzido. | Resolveu totalmente | Testar títulos grandes em vários tamanhos |

---

## Parte C: QA completo

A atividade pede para "abrir a página, clicar em todos os botões, links e interações, testar em todas as telas". O QA foi feito com **navegador automatizado (Chromium, via Playwright)** em 17/10 e deve ser complementado com o QA manual abaixo.

### C1. O que foi testado automaticamente

| Teste | Resultado |
|---|---|
| Intro na primeira visita aparece, termina sozinha e salva "já vista" | Passou |
| Recarregar na mesma sessão não mostra a intro de novo | Passou |
| Botão "Pular" da intro | Passou |
| Os 7 links do menu e o botão "Ver minha jornada" levam à seção certa | Passou |
| Troca de tema (escuro/claro) nos dois sentidos e o texto do botão muda | Passou |
| Troca PT ↔ EN: URL, idioma da página (`lang`) e títulos mudam | Passou |
| Botão "Baixar currículo" entrega o PDF (200, `application/pdf`) | Passou |
| Todos os 26 links externos abrem em nova aba com `rel="noopener"` | Passou |
| Nenhum link interno aponta para uma seção que não existe | Passou |
| 15 logos de skills presentes com desenho | Passou |
| Card de projeto inclina com o mouse e mostra a etiqueta "Ver código" | Passou |
| Botão magnético se move em direção ao mouse | Passou |
| Teclado: primeiro Tab abre "Pular para o conteúdo", ordem de foco lógica, contorno visível | Passou |
| "Reduzir movimento": sem intro, sem animações, conteúdo todo visível | Passou |
| Sem erros no console do navegador | Passou |
| Estouro horizontal em 320, 375, 414, 768, 1024, 1280, 1440 e 1920 px | **Falhou em 320 px (corrigido, ver C2)**; passou nos outros |

### C2. Problemas achados no QA e corrigidos

| # | Problema | Onde | Correção | Resultado |
|---|---|---|---|---|
| C-1 | Em 320 px a página rolava para o lado: os cards de projeto ficavam mais largos que a tela por causa do título longo ("Reconhecimento facial para pacientes") e das etiquetas de tecnologia. | Projetos | Colunas com largura mínima zero, título com quebra de palavra e tamanho menor no celular. | Resolveu totalmente |
| C-2 | Em 320 px os botões do cabeçalho (idioma e tema) passavam da borda. | Cabeçalho | Espaços menores no celular e o botão de tema vira só um ícone abaixo de 360 px. | Resolveu totalmente (testado de novo) |
| C-3 | Em 320 px os títulos grandes ("CERTIFICAÇÕES", "VAMOS CONVERSAR?") passavam da largura. | Certificações, Contato, Jornada | Tamanho mínimo menor e quebra de palavra como segurança. | Resolveu totalmente |
| C-4 | Os links do menu no desktop tinham só 17 px de altura de clique (pequeno demais). | Cabeçalho | Área de clique aumentada com espaçamento interno. | Resolveu totalmente |
| C-5 | O texto "Microsoft Azure (DP-900)" quebrava no meio do código ("DP-" / "900"). | Skills | O nome ficou "Microsoft Azure" e "DP-900" virou uma linha separada, menor. | Resolveu totalmente |
| C-6 | O símbolo usado como ícone do botão de tema no celular pequeno aparecia como um traço minúsculo (fonte sem esse símbolo). | Cabeçalho | Trocado por um ícone desenhado (SVG). | Resolveu totalmente |

Depois das correções, o teste de estouro horizontal passou em **todos os 8 tamanhos**. Print em 320 px: [qa-320px-hero.png](img/resultado/qa-320px-hero.png). Print do link de acessibilidade: [qa-skip-link.png](img/resultado/qa-skip-link.png).

### C3. Observação (não é defeito)

Depois de trocar de idioma, a versão anterior da página continua na memória do navegador, escondida (comportamento do Next.js para voltar rápido). Os links do menu continuam levando à seção certa e quem usa leitor de tela não percebe, pois o conteúdo escondido é ignorado.

### C4. QA manual (preencher)

O que o navegador automatizado **não** garante é a percepção humana. Abra a página publicada, no computador e no celular de verdade, e marque:

| ☐ | Verificação | Anotações |
|---|---|---|
| ☐ | A intro e o nome animado parecem bons e rápidos? | |
| ☐ | A foto acompanha o mouse sem travar? (a foto real ainda não foi colocada) | |
| ☐ | O texto da Jornada acende na velocidade certa? | |
| ☐ | A linha do tempo é fácil de acompanhar no celular? | |
| ☐ | A etiqueta "Ver código" nos cards atrapalha a leitura? | |
| ☐ | Os logos de Skills estão corretos e nítidos? | |
| ☐ | Os links do LinkedIn da equipe abrem os perfis certos? | |
| ☐ | Os links de GitHub dos projetos abrem os repositórios certos? | |
| ☐ | O PDF do currículo baixa e abre? | |
| ☐ | O inglês (EN) está natural? | |
| ☐ | Tudo está legível nos dois temas? | |
| ☐ | Em Safari/iPhone e em outros navegadores, algo se comporta diferente? | |

Cada problema que aparecer aqui vira uma nova ficha nesta tabela, com o prompt de correção que eu enviar à IA:

| Campo | Registro |
|---|---|
| **Problema** | |
| **Prompt de correção** | |
| **Resultado** | |
| **Aprendizado** | |
