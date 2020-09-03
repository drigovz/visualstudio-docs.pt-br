---
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731885"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento com uma determinada matriz de contextos de documento.

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
no Um valor da enumeração [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) que especifica o tipo de comparação.

`rgpDocContextSet`\
no Uma matriz de objetos [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que representam os contextos de documento que estão sendo comparados.

`dwDocContextSetLen`\
no O comprimento da matriz de contextos de documento a ser comparado.

`pdwDocContext`\
fora Retorna o índice para a `rgpDocContextSet` matriz do primeiro contexto de documento que satisfaz a comparação.

## <a name="return-value"></a>Valor Retornado
 Retorna `S_OK` se uma correspondência foi encontrada. Retorna `S_FALSE` se nenhuma correspondência foi encontrada. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Os objetos [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que são passados na matriz devem ser implementados pelo mesmo mecanismo de depuração que implementa o `IDebugDocumentContext2` objeto que está sendo chamado; caso contrário, a comparação não é válida.

## <a name="see-also"></a>Confira também
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
