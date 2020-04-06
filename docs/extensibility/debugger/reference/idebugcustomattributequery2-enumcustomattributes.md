---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732590"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Obtém um enumerador para todos os atributos personalizados anexados a este campo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>parâmetros
`ppEnum`\
[fora] Retorna um objeto [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) representando a lista de atributos personalizados; caso contrário, retorna um valor nulo se não houver atributos personalizados.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna S_OK ou S_FALSE se não houver atributos personalizados neste campo. Caso contrário, retorna um código de erro;

## <a name="remarks"></a>Comentários
 Um campo pode ter vários atributos personalizados.

## <a name="see-also"></a>Confira também
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
