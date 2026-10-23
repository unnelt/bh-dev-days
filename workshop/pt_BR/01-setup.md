<!-- l10n-sync: source-file="workshop/01-setup.md" -->
# Parte 1: Configuração e engenharia de contexto

---

Nesta parte, você vai configurar seu ambiente de desenvolvimento **e** ensinar ao Copilot como é a base de código, para que cada prompt futuro comece com o contexto adequado.

## Seção 1: Configuração inicial

### Passo 1: Crie seu repositório

1. Abra [github.com/copilot-dev-days/mona-mayhem](https://github.com/copilot-dev-days/mona-mayhem)
2. Crie seu próprio repositório de uma destas formas:
   - clique em **Use this template** → **Create a new repository**, ou
   - faça um fork do repositório.
3. Dê a ele o nome `my-mona-mayhem` e defina a visibilidade como **Public** (se você o criou a partir do template).

<!-- track:vscode:start -->
### Passo 2: Escolha seu ambiente de desenvolvimento

#### Opção A: VS Code local

1. Abra o VS Code e execute **Git: Clone** → **Clone from GitHub**
2. Selecione seu repositório `my-mona-mayhem`
3. Quando solicitado, instale as **extensões recomendadas**

#### Opção B: GitHub Codespaces

1. Abra seu repositório no GitHub
2. Clique em **Code** → **Codespaces** → **Create codespace on main**
3. Aguarde o ambiente iniciar e as dependências serem instaladas

### Passo 3: Instale as dependências e inicie o aplicativo

1. Abra o terminal integrado no seu repositório.
2. Instale as dependências:

   ```bash
   npm install
   ```

3. Inicie o aplicativo:

   ```bash
   npm run dev
   ```

> ✅ **O aplicativo está em execução no seu navegador!**
<!-- track:vscode:end -->

<!-- track:cli:start -->
### Passo 2: Instale o GitHub Copilot CLI

Use o método de instalação adequado para sua máquina:

- **npm (multiplataforma, requer Node.js 22+)**

  ```bash
  npm install -g @github/copilot
  ```

- **Homebrew (macOS/Linux)**

  ```bash
  brew install copilot-cli
  ```

- **WinGet (Windows)**

  ```bash
  winget install GitHub.Copilot
  ```

### Passo 3: Inicie o aplicativo e autentique o CLI

1. Clone seu repositório localmente e abra um terminal na raiz do projeto.
2. Instale as dependências e inicie o aplicativo:

   ```bash
   npm install
   npm run dev
   ```

3. Abra um **segundo terminal** no mesmo repositório e inicie o Copilot CLI:

   ```bash
   copilot
   ```

4. Na sessão interativa, digite:

   ```
   /login
   ```

5. Siga as instruções do fluxo de autenticação do dispositivo e, quando o CLI solicitar aprovação, confirme que você confia no repositório.

> ✅ **Agora você tem a prévia do aplicativo em um terminal e o Copilot CLI pronto em outro.**
<!-- track:cli:end -->

## Seção 2: Engenharia de contexto

A engenharia de contexto é a forma de ensinar à IA como é sua base de código. Quanto melhor o contexto, melhores serão as respostas futuras.

<!-- track:vscode:start -->
### Tarefa 1: Gere instruções do workspace com /init

Vamos usar o comando integrado `/init` para gerar um arquivo de instruções do workspace para o Copilot:

1. Abra o **Copilot Chat** e digite:

   ```
   /init simple instructions with a project overview, build/dev commands, and Astro best practices, (ignore the workshop).
   ```

2. Revise o arquivo gerado: o Copilot analisará o projeto e criará `.github/copilot-instructions.md`.
3. Aceite as alterações e faça **commit** do arquivo de instruções.

> **Resultado:** Todas as suas solicitações futuras ao Copilot incluirão um mapa do seu workspace.

### Tarefa 2: Agentes em segundo plano

**Agente local em segundo plano:**

1. No painel de Chat, clique em **+** para abrir um novo chat.
2. Na parte inferior da janela, altere **Local** para **Copilot CLI**.
3. Digite o prompt:

   > “Adicione regras de linting para variáveis não utilizadas, melhore o estilo do código e corrija os erros encontrados.”

4. Quando terminar, **revise e aplique** as alterações; depois, arquive a sessão se quiser.

**Agente na nuvem:**

1. No painel de Chat, clique em **+** para abrir um novo chat.
2. Na parte inferior da janela, altere **Local** para **Cloud**.

   > “Deixe o README mais atraente como página inicial.”

> **Resultado:** Regras de linting são adicionadas, erros são corrigidos e o README melhora, sem sair do editor.

### Tarefa 3: Explore o projeto

Abra o **Copilot Chat** no **modo Ask** e experimente estes prompts:

- `"Explain the architecture of this project"`
- `"What files are in the src directory and what do they do?"`
- `"What would I need to build to make the Battle button work?"`

> 💡 Use **@workspace** para fornecer ao Copilot o contexto de todo o projeto e obter respostas mais precisas.
<!-- track:vscode:end -->

<!-- track:cli:start -->
### Tarefa 1: Gere instruções do repositório com /init

Vamos usar `/init` para gerar um arquivo de instruções do workspace para o Copilot:

1. No Copilot CLI, digite:

   ```
   /init simple instructions with a project overview, build/dev commands, and Astro best practices, (ignore the workshop).
   ```

2. Revise o arquivo gerado: o Copilot analisará seu projeto e criará `.github/copilot-instructions.md`.
3. Faça commit do arquivo de instruções.

> **Resultado:** As sessões futuras do CLI herdarão automaticamente as instruções específicas do repositório a partir de `.github/copilot-instructions.md`.

### Tarefa 2: Ajuste seu ambiente do CLI

Pratique os controles do CLI que vão facilitar as próximas etapas:

1. Execute `/help` para consultar os comandos slash disponíveis.
2. Use `/model` para consultar os modelos disponíveis.
3. Se o Copilot tiver aprendido aprovações demais durante a experimentação, redefina-as com:

   ```
   /reset-allowed-tools
   ```

4. Se seu repositório estiver dentro de um diretório pai maior, use `/add-dir PATH` para ampliar explicitamente o workspace permitido.

> 💡 A documentação do CLI recomenda instruções personalizadas concisas e permissões explícitas para as ferramentas, para que o Copilot seja rápido e previsível.

### Tarefa 3: Explore o projeto pelo terminal

Experimente estes prompts no Copilot CLI:

- `Give me an overview of this project.`
- `@src/pages/api/contributions/[username].ts What is this file for and what needs to be built here?`
- `@src/pages/index.astro What exists here and what would I need to add to build the battle page?`

Se quiser uma resposta rápida em uma única execução fora da sessão interativa, experimente:

```bash
copilot -p "Summarize the architecture of this repo in 5 bullet points"
```

> **Resultado:** Agora você tem instruções, conhece os comandos e sabe como fornecer arquivos como contexto para o Copilot CLI.
<!-- track:cli:end -->

## ✅ Parte 1 concluída

Você aprendeu a:

- **Configurar** o repositório e o ambiente de desenvolvimento local
- **Gerar instruções** com `/init` para que o Copilot entenda o projeto e sua direção de design
- **Criar o hábito de revisar** as alterações geradas antes de aplicá-las
- **Explorar a base de código** com prompts que incluem contexto
