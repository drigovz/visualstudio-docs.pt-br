---
title: Depurar em tempo de design | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bc5d08e8b0ae71acb846e1e863e24e8b8def0ee
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183555"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Depurar em tempo de design no Visual Studio (C#, C++/CLI, Visual Basic, F #)

Para depurar o código em tempo de design em vez de enquanto um aplicativo está em execução, você pode usar a janela **imediata** .

Para depurar o código XAML por trás de um aplicativo do designer XAML, como cenários de ligação de dados declarativos, você pode usar **Debug**  >  **a anexação de depuração para processar**.

## <a name="use-the-immediate-window"></a>Usar a janela imediata

Você pode usar a janela **imediata** do Visual Studio para executar uma função ou sub-rotina sem executar seu aplicativo. Se a função ou a sub-rotina contiver um ponto de interrupção, o Visual Studio será interrompido no ponto de interrupção. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Esse recurso é chamado *de depuração em tempo de design*.

O exemplo a seguir está em Visual Basic. Você também pode usar a janela **imediata** em tempo de design em aplicativos C#, F # e C++/CLI.

1. Cole o código a seguir em um aplicativo de console Visual Basic em branco:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Defina um ponto de interrupção na **função de extremidade**de linha.

1. Abra a janela **imediata** selecionando **depurar**  >  **janelas**  >  **imediatamente**. Digite `?MyFunction` na janela e pressione **Enter**.

   O ponto de interrupção é atingido e o valor de **MyFunction** na janela **locais** é **1**. Você pode examinar a pilha de chamadas e outras janelas de depuração enquanto o aplicativo estiver no modo de interrupção.

1. Selecione **continuar** na barra de ferramentas do Visual Studio. O aplicativo termina e **1** é retornado na janela **imediata** . Verifique se você ainda está no modo de design.

1. Digite `?MyFunction` a janela **imediata** novamente e pressione **Enter**. O ponto de interrupção é atingido e o valor de **MyFunction** na janela **locais** é **2**.

1. Sem selecionar **continuar**, digite `?MySub()` na janela **imediato** e pressione **Enter**. O ponto de interrupção é atingido e o valor de **MyFunction** na janela **locais** é **3**. Você pode examinar o estado do aplicativo enquanto o aplicativo está no modo de interrupção.

1. Selecione **Continuar**. O ponto de interrupção é atingido novamente e o valor de **MyFunction** na janela **locais** agora é **2**. A janela **Immediate** retorna **expressão foi avaliada e não tem valor**.

1. Selecione **continuar** novamente. O aplicativo termina e **2** é retornado na janela **imediata** . Verifique se você ainda está no modo de design.

1. Para limpar o conteúdo da janela **imediata** , clique com o botão direito do mouse na janela e selecione **limpar tudo**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Depurar um controle XAML personalizado em tempo de design anexando ao designer XAML

1. Abra sua solução ou projeto no Visual Studio.

1. Crie a solução/projeto.

1. Abra a página XAML que contém o controle personalizado que você deseja depurar.

   Para projetos UWP direcionados para o Windows Build 16299 ou superior, essa etapa iniciará o processo *UwpSurface. exe* . Para projetos do WPF direcionados para o Windows Build 16299 ou superior, essa etapa iniciará o processo *WpfSurface. exe* . Para versões do WPF ou UWP anteriores ao Windows Build 16299, essa etapa iniciará o processo *XDesProc. exe* . 

1. Abra uma segunda instância do Visual Studio. Não abra uma solução ou projeto na segunda instância.

1. Na segunda instância do Visual Studio, abra o menu **depurar** e escolha **anexar ao processo...**.

1. Dependendo do tipo de projeto (consulte as etapas anteriores), selecione o *UwpSurface. exe*, o *WpfSurface. exe*ou o processo *XDesProc. exe* na lista de processos disponíveis.

1. No campo **anexar a** do caixa de diálogo **anexar ao processo** , escolha o tipo de código correto para o controle personalizado que você deseja depurar.

   Se seu controle personalizado tiver sido escrito em uma linguagem .NET, escolha o tipo de código .NET apropriado, como **gerenciado (CoreCLR)**. Se o seu controle personalizado tiver sido escrito em C++, escolha **nativo**.

1. Anexe a segunda instância do Visual Studio clicando no botão **anexar** .

1. Na segunda instância do Visual Studio, abra os arquivos de código associados ao controle personalizado que você deseja depurar. Certifique-se de apenas abrir os arquivos, não a solução ou o projeto inteiro.

1. Coloque os pontos de interrupção necessários nos arquivos abertos anteriormente.

1. Na primeira instância do Visual Studio, feche a página XAML que contém o controle personalizado que você deseja depurar (a mesma página que você abriu nas etapas anteriores).

1. Na primeira instância do Visual Studio, abra a página XAML que você fechou na etapa anterior. Isso fará com que o depurador pare no primeiro ponto de interrupção definido na segunda instância do Visual Studio.

1. Depure o código na segunda instância do Visual Studio.

## <a name="see-also"></a>Veja também
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Segurança do depurador](../debugger/debugger-security.md)