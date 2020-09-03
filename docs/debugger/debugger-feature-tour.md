---
title: Introdução ao depurador
description: Introdução à depuração de aplicativos usando o depurador do Visual Studio
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffaeff850c739cd81569a88ae980acf837c413c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184205"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Introdução ao Depurador do Visual Studio

Este tópico apresenta as ferramentas de depurador fornecidas pelo Visual Studio. No contexto do Visual Studio, quando você *depura seu aplicativo*, significa que você está executando o aplicativo com o depurador anexado (ou seja, no modo de depurador). Quando você faz isso, o depurador fornece várias maneiras de mostrar o que o código está fazendo enquanto é executado. Você pode percorrer seu código e examinar os valores armazenados em variáveis, pode definir inspeções em variáveis para ver quando os valores são alterados, você pode examinar o caminho de execução do seu código, et al. Se esta for a primeira vez que você tentou depurar o código, talvez queira ler a [depuração de iniciantes absolutos](../debugger/debugging-absolute-beginners.md) antes de passar por este tópico.

Os recursos descritos aqui são aplicáveis a C#, C++, Visual Basic, JavaScript e a outras linguagens compatíveis com o Visual Studio (exceto quando indicado).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

Para depurar, você precisa iniciar o aplicativo com o depurador anexado ao processo do aplicativo. **F5** (**Depurar > Iniciar Depuração**) é a maneira mais comum de fazer isso. No entanto, talvez você ainda não definiu pontos de interrupção para examinar o código do seu aplicativo, portanto faremos isso primeiro e, em seguida, iniciaremos a depuração. Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não.

Se você tem um arquivo aberto no editor de código, é possível definir um ponto de interrupção clicando na margem à esquerda de uma linha de código.

![Definir um ponto de interrupção](../debugger/media/dbg-tour-set-a-breakpoint.gif "Definir um ponto de interrupção")

Pressione **F5** (**depurar > iniciar depuração**) ou o botão **Iniciar Depuração** ![Iniciar Depuração](../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração") na barra de ferramentas depurar e o depurador será executado para o primeiro ponto de interrupção que encontrar. Se o aplicativo ainda não estiver em execução, F5 iniciará o depurador e o interromperá no primeiro ponto de interrupção.

Os pontos de interrupção são um recurso útil quando você sabe qual linha ou seção de código deseja examinar em detalhes.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Navegar pelo código no depurador usando comandos Step

Nós fornecemos os atalhos de teclado para a maioria dos comandos porque eles tornam a navegação pelo código do aplicativo mais rápida. (Os comandos equivalentes, como comandos de menu, são mostrados entre parênteses).

Para iniciar seu aplicativo com o depurador anexado, pressione **F11** (**Depurar > Intervir**). F11 é o comando **Intervir**, que avança a execução do aplicativo uma instrução por vez. Quando você inicia o aplicativo com F11, o depurador é interrompido na primeira instrução que é executada.

![Depuração de F11 em](../debugger/media/dbg-tour-f11.png "Depuração de F11 em")

A seta amarela representa a instrução na qual o depurador ficou em pausa, que também suspende a execução do aplicativo no mesmo ponto (essa instrução ainda não foi executada).

F11 é uma boa maneira de examinar o fluxo de execução com o máximo de detalhes. (Para mover-se mais rapidamente pelo código, mostraremos algumas outras opções também.) Por padrão, o depurador ignora o código que não é do usuário (se você quiser obter mais detalhes, consulte [apenas meu código](../debugger/just-my-code.md)).

>[!NOTE]
> No código gerenciado, você verá uma caixa de diálogo perguntando se deseja ser notificado quando passar automaticamente por propriedades e operadores (comportamento padrão). Se você quiser alterar a configuração depois, desabilite a configuração **Passar por propriedades e operadores** no menu **Ferramentas > Opções** em **Depuração**.

## <a name="step-over-code-to-skip-functions"></a>Passar pelo código para ignorar funções

Quando você estiver em uma linha de código que é uma chamada de função ou de método, poderá pressionar **F10** (**Depurar > Passar**) em vez de F11.

Pressionar F10 avança o depurador sem intervir em funções ou métodos no código do aplicativo (o código ainda é executado). Ao pressionar F10, será possível ignorar o código no qual você não está interessado. Dessa forma, você poderá chegar rapidamente no código que está mais interessado.

## <a name="step-into-a-property"></a>Intervir em uma propriedade

Como mencionado anteriormente, por padrão, o depurador ignora propriedades gerenciadas e campos, mas o comando **Intervir Específico** permite substituir esse comportamento.

Clique com o botão direito do mouse em uma propriedade ou um campo e escolha **Intervir Específico** e, em seguida, escolha uma das opções disponíveis.

![Entrar em específico](../debugger/media/dbg-tour-step-into-specific.png "Entrar em específico")

Neste exemplo, **Intervir Específico** nos leva ao código de `Path.set`.

![Entrar em específico](../debugger/media/dbg-tour-step-into-specific-2.png "Entrar em específico")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Executar rapidamente até um ponto no código usando o mouse

No depurador, passe o mouse sobre uma linha de código até que o botão **Executar para clicar** (executar a execução aqui) ![Execute para clicar à](../debugger/media/dbg-tour-run-to-click.png "RunToClick") esquerda.

![Executar com um Clique](../debugger/media/dbg-tour-run-to-click-2.png "Executar com um Clique")

> [!NOTE]
> O botão **Executar com um Clique** (Realizar a execução até aqui) está disponível no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] em diante.

Clique no botão **Executar com um Clique** (Realizar a execução até aqui). O depurador avança até a linha de código em que você clicou.

O uso desse botão é semelhante à configuração de um ponto de interrupção temporário. Esse comando também é útil para percorrer rapidamente uma região visível do código do aplicativo. Você pode usar **Executar com um Clique** em qualquer arquivo aberto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avançar o depurador para fora da função atual

Às vezes, talvez você queira continuar a sessão de depuração, avançando o depurador até o fim da função atual.

Pressione **Shift + F11** (ou **Depurar > Sair**).

Este comando retoma a execução do aplicativo (e avança o depurador) até que a função atual retorne.

## <a name="run-to-cursor"></a>Executar até o cursor

Quando você estiver editando código (em vez de pausado no depurador), clique com o botão direito do mouse em uma linha de código em seu aplicativo e escolha **executar até o cursor**. Esse comando inicia a depuração e define um ponto de interrupção temporário na linha de código atual.

![Executar até o cursor](../debugger/media/dbg-tour-run-to-cursor.png "Executar até o cursor")

Se você tiver definido pontos de interrupção, o depurador parará no primeiro ponto de interrupção que encontrar.

Pressione **F5** até alcançar a linha de código em que você selecionou **Executar até o Cursor**.

Esse comando é útil quando você está editando o código e deseja definir rapidamente um ponto de interrupção temporário e iniciar o depurador ao mesmo tempo.

> [!NOTE]
> Você pode usar **Executar até o Cursor** na janela **Pilha de Chamadas** enquanto está depurando.

## <a name="restart-your-app-quickly"></a>Reinicie o aplicativo rapidamente

Clique no botão **reiniciar** ![aplicativo](../debugger/media/dbg-tour-restart.png "Reiniciar o aplicativo") de reinicialização na barra de ferramentas depurar (**Ctrl + Shift + F5**).

Ao pressionar **Reiniciar**, você economiza tempo em comparação com a opção de parar o aplicativo e reiniciar o depurador. O depurador é pausado no primeiro ponto de interrupção que é atingido pela execução do código.

Se você quiser interromper o depurador e voltar para o editor de código, poderá pressionar o botão vermelho parar ![parar depuração](../debugger/media/dbg-tour-stop-debugging.png "Parar Depuração") em vez de **reiniciar**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Editar seu código e continuar a depuração (C#, VB, C++, XAML)

Na maioria dos idiomas com suporte no Visual Studio, você pode editar seu código no meio de uma sessão de depuração e continuar a depuração. Para usar esse recurso, clique em seu código com o cursor enquanto estiver em pausa no depurador, faça edições e pressione **F5**, **F10**ou **F11** para continuar a depuração.

![Editar e continuar a depuração](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obter mais informações sobre como usar o recurso e as limitações de recursos, consulte [Editar e continuar](../debugger/edit-and-continue.md).

Para modificar o código XAML durante uma sessão de depuração, consulte [gravar e depurar o código XAML em execução com o Hot recarregamento de XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

Agora que você sabe um pouco mais sobre a navegação, é uma boa oportunidade começar a inspecionar o estado do aplicativo (variáveis) com o depurador. Os recursos que permitem que você inspecione variáveis são alguns dos mais úteis do depurador e há diferentes maneiras de fazer isso. Muitas vezes, ao tentar depurar um problema, você tenta descobrir se as variáveis estão armazenando os valores que elas deveriam conter em um estado específico do aplicativo.

Com o depurador em pausa, passe o mouse sobre um objeto com o mouse e você verá o valor da propriedade padrão (neste exemplo, o nome do arquivo `market 031.jpg` é o valor da propriedade padrão).

![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "Exibir uma dica de dados")

Expanda o objeto para ver todas as suas propriedades (como a propriedade `FullPath` neste exemplo).

Muitas vezes, durante a depuração, queremos uma maneira rápida de verificar valores de propriedade em objetos e as dicas de dados são uma ótima maneira de fazer isso.

> [!TIP]
> Na maioria das linguagens compatíveis, você pode editar o código durante uma sessão de depuração. Para obter mais informações, confira [Editar e Continuar](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com as janelas Autos e Locais

Durante a depuração, examine a janela **Autos** na parte inferior do editor de códigos.

![Janela de automóveis](../debugger/media/dbg-tour-autos-window.png "Janela Autos")

Na janela **Autos**, veja as variáveis, bem como seus valores atuais e os respectivos tipos. A janela **Autos** mostra todas as variáveis usadas na linha atual ou na linha anterior (No C++, a janela mostra as variáveis nas três linhas de código anteriores. Verifique a documentação para saber o comportamento específico a uma linguagem).

> [!NOTE]
> Em JavaScript, há compatibilidade com a janela **Locais**, mas não com a janela **Autos**.

Em seguida, examine a janela **Locais**. A janela **Locais** mostra as variáveis que estão no escopo no momento.

![Janela Locais](../debugger/media/dbg-tour-locals-window.png "Janela Locais")

Neste exemplo, o objeto `this` e o objeto `f` estão no escopo. Para obter mais informações, confira [Inspecionar variáveis nas janelas Locais e Autos](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Definir uma inspeção

Você pode usar uma janela **Inspeção** para especificar uma variável (ou uma expressão) que deseja acompanhar.

Durante a depuração, clique com o botão direito do mouse em um objeto e escolha **Adicionar Inspeção**.

![Janela de Observação](../debugger/media/dbg-tour-watch-window.png "Janela Inspecionar")

Neste exemplo, há uma inspeção definida no objeto `f` e você pode ver seu valor sendo alterado, conforme percorre o depurador. Ao contrário das outras janelas de variáveis, a janela **Inspeção** sempre mostra as variáveis que você está inspecionando (eles ficam esmaecidas quando estão fora do escopo).

Para obter mais informações, confira [Definir uma Inspeção usando as janelas Inspeção e QuickWatch](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

Clique na janela **Pilha de Chamadas** durante a depuração, a qual fica aberta por padrão no painel inferior direito.

![Examinar a pilha de chamadas](../debugger/media/dbg-tour-call-stack.png "Examinar a pilha de chamadas")

A janela **Pilha de Chamadas** mostra a ordem em que os métodos e as funções são chamados. A linha superior mostra a função atual (o método `Update` neste exemplo). A segunda linha mostra que `Update` foi chamado por meio da propriedade `Path.set` e assim por diante. A pilha de chamadas é uma boa maneira de examinar e entender o fluxo de execução de um aplicativo.

> [!NOTE]
> A janela **Pilha de Chamadas** é semelhante à perspectiva de Depuração em alguns IDEs, como o Eclipse.

Você pode clicar duas vezes em uma linha de código para examinar esse código-fonte. Isso também altera o escopo atual que está sendo inspecionado pelo depurador. Isso não avança o depurador.

Você também pode usar os menus acessados ao clicar com o botão direito do mouse na janela **Pilha de Chamadas** para fazer outras coisas. Por exemplo, você pode inserir pontos de interrupção em funções especificas, reiniciar o aplicativo usando **Executar até o Cursor** e examinar o código-fonte. Confira [Como examinar a Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a> Examinar uma exceção

Quando seu aplicativo gera uma exceção, o depurador leva você até a linha de código que lançou a exceção.

![Auxiliar de exceção](../debugger/media/dbg-tour-exception-helper.png "Auxiliar de exceção")

Neste exemplo, o **Auxiliar de Exceção** mostra uma exceção `System.Argument` e uma mensagem de erro que diz que o caminho não é um formato válido. Portanto, sabemos que o erro ocorreu em um método ou um argumento de função.

Neste exemplo, a chamada `DirectoryInfo` gerou o erro na cadeia de caracteres vazia armazenada na variável `value`.

O Auxiliar de Exceção é um ótimo recurso que pode ajudá-lo a depurar erros. Você também pode fazer coisas como exibir detalhes do erro e adicionar uma inspeção por meio do Auxiliar de Exceção. Ou, se necessário, você pode alterar as condições para lançar a exceção específica. Para obter mais informações de como tratar exceções no código, confira [Técnicas e ferramentas de depuração](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> O Auxiliar de Exceção substituiu o Assistente de Exceção do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Expanda o nó **Configurações de Exceção** para ver mais opções de como lidar com esse tipo de exceção, mas você não precisa alterar nada neste tour!

## <a name="configure-debugging"></a>Configurar a depuração

Você pode configurar seu projeto para compilar como uma [configuração de depuração ou versão](../debugger/how-to-set-debug-and-release-configurations.md), configurar as propriedades do projeto para depuração ou definir [as configurações gerais](../debugger/how-to-specify-debugger-settings.md) para depuração. Além disso, você pode configurar o depurador para exibir informações personalizadas usando recursos como o atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) ou, para C/C++, a [estrutura NatVis](create-custom-views-of-native-objects.md).

As propriedades de depuração são específicas para cada tipo de projeto. Por exemplo, você pode especificar um argumento para passar ao aplicativo ao iniciá-lo. Você pode acessar as propriedades específicas do projeto clicando com o botão direito do mouse no projeto em Gerenciador de Soluções e selecionando **Propriedades**. As propriedades de depuração normalmente aparecem na guia **Compilar** ou **depurar** , dependendo do tipo de projeto específico.

![Propriedades do projeto](../debugger/media/dbg-tour-project-properties.png "Propriedades do projeto")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Depurar aplicativos ASP.NET dinâmicos no Serviço de Aplicativo do Azure

o **depurador de instantâneos** tira um instantâneo dos aplicativos em produção quando o código que você está interessado em executar. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

![Iniciar o Depurador de Instantâneos](../debugger/media/snapshot-launch.png "Iniciar o Depurador de Instantâneos")

A coleção de instantâneos está disponível para aplicativos do ASP.NET em execução no Serviço de Aplicativo do Azure. Aplicativos ASP.NET devem estar em execução no .NET Framework 4.6.1 ou posterior e os aplicativos ASP.NET Core devem ser executados no .NET Core 2.0 ou posterior no Windows.

Para obter mais informações, confira [Depurar aplicativos ASP.NET dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Exibir instantâneos com o retrocesso do IntelliTrace (Visual Studio Enterprise)

O **retrocesso do IntelliTrace** tira automaticamente um instantâneo do seu aplicativo em cada evento de etapa do depurador e do ponto de interrupção. Os instantâneos registrados permitem retornar aos pontos de interrupção ou às etapas anteriores e exibir o estado do aplicativo como ele era no passado. O retrocesso do IntelliTrace poderá poupar seu tempo quando você desejar ver o estado do aplicativo anterior, mas não desejar reiniciar a depuração nem recriar o estado do aplicativo desejado.

É possível navegar e exibir instantâneos usando os botões **Voltar** e **Avançar** na barra de ferramentas Depurar. Esses botões navegam pelos eventos exibidos na guia **Eventos** na janela **Ferramentas de Diagnóstico**.

![Botões voltar e avançar da etapa](../debugger/media/intellitrace-step-back-icons-description.png  "Botões voltar e avançar da etapa")

Para obter mais informações, confira a página [Inspecionar estados anteriores do aplicativo usando o IntelliTrace](../debugger/view-historical-application-state.md).

## <a name="debug-performance-issues"></a>Problemas de desempenho de depuração

Se seu aplicativo for executado muito lentamente ou usar muita memória, talvez seja necessário testar seu aplicativo com as ferramentas de criação de perfil no início. Para obter mais informações sobre ferramentas de criação de perfil, como a ferramenta de uso da CPU e o analisador de memória, consulte [primeira análise das ferramentas de criação de perfil](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você obteve uma visão rápida de muitos recursos do depurador. Talvez você deseje fazer uma análise mais detalhada de uma dessas funcionalidades, como pontos de interrupção.

> [!div class="nextstepaction"]
> [Aprender a usar pontos de interrupção](../debugger/using-breakpoints.md)
