---
title: Introdução com o depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202357"
---
# <a name="getting-started-with-the-debugger"></a>Introdução ao depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador do Visual Studio é fácil de usar em qualquer linguagem. Aqui, mostraremos como depurar um programa C# simples, mas você pode aplicar as mesmas etapas para codificar em outras linguagens, como C++ e JavaScript.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Depurar um projeto básico do C#  
 Vamos começar com um aplicativo de console C# simples (**arquivo/novo/projeto**, em seguida, selecione **Visual C#** e, em seguida, selecione **aplicativo de console**). Se você nunca trabalhou com o Visual Studio antes, confira [passo a passos: criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). O método **Main** apenas adiciona 1 a uma variável Integer 10 vezes e imprime o resultado no console:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Compile este código na configuração de **depuração** . Essa configuração é definida por padrão. Para obter mais informações sobre configurações, consulte [noções básicas sobre configurações de compilação](../ide/understanding-build-configurations.md).  
  
 Execute esse código no depurador clicando em **depurar/iniciar depuração** (ou **Iniciar** na barra de ferramentas ou **F5**). O aplicativo deve sair quase imediatamente, portanto, você não pode realmente dizer se algo foi impresso na janela do console.  
  
 Você pode interromper a execução por tempo suficiente para ver a janela do console definindo um ponto de interrupção e, em seguida, avançando. Para definir um ponto de interrupção, coloque o cursor na `Console.WriteLine` linha e clique em **depurar/novo ponto**de interrupção/cursor de função ou apenas clique na margem esquerda na mesma linha. O ponto de interrupção deve ter a seguinte aparência:  
  
 ![Definir um ponto de interrupção](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Para obter mais informações sobre pontos de interrupção, consulte [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Inspecionar variáveis  
 A depuração geralmente envolve a localização de variáveis que não contêm os valores esperados em um determinado ponto. Mostraremos algumas das maneiras pelas quais você pode inspecionar variáveis.  
  
 Inicie a depuração novamente. A execução é interrompida antes da execução do `Console.WriteLine` código. Você pode fazer com que ele seja executado avançando (clique em **depurar/passar sobre** ou **F10**). Nesse caso, você poderia ter escolhido **Step Into** (**F11**) e obter o mesmo resultado; Explicaremos a diferença posteriormente. A linha com a última chave do método deve ficar amarela. Examine a janela do console. Você deve ver **10**.  
  
 Você pode passar o mouse sobre a variável **testInt** para exibir o valor atual em uma dica de dados.  
  
 ![DBG&#95;noções básicas&#95;dicas de&#95;de dados](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Logo abaixo da janela de código, você verá as janelas **automáticos**, **locais**e de **inspeção** . Essas janelas mostram os valores atuais das variáveis no momento da execução. As janelas **automáticos** e **locais** mostram **testInt** com um valor de **10**.  
  
 ![Janela automática ao depurar](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Para obter mais informações sobre essas janelas, consulte [janelas automáticas e locais](../debugger/autos-and-locals-windows.md).  
  
 Vamos ver como o valor da variável muda à medida que percorremos o programa. Defina um ponto de interrupção na `testInt += 1;` linha e reinicie a depuração. Você deve ver que **testInt** nos **locais** e janelas **automáticas** é **0**, e **i** é **1**. Quando você continuar a depuração (**debug/continue**ou **continue** na barra de ferramentas, ou **F5**), poderá ver que o valor de **testInt** é alterado para **1**, depois **2**, e assim por diante. Quando você ficar cansado de examinar essas alterações, remova o ponto de interrupção (**depure/Alterne o ponto de interrupção**ou clique nele na margem) e continue a depuração. Se você quiser remover todos os pontos de interrupção, clique em **depurar/excluir todos os pontos de interrupção**ou **Ctrl + Shift + F9**e clique em **Sim** na caixa de diálogo que pergunta se **deseja remover todos os pontos de interrupção?**.  
  
## <a name="stepping-into-and-over-function-calls"></a>Percorrendo e over chamadas de função  
 Você pode executar o código na instrução do depurador-por-instrução (**Step Into**) ou pode executar o código enquanto o depurador ignora funções (**depuração**) para obter rapidamente o código de que você está mais interessado (o código de função ainda é executado). Você pode alternar entre os dois métodos na mesma sessão de depuração.  
  
 Para ver a diferença entre **Step Into** e **Step**, precisamos adicionar um método que é chamado por outro método. Adicione um método ao aplicativo C# e chame-o do método Main. O código deve ser semelhante a este:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Defina um ponto de interrupção na `Method1();` chamada no método principal e inicie a depuração. Quando a execução for interrompida, clique em **depurar/entrar** (ou **entrar** na barra de ferramentas ou **F11**). A execução é interrompida novamente na primeira chave em Method1 ():  
  
 ![Percorrendo o código](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Pare a depuração e inicie novamente e, quando a execução for interrompida no ponto de interrupção, clique em **depurar/percorrer** **(ou passar sobre a** barra de ferramentas ou **F10**). A execução é interrompida novamente em `Console.WriteLine("end");` .  
  
 Se você quiser saber mais sobre como navegar no código com o depurador, consulte [navegando pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md).
