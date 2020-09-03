---
title: Otimização e depuração JIT | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690532"
---
# <a name="jit-optimization-and-debugging"></a>Otimização e depuração JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você depura um aplicativo gerenciado, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] suprime a otimização do código JIT (just-in-time) por padrão. A supressão da otimização JIT significa que você está depurando código não otimizado. O código é executado um pouco mais lentamente porque não é otimizado, mas sua experiência de depuração é muito mais completa. A depuração de código otimizado é mais difícil e recomendada somente se você encontrar um bug no código otimizado que não pode ser reproduzido na versão não otimizada.  
  
 A otimização JIT é controlada [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pela opção **suprimir otimização JIT na carga do módulo** . Você pode encontrar essa opção na página **geral** sob o nó **depuração** na caixa de diálogo **Opções** .  
  
 Se você desmarcar a opção **suprimir a otimização JIT na carga do módulo** , poderá depurar o código JIT otimizado, mas sua capacidade de depurar pode ser limitada porque o código otimizado não corresponde ao código-fonte. Como resultado, as janelas do depurador, como a janela **locais** e **automáticas** , podem não exibir tantas informações quanto seriam se você estivesse Depurando código não otimizado.  
  
 Outra diferença importante está relacionada à depuração com Apenas Meu Código. Se você estiver depurando com Apenas Meu Código, o depurador considerará o código otimizado como código de não usuário, que não deve ser exibido durante a depuração. Consequentemente, se estiver depurando código otimizado JIT, provavelmente será conveniente desativar Apenas Meu Código. Para obter mais informações, consulte  [restringir a depuração para apenas meu código](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Lembre-se de que a opção **suprimir otimização JIT na carga do módulo** suprime a otimização do código quando os módulos são carregados. Se você anexar a um processo que já estiver em execução, ele poderá conter código já carregado, compilado por JIT e otimizado. A opção **suprimir otimização JIT na carga do módulo** não tem nenhum efeito sobre esse código, embora isso afete os módulos carregados após a anexação. Além disso, a opção **suprimir otimização JIT na carga do módulo** não afeta módulos, como WinForms.dll, que são criados com NGen.  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração de código gerenciado](../debugger/debugging-managed-code.md)   
 [Navegando pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo de execução gerenciada](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
