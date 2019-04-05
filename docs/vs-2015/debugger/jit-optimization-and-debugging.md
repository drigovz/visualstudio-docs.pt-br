---
title: JIT otimização e depuração | Microsoft Docs
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
ms.openlocfilehash: b4a0cf53dcc9870b5d0c93d2fcaaf2d942fd9959
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924254"
---
# <a name="jit-optimization-and-debugging"></a>Otimização e depuração JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você depura um aplicativo gerenciado, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] suprime a otimização de código just-in-time (JIT) por padrão. A supressão da otimização JIT significa que você está depurando código não otimizado. O código é executado um pouco mais lentamente porque não é otimizado, mas sua experiência de depuração é muito mais completa. A depuração de código otimizado é mais difícil e recomendada somente se você encontrar um bug no código otimizado que não pode ser reproduzido na versão não otimizada.  
  
 Otimização JIT é controlada no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , o **suprimir Otimização JIT no carregamento do módulo** opção. Você pode encontrar essa opção na **gerais** página sob a **depuração** nó no **opções** caixa de diálogo.  
  
 Se você desmarcar a **suprimir Otimização JIT no carregamento do módulo** opção, você pode depurar o código otimizado JIT, mas sua capacidade de depuração pode ser limitada porque o código otimizado não corresponde ao código-fonte. Como resultado, janelas do depurador, como o **Locals** e **Autos** janela não podem exibir tanta informação quanto eles seriam se você estivesse depurando código não otimizado.  
  
 Outra diferença importante está relacionada à depuração com Apenas Meu Código. Se você estiver depurando com Apenas Meu Código, o depurador considerará o código otimizado como código de não usuário, que não deve ser exibido durante a depuração. Consequentemente, se estiver depurando código otimizado JIT, provavelmente será conveniente desativar Apenas Meu Código. Para obter mais informações, consulte [restringir o passo ao Just My Code](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Lembre-se de que o **suprimir Otimização JIT no carregamento do módulo** opção suprime a otimização de código quando os módulos são carregados. Se você anexar a um processo que já estiver em execução, ele poderá conter código já carregado, compilado por JIT e otimizado. O **suprimir Otimização JIT no carregamento do módulo** opção não tem nenhum efeito sobre esse código, embora afete os módulos são carregados depois da anexação. Além disso, o **suprimir Otimização JIT no carregamento do módulo** opção não afeta módulos, como WinForms, que são criados com NGEN.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Navegar pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo de execução gerenciada](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
