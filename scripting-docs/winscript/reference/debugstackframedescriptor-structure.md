---
title: Estrutura DebugStackFrameDescriptor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153312"
---
# <a name="debugstackframedescriptor-structure"></a>Estrutura DebugStackFrameDescriptor
Enumera os registros de ativação e mescla saídas de vários enumeradores no mesmo thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Membros  
 `pdsf`  
 O objeto de quadro de pilha.  
  
 `dwMin`  
 Uma representação depende do computador do intervalo de endereços físicos associados a esse registro de ativação inferior.  
  
 `dwLim`  
 Uma representação depende do computador do intervalo de endereços físicos associados a esse registro de ativação superior.  
  
 `fFinal`  
 Sinalizador que indica que o quadro está sendo processado.  
  
 `punkFinal`  
 Se esse parâmetro não for `NULL`, o enumerador atual mesclagem deve ser interrompida e uma nova deve ser iniciada. O objeto indica como iniciar a nova enumeração.  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração do processo usa essa estrutura para classificar os registros de ativação de vários mecanismos de script. Por convenção, as pilhas crescem para baixo. Consequentemente, arquiteturas em que as pilhas crescem para cima, os endereços devem ser complementado por pares.  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)