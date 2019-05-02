---
title: Interface IEnumDebugStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugStackFrames interface
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 224c26bccc5443cb20e2ca514ac6df1a111df05e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963358"
---
# <a name="ienumdebugstackframes-interface"></a>Interface IEnumDebugStackFrames
Enumera os registros de ativação correspondente a um thread.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `IEnumDebugStackFrames` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|Recupera um número especificado de segmentos na sequência de enumeração.|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|Ignora um número especificado de segmentos em uma sequência de enumeração.|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|Cria um enumerador que contém o mesmo estado que o enumerador atual.|