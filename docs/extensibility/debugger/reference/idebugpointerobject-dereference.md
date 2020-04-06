---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725568"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Aponta o objeto para.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>parâmetros
`dwIndex`\
[em] Um simples byte offset desde o início do objeto apontou para.

`ppObject`\
[fora] Retorna um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) representando o objeto apontado para, mais deslocamento, se houver.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro. Retorna E_FAIL se este objeto não apontar para outro objeto.

## <a name="remarks"></a>Comentários
 O objeto apontado pode ser um tipo primitivo ou mais complexo, como uma classe ou estrutura.

## <a name="see-also"></a>Confira também
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
