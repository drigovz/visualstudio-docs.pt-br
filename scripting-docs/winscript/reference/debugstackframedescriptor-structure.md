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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576546"
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
 Uma representação dependente de computador do intervalo inferior de endereços físicos associados a esse quadro de pilhas.  
  
 `dwLim`  
 Uma representação dependente de computador do intervalo superior de endereços físicos associados a esse quadro de pilhas.  
  
 `fFinal`  
 Sinalizador que indica que o quadro está sendo processado.  
  
 `punkFinal`  
 Se esse parâmetro não for `NULL`, a mesclagem atual do enumerador deverá parar e um novo deverá ser iniciado. O objeto indica como iniciar a nova enumeração.  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração de processos usa essa estrutura para classificar os quadros de pilha de vários mecanismos de script. Por convenção, as pilhas crescem para baixo. Consequentemente, em arquiteturas em que as pilhas crescem, os endereços devem ser dois Complementos.  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)