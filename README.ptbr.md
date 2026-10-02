# X Ambient

Luz ambiente para X, Instagram, Twitch, Kick, o feed Para Você do TikTok e vídeos do Niconico. No X, o detalhe de uma publicação é iluminado automaticamente; na cronologia e nas respostas, passe o cursor sobre uma publicação. Instagram e TikTok seguem o conteúdo ativo sem passar o cursor. Twitch e Kick seguem o vídeo visível maior, e o Niconico o player principal.

[English](README.md) · [Español](README.es.md) · [日本語](README.ja.md) · Português

## Funcionalidades

- Iluminação no fundo de toda a página ou ao redor da publicação ou do player.
- Iluminação automática da publicação aberta em seu detalhe. As respostas mudam a luz ao passar o cursor; ao sair de uma resposta, volta à publicação aberta. O conteúdo fora da janela é excluído.
- No feed e nos Reels do Instagram, a publicação centralizada é selecionada; os vídeos em reprodução têm prioridade quando estão majoritariamente visíveis. Os carrosséis usam apenas a imagem visível.
- O TikTok segue automaticamente o vídeo ativo do Para Você, mesmo que ele seja exibido por meio de um canvas, e muda ao rolar.
- O Niconico segue o vídeo principal na página de reprodução e preserva os comentários e controles originais.
- Cores projetadas a partir das bordas do conteúdo, sem desfocar as fotos ou os vídeos originais.
- Atualização das cores do vídeo até 12 vezes por segundo, com suporte para pausas e rolagens.
- Compatibilidade com temas claros e escuros e com a preferência de movimento reduzido.
- Intensidade, desfoque e extensão ajustáveis.
- No X, a intensidade vai do tema original a 0% às cores originais e desfocadas das bordas a 100%, sem aumentar a saturação.
- Ajuste opcional da largura dos cards do X, desativado por padrão.
- Idiomas: espanhol, inglês, japonês, coreano, chinês simplificado e tradicional, tailandês, vietnamita, indonésio, francês, alemão, português do Brasil e de Portugal, italiano, russo, árabe e hindi. O idioma é detectado automaticamente pelo Chrome e também pode ser escolhido na extensão.

## Instalar no Chrome

1. Extraia o ZIP desta versão, ou baixe e extraia o código deste repositório.
2. Abra `chrome://extensions` e ative o **Modo do desenvolvedor**.
3. Escolha **Carregar sem compactação** e selecione a pasta que contém o `manifest.json`.
4. Recarregue o site compatível. Abra o detalhe de uma publicação do X ou passe o cursor sobre publicações e respostas, navegue pelo feed ou Reels do Instagram ou pelo Para Você do TikTok, ou abra um vídeo na Twitch, Kick ou Niconico.

Você não precisa do Node.js nem instalar dependências para usar a extensão. Para atualizá-la, substitua os arquivos na mesma pasta, clique em **Recarregar** na extensão e recarregue as páginas abertas.

## Ajustes

Abra o ícone da extensão na barra de ferramentas. As alterações são salvas no seu dispositivo e aplicadas às abas compatíveis.

| Ajuste                         | Valor inicial                 |
| ------------------------------ | ----------------------------- |
| Luz ambiente                   | Ativada                       |
| Área de iluminação             | Fundo de toda a página        |
| Intensidade                    | 65%                           |
| Desfoque                       | 56 px                         |
| Extensão                       | 75%                           |
| Seguir as cores do vídeo       | Ativado                       |
| Ajustar os cards do X à janela | Desativado                    |
| Idioma                         | Automático, conforme o Chrome |

Em **Idioma**, você pode escolher qualquer idioma compatível pelo seu nome nativo. O chinês é detectado pela escrita e pela região do navegador; a seleção manual tem prioridade. O português distingue Brasil e Portugal; se nenhuma região for indicada, usa a tradução do Brasil. O árabe é exibido da direita para a esquerda. Os idiomas do navegador que não estiverem disponíveis usam o inglês. **Restaurar ajustes** restaura a iluminação e mantém sua escolha de idioma.

![Interface em espanhol e inglês](docs/images/localized-popup.jpg)

## Testar e compilar

Para desenvolver, use Node.js 22 ou superior. Não há dependências de npm.

```sh
npm run check
npm test
npm run demo
