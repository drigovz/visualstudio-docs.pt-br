---
title: 'Como: Depurar exceções ASP.NET | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ccd8c399bd92bd98307d44aff913c30390033c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205433"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Como depurar exceções do ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A depuração de exceções é uma parte importante do desenvolvimento de um aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] robusto. As informações gerais sobre como depurar exceções estão no [Gerenciamento de exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Para depurar as exceções não tratadas do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], você deve verificar se o depurador é interrompido para elas. O runtime do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tem um manipulador de exceção de nível superior. Portanto, por padrão, o depurador nunca é interrompido em exceções não tratadas. Para interromper o depurador quando uma exceção é lançada, você deve selecionar a configuração **Interromper quando uma exceção for: Lançada** para essa exceção específica na caixa de diálogo **Exceções**.  
  
 Se você tiver habilitado Apenas Meu Código, **Interromper quando uma exceção for: Lançada** não fará com que o depurador seja imediatamente interrompido caso uma exceção seja lançada em um método do .NET Framework ou em outro código do sistema. Em vez disso, a execução continua até que o depurador atinja código que não seja do sistema, e então é interrompida. Como resultado, você não precisa depurar o código do sistema quando ocorre uma exceção.  
  
 Apenas Meu Código oferece outra opção que pode ser ainda mais útil: **Interromper quando uma exceção for: Sem tratamento do usuário**. Se você escolher essa configuração para uma exceção, o depurador interromperá a execução no código do usuário, mas apenas se a exceção não for detectada e não for tratada pelo código do usuário. Essa configuração anula o efeito do manipulador de exceção de nível superior do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], porque esse manipulador está em código de não usuário.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Para ativar a depuração de exceções do ASP.NET com Apenas Meu Código  
  
1. No menu **Depurar**, clique em **Exceções**.  
  
     A caixa de diálogo **Exceções** é exibida.  
  
2. Na linha **Exceções do Common Language Runtime**, selecione **Geradas** ou **Sem tratamento do usuário**.  
  
     Para usar a configuração **Sem tratamento do usuário**, **Apenas Meu Código** deve estar habilitado.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Para usar as práticas recomendadas para o tratamento de exceção do ASP.NET  
  
- Coloque blocos de `try … catch` em torno do código que pode lançar exceções que você pode prever e sabe como manipular. Por exemplo, se o aplicativo estiver fazendo chamadas para um serviço Web XML ou diretamente para um SQL Server, esse código deverá estar em **try... blocos catch** porque há várias exceções que podem ocorrer.
