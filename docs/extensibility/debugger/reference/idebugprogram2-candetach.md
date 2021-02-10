---
title: 'IDebugProgram2:: desanexar | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaff16923023598793dfdf9200105cc6b158ccb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936126"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Determina se um mecanismo DE depuração (DE) pode ser desanexado do programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valor retornado
 Se pode desanexar, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `S_FALSE` se o de não pode desanexar do programa.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
