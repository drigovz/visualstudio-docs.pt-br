---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f21b338511890879d805ce49377554719070604
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344388"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento para uma determinada matriz de contextos de documento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parâmetros
`compare`\
[in] Um valor a partir de [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumeração que especifica o tipo de comparação.

`rgpDocContextSet`\
[in] Uma matriz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que representam os contextos de documento de comparação.

`dwDocContextSetLen`\
[in] O comprimento da matriz de contextos de documento a ser comparado.

`pdwDocContext`\
[out] Retorna o índice para o `rgpDocContextSet` matriz do primeiro contexto de documento que satisfaz a comparação.

## <a name="return-value"></a>Valor de retorno
 Retorna `S_OK` se uma correspondência foi encontrada. Retorna `S_FALSE` se nenhuma correspondência foi encontrada. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que são passados na matriz devem ser implementados pelo mesmo mecanismo de depuração que implementa o `IDebugDocumentContext2` do objeto que está sendo chamado; caso contrário, a comparação não é válida.

## <a name="see-also"></a>Consulte também
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)