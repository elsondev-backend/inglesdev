# English for Devs

Site de apresentação do curso **Inglês para profissionais de TI**, do nível A1 ao B1, com 12 episódios em vídeo e 4 módulos avançados. Funciona no celular e no computador e tem contato pelo WhatsApp.

O site é um único arquivo, `index.html`, sem dependências nem etapa de build. Basta abrir no navegador ou subir em qualquer hospedagem de site estático.

## O que tem no site

| Seção | Âncora | Conteúdo |
|---|---|---|
| Início | `#inicio` | Chamada principal, níveis cobertos (A1, A2, B1) e um trecho de diálogo do episódio 2 |
| Para quem é | `#para-quem` | Devs e QAs, SREs e suporte, quem quer vaga no exterior |
| Como funciona | `#como-funciona` | As 6 partes de cada episódio: cena e diálogo, vocabulário, gramática, leitura e interpretação, fala e escrita |
| Módulos | `#modulos` | Módulos 1 (A1), 2 (A2) e 3 (B1) com os 12 episódios, mais os 4 módulos avançados |
| Rotina sugerida | `#rotina` | Um episódio por semana, de segunda a sexta |
| Dúvidas | `#duvidas` | Perguntas frequentes |
| Contato | `#contato` | Número do WhatsApp, mensagens prontas e formulário que monta a mensagem |

Além disso, há um botão do WhatsApp fixo no canto inferior direito da tela, visível em todas as seções.

## Configurar o número do WhatsApp

O número aparece em **um único lugar**, no `<script>` perto do fim do `index.html`:

```js
// Troque pelo número real: código do país + DDD + número, só dígitos. Ex.: 5511987654321
var WHATSAPP_NUMBER = "5500000000000";
```

Escreva só dígitos: `55` (Brasil), o DDD e o número, sem `+`, espaços, parênteses ou traços. Por exemplo, `(71) 98765-4321` vira `5571987654321`.

Ao trocar esse valor, o site atualiza sozinho:

- o número mostrado na seção de contato (formatado como `+55 (71) 98765-4321`);
- o botão "Copiar número";
- todos os links `https://wa.me/...` (botão flutuante, botões do topo, mensagens prontas e formulário).

## Mudar as mensagens prontas

Cada botão do WhatsApp tem a classe `js-wa` e um atributo `data-msg` com o texto que vai pré-preenchido na conversa:

```html
<a class="js-wa" data-msg="Olá! Quanto custa o curso English for Devs?" ...>Quanto custa?</a>
```

Para mudar a mensagem, edite o `data-msg`. Para criar um botão novo, copie um desses links e troque o texto. O script gera o link `wa.me` de todos os elementos com `js-wa` ao carregar a página.

A mensagem do formulário é montada na função `buildMsg()` do script, com nome, área, nível e texto livre.

## Mudar cores e fontes

As cores ficam em variáveis CSS no início do `<style>`:

- `:root` tem as cores do tema claro;
- os blocos `prefers-color-scheme: dark` e `[data-theme="dark"]` têm as do tema escuro (mantenha os dois iguais).

As principais são `--accent` (azul dos destaques), `--amber` (rótulos das seções) e `--wa` (verde do WhatsApp). As fontes vêm do Google Fonts: Bricolage Grotesque (títulos), IBM Plex Sans (texto) e IBM Plex Mono (rótulos e código).

## Publicar

Qualquer hospedagem de site estático serve, porque é só um arquivo HTML.

- **GitHub Pages:** crie um repositório, envie o `index.html` para a raiz e ative em *Settings → Pages*, escolhendo a branch `main`.
- **Netlify:** em [app.netlify.com/drop](https://app.netlify.com/drop), arraste a pasta com o `index.html`.
- **Render:** crie um *Static Site* apontando para o repositório, sem comando de build e com *Publish directory* `.`.
- **Hospedagem própria:** envie o `index.html` para a pasta pública do servidor (por exemplo, `public_html`).

Para testar no computador antes de publicar, abra o `index.html` direto no navegador. Para testar no celular, use as ferramentas de desenvolvedor do navegador (modo dispositivo) ou publique e abra o link no telefone.

## Checklist antes de divulgar

- [ ] Trocar `WHATSAPP_NUMBER` pelo número real.
- [ ] Clicar no botão flutuante e conferir se o WhatsApp abre com a mensagem.
- [ ] Revisar a seção "Dúvidas", principalmente a resposta sobre valores.
- [ ] Abrir o site no celular e no computador.

## Material do curso

O conteúdo do site resume dois documentos:

- *Inglês para profissionais de TI: curso em vídeo (A1 → B1)*: roteiros dos 12 episódios.
- *Inglês para TI: módulos avançados*: Daily Scrum, documentações técnicas, negociação de escopo e entrevistas internacionais.

Se um episódio ou módulo mudar nesses documentos, atualize a seção `#modulos` do `index.html`.
