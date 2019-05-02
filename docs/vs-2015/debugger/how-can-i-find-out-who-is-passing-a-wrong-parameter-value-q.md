---
title: Como posso descobrir quem está passando um valor de parâmetro incorreto? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa3f96cd6ee5ff3c4f78a3e9a9bc89b2037066fc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053826"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Como posso descobrir quem está passando um valor de parâmetro incorreto?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrição do problema  
 O valor de parâmetro errado está sendo passado a uma de minhas funções. Essa função é chamada de todos os pontos Como posso descobrir o que está passando o valor errado?  
  
## <a name="solution"></a>Solução  
  
#### <a name="to-resolve-this-problem"></a>Para resolver esse problema  
  
1. Defina um local de ponto de interrupção no início da função.  
  
2. Clique com o botão direito do mouse no ponto de interrupção e selecione **Condição**.  
  
3. Na caixa de diálogo **Condição de Ponto de Interrupção**, clique na caixa de seleção **Condição**. Ver [avançadas de pontos de interrupção](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4. Digite uma expressão, como `Var==3`, na caixa de texto, onde `Var` é o nome do parâmetro que contém o valor incorreto, e `3` é o valor incorreto passado para ele.  
  
5. Selecione o botão de opção **é True** e clique no botão **OK**.  
  
6. Agora, execute o programa novamente. O ponto de interrupção faz com que o programa pare no início da função quando o parâmetro `Var` tiver o valor `3`.  
  
7. Use a janela Pilha de Chamadas para localizar a função de chamada e navegar até seu código-fonte. Para obter mais informações, confira [Como: Usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Pontos de interrupção](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
