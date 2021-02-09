---
title: 'IDebugCustomAttribute:: getattributetypefield | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fa72b6dfc02f29e5efd8d3e04f98f078cba66a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928439"
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
fora Retorna o objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa a classe da qual o atributo personalizado é uma instância.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um atributo personalizado é sempre uma classe. Esse método fornece acesso a um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que descreve essa classe.

## <a name="see-also"></a>Confira também
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
