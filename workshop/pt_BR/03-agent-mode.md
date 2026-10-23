<!-- l10n-sync: source-file="workshop/03-agent-mode.md" -->
# Parte 3: Crie o jogo com fluxos de trabalho agênticos

---

Nesta parte, o Copilot passa de planejador a implementador. Em vez de escrever código linha por linha, você descreve o que precisa e deixa o Copilot executar o trabalho nos arquivos que precisarem ser alterados.

## Tarefa 1: Conecte a batalha

<!-- track:vscode:start -->
1. Mude para o modo **Agent** no Copilot Chat.
2. Insira este prompt:
<!-- track:vscode:end -->

<!-- track:cli:start -->
1. Volte o Copilot CLI ao fluxo de codificação padrão (ou continue no autopilot se quiser que ele siga trabalhando até você pará-lo).
2. Se for útil, mencione o arquivo da página para dar mais contexto: `@src/pages/index.astro`
3. Insira este prompt:
<!-- track:cli:end -->

   > Adicione JavaScript do lado do cliente à página de batalha para que:
   > 1. Ao clicar no botão Battle, obtenha dos campos de entrada os dois nomes de usuário.
   > 2. Valide se ambos foram preenchidos e mostre um erro caso contrário.
   > 3. Busque em paralelo, pela nossa API, os dados de contribuições dos dois usuários.
   > 4. Renderize os gráficos de contribuições como grades coloridas, com um quadrado colorido por dia e usando a paleta de cores do GitHub.
   > 5. Mostre um selo VS entre os dois usuários.
   > 6. Exiba o nome de usuário, o total de contribuições e o intervalo de datas de cada usuário.
   > 7. Trate os estados de carregamento e os erros.
   > 8. Dispare a batalha também ao pressionar Enter nos campos de entrada.
   > 9. Por enquanto, use a interface simples que já está estruturada.
   >
   > Use interfaces do TypeScript para a estrutura dos dados de contribuições.

<!-- track:vscode:start -->
3. Deixe o Agent Mode implementar as alterações em `index.astro`.
4. Revise as alterações propostas na visualização de diff antes de aceitá-las.
<!-- track:vscode:end -->

<!-- track:cli:start -->
4. Deixe o Copilot CLI implementar as alterações em `src/pages/index.astro`.
5. Use `/diff` para inspecionar as alterações geradas e depois aprove-as.
<!-- track:cli:end -->

## Tarefa 2: Teste a batalha

> **⚠️ Não está vendo as alterações?** Se a página de batalha não tiver sido atualizada, pare o servidor de desenvolvimento (`Ctrl+C`), reinicie com `npm run dev` e atualize o navegador.

1. Digite `octocat` e `torvalds` como nomes de usuário e clique em **Battle**.
2. Você deve ver os gráficos de contribuições dos dois usuários lado a lado, em grades coloridas.
3. Teste os casos de erro:
   - Deixe um ou os dois campos vazios e clique em Battle: deve aparecer um erro de validação.
   - Digite um nome de usuário inválido: o aplicativo deve exibir um erro da API.
4. Pressione **Enter** em qualquer campo: isso deve iniciar a batalha como se você tivesse clicado no botão.

## Tarefa 3: Itere com o Copilot

Se algo não estiver exatamente certo, envie comentários de acompanhamento ao Copilot. Por exemplo:

- *“Os quadrados de contribuições estão grandes demais; altere-os para 12x12 px.”*
- *“Adicione uma dica ao passar o cursor que mostre a data e a contagem de contribuições.”*
- *“O estado de carregamento precisa de uma animação pulsante.”*

<!-- track:vscode:start -->
O Agent Mode lida naturalmente com alterações em vários arquivos e com iterações. Cada prompt de acompanhamento se baseia na conversa anterior, então você pode aprimorar a implementação gradualmente sem recomeçar.
<!-- track:vscode:end -->

<!-- track:cli:start -->
As sessões do Copilot CLI mantêm o histórico, então cada prompt de acompanhamento se baseia nos anteriores. Use `/session` ou `/context` para inspecionar o contexto que o Copilot está mantendo e `/review` após uma iteração maior para procurar erros ou oportunidades de melhoria.
<!-- track:cli:end -->

## Dicas para esta parte

- **Seja específico sobre o que você precisa** — requisitos claros levam a resultados melhores.
- **Divida tarefas grandes em prompts menores** se o Copilot sair do rumo.
- **Revise as alterações antes de aceitá-las** — inspecionar o código gerado costuma ser mais rápido do que reescrevê-lo depois.
- **Teste o aplicativo após cada etapa de implementação** para localizar os problemas enquanto ainda estão restritos.

## ✅ Parte 3 concluída

Você aprendeu a:

- Usar o Copilot para **implementar alterações em vários arquivos**
- **Iterar nos resultados** com comentários de acompanhamento direcionados
- Conduzir o **ciclo completo de uma funcionalidade**: implementação, revisão, testes e refinamento
