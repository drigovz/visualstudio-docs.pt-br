---
title: IDebugReference2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b14ca1293a709dce35f2e8aa45a7fa22bf29845
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178193"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Define o valor de uma referência de outra referência. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

#### <a name="parameters"></a>Parâmetros
 `rgpArgs`

 [in] Uma matriz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objetos usados para determinar como definir o valor de referência.

 `dwArgCount`

 [in] O número de referências na matriz.

 `pValue`

 [in] Uma [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto do qual definir o valor da propriedade.

 `dwTimeout`

 [in] Tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use `INFINITE` para aguardar indefinidamente.

## <a name="return-value"></a>Valor de retorno
 Sempre retorna `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)