---
title: Interface IDebugExpression | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9684253343aa83cf95f7d816781705eab7fbc327
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345507"
---
# <a name="idebugexpression-interface"></a>Interface IDebugExpression
Representa uma expressão avaliada de forma assíncrona. Mecanismos de script geralmente implementam essa interface. Um IDE de depurador normalmente usa essa interface para habilitar uma janela de execução imediata ou janela de observação.  
  
> [!NOTE]
>  O `IDebugExpression` interface está disponível somente a partir de um quadro de pilha.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugExpression` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Começa a avaliação da expressão.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Anula a expressão.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina se a operação for concluída.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Retorna o resultado da avaliação da expressão como uma cadeia de caracteres e o valor de retorno da operação.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Retorna o resultado da avaliação da expressão como uma propriedade de depuração e o valor de retorno da operação.|