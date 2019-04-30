---
title: 'Como: Usar Editar e continuar (c#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63384018"
---
# <a name="how-to-use-edit-and-continue-c"></a>Como: Usar Editar e Continuar (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com a função Editar e Continuar no C#, é possível fazer alterações em seu código no modo de interrupção durante a depuração. As alterações podem ser aplicadas sem precisar interromper e reiniciar a sessão de depuração.  
  
 Editar e continuar é invocado automaticamente quando você faça alterações no modo de interrupção e escolha a execução de um depurador comando, como **Continue**, **etapa**, ou **definir próxima instrução**, ou avaliar uma função em uma janela do depurador.  
  
> [!NOTE]
> A função Editar e Continuar não tem suporte ao depurar o Compact Framework, código otimizado, código nativo misto/gerenciado ou código de integração do SQL Server Common Language Runtime (CLR). Se você tentar aplicar alterações de código em um desses cenários, o depurador coloca uma caixa de diálogo explicando que a função Editar e Continuar não tem suporte.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Para invocar a função Editar e Continuar automaticamente  
  
1. No modo de interrupção, faça uma alteração no código-fonte.  
  
2. Dos **Debug** menu, clique em **continuar**, **etapa**, ou **definir próxima instrução** ou avaliar uma função em uma janela do depurador.  
  
     O novo código é compilado e a depuração continua com o novo código. Algumas alterações não têm suporte para a função Editar e Continuar. Para obter mais informações, consulte [Supported Code Changes (c#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar/desabilitar a função Editar e Continuar  
  
1. No menu **Ferramentas**, clique em **Opções**.  
  
2. No **opções** diálogo caixa, expanda o **depuração** nó e selecione **editar e continuar**.  
  
3. No **opções** caixa de diálogo **editar e continuar** página, marque ou desmarque as **habilitar editar e continuar** caixa de seleção.  
  
     A configuração entra em vigor quando você reinicia a sessão de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Editar e continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Alterações de código suportadas (c#)](../debugger/supported-code-changes-csharp.md)   
 [Erros e avisos de Editar e Continuar (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
