---
title: Dicas e truques no depurador
description: Conheça alguns dos recursos menos conhecidos suportados pelo depurador visual studio
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302213"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Aprenda dicas e truques de produtividade para o depurador no Visual Studio

Leia este tópico para aprender algumas dicas e truques de produtividade para o depurador visual Studio. Para dar uma olhada nos recursos básicos do depurador, consulte [Primeiro olhar para o depurador](../debugger/debugger-feature-tour.md). Neste tópico, abrangemos algumas áreas que não estão incluídas no longa-metragem.

## <a name="pin-data-tips"></a>Dicas de dados de pinos

Se você passar o tempo sobre as dicas de dados durante a depuração, você pode querer fixar a dica de dados para a variável para dar a si mesmo acesso rápido. A variável permanece fixada mesmo após a reinicialização. Para fixar a ponta de dados, clique no ícone do pino enquanto paira sobre ele. Você pode fixar várias variáveis.

![Fixar uma dica de dados](../debugger/media/dbg-tips-data-tips-pinned.png "FixaçãoDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edite seu código e continue depurando (C#, VB, C++)

Na maioria dos idiomas suportados pelo Visual Studio, você pode editar seu código no meio de uma sessão de depuração e continuar depurando. Para usar este recurso, clique em seu código com o cursor enquanto pausado no depurador, faça edições e pressione **F5**, **F10**ou **F11** para continuar a depuração.

![Editar e continuar a depuração](../debugger/media/dbg-tips-edit-and-continue.gif "Editare continuar")

Para obter mais informações sobre o uso do recurso e sobre as limitações de recursos, consulte [Editar e Continuar](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Editar código XAML e continuar depurando

Para modificar o código XAML durante uma sessão de depuração, consulte [Gravar e depurar o código XAML com XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Depurar problemas difíceis de reproduzir

Se for difícil ou demorado recriar um determinado estado em seu aplicativo, considere se o uso de um ponto de ruptura condicional pode ajudar. Você pode usar [pontos de interrupção condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) e filtrar pontos de interrupção para evitar invadir o código do aplicativo até que o aplicativo entre em um estado desejado (como um estado em que uma variável está armazenando dados ruins). Você pode definir condições usando expressões, filtros, contagem de hits, e assim por diante.

#### <a name="to-create-a-conditional-breakpoint"></a>Para criar um ponto de ruptura condicional

1. Clique com o botão direito do mouse em um ícone de ponto de partida (a bola vermelha) e escolha **Condições**.

2. Na janela **Configurações de ponto de** intervalo, digite uma expressão.

    ![Ponto de Ruptura Condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Ponto de ruptura condicional")

3. Se você estiver interessado em outro tipo de condição, selecione **Filtro** em vez de **expressão condicional** na caixa de diálogo **Configurações de ponto** de ruptura e siga as dicas do filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configure os dados a serem exibidos no depurador

Para C#, Visual Basic e C++ (somente código C++/CLI), você pode dizer ao depurador quais informações mostrar usando o atributo [DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) Para o código C++, você pode fazer o mesmo usando [visualizações Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

Com o depurador pausado em uma linha de código, use o mouse para pegar o ponteiro da seta amarela à esquerda. Mova o ponteiro da seta amarela para um ponto diferente no caminho de execução do código. Em seguida, você usa F5 ou um comando de passo para continuar executando o aplicativo.

![Mova o ponteiro de execução](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Mova o ponteiro de execução")

Alterando o fluxo de execução, você pode fazer coisas como testar caminhos de execução de código diferentes ou executar novamente o código sem reiniciar o depurador.

> [!WARNING]
> Geralmente, você precisa ter cuidado com esse recurso. Um aviso é exibido na dica de ferramenta. Outros avisos também podem ser exibidos. Mover o ponteiro não pode reverter seu aplicativo para um estado de aplicativo anterior.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Rastreie um objeto fora do escopo (C#, Visual Basic)

É fácil visualizar variáveis usando janelas de depurador como a janela **do relógio.** No entanto, quando uma variável sai do escopo na janela do **relógio,** você pode notar que ela está acinzentada. Em alguns cenários de aplicativos, o valor de uma variável pode mudar mesmo quando a variável está fora de escopo, e você pode querer vê-la de perto (por exemplo, uma variável pode receber lixo coletado). Você pode rastrear a variável criando um ID de objeto para ela na janela **do relógio.**

#### <a name="to-create-an-object-id"></a>Para criar um ID de objeto

1. Defina um ponto de ruptura perto de uma variável que você deseja rastrear.

2. Inicie o depurador **(F5)** e pare no ponto de partida.

3. Encontre a variável na janela **Locals** **(Depurar > Windows > Locals),** clique com o botão direito do mouse na variável e selecione **Fazer ID de objeto**.

    ![Criar um ID de objeto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Você deve **$** ver um número mais um na janela **local.** Esta variável é o ID do objeto.

5. Clique com o botão direito do mouse na variável ID do objeto e escolha **Adicionar relógio**.

Para obter mais informações, consulte [Criar um ID de objeto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Exibir valores de retorno para funções

Para visualizar valores de retorno para suas funções, olhe para as funções que aparecem na janela **Autos** enquanto você está pisando em seu código. Para ver o valor de retorno de uma função, certifique-se de que a função em que você está interessado já foi executada (pressione **F10** uma vez se você estiver parado na chamada de função). Se a janela estiver fechada, use **Debug > Windows > Autos** para abrir a janela **Autos.**

![Janela de automóveis](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Além disso, você pode inserir funções na janela **Imediato** para visualizar valores de retorno. (Abra-o usando **o Debug > o Windows > Imediato**.)

![Janela imediata](../debugger/media/dbg-tips-immediate-window.png "Janela imediata")

Você também pode usar [pseudovariáveis](../debugger/pseudovariables.md) na janela **Relógio** e **Imediato,** tais como `$ReturnValue`.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Inspecione as cordas em um visualizador

Ao trabalhar com strings, pode ser útil visualizar toda a seqüência formatada. Para visualizar uma seqüência de texto simples, XML, HTML ou JSON, clique no ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ícone do visualizador") enquanto paira sobre uma variável que contém um valor de seqüência.

![Abra um visualizador de cordas](../debugger/media/dbg-tips-string-visualizers.png "Visualizador OpenString")

Um visualizador de cordas pode ajudá-lo a descobrir se uma string está mal formada, dependendo do tipo de string. Por exemplo, um campo **valor** em branco indica que a seqüência não é reconhecida pelo tipo de visualizador. Para obter mais informações, consulte [Caixa de diálogo visualizador de cordas](../debugger/string-visualizer-dialog-box.md).

![Visualizador de cordas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizador JSONString")

Para alguns outros tipos, como dataset e datatable objetos que aparecem nas janelas de depurador, você também pode abrir um visualizador embutido.

## <a name="break-into-code-on-handled-exceptions"></a>Desfazer código em exceções manuseadas

O depurador infringe seu código em exceções não manuseadas. No entanto, exceções manuseadas (como exceções que ocorrem dentro de um `try/catch` bloco) também podem ser uma fonte de bugs e você pode querer investigar quando eles ocorrem. Você pode configurar o depurador para invadir código para exceções manuseadas, configurando opções na caixa de diálogo **Configurações de exceção.** Abra esta caixa de diálogo escolhendo **Depurar > Configurações de exceção do Windows >**.

A caixa de diálogo **Configurações de exceção** permite que você diga ao depurador para invadir código em exceções específicas. Na ilustração abaixo, o depurador infringe seu código sempre que ocorre. `System.NullReferenceException` Para obter mais informações, consulte [Gerenciar exceções](../debugger/managing-exceptions-with-the-debugger.md).

![Caixa de diálogo configurações de exceção](../debugger/media/dbg-tips-exception-settings.png "ExceçõesConfigurandocaixadediálogo")

## <a name="debug-deadlocks-and-race-conditions"></a>Impasses de depuração e condições de corrida

Se você precisa depurar os tipos de problemas que são comuns a aplicativos multithreaded, muitas vezes ajuda a visualizar a localização dos threads durante a depuração. Você pode fazer isso facilmente usando o botão **Mostrar linhas na origem.**

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar tópicos em seu código-fonte

1. Durante a depuração, clique no botão **Mostrar tópicos na** fonte ![Mostrar tópicos na fonte](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") na barra de ferramentas **Debug.**

2. Examine a medianiz no lado esquerdo da janela. Nesta linha, você vê um ícone *de marcador de rosca* ![Thread Marker](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se assemelha a dois fios de pano. O marcador de thread indica que um thread está parado nesse local.

    Observe que um marcador de rosca pode ser parcialmente escondido por um ponto de ruptura.

3. Passe o ponteiro sobre o marcador de thread. Um DataTip aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado.

    Você também pode visualizar a localização dos segmentos na [janela Pilhas Paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examine cargas para serviços web e recursos de rede (UWP)

Em aplicativos UWP, você pode analisar `Windows.Web.Http` as operações de rede realizadas usando a API. Você pode usar esta ferramenta para ajudar a depurar serviços web e recursos de rede. Para usar a ferramenta, selecione **Depurar > Profiler de desempenho**. Selecione **Rede**e escolha **Iniciar**. No aplicativo, percorra o cenário que usa `Windows.Web.Http` e escolha **Parar coleta** para gerar o relatório.

![Ferramenta de criação de perfil de uso de rede](../profiling/media/prof-tour-network-usage.png "RedeUsoProfTool")

Selecione uma operação na exibição de resumo para exibir mais detalhes.

![Informações detalhadas na ferramenta Deuso de Rede](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obter mais informações, consulte [Uso de rede](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Familiarize-se mais com a forma como o depurador se conecta ao seu aplicativo (C#, C++, Visual Basic, F#)

Para anexar ao seu aplicativo em execução, o depurador carrega arquivos símbolo (.pdb) gerados para a mesma compilação do aplicativo que você está tentando depurar. Em alguns cenários, um pouco de conhecimento de arquivos símbolopode ser útil. Você pode examinar como o Visual Studio carrega arquivos de símbolos usando a janela **Módulos.**

Abra a janela **Módulos** durante a depuração selecionando **Depuração > Módulos de > do Windows**. A janela **Módulos** pode dizer quais módulos o depurador está tratando como código do usuário, ou [*Meu Código,*](../debugger/just-my-code.md)e o status de carregamento de símbolos para o módulo. Na maioria dos cenários, o depurador encontra automaticamente arquivos símbolo para código de usuário, mas se você quiser entrar (ou depurar) código .NET, código do sistema ou código de biblioteca de terceiros, passos extras são necessários para obter os arquivos de símbolo corretos.

![Exibir informações de símbolo satiscários na janela Módulos](../debugger/media/dbg-tips-modules-window.png "Exibirinformações de símbolo")

Você pode carregar informações de símbolos diretamente da janela **Módulos** clicando com o botão direito e escolhendo **Símbolos de carga**.

Às vezes, os desenvolvedores de aplicativos enviam aplicativos sem os arquivos símbolo correspondentes (para reduzir a pegada), mas mantêm uma cópia dos arquivos símbolo correspondentes para a compilação para que eles possam depurar uma versão lançada mais tarde.

Para descobrir como o depurador classifica o código como código do usuário, consulte [Just My Code](../debugger/just-my-code.md). Para saber mais sobre arquivos de símbolos, consulte [Especificar símbolo (.pdb) e arquivos de origem no depurador visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Saiba mais

Para obter dicas adicionais e truques e informações mais detalhadas, consulte estes posts no blog:

- [7 hacks menos conhecidos para depuração no Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 joias escondidas no Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Confira também

[Atalhos de teclado](../ide/productivity-shortcuts.md)
