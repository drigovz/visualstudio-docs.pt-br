---
title: Interface IEnumDebugExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugExpressionContexts interface
ms.assetid: 1c11f9ff-c5a6-48b8-a287-0d782513ba55
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c257fe12f27bb5e6ffd5835986d0c7cac6193a8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146676"
---
# <a name="ienumdebugexpressioncontexts-interface"></a>Interface IEnumDebugExpressionContexts
Enumera uma coleção de objetos `IDebugExpressionContexts`.  
  
 Além dos métodos herdados de `IUnknown`, o `IEnumDebugExpressionContexts` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IEnumDebugExpressionContexts::Next](../../winscript/reference/ienumdebugexpressioncontexts-next.md)|Recupera um número especificado de segmentos na sequência de enumeração.|  
|[IEnumDebugExpressionContexts::Skip](../../winscript/reference/ienumdebugexpressioncontexts-skip.md)|Ignora um número especificado de segmentos em uma sequência de enumeração.|  
|[IEnumDebugExpressionContexts::Reset](../../winscript/reference/ienumdebugexpressioncontexts-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[IEnumDebugExpressionContexts::Clone](../../winscript/reference/ienumdebugexpressioncontexts-clone.md)|Cria um enumerador que contém o mesmo estado que o enumerador atual.|