---
title: Depuração histórica | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7db175535e0eebdcf1974f0f85123959ba5a3ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192170"
---
# <a name="historical-debugging"></a>Depuração de histórico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A depuração histórica é um modo de depuração que depende das informações coletadas pelo IntelliTrace. Ele permite que você se mova para trás e para frente pela execução do seu aplicativo e inspecione seu estado.  
  
 Você pode usar o IntelliTrace no Visual Studio Enterprise Edition (mas não as edições Professional ou Community).  
  
## <a name="why-use-historical-debugging"></a>Por que usar a depuração histórica?  
 A definição de pontos de interrupção para localizar bugs pode ser um sórdida ou um problema de perda. Você define um ponto de interrupção próximo ao local em seu código em que você suspeita que o bug seja, execute o aplicativo no depurador e espero que o ponto de interrupção seja atingido e que o local em que a execução é interrompida possa revelar a origem do bug. Caso contrário, você precisará tentar definir um ponto de interrupção em outro lugar no código e executar novamente o depurador, executando as etapas de teste repetidamente até encontrar o problema.  
  
 ![definindo um ponto de interrupção](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Você pode usar o IntelliTrace e a depuração histórica para fazer o roaming em seu aplicativo e inspecionar seu estado (pilha de chamadas e variáveis locais) sem precisar definir pontos de interrupção, reiniciar a depuração e repetir etapas de teste. Isso pode poupar muito tempo, especialmente quando o bug está mais profundo em um cenário de teste que leva muito tempo para ser executado.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Como fazer começar a usar a depuração histórica?  
 O IntelliTrace está ativado por padrão. Tudo o que você precisa fazer é decidir quais eventos e chamadas de função são de seu interesse. Para obter mais informações sobre como definir o que você deseja procurar, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md). Para obter uma conta passo a passo de depuração com o IntelliTrace, consulte [passo a passos: usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Navegando em seu código com a depuração histórica  
 Vamos começar com um programa simples que tem um bug. Em um aplicativo de console em C#, adicione o seguinte código:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Vamos pressupor que o valor esperado de `resultInt` após a chamada `AddAll()` seja 20 (o resultado de incrementos `testInt` 20 vezes). (Também vamos supor que você não consiga ver o bug no `AddInt()` ). Mas o resultado é, na verdade, 44. Como podemos encontrar o bug sem passar por `AddAll()` 10 vezes? Podemos usar a depuração histórica para encontrar o bug com mais rapidez e facilidade. Veja como fazer isso:  
  
1. Em ferramentas/opções/IntelliTrace/geral, verifique se o IntelliTrace está habilitado e selecione a opção eventos do IntelliTrace e informações de chamada. Se você não selecionar essa opção, não será possível ver a medianiz de navegação (conforme explicado abaixo).  
  
2. Defina um ponto de interrupção na linha `Console.WriteLine(resultInt);`.  
  
3. Inicie a depuração. O código é executado para o ponto de interrupção. Na janela **locais** , você pode ver que o valor de `resultInt` é 44.  
  
4. Abra a janela de **ferramentas de diagnóstico** (**depurar/mostrar ferramentas de diagnóstico**). A janela de código deve ter a seguinte aparência:  
  
    ![Janela de código no ponto de interrupção](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Você deve ver uma seta dupla ao lado da margem esquerda, logo acima do ponto de interrupção. Essa área é chamada de medianiz de navegação e é usada para depuração histórica. Clique na seta.  
  
    Na janela de código, você verá que a linha de código anterior ( `int resultInt = AddIterative(testInt);` ) é cor rosa. Acima da janela, você verá uma mensagem informando que agora está na depuração histórica.  
  
    A janela de código agora tem esta aparência:  
  
    ![janela de código no modo de depuração histórica](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Agora você pode entrar no `AddAll()` método (**F11**ou no botão entrar **Step Into** na medianiz de navegação. Avançar (**F10**ou **ir para próxima chamada** na medianiz de navegação. A linha rosa está agora na `j = AddInt(j);` linha. O **F10** , nesse caso, não faz a etapa para a próxima linha de código. Em vez disso, ele percorre a próxima chamada de função. A depuração histórica navega da chamada para chamada e ignora as linhas de código que não incluem uma chamada de função.  
  
7. Agora, percorra o `AddInt()` método. Você deve ver o bug neste código imediatamente.  
  
   Esse procedimento apenas arranha a superfície do que você pode fazer com a depuração histórica. Para saber mais sobre as diferentes configurações e os efeitos dos diferentes botões na medianiz de navegação, consulte recursos do [IntelliTrace](../debugger/intellitrace-features.md).
