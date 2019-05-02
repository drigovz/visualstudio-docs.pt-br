---
title: Interface IDebugExpression | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1757317e9ab148b508bfed95107b5c3b3369b598
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430021"
---
# <a name="idebugexpression-interface"></a>Interface IDebugExpression
Representa uma expressão avaliada de forma assíncrona. Mecanismos de script geralmente implementam essa interface. Um IDE de depurador normalmente usa essa interface para habilitar uma janela de execução imediata ou janela de observação.  
  
> [!NOTE]
> O `IDebugExpression` interface está disponível somente a partir de um quadro de pilha.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugExpression` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Começa a avaliação da expressão.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Anula a expressão.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina se a operação for concluída.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Retorna o resultado da avaliação da expressão como uma cadeia de caracteres e o valor de retorno da operação.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Retorna o resultado da avaliação da expressão como uma propriedade de depuração e o valor de retorno da operação.|