---
title: IDebugCustomAttribute::GetParentField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 158887e9f2d7d7b250b435570d6780e460508816
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921653"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Obtém o campo ao qual o atributo personalizado está anexado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Parâmetros
 `ppField`

 [out] Retorna o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa o campo ao qual o atributo personalizado está anexado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Chame o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em retornado [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) é de objeto para determinar qual tipo de campo pai.

## <a name="see-also"></a>Consulte também
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)