---
title: 'IDebugProgram2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3593dd8d139bbb23cbb8128378399642bee03fdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897337"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Solicita que o programa pare a execução na próxima vez que um de seus threads tentar executar.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um evento [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) é enviado quando o programa em seguida tenta executar o código depois que esse método é chamado.

 Esse método é assíncrono, pois o método retorna imediatamente sem aguardar a interrupção do programa.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
