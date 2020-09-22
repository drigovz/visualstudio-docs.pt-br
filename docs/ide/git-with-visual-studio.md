---
title: Nova experiência de git no Visual Studio (visualização)
titleSuffix: ''
description: Saiba mais sobre a nova experiência de git integrada no Visual Studio 2019
ms.date: 09/22/2020
ms.topic: conceptual
ms.author: tglee
author: prnadago
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: e8bc35a6434ab619e7232b5351ba95aae68db2cd
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005120"
---
# <a name="new-git-experience-in-visual-studio-preview"></a>Nova experiência de git no Visual Studio (visualização)

A partir da [versão 16,6](/visualstudio/releases/2019/release-notes-v16.6), o Visual Studio 2019 agora inclui uma nova experiência de git que torna mais fácil usar o Git do IDE. O Git é o sistema de controle de versão moderno mais amplamente usado, portanto, não importa se você é um desenvolvedor profissional ou se está aprendendo a codificar, o Git pode ser muito útil para você.

> [!TIP]
> Se você for novo no git, o https://git-scm.com/ site será um bom lugar para começar. Lá, você encontrará um livro online popular, vídeos de informações básicas do git e folhas de consulta.

## <a name="how-to-start-using-git-in-visual-studio"></a>Como começar a usar o Git no Visual Studio

Para alternar a nova experiência de git, vá para **ferramentas**  >  **Opções**  >  visualização de**ambiente**  >  **recursos** e, em seguida, marque a caixa de seleção **nova experiência do usuário git** .

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Captura de tela da seção recursos de visualização da caixa de diálogo opções no Visual Studio ":::

Há três maneiras de usar o Git no Visual Studio 2019:

- [Abra um repositório git existente](#open-an-existing-local-repository). Se o seu código já estiver em seu computador, você poderá abri-lo usando **arquivo**  >  **aberto**  >  **projeto/solução** (ou **pasta**) e o Visual Studio detectará automaticamente se ele tem um repositório git inicializado.
- [Crie um novo repositório git](#create-a-new-git-repository). Se o seu código não estiver associado ao git, você poderá criar um novo repositório git.
- [Clonar um repositório git existente](#clone-an-existing-git-repository). Se o código no qual você deseja trabalhar não estiver em seu computador, você poderá clonar quaisquer repositórios remotos existentes.

## <a name="create-a-new-git-repository"></a>Criar um novo repositório git

Se o seu código não estiver associado ao git, você poderá começar criando um novo repositório git. Para fazer isso, selecione **git**  >  **criar repositório git** na barra de menus. Em seguida, na caixa de diálogo **criar um repositório git** , insira suas informações.

:::image type="content" source="media/git-create-repository.png" alt-text="Captura de tela da caixa de diálogo criar um repositório git no Visual Studio ":::

A caixa de diálogo **criar um repositório git** facilita o envio por push do novo repositório para o github. Por padrão, o novo repositório é privado, o que significa que você é o único que pode acessá-lo. Se você desmarcar a caixa, seu repositório será público, o que significa que qualquer pessoa no GitHub poderá exibi-lo.

> [!TIP]
> Independentemente de seu repositório ser público ou privado, é melhor ter um backup remoto do código armazenado com segurança no GitHub, mesmo que você não esteja trabalhando com uma equipe. Isso também torna seu código disponível para você, independentemente do computador que você está usando.

Você pode optar por criar um repositório git somente local usando a opção **somente local** . Ou então, você pode vincular seu repositório com qualquer repositório remoto vazio existente em qualquer outro provedor de git usando a opção **remota existente** .

## <a name="clone-an-existing-git-repository"></a>Clonar um repositório git existente

O Visual Studio inclui uma experiência de clonagem simples. Se você souber a URL do repositório que deseja clonar, poderá colar a URL na seção **local do repositório** e, em seguida, escolher o local do disco no qual deseja que o Visual Studio seja clonado.

:::image type="content" source="media/git-clone-repository.png" alt-text="Captura de tela da caixa de diálogo clonar um repositório git no Visual Studio ":::

Se você não souber a URL do repositório, o Visual Studio facilitará a navegação e a clonagem do seu repositório existente do GitHub ou DevOps do Azure.

### <a name="open-an-existing-local-repository"></a>Abrir um repositório local existente

Depois de clonar um repositório ou criar um, o Visual Studio detecta o repositório git e o adiciona à lista de **repositórios locais** no menu git. A partir daqui, você pode acessar e alternar rapidamente entre seus repositórios git.

:::image type="content" source="media/git-local-repositories.png" alt-text="Captura de tela da opção de repositórios locais no menu git no Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Exibir arquivos no Gerenciador de Soluções

Quando você clona um repositório ou abre um repositório local, o Visual Studio o alterna para o contexto do git salvando e fechando todas as soluções e projetos abertos anteriormente. Gerenciador de Soluções carrega a pasta na raiz do repositório git e examina a árvore de diretórios em busca de qualquer arquivo de exibição. Isso inclui arquivos como CMakeLists.txt ou aqueles com a extensão de arquivo. sln.

O Visual Studio ajusta sua exibição com base no arquivo de exibição que você carrega no Gerenciador de Soluções:

- Se você clonar um repositório que contém um único arquivo. sln, Gerenciador de Soluções carregar diretamente essa solução para você.
- Se Gerenciador de Soluções não detectar nenhum arquivo. sln em seu repositório, por padrão ele carregará a exibição de pasta.
- Se o repositório tiver mais de um arquivo. sln, Gerenciador de Soluções mostrará a lista de modos de exibição disponíveis para sua escolha.

Você pode alternar entre a exibição aberta no momento e a lista de exibições usando o botão **alternar exibições** na barra de ferramentas Gerenciador de soluções.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Captura de tela de Gerenciador de Soluções com o botão alternar modos de exibição selecionado no Visual Studio ":::

## <a name="git-changes-window"></a>Janela de alterações git

O Git rastreia alterações de arquivo em seu repositório à medida que você trabalha e separa os arquivos em seu repositório em três categorias. Essas alterações são equivalentes ao que você veria ao inserir o `git status` comando na linha de comando:

- **Arquivos não modificados**: esses arquivos não foram alterados desde a última confirmação.
- **Arquivos modificados**: esses arquivos têm alterações desde a última confirmação, mas você ainda não os preparou para a próxima confirmação.
- **Arquivos preparados**: esses arquivos têm alterações que serão adicionadas à próxima confirmação.

Conforme você faz seu trabalho, o Visual Studio controla as alterações de arquivo em seu projeto na seção de **alterações** da janela de **alterações do git** .

:::image type="content" source="media/git-changes-window.png" alt-text="Captura de tela da janela de alterações do git no Visual Studio ":::

Quando estiver pronto para preparar as alterações, clique no **+** botão (mais) em cada arquivo que deseja preparar ou clique com o botão direito do mouse em um arquivo e selecione **estágio**. Você também pode preparar todos os arquivos modificados com um clique usando o botão preparar todos **+** (mais) na parte superior da seção de **alterações** .

Quando você testa uma alteração, o Visual Studio cria uma seção de **alterações em etapas** . Somente as alterações na seção de **alterações em etapas** são adicionadas à próxima confirmação, que você pode fazer selecionando **confirmar preparação**. As alterações também podem ser despreparadas clicando no botão **–** (menos). O comando equivalente para essa ação é `git commit -m "Your commit message"` .

Você também pode optar por não preparar os arquivos modificados ignorando a área de preparo. Nesse caso, o Visual Studio permite que você confirme suas alterações diretamente sem precisar prepará-las. Basta inserir sua mensagem de confirmação e, em seguida, selecionar **confirmar tudo**. O comando equivalente para essa ação é `git commit -a` .

O Visual Studio também facilita a confirmação e a sincronização com um clique usando os atalhos **confirmar tudo e enviar** e **confirmar todos e sincronizar** . Quando você clica duas vezes em qualquer arquivo nas seções **alterações** e **alterações em etapas** , você pode ver uma comparação linha por linha com a versão não modificada do arquivo.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Captura de tela da comparação linha por linha de versões de arquivo no Visual Studio ":::

### <a name="select-an-existing-branch"></a>Selecionar uma ramificação existente

O Visual Studio exibe o Branch atual no seletor na parte superior da janela de **alterações do git** .

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Captura de tela dos branches atuais que você pode exibir usando o seletor na parte superior do seletor de alterações git no Visual Studio ":::

O Branch atual também está disponível na barra de status no canto inferior direito do IDE do Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Captura de tela dos branches atuais que você pode exibir usando a barra de status no canto inferior direito no IDE do Visual Studio ":::

Em ambos os locais, você pode alternar entre branches existentes.

### <a name="create-a-new-branch"></a>Criar uma nova ramificação

Você também pode criar uma nova ramificação. O comando equivalente para essa ação é `git checkout <branchname>` .

A criação de uma nova ramificação é tão simples quanto inserir o nome da ramificação e baseá-la em uma ramificação existente.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Captura de tela da caixa de diálogo criar uma nova ramificação no Visual Studio ":::

Você pode escolher uma ramificação local ou remota existente como base. A caixa de seleção **Branch de check-out** alterna automaticamente para o Branch recém-criado. O comando equivalente para essa ação é `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Janela do repositório git

O Visual Studio tem uma nova janela de **repositório git** , que é uma exibição consolidada de todos os detalhes em seu repositório, incluindo todas as ramificações, remotos e históricos de confirmação. Você pode acessar essa janela diretamente do **git** ou da **exibição** na barra de menus ou na barra de status.

### <a name="manage-branches"></a>Gerenciar branches

Ao selecionar **gerenciar branches** no menu **git** , você verá a exibição de árvore branches na janela **repositório git** . No painel esquerdo, você pode usar o menu de contexto de clique com o botão direito do mouse para fazer checkout de branches, criar novos branches, mesclar, trocar base, Cherry-escolha e muito mais. Ao clicar na ramificação, você poderá ver uma visualização do histórico de confirmação no painel direito.

### <a name="incoming-and-outgoing-commits"></a>Confirmações de entrada e de saída

Quando você busca um Branch, a janela de **alterações do git** tem um indicador sob a lista suspensa Branch, que exibe o número de confirmações não recebidas do Branch remoto. Esse indicador também mostra o número de confirmações locais sem envio por push.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Captura de tela da janela de alterações do git que mostra o elemento da interface do usuário suspensa do indicador no Visual Studio ":::

O indicador também funciona como um link para levá-lo ao histórico de confirmação dessa ramificação na janela do **repositório git** . A parte superior do histórico agora exibe os detalhes dessas confirmações de entrada e de saída. A partir daqui, você também pode optar por efetuar pull ou enviar por push as confirmações.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Captura de tela da janela do repositório git que mostra o histórico de confirmação de uma ramificação no Visual Studio ":::

#### <a name="commit-details"></a>Detalhes da confirmação

Quando você clica duas vezes em uma **confirmação**, o Visual Studio abre seus detalhes em uma janela de ferramentas separada. A partir daqui, você pode reverter a confirmação, redefinir a confirmação, corrigir a mensagem de confirmação ou criar uma marca na confirmação. Quando você clica em um arquivo alterado na confirmação, o Visual Studio abre a exibição de **comparação** lado a lado da confirmação e seu pai.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Captura de tela da caixa de diálogo detalhes da confirmação no Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Lidar com conflitos de mesclagem

Os conflitos podem ocorrer durante uma mesclagem se dois desenvolvedores modificarem as mesmas linhas em um arquivo e o Git não souber automaticamente qual está correto. O Git interrompe a mesclagem e informa que você está em um estado conflitante.

O Visual Studio torna mais fácil identificar e resolver um conflito de mesclagem. Primeiro, a janela do **repositório git** mostra uma barra de informações Gold na parte superior da janela.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Captura de tela da mensagem "mesclagem concluída com conflitos" no Visual Studio ":::

A janela de **alterações do git** também exibe uma mensagem*de "mesclagem em andamento com conflitos*", com os arquivos não mesclados na seção separada abaixo dele.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Captura de tela da mensagem "Mesclar em andamento com conflitos" no Visual Studio ":::

Mas se você não tiver nenhuma dessas janelas abertas e, em vez disso, acessar o arquivo que tem conflitos de mesclagem, não precisará pesquisar o seguinte texto:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Em vez disso, o Visual Studio exibe uma barra de informações Gold na parte superior da página que indica que o arquivo aberto tem conflitos. Em seguida, você pode clicar no link para abrir o **Editor de mesclagem**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Captura de tela da mensagem ' arquivo contém conflitos de mesclagem ' no Visual Studio ":::

### <a name="the-merge-editor"></a>O editor de mesclagem

O editor de mesclagem no Visual Studio é uma ferramenta de mesclagem de três vias que exibe as alterações de entrada, as alterações atuais e o resultado da mesclagem. Você pode usar a barra de ferramentas no nível superior do **Editor de mesclagem** para navegar entre conflitos e diferenças mescladas automaticamente no arquivo.

:::image type="content" source="media/git-merge-editor.png" alt-text="Captura de tela do editor de mesclagem no Visual Studio ":::

Você também pode usar as alternâncias para mostrar/ocultar diferenças, mostrar/ocultar diferenças de palavras e personalizar o layout. Há caixas de seleção na parte superior de cada lado que você pode usar para fazer todas as alterações de um lado ou de outra. Mas, para fazer alterações individuais, você pode clicar nas caixas de seleção à esquerda das linhas conflitantes em cada lado. Por fim, quando você concluir a resolução dos conflitos, poderá selecionar o botão **aceitar mesclagem** no editor de mesclagem. Em seguida, você escreve uma mensagem de confirmação e confirma as alterações para concluir a resolução.

## <a name="personalize-your-git-settings"></a>Personalizar as configurações do git

Para personalizar e personalizar as configurações do git em um nível de repositório, bem como em um nível global, vá **Git**para  >  **configurações** de git na barra de menus ou para **ferramentas**  >  **Opções**  >  **controle de origem** na barra de menus. Em seguida, escolha as opções desejadas.

:::image type="content" source="media/git-options-settings.png" alt-text="Captura de tela da caixa de diálogo opções, onde você pode escolher as configurações de personalização e personalização no IDE do Visual Studio ":::

## <a name="whats-next"></a>O que vem a seguir

Fique atento; atualizaremos esta página à medida que continuarmos a refinar a nova experiência de git no Visual Studio 2019.

> [!IMPORTANT]
> Se você tiver uma sugestão para nós, informe-nos! Agradecemos a oportunidade de se envolver com você em decisões de design por meio do portal [**da comunidade de desenvolvedores**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Confira também

- [O novo vídeo de experiência git](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) no Channel 9 e no [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Novas atualizações incríveis para a experiência de git na](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) postagem de blog do Visual Studio
- [Experiência de git aprimorada na postagem no blog do Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Notas de versão do Visual Studio 2019](/visualstudio/releases/2019/release-notes)
