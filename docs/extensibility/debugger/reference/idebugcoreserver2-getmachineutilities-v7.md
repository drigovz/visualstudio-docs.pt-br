---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733144"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Este método obtém os utilitários da máquina para um servidor.

> [!NOTE]
> Este método é obsoleto: não use (sempre[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] retorna `E_NOTIMPL` se este método for chamado). É retido por razões históricas.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>parâmetros
`ppUtil`\
[fora] Retorna `IDebugMDMUtil2_V7` uma interface que representa as informações dos utilitários da máquina.

## <a name="return-value"></a>Valor retornado
 Sempre `E_NOTIMPL`retorna, indicando que o método não é implementado.

## <a name="remarks"></a>Comentários
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]sempre `E_NOTIMPL` retorna se esse método for chamado.

## <a name="see-also"></a>Confira também
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
