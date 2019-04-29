---
title: Continuando a execução após uma exceção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d557fc0ec056cac22603338f95920e5c721f67dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564093"
---
# <a name="continuing-execution-after-an-exception"></a>Continuando a execução depois de uma exceção
Quando o depurador interrompe a execução devido a uma exceção, você verá a **auxiliar de exceção**, por padrão. Se você tiver desabilitado as **auxiliar de exceção** na **opções** caixa de diálogo, você verá o **Assistente de exceção** (c# ou Visual Basic) ou o **exceção**  caixa de diálogo (C++).

 Quando o **auxiliar de exceção** for exibida, você pode tentar corrigir o problema que causou a exceção.

## <a name="managed-and-native-code"></a>Código gerenciado e nativo
 No código gerenciado e nativo, você pode continuar a execução no mesmo thread após uma exceção sem tratamento. O **auxiliar de exceção** desenrola a pilha de chamadas para o ponto em que a exceção foi lançada.

## <a name="mixed-code"></a>Código misto
 Se você atinge uma exceção não tratada ao depurar um código nativo misto e gerenciado, as restrições do sistema operacional impedem o desenrolar da pilha de chamadas. Se você tentar voltar a pilha de chamadas usando o menu de atalho, uma mensagem de erro explicará que o depurador não pode desenrolar de uma exceção não tratada exceto durante a depuração de código misto.

## <a name="see-also"></a>Consulte também

- [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)