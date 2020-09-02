---
title: 'Walkthrough: Depurando em tempo de design | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149424"
---
# <a name="walkthrough-debugging-at-design-time"></a>Instruções passo a passo: depurando na hora de design
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar a janela **imediata** do Visual Studio para executar uma função ou sub-rotina enquanto o aplicativo não está em execução. Se a função ou a sub-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado. Então, você poderá usar o depurador do Windows para examinar o estado do programa. Esse recurso é chamado de depuração em tempo de design.  
  
 O procedimento a seguir exibe como usar esse recurso.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Para usar pontos de interrupção da janela Imediato  
  
1. Cole o seguinte código no aplicativo de console do Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. Defina um ponto de interrupção na linha em que se lê `s="Add BreakPoint Here"`.  
  
3. Digite o seguinte na janela **imediata** : `?MyFunction<enter>`  
  
4. Certifique-se de que o ponto de interrupção foi alcançado, e que a pilha de chamadas está correta.  
  
5. No menu **depurar** , clique em **continuar**e verifique se você ainda está no modo de design.  
  
6. Digite o seguinte na janela **imediata** : `?MyFunction<enter>`  
  
7. Digite o seguinte na janela **imediata** : `?MySub<enter>`  
  
8. Verifique se você atingiu o ponto de interrupção e examine o valor de variável estática `i` na janela **locais** . Deve ter o valor 3.  
  
9. Verifique se a pilha de chamadas está correta.  
  
10. No menu **depurar** , clique em **continuar**e verifique se você ainda está no modo de design.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)
