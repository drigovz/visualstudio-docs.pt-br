---
title: 'Walkthrough: usando o IntelliTrace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d18ae0684dab5b6dc5c4001b93804bb13aa75e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838430"
---
# <a name="walkthrough-using-intellitrace"></a>Passo a passo: usando o IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o IntelliTrace para coletar informações sobre eventos específicos ou categorias de eventos ou sobre chamadas de função individuais, além de eventos. Os procedimentos a seguir mostram como fazer isso.  
  
 Você pode usar o IntelliTrace no Visual Studio Enterprise Edition (mas não as edições Professional ou Community).  
  
## <a name="using-intellitrace-with-events-only"></a><a name="GettingStarted"></a> Usando o IntelliTrace apenas com eventos  
 Você pode tentar depurar com apenas eventos do IntelliTrace. Os eventos do IntelliTrace são eventos do depurador, exceções, eventos do .NET Framework e outros eventos do sistema. Você deve ativar ou desativar eventos específicos para controlar os eventos que o IntelliTrace registra antes de iniciar a depuração. Para obter mais informações, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
 As etapas a seguir mostram como depurar somente com eventos do IntelliTrace:  
  
1. Ative o evento do IntelliTrace para acesso ao arquivo. Vá para a página **ferramentas/opções/IntelliTrace/IntelliTrace eventos** e expanda a categoria **arquivo** . Verifique a categoria de evento **File** . Isso faz com que todos os eventos de arquivo (acesso, fechamento, exclusão) sejam verificados.  
  
2. Crie um aplicativo de console C#. No arquivo Program.cs, adicione a seguinte `using` instrução:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3. Crie um <xref:System.IO.FileStream> no método principal, leia-o, feche-o e exclua o arquivo. Adicione outra linha apenas para ter um local para definir um ponto de interrupção:  
  
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
  
4. Definir um ponto de interrupção em `Console.WriteLine("done");`  
  
5. Inicie a depuração como de costume. (Pressione **F5** ou clique em **depurar/iniciar depuração**.  
  
    > [!TIP]
    > Mantenha as janelas **locais** e **automáticas** abertas enquanto estiver Depurando para ver e registrar os valores nessas janelas.  
  
6. A execução é interrompida no ponto de interrupção. Se você não vir a janela **ferramentas de diagnóstico** , clique em **depurar/Windows/eventos do IntelliTrace**.  
  
     Na janela **ferramentas de diagnóstico** , localize a guia **eventos** (você deve ver 3 guias, **eventos**, **uso de memória**e **uso de CPU**). A guia **eventos** mostra uma lista cronológica de eventos, terminando com o último evento antes da execução do depurador. Você deverá ver um evento chamado **Access WordSearchInputs.txt**.  
  
     A captura de tela a seguir é do Visual Studio 2015 atualização 1.  
  
     ![Atualização1 do IntelliTrace&#45;](../debugger/media/intellitrace-update1.png "IntelliTrace-Atualização1")  
  
7. Selecione o evento para expandir seus detalhes.  
  
     A captura de tela a seguir é do Visual Studio 2015 atualização 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Você pode escolher o link de nome de caminho para abrir o arquivo. Se o nome do caminho completo não estiver disponível, a caixa de diálogo **Abrir arquivo** será exibida.  
  
     Clique em **Ativar depuração histórica**, que define o contexto do depurador como a hora em que o evento selecionado foi coletado, mostrando dados históricos na **pilha de chamadas**, **locais** e as outras janelas do depurador participantes. Se o código-fonte estiver disponível, o Visual Studio moverá o ponteiro para o código correspondente na janela de origem para que você possa examiná-lo.  
  
     A captura de tela a seguir é do Visual Studio 2015 atualização 1.  
  
     ![HistoricalDebugging&#45;Atualização1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Atualização1")  
  
8. Se você não encontrou o bug, tente examinar outros eventos que levam ao bug. Você também pode fazer o IntelliTrace registrar informações de chamada para que você possa passar por chamadas de função.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Usando o IntelliTrace com eventos e chamadas de função  
 O IntelliTrace pode registrar chamadas de função juntamente com eventos. Isso permite que você veja o histórico da pilha de chamadas e percorra as chamadas para trás e para frente em seu código. O IntelliTrace registra dados como nomes de função, pontos de entrada e saída de função e certos valores de parâmetro e valores de retorno. Consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
1. Ative a coleta de chamadas. (Em **ferramentas/opções/IntelliTrace/geral**, selecione **eventos do IntelliTrace e informações de chamada**. O IntelliTrace começará a coletar essas informações quando a próxima sessão de depuração for iniciada.  
  
    > [!TIP]
    > Isso pode tornar o aplicativo lento e aumentar o tamanho de quaisquer arquivos de log do IntelliTrace (arquivos. iTrace) que você está salvando no disco. Para obter a maioria de dados de chamada, mas minimizar os efeitos, o registra dados somente dos módulos de seu interesse. Para alterar o tamanho máximo de seus arquivos. iTrace, vá para **ferramentas/opções/IntelliTrace/avançado**e especifique a quantidade máxima de espaço em disco. O padrão é 250 MB.  
  
2. Inicie a depuração do aplicativo de console em C# criado na seção anterior. A execução é interrompida no ponto de interrupção. Se você não vir a janela **ferramentas de diagnóstico** , clique em **depurar/Windows/eventos do IntelliTrace**.  
  
3. Alterne para a guia **chamadas** .  
  
     Agora você vê as chamadas de função do aplicativo, começando com a chamada raiz (na solução atual, o ponto de entrada principal) e terminando com o local no qual a execução foi interrompida.  
  
     Selecione uma das chamadas de função e clique duas vezes nela. Você deve ver os pontos de entrada e saída da função, bem como as chamadas feitas pela chamada atual a outras funções e os eventos do IntelliTrace gerados pela chamada. Se você não tiver a depuração histórica ativada, essa ação a ativará. Para saber mais sobre a depuração histórica, consulte [depuração histórica](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    > Você pode ver que algumas chamadas estão esmaecidas. Isso ocorre porque o IntelliTrace não registrou dados dos módulos correspondentes. Para ver esses dados, faça com que o IntelliTrace colete dados desses módulos. Para obter informações sobre como especificar módulos, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Próximas etapas
