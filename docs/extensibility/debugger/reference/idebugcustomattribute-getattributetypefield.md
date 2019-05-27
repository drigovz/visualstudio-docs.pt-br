---
title: IDebugCustomAttribute::GetAttributeTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e56553a8598bb885f6752332f795ca8fe2a7484
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205387"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Obtém o tipo de classe de atributo personalizado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

## <a name="parameters"></a>Parâmetros
`ppCAType`\
[out] Retorna o [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que representa a classe da qual o atributo personalizado é uma instância.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Um atributo personalizado é sempre uma classe. Esse método fornece acesso a um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que descreve essa classe.

## <a name="see-also"></a>Consulte também
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)