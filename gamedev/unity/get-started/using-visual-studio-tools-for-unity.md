---
title: Usando ferramentas do Visual Studio para Unity | Microsoft Docs
description: Aprenda a usar os recursos de integração e produtividade do Ferramentas do Visual Studio para Unity. Use também o depurador do Visual Studio para o desenvolvimento do Unity.
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 9a89f83ecaa4545eb6151c7a92e76a08708c3855
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341477"
---
# <a name="use-visual-studio-tools-for-unity"></a>Usar as Ferramentas do Visual Studio para Unity

Nesta seção, você aprenderá como usar os recursos de integração e produtividade das Ferramentas do Visual Studio para Unity e como usar o depurador do Visual Studio para desenvolvimento no Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Abrir scripts do Unity no Visual Studio

Depois que o Visual Studio for [definido como o editor externo para o Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio), clicar duas vezes em um script do editor do Unity será iniciado automaticamente ou alternará para o Visual Studio e abrirá o script escolhido.

Como alternativa, você pode abrir o Visual Studio sem nenhum script aberto no editor de origem, selecionando o menu **ativos > Abrir projeto C#** no Unity.

:::zone pivot="windows"
![Abrir projeto C# no Visual Studio](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![Abrir projeto C# no Visual Studio para Mac](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Acesso de documentação do Unity

Você pode acessar a documentação de script do Unity rapidamente pelo Visual Studio. Se as Ferramentas do Visual Studio para Unity não encontrarem a documentação da API localmente, elas tentarão localizá-la online.

:::zone pivot="windows"
- No Visual Studio, realce ou coloque o cursor sobre a API do Unity sobre a qual você deseja aprender e pressione **Ctrl** + **ALT** + **M** , **Ctrl** + **H**
- Você também pode usar a **ajuda > menu referência da API do Unity** em vez da Associação de teclas.
![O menu referência da API do Unity no Visual Studio](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- Em Visual Studio para Mac, realce ou coloque o cursor sobre a API do Unity sobre a qual você deseja aprender e pressione **cmd** + **'**
- Você também pode usar a **ajuda > menu referência da API do Unity** em vez da Associação de teclas.
![O menu referência da API do Unity no Visual Studio para Mac](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>Intellisense para mensagens da API do Unity

O preenchimento de código Intellisense facilita a implementação de mensagens de API do Unity em scripts MonoBehaviour e auxilia no aprendizado da API do Unity. Para usar o IntelliSense para mensagens Unity:

1. Posicione o cursor em uma nova linha dentro do corpo de uma classe derivada de `MonoBehaviour`.

2. Comece a digitar o nome de uma mensagem do Unity, como `OnTriggerEnter`.

3. Após digitar as letras " **ont** ", uma lista de sugestões do IntelliSense será exibida.

:::zone pivot="windows"

![Usando o IntelliSense no Visual Studio](../media/vs/intellisense-example.png)  

:::zone-end

4. A seleção na lista pode ser alterada de três maneiras:

    - Com as teclas de direção **Para cima** e **Para baixo**.

    - Clicando com o mouse no item desejado.

    - Continuando a digitar o nome do item desejado.

5. O IntelliSense pode inserir a mensagem Unity selecionada, incluindo todos os parâmetros necessários:

    - Pressionando **Tab**.

    - Pressionando **Enter**.

    - Clicando duas vezes no item selecionado.

:::zone pivot="windows"

![Inserir mensagem do Unity do IntelliSense no Visual Studio](../media/vs/vstu-intellisense2.png)

:::zone-end

## <a name="unity-monobehavior-scripting-wizard"></a>Assistente de script do Unity MonoBehavior

Você pode usar o assistente do MonoBehavior para exibir uma lista de todos os métodos de API do Unity e implementar rapidamente uma definição vazia. Esse recurso, especialmente com o opção **Gerar comentários de método** habilitada, será útil se você ainda estiver aprendendo o que está disponível na API do Unity.

Para criar definições de método MonoBehavior vazias usando o assistente do MonoBehavior:

1. No Visual Studio, posicione o cursor onde você deseja que os métodos sejam inseridos e pressione **Ctrl** + **Shift** + **M** para iniciar o assistente de monocomportamento. Em Visual Studio para Mac, pressione **cmd** + **Shift** + **M**.

2. Na janela **Criar métodos de script** , marque a caixa de seleção ao lado do nome de cada método que você quer adicionar.

3. Use a lista suspensa **versão do Framework** para selecionar a versão desejada.

4. Por padrão, os métodos são inseridos na posição do cursor. Como alternativa, você pode inseri-los após qualquer método que já esteja implementado em sua classe alterando o valor do **Ponto de inserção** na lista suspensa para o local desejado.

5. Se desejar que o Assistente gere comentários para os métodos que você selecionou, marque a caixa de seleção **Gerar comentários do método**. Esses comentários servem para ajudá-lo a entender quando o método é chamado e quais são suas responsabilidades gerais.

6. Selecione o botão **OK** para sair do assistente e inserir os métodos em seu código.

:::zone pivot="windows"

![A caixa de diálogo do assistente de monocomportamento no Visual Studio.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![A caixa de diálogo do assistente de monocomportamento no Visual Studio para Mac.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Gerenciador de Projetos do Unity
O Gerenciador de Projetos do Unity exibe todos os seus arquivos e diretórios de projeto do Unity da mesma maneira que o Editor do Unity. Isso é diferente de navegar nos scripts do Unity com a solução normal do Gerenciador de Soluções do Visual Studio, que os organiza em projetos e em uma solução gerada pelo Visual Studio.

:::zone pivot="windows"
- No menu principal do Visual Studio, escolha **Exibir > Gerenciador de Projetos do Unity**. Atalho de teclado: **ALT** + **Shift** + **E** 
 ![ exibir a janela Explorador de projetos do Unity.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
- No Visual Studio para Mac, o Painel de Soluções se comporta automaticamente dessa forma quando um projeto do Unity é aberto.
:::zone-end
## <a name="unity-debugging"></a>Depuração do Unity

Ferramentas do Visual Studio para Unity permitem depurar scripts do editor e jogos para seu projeto do Unity usando um depurador poderoso do Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Depuração no editor do Unity

#### <a name="start-debugging"></a>Iniciar a depuração
:::zone pivot="windows"

1. Conecte o Visual Studio com o Unity clicando no botão de **Reprodução** rotulado **Anexar ao Unity** , ou use o atalho de teclado **F5**.
![Clique em Executar no Visual Studio](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. Conecte-se ao Visual Studio para Unity clicando no botão **Executar** ou pressione **Comando + Enter** ou **F5**.
![Clique em reproduzir em Visual Studio para Mac](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Alterne para o Unity e clique no botão **Reproduzir** para executar o jogo no editor.
:::zone pivot="windows"
![Clique em reproduzir no Unity no Windows](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![Clique em reproduzir no Unity no macOS](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. Quando o jogo estiver em execução no editor do Unity e ao mesmo conectado ao Visual Studio, qualquer ponto de interrupção encontrado pausará a execução do jogo e mostrará a linha de código em que o jogo atingiu o ponto de interrupção no Visual Studio.

#### <a name="stop-debugging"></a>Parar a depuração

:::zone pivot="windows"

Clique no botão **Parar** no Visual Studio, ou use o atalho de teclado **Shift+F5**.
![Clique em Parar no Visual Studio](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Clique no botão **Parar** no Visual Studio para Mac ou pressione **Shift + Comando + Enter**.
![Clique em parar no Visual Studio para Mac](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Para saber mais sobre a depuração no Visual Studio, confira [Primeiro acesso ao Depurador do Visual Studio](/debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Anexar ao Unity e Reproduzir

Para maior conveniência, você pode alterar o botão **Anexar ao Unity** para o modo **Anexar ao Unity e Reproduzir**.

:::zone pivot="windows"

1. Clique na **setinha para baixo** ao lado do botão **Anexar ao Unity**.
2. Selecione **Anexar ao Unity e Reproduzir** no menu suspenso.
   ![Anexar e reproduzir no Visual Studio](../media/vs/vstu-attach-and-play.png)

O botão de reprodução muda para **Anexar ao Unity e Reproduzir**. Agora, ao clicar nesse botão ou usar o atalho de teclado **F5** , alterna automaticamente para o editor do Unity e executa o jogo no editor, além de anexar o depurador do Visual Studio.

:::zone-end
:::zone pivot="macos"
É possível iniciar a depuração e reproduzir o editor do Unity em uma única etapa diretamente do Visual Studio para Mac, escolhendo a configuração **Anexar ao Unity e Reproduzir**.

![Selecione anexar ao Unity e reproduzir no Visual Studio para Mac](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> Se você iniciou a depuração usando a **opção anexar ao Unity e executar** a configuração, o botão **parar** também irá parar o editor do Unity.

### <a name="debug-unity-player-builds"></a>Depuração de builds de player do Unity

Você pode Depurar compilações de desenvolvimento de players de Unity com o Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Habilitar a depuração de scripts em um player do Unity

1. No Unity, abra as Configurações de Build selecionando **Arquivo > Configurações de Build**.
2. Na janela Configurações de Build, marque as caixas de seleção **Build de Desenvolvimento** e **Depuração de Script**.

   ![Defina as configurações de Build do Unity para depuração.](../media/vs/vstu-debugging-build-settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Selecione uma instância do Unity à qual anexar o depurador

:::zone pivot="windows"

- No Visual Studio, no menu principal, escolha **Depurar > Anexar Depurador do Unity**.

   ![Anexe o depurador do Unity.](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   A caixa de diálogo **Selecionar Instância do Unity** exibe informações sobre cada instância do Unity a que você pode se conectar.

   ![Escolha uma instância do Unity ao qual se conectar.](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Projeto**

   O nome do projeto para Unity que está sendo executado nesta instância do Unity.

   **Computador** O nome do computador ou dispositivo no qual essa instância do Unity está em execução.

   **Digite** **Editor** se esta instância do Unity for executada como parte do Editor do Unity; **Player** se esta instância do Unity for um player autônomo.

   **Porta** O número da porta do soquete UDP pela qual esta instância do Unity está se comunicando.

> [!IMPORTANT]
> Como Ferramentas do Visual Studio para Unity e a instância do Unity estão se comunicando por meio de um soquete de rede UDP, seu firewall pode precisar de uma regra para permiti-la. Se necessário, você pode ver um prompt, você precisará autorizar a conexão para que o VSTU e o Unity possam se comunicar.

:::zone-end
:::zone pivot="macos"

- No Visual Studio para Mac, no menu superior, escolha **executar > anexar ao processo**. 
- Na caixa de diálogo **anexar ao processo** , selecione opção do **depurador do Unity** no menu suspenso do depurador na parte inferior.
- Selecione uma instância do Unity na lista e clique no botão **anexar** .

:::zone-end

### <a name="debug-a-dll-in-your-unity-project"></a>Depurar uma DLL no projeto do Unity

Muitos desenvolvedores do Unity estão escrevendo componentes de código como DLLs externas para que a funcionalidade que desenvolvem possa ser facilmente compartilhada com outros projetos. Ferramentas do Visual Studio para Unity facilitam a depuração do código nessas DLLs perfeitamente com outro código no seu projeto do Unity.

> [!NOTE]
> Neste momento, as Ferramentas do Visual Studio para Unity dá suporte somente DLLs gerenciadas. Elas não oferecem suporte à depuração de DLLs de código nativo, como aquelas escritas em C++.

Observe que o cenário descrito aqui pressupõe que você tenha o código-fonte, ou seja, se você estiver desenvolvendo ou reutilizando seu próprio código primário ou se você tiver o código-fonte em uma biblioteca de terceiros e pretender implantá-lo em seu projeto do Unity como uma DLL. Esse cenário não descreve como depurar uma DLL para a qual você não tem o código-fonte.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Para depurar um projeto de DLL gerenciado usado em seu projeto do Unity

1. Adicione o projeto de DLL existente para a solução do Visual Studio gerada pelas Ferramentas do Visual Studio para Unity. Com menos frequência, você pode iniciar um novo projeto DLL gerenciado para conter componentes de código no seu projeto do Unity; Se esse for o caso, você poderá adicionar um novo projeto de DLL gerenciado para a solução do Visual Studio em vez disso.

   ![Adicione o projeto DLL existente à solução.](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   Em ambos os casos, as Ferramentas do Visual Studio para Unity mantêm a referência de projeto, mesmo se ele tiver de gerar novamente os arquivos de projeto e solução novamente, então, você precisa executar essas etapas de uma vez.

2. Faça referência ao perfil de framework do Unity correto no projeto de DLL. No Visual Studio, nas propriedades do projeto DLL, defina a propriedade **Estrutura de destino** para a versão do framework do Unity que você está usando. Essa é a Biblioteca de classes base di Unity que corresponde à compatibilidade de API que seu projeto tenha como alvo, como bibliotecas de classes base completas, micro ou da Web. Isso impede que a DLL chame métodos do framework que existem em outros frameworks ou níveis de compatibilidade, mas que podem não existir na versão de framework do Unity que você está usando.

> [!NOTE]
> O seguinte só é necessário se você estiver usando o runtime herdado do Unity. Se você estiver usando o novo runtime do Unity, não precisará mais usar esses perfis dedicados do 3.5. Use um perfil do .NET 4.x compatível com sua versão do Unity.

   ![Defina a estrutura de destino da DLL para o Unity Framework.](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. Copie a DLL para a pasta Ativos do seu projeto do Unity. No Unity, ativos são arquivos que são empacotados e implantados juntos com seu aplicativo do Unity para que eles possam ser carregados no tempo de execução. Como as DLLs são vinculadas em tempo de execução, as DLLs devem ser implantadas como ativos. Para serem implantadas como um ativo, o Editor do Unity exige que as DLLs sejam colocadas dentro da pasta Ativos em seu projeto do Unity. Há duas formas de fazer isso:

   - Modifique as configurações de build do seu projeto de DLL para incluir uma tarefa posterior ao build que copia os arquivos DLL e PDB de saída de sua pasta de saída para a pasta **Ativos** do seu projeto do Unity.

   - Modifique as configurações de build do seu projeto de DLL para definir a pasta de saída como a pasta **Ativos** do seu projeto do Unity. Arquivos DLL e PDB serão colocados na pasta **Ativos**.

   Os arquivos PDB são necessários para a depuração porque eles contêm símbolos de depuração da DLL e mapeiam o código da DLL para sua forma de código-fonte. Se você tem como objetivo o runtime herdado, as Ferramentas do Visual Studio para Unity usarão informações da DLL e PDB para criar um arquivo DLL.MDB, que é o formato de símbolo de depuração usado pelo mecanismo de script do Unity herdado. Se você tem como objetivo o novo runtime e usa o Portable-PDB, o Ferramentas do Visual Studio para Unity não tentará fazer nenhuma conversão de símbolo, pois o novo runtime do Unity é capaz de consumir nativamente PDBs portáteis.

   Veja mais informações sobre a geração de PDB [aqui](/debugger/how-to-set-debug-and-release-configurations.md). Se você tem como objetivo o novo runtime, certifique-se de que "Informações de depuração" está definido como "Portátil", para gerar o PDB portátil corretamente. Se você tem como objetivo o runtime herdado, precisará usar "Full".

4. Depure seu código. Agora você pode depurar seu código-fonte de DLL junto com o código-fonte do seu projeto do Unity e usar todos os recursos de depuração com os quais esteja acostumado, como pontos de interrupção e depuração no código.

## <a name="keyboard-shortcuts"></a>Atalhos do teclado

Você pode acessar rapidamente a funcionalidade Ferramentas do Unity para Visual Studio usando seus atalhos de teclado. Este é um resumo dos atalhos que estão disponíveis.

:::zone pivot="windows"

|Comando|Atalho|Nome de comando de atalho|
|-------------|--------------|---------------------------|
|Abrir o Assistente do MonoBehavior|**Ctrl** + **Shift** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Abrir o Gerenciador de Projetos do Unity|**ALT** + **Shift** + **E**|**View.UnityProjectExplorer**|
|Acessar a documentação do Unity|**Ctrl** + **ALT** + **M, CTRL** + **H**|**Help.UnityAPIReference**|
|Anexar ao depurador do Unity (player ou editor)|**_nenhum padrão_**|**Debug.AttachUnityDebugger**|

Será possível alterar as combinações de teclas de atalho se não desejar o padrão. Para obter informações sobre como alterá-las, confira [Identificar e personalizar atalhos de teclado no Visual Studio](/docs/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

:::zone-end
:::zone pivot="macos"

|Comando|Atalho|Nome de comando de atalho|
|-------------|--------------|---------------------------|
|Abrir o Assistente do MonoBehavior|**Cmd** + **Shift** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Acessar a documentação do Unity|**Cmd + '**|**Help.UnityAPIReference**|

Será possível alterar as combinações de teclas de atalho se não desejar o padrão. Para obter informações sobre como Alterá-lo, consulte [Personalizando o IDE](/mac/customizing-the-ide#key-bingings).

:::zone-end
