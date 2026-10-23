<!-- l10n-sync: source-file="workshop/04-design-vibes.md" -->
# Parte 4: Tematização orientada ao design

---

Nesta parte, você vai usar os ciclos de planejamento e implementação do Copilot para projetar uma transformação completa do tema. Essa é uma abordagem de desenvolvimento orientada ao design: comece com uma visão, itere nos elementos visuais e deixe o Copilot cuidar do trabalho pesado de CSS.

## Tarefa 1: Planeje o tema retrô

<!-- track:vscode:start -->
Mude para o modo **Plan** no GitHub Copilot Chat.
<!-- track:vscode:end -->

<!-- track:cli:start -->
Use `/plan` no GitHub Copilot CLI ou pressione **Shift+Tab** até o modo Plan ser ativado.
<!-- track:cli:end -->

Insira este prompt:

> Quero transformar esta página em uma experiência completa de fliperama retrô. Planeje uma reformulação visual abrangente que inclua: efeitos de linhas de varredura CRT no fundo, brilho neon pulsante no título, selo VS animado com mudanças de cor no gradiente, uma sobreposição de brilho nos cartões de resultados dos usuários, animações de entrada flutuante para os campos, texto de carregamento que muda entre verde e roxo e efeitos de brilho ao passar o cursor sobre os quadrados de contribuições. Mantenha o fundo escuro (`#0a0a1a`) e as cores de destaque verde (`#5fed83`) e roxo (`#8a2be2`). Use o tema escuro e a fonte retrô Press Start 2P do Google Fonts.

O Copilot vai gerar um plano detalhado de implementação cobrindo todos os efeitos visuais. **Não aceite imediatamente** — revise o plano e itere:

- Sugira ajustes na duração das animações (por exemplo, *“Deixe o pulso neon mais lento, em torno de 3 segundos.”*)
- Pergunte sobre efeitos específicos (por exemplo, *“Como vai funcionar a sobreposição de brilho nos cartões?”*)
- Peça mudanças na abordagem se algo não parecer adequado

## Tarefa 2: Implemente o tema

Quando estiver satisfeito com o plano, peça ao Copilot para implementá-lo:

> Implemente o plano do tema de fliperama retrô que acabamos de criar.

O Copilot vai adicionar várias animações CSS, pseudo-elementos e transições à folha de estilos. Isso pode incluir:

- `@keyframes` para linhas de varredura, pulsos neon, brilho e efeitos de entrada flutuante
- Pseudo-elementos (`::before`, `::after`) para efeitos de sobreposição
- Propriedades personalizadas de CSS para as cores do tema
- Transições e estados de hover para elementos interativos

<!-- track:cli:start -->
Depois que as alterações forem aplicadas, use `/diff` para revisar os estilos antes de aprová-los.
<!-- track:cli:end -->

## Tarefa 3: Ajuste o visual

> **⚠️ Não está vendo as alterações?** Se o novo tema ou as animações não aparecerem, pare o servidor de desenvolvimento (`Ctrl+C`), reinicie com `npm run dev` e atualize o navegador forçando a recarga (`Ctrl+Shift+R`).

Mantenha a prévia do navegador aberta e itere no design. Experimente prompts como:

> O efeito de linhas de varredura está forte demais; reduza a opacidade para 0.03.

> Adicione uma cintilação elétrica sutil ao texto do título.

> O selo VS deve pulsar de forma mais intensa.

Essa é uma abordagem de **desenvolvimento orientada ao design**: você itera no resultado visual em tempo real. Cada prompt aprimora a experiência até que ela fique do jeito certo. Não se contente com “bom o suficiente” — continue ajustando o visual até a página parecer pertencer a um fliperama.

## Tarefa 4: Atualize as instruções

As instruções devem refletir as principais decisões de design para que os próximos prompts mantenham a consistência.

<!-- track:vscode:start -->
Peça ao Copilot Chat:

> Adicione ao `copilot-instructions.md` uma seção de guia de design que descreva nosso tema de fliperama retrô: cores, fontes e estilo das animações.
<!-- track:vscode:end -->

<!-- track:cli:start -->
Peça ao Copilot CLI:

> Atualize as instruções do repositório com um guia breve de design para o tema de fliperama retrô: cores, fontes, estilo das animações e a regra de que novas interfaces devem manter a estética neon.
<!-- track:cli:end -->

Quando a página estiver com a aparência desejada, faça commit das instruções e das alterações de design.

## ✅ Parte 4 concluída

**O que você aprendeu:**

- Usar fluxos de planejamento para criar um **sistema visual antes de implementá-lo**
- **Iterar no resultado visual** com comentários de acompanhamento rápidos
- **Atualizar as instruções após decisões importantes** para que o Copilot mantenha a identidade visual
