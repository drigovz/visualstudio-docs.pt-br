---
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ccfea65f7f24b3d48fc5ec5d68028c72b9b4eece
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692640"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Define o valor do objeto de uma série consecutiva de bytes.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

#### <a name="parameters"></a>Parâmetros
 `pValue`

 [in] Uma matriz de bytes que representa o novo valor.

 `nSize`

 [in] O tamanho do valor em bytes.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Os valores na matriz são copiados para este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto, substituindo qualquer valor existente. O tamanho do novo valor pode ser maior ou menor que o valor existente. Isso `IDebugObject` não pode ser uma referência nula.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)