---
title: Exibir eventos com o IntelliTrace | Microsoft Docs
description: Saiba como usar o IntelliTrace no Visual Studio Enterprise para coletar dados sobre eventos específicos, categorias de eventos e chamadas de função individuais.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fef839b5473881450581db77a885da158e67bbc
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815744"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Exibir eventos com o IntelliTrace no Visual Studio Enterprise (C#, Visual Basic)

Você pode usar o IntelliTrace para coletar informações sobre eventos específicos ou categorias de eventos ou sobre chamadas de função individuais, além de eventos. Os procedimentos a seguir mostram como fazer isso.

Você pode usar o IntelliTrace no Visual Studio Enterprise Edition, mas não as edições Professional ou Community.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Configurar o IntelliTrace

Você pode tentar depurar com apenas eventos do IntelliTrace. Os eventos do IntelliTrace são eventos do depurador, exceções, eventos do .NET Framework e outros eventos do sistema. Você deve ativar ou desativar eventos específicos para controlar os eventos que o IntelliTrace registra antes de iniciar a depuração. Para obter mais informações, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md).

- Ative o evento do IntelliTrace para acesso ao arquivo. Vá para as **ferramentas > opções > página de eventos intellitrace > IntelliTrace** e expanda a categoria **arquivo** . Verifique a categoria de evento **File** . Isso faz com que todos os eventos de arquivo (acesso, fechamento, exclusão) sejam verificados.

## <a name="create-your-app"></a>Criar o aplicativo

1. Crie um aplicativo de console C#. No arquivo Program.cs, adicione a seguinte `using` instrução:

    ```csharp
    using System.IO;
    ```

2. Crie um <xref:System.IO.FileStream> no método principal, leia-o, feche-o e exclua o arquivo. Adicione outra linha apenas para ter um local para definir um ponto de interrupção:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Definir um ponto de interrupção em `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Iniciar Depuração e exibir eventos do IntelliTrace

1. Inicie a depuração como de costume. (Pressione **F5** ou clique em **depurar > iniciar a depuração**.)

    > [!TIP]
    > Mantenha as janelas **locais** e **automáticas** abertas enquanto estiver Depurando para ver e registrar os valores nessas janelas.

2. A execução é interrompida no ponto de interrupção. Se você não vir a janela **ferramentas de diagnóstico** , clique em **depurar > eventos do IntelliTrace do Windows >**.

    Na janela **ferramentas de diagnóstico** , localize a guia **eventos** (você deve ver 3 guias, **eventos**, **uso de memória** e **uso de CPU**). A guia **eventos** mostra uma lista cronológica de eventos, terminando com o último evento antes da execução do depurador. Você deverá ver um evento chamado **Access WordSearchInputs.txt**.

    A captura de tela a seguir é do Visual Studio 2015 atualização 1.

    ![Captura de tela da janela do Visual Studio Code. A execução é interrompida em um ponto de interrupção e a guia eventos na janela Ferramentas de Diagnóstico lista os eventos.](../debugger/media/intellitrace-update1.png)

3. Selecione o evento para expandir seus detalhes.

    A captura de tela a seguir é do Visual Studio 2015 atualização 1.

    ![Captura de tela da guia eventos na janela de Ferramentas de Diagnóstico do Visual Studio. Um evento é selecionado e expandido para mostrar os detalhes.](../debugger/media/intellitraceupdate1-singleevent.png)

    Você pode escolher o link de nome de caminho para abrir o arquivo. Se o nome do caminho completo não estiver disponível, a caixa de diálogo **Abrir arquivo** será exibida.

    Clique em **Ativar depuração histórica**, que define o contexto do depurador como a hora em que o evento selecionado foi coletado, mostrando dados históricos na **pilha de chamadas**, **locais** e as outras janelas do depurador participantes. Se o código-fonte estiver disponível, o Visual Studio moverá o ponteiro para o código correspondente na janela de origem para que você possa examiná-lo.

    A captura de tela a seguir é do Visual Studio 2015 atualização 1.

    ![Captura de tela da janela do Visual Studio Code. A execução é interrompida em um ponto de interrupção, um evento é selecionado e a linha de código correspondente é realçada.](../debugger/media/historicaldebugging-update1.png)

4. Se você não encontrou o bug, tente examinar outros eventos que levam ao bug. Você também pode fazer o IntelliTrace registrar informações de chamada para que você possa passar por chamadas de função.

## <a name="next-steps"></a>Próximas etapas

Você pode usar alguns dos recursos avançados do IntelliTrace com a depuração histórica:

- Para exibir instantâneos, consulte [inspecionar Estados de aplicativos anteriores usando o IntelliTrace](../debugger/view-historical-application-state.md)
- Para saber como inspecionar variáveis e navegar pelo código, consulte [inspecionar seu aplicativo com a depuração histórica](../debugger/historical-debugging-inspect-app.md)
