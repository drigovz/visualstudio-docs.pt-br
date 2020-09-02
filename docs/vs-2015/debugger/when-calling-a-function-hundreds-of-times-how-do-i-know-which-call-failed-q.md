---
title: Durante a chamada de uma função centenas de vezes, como sei qual chamada falhou? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fba5032860e21bbd323b8e49d5f32ab9b6f90540
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688127"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Durante a chamada de uma função centenas de vezes, como sei qual chamada falhou?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrição do problema  
 Meu programa falha em uma chamada para uma determinada função, `CnvtV`. O programa provavelmente chama essa função algumas centenas de vezes antes de falhar. Se eu definir um ponto de interrupção de local em `CnvtV`, o programa parará em cada chamada a essa função, e eu não quero isso. Eu não sei quais condições causam a falha na chamada, portanto, não consigo definir um ponto de interrupção condicional. O que posso fazer?  
  
## <a name="solution"></a>Solução  
 Você pode definir um ponto de interrupção na função com o campo **Contagem de Ocorrências** para um valor mais alto que nunca será atingido. Nesse caso, como você acredita que a função `CnvtV` será chamada algumas centenas de vezes, defina a **Contagem de Ocorrências** como 1000 ou mais. Execute o programa e aguarde a chamada falhar. Quando falhar, abra a janela Pontos de Interrupção e verifique a lista de pontos de interrupção. O ponto de interrupção definido em `CnvtV` aparece, seguido pela contagem de ocorrências e o número de iterações restantes:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Agora você sabe que a função falha na 101a chamada. Se você redefinir o ponto de interrupção com uma contagem de ocorrências de 101 e executar o programa novamente, o programa de chamada parará na chamada para `CnvtV` que causou a falha.  
  
## <a name="see-also"></a>Consulte Também  
 [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Configuração dos pontos de interrupção](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
