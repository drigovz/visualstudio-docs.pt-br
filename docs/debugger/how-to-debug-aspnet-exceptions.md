---
title: 'Como: Depurar exceções do ASP.NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 002f100f11bd88e31b94283e7efe5e25299448bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944292"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Como: Depurar exceções do ASP.NET
A depuração de exceções é uma parte importante do desenvolvimento de um aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] robusto. Informações gerais sobre como depurar exceções estão na [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Para depurar as exceções não tratadas do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], você deve verificar se o depurador é interrompido para elas. O tempo de execução do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tem um manipulador de exceção de nível superior. Portanto, por padrão, o depurador nunca é interrompido em exceções não tratadas. Para interromper o depurador quando uma exceção é lançada, você deve selecionar **interromper quando uma exceção for: Lançada** definindo para essa exceção específica na **exceções** caixa de diálogo.  
  
 Se você tiver habilitado apenas meu código, **interromper quando uma exceção for: Lançada** não faz com que o depurador para interromper imediatamente se uma exceção é gerada em um método do .NET Framework ou outro código do sistema. Em vez disso, a execução continua até que o depurador atinja código que não seja do sistema, e então é interrompida. Como resultado, você não precisa depurar o código do sistema quando ocorre uma exceção.  
  
 Apenas meu código oferece outra opção que pode ser ainda mais útil: **Interromper quando uma exceção é: User-unhandled**. Se você escolher essa configuração para uma exceção, o depurador interromperá a execução no código do usuário, mas apenas se a exceção não for detectada e não for tratada pelo código do usuário. Essa configuração anula o efeito do manipulador de exceção de nível superior do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], porque esse manipulador está em código de não usuário.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Para ativar a depuração de exceções do ASP.NET com Apenas Meu Código  
  
1.  No menu **Depurar**, clique em **Exceções**.  
  
     A caixa de diálogo **Exceções** é exibida.  
  
2.  Na linha **Exceções do Common Language Runtime**, selecione **Geradas** ou **Sem tratamento do usuário**.  
  
     Para usar a configuração **Sem tratamento do usuário**, **Apenas Meu Código** deve estar habilitado.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Para usar as práticas recomendadas para o tratamento de exceção do ASP.NET  
  
-   Coloque blocos de `try ... catch` em torno do código que pode lançar exceções que você pode prever e sabe como manipular. Por exemplo, se o aplicativo estiver fazendo chamadas para um serviço Web XML ou diretamente para o SQL Server, o código deve estar em blocos **try … catch** porque várias exceções podem ocorrer.

## <a name="see-also"></a>Consulte também
[Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)