---
title: Continuando a execução após uma exceção | Microsoft Docs
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
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702262"
---
# <a name="continuing-execution-after-an-exception"></a>Continuando a execução depois de uma exceção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando o depurador interrompe a execução devido a uma exceção, uma caixa de diálogo é exibida. Para Visual Basic ou C#, você verá a caixa de diálogo [Assistente de exceção](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) , por padrão. Para C++, você verá a caixa de diálogo **exceção** mais antiga. Se você estiver usando Visual Basic ou C#, mas tiver desabilitado o **Assistente de exceção** na caixa de diálogo **Opções** , verá a caixa de diálogo **exceção** .  
  
 Quando a caixa de diálogo **Assistente de exceção** ou **exceção** for exibida, você poderá tentar corrigir o problema que causou a exceção.  
  
## <a name="managed-code"></a>Código gerenciado  
 No código gerenciado, você poderá continuar a execução no mesmo thread após uma exceção não tratada. O **Assistente de exceção** desenrola a pilha de chamadas até o ponto em que a exceção foi gerada.  
  
## <a name="native-code"></a>Código nativo  
 No modo nativo C/C++, você tem duas opções:  
  
- Você pode clicar em **interromper** e tentar corrigir o problema. Enquanto estiver no modo de interrupção, você pode desenrolar a pilha de chamadas clicando com o botão direito do mouse em um quadro na janela **pilha de chamadas** e selecionando **desenrolar nesse quadro** no menu de atalho. Quando você continuar a depurar, a caixa de diálogo de **exceção** será exibida novamente se você não tiver corrigido o problema. Caso contrário, a caixa de diálogo de **exceção** não será reexibida.  
  
- Você pode clicar em **continuar** para continuar a execução sem tentar corrigir o problema. A caixa de diálogo de **exceção** é exibida novamente.  
  
## <a name="mixed-code"></a>Código misto  
 Se você atinge uma exceção não tratada ao depurar um código nativo misto e gerenciado, as restrições do sistema operacional impedem o desenrolar da pilha de chamadas. Se você tentar voltar a pilha de chamadas usando o menu de atalho, uma mensagem de erro explicará que o depurador não pode desenrolar de uma exceção não tratada exceto durante a depuração de código misto.  
  
## <a name="see-also"></a>Consulte Também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)
