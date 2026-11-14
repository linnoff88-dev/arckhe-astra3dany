# astra3dany â€” um mundo 3D pra ensinar qualquer coisa

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

[![astra3dany](guia/assets/banner.jpg)](https://inematds.github.io/astra3dany/guia/)

**Ao vivo:** https://inematds.github.io/astra3dany/app/ Â· **Guia de uso:** https://inematds.github.io/astra3dany/guia/

Um "mundo de aprendizagem" em miniatura, no browser: trÃªs estaÃ§Ãµes, um mascote-guia, um World Tour ritmado e exploraÃ§Ã£o livre.
Cada estaÃ§Ã£o mostra **uma ideia acontecendo** (antes â†’ depois) com um card que explica o que vocÃª vÃª, o que estÃ¡ acontecendo e o que lembrar.

O primeiro mundo ensina **"IA no dia a dia: trÃªs hÃ¡bitos que evitam problemas"**, em portuguÃªs, pra adultos que comeÃ§am a usar IA no trabalho:

| # | EstaÃ§Ã£o | HÃ¡bito | O que acontece |
|---|---|---|---|
| 01 | O portÃ£o | Confirme antes de agir | Um pedido Ã© barrado e vai pra revisÃ£o; o segundo passa na checagem, o portÃ£o abre e a aÃ§Ã£o roda |
| 02 | As gavetas | DÃª contexto onde a IA lÃª | O card de instruÃ§Ãµes entra na gaveta do projeto e os dois colegas ficam conectados |
| 03 | A conferÃªncia | Confira a fonte | O formato passa; a conferÃªncia corrige o total de 100 pra 90 e deixa a data em aberto |

Segue a receita do field guide **Build a Learning World** (Mark Kashef, comunidade Early AI Adopters): seis partes, ritmo de cÃ¢mera *chegar â†’ aproximar â†’ demonstrar â†’ segurar*, cards sincronizados e checklist de aceite. O material de estudo estÃ¡ em [`docs/`](docs/00-INDICE.md); a sÃ­ntese em [`docs/05-sintese.md`](docs/05-sintese.md); o plano em [`PLANO.md`](PLANO.md); as evidÃªncias de inspeÃ§Ã£o em [`evidence/revisao.md`](evidence/revisao.md).

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/astra3dany/guia/**

## InstalaÃ§Ã£o

PrÃ©-requisitos:

- **Node.js 20 ou mais novo** (desenvolvido e testado com Node 24.13) e **npm**.
- Um browser com **WebGL2** (Chrome, Edge, Firefox, Safari 15+). NÃ£o precisa de GPU dedicada, mas ajuda.
- Nada de backend, chave de API, banco ou Blender: o site Ã© 100% estÃ¡tico.

```bash
git clone https://github.com/inematds/astra3dany.git
cd astra3dany/game
npm ci                 # instala exatamente as versÃµes do package-lock (Vite 8.2.2, Babylon.js 9.25.0)
npm run dev            # servidor de desenvolvimento em http://127.0.0.1:43220
```

Outros comandos, sempre dentro de `game/`:

| Comando | O que faz |
|---|---|
| `npm test` | 7 testes do timeline e das legendas do tour (`node --test`, sem browser) |
| `npm run build` | gera o site estÃ¡tico em **`../app/`** (caminhos relativos, serve de qualquer pasta) |
| `npm run preview` | serve o build de `../app/` em http://127.0.0.1:43221 pra inspecionar o que vai pro ar |

Sem internet o `npm run dev` funciona normalmente depois do `npm ci`; nenhum asset vem de CDN.

## Uso

**Abrir:** https://inematds.github.io/astra3dany/app/ (ou o `npm run dev`). Acrescente `?diagnostics` Ã  URL pra ver fps, p95 e resoluÃ§Ã£o de render no canto do palco.

**World Tour** (botÃ£o laranja): ~60 segundos guiados. Por estaÃ§Ã£o: chegada (3 s) â†’ aproximaÃ§Ã£o (3 s) â†’ demonstraÃ§Ã£o (6 s) â†’ resultado parado (5 s); no fim, o recap com os trÃªs hÃ¡bitos.
- *Pausar / Retomar* congela cÃ¢mera e demonstraÃ§Ã£o (tambÃ©m pela barra de espaÃ§o ou pelo link "Pausar pra ler" no card).
- *Reiniciar* volta ao inÃ­cio; *0,75Ã— / 1Ã—* muda a velocidade; *Sair* ou `Esc` volta pra visÃ£o geral.
- No desktop o card fica Ã  direita e a cena Ã© renderizada ao lado dele; no celular o card fica embaixo. O card nunca cobre a demonstraÃ§Ã£o.

**Explorar no seu ritmo:** clique num pedestal (ou nos botÃµes 01/02/03).
- *Ver de perto e rodar* aproxima a cÃ¢mera e roda a demonstraÃ§Ã£o; *Repetir a demonstraÃ§Ã£o* roda de novo; *Vista ampla* recua; *PrÃ³xima estaÃ§Ã£o* avanÃ§a; a terceira leva ao recap.
- A frase do card muda junto com o que estÃ¡ acontecendo na cena; na estaÃ§Ã£o 3 os valores (total e data) aparecem tambÃ©m em texto.

**CÃ¢mera livre** (fora do tour):

| AÃ§Ã£o | Mouse | Teclado | Touch |
|---|---|---|---|
| Orbitar | arrastar | setas | um dedo |
| Aproximar / afastar | roda, botÃµes + e âˆ’ | `+` / `-` | pinÃ§a |
| Deslocar (pan) | shift + arrastar, botÃ£o direito ou do meio | â€” | dois dedos |
| Voltar ao enquadramento | botÃ£o *Reset* | `R` | botÃ£o *Reset* |

**Reduzir movimento:** respeita `prefers-reduced-motion` do sistema e pode ser alternado no topo. Com ele ligado a cÃ¢mera pula direto pra cada pose em vez de animar; as demonstraÃ§Ãµes continuam.

**Fontes e crÃ©ditos:** link no rodapÃ© da barra lateral.

## Trocar o assunto (ensinar outra coisa)

1. Edite **`game/src/mundo.config.js`**: tÃ­tulo, intro, pÃºblico, mascote e as trÃªs estaÃ§Ãµes (nome, princÃ­pio, explicaÃ§Ã£o, sequÃªncia, observaÃ§Ãµes por tempo da demo, takeaway, poses de cÃ¢mera). Todo o texto do site vem daÃ­.
2. Se a mecÃ¢nica de uma estaÃ§Ã£o for diferente, crie um mÃ³dulo em `game/src/estacoes/` com a interface `{ reset(), update(demoTime), foco, pick }` e registre em `DEMOS` no `main.js`. Os trÃªs mÃ³dulos existentes servem de molde: sÃ£o metÃ¡foras fÃ­sicas que jÃ¡ se mostraram legÃ­veis em close-up.
3. Rode `npm test` (os testes leem o config: duraÃ§Ã£o, holds de 5 s, frases por fase) e inspecione no browser: vista ampla, close-up, demo, resultado, desktop e celular.

Regra do guia: *mude o assunto, mantenha a receita*. Uma estaÃ§Ã£o = um princÃ­pio = uma metÃ¡fora fÃ­sica = uma mudanÃ§a visÃ­vel.

## Limites conhecidos

- **Mascote procedural.** Blender nÃ£o estava disponÃ­vel na mÃ¡quina de build (aarch64), entÃ£o o mascote Any Ã© gerado em cÃ³digo (`game/src/mascote.js`). Pra usar um asset Blender, exporte um GLB pra `game/public/assets/`, aponte `mascote.glb` no config e nomeie as pernas `Perna1..4` (ou `Leg1..4`) pra ganhar o andar.
- **Tamanho.** O bundle principal tem ~5,8 MB (1,2 MB gzip) por causa do Babylon.js; a primeira carga em 4G leva alguns segundos. NÃ£o hÃ¡ code-splitting ainda.
- **Desempenho.** SÃ³ foi medido em Chromium headless com WebGL por software (25â€“35 fps), o que nÃ£o representa um dispositivo real. Em GPU comum espera-se 60 fps; em celulares antigos, reduza `hardwareScalingLevel` no `main.js` ou desligue as sombras no `palco.js`.
- **NÃ£o testado** em aparelho fÃ­sico, Safari ou Firefox, nem com gestos de toque reais (a pinÃ§a foi exercitada sÃ³ por cÃ³digo).
- **Sem Ã¡udio, sem quiz, sem IA ao vivo.** As demonstraÃ§Ãµes sÃ£o animaÃ§Ãµes determinÃ­sticas; voz/mÃºsica ficam pra uma prÃ³xima versÃ£o.
- **Uma lÃ­ngua.** Textos em portuguÃªs no config; nÃ£o hÃ¡ i18n.
- **Acessibilidade parcial.** BotÃµes e painÃ©is sÃ£o navegÃ¡veis por teclado e o card do tour Ã© `aria-live`, mas a cena 3D em si nÃ£o tem descriÃ§Ã£o alternativa alÃ©m dos cards.

## Publicar

`npm run build` gera `app/` (estÃ¡tico, caminhos relativos). O repositÃ³rio serve pelo **GitHub Pages a partir da raiz da branch `main`**, entÃ£o basta commitar `app/` e o `guia/` e fazer push:

- App: `https://inematds.github.io/astra3dany/app/`
- Guia: `https://inematds.github.io/astra3dany/guia/`

Serve igualmente em Vercel, Netlify ou Here.Now apontando pra pasta `app/`. Publique sempre o build que foi inspecionado no `npm run preview`.

## Estrutura

```
app/                          build estÃ¡tico publicado (gerado por npm run build)
guia/index.html               pÃ¡gina landing + guia de uso (GitHub Pages)
game/index.html               layout, painÃ©is e controles
game/src/main.js              engine, cena, mÃ¡quina de estados, tour, UI
game/src/mundo.config.js      DADOS do mundo (assunto, estaÃ§Ãµes, textos, cÃ¢mera)
game/src/tour.js              timeline e cues do World Tour (sem Babylon, testado)
game/src/palco.js             chÃ£o, pedestais, luzes, sombras, placas de texto
game/src/mascote.js           mascote procedural / loader GLB
game/src/camera-controls.js   orbit, pan, zoom, teclado, touch
game/src/estacoes/*.js        as trÃªs mecÃ¢nicas
game/tests/tour.test.mjs      7 testes de timing e narraÃ§Ã£o
evidence/                     screenshots e revisÃ£o da inspeÃ§Ã£o
docs/                         post, guia, prompt, transcriÃ§Ã£o, sÃ­ntese
```

## CrÃ©ditos

Receita, ritmo e checklist: [Build a Learning World](https://build-a-learning-world.markkashef.chatgpt.site/) e o repo [promptadvisers/early-ai-dopters](https://github.com/promptadvisers/early-ai-dopters), de Mark Kashef. Este projeto reimplementa a receita com assunto, textos, mascote e cÃ³digo prÃ³prios. LicenÃ§a MIT.

---

Projeto adaptado da comunidade INEMA TDS - Marca Arckhe