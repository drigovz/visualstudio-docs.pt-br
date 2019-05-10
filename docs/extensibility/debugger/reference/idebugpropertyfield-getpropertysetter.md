---
title: IDebugPropertyField::GetPropertySetter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f974874eb18f5893bf736a4f15922e3a86c13c67
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457645"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Obtém o método que define a propriedade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPropertySetter( 
   IDebugMethodField** ppField
);
```

```csharp
int GetPropertySetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>Parâmetros
 `ppField`\

 [out] Retorna um [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) que representa o método que define a propriedade do objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Para obter o método que obtém a propriedade, chame o [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)