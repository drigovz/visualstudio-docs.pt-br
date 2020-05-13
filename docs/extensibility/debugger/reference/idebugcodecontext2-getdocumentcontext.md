---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734350"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtém o contexto do documento que corresponde a este contexto de código. O contexto do documento representa uma posição no arquivo de origem que corresponde ao código fonte que gerou essa instrução.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>parâmetros
`ppSrcCxt`\
[fora] Retorna o objeto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que corresponde ao contexto de código. Se `S_OK` for devolvido, deve ser`null`não- .

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Um mecanismo de depuração deve `E_FAIL` retornar `out` um `null` código de falha, como quando o parâmetro é como quando o contexto de código não tem posição de origem associada.

## <a name="remarks"></a>Comentários
 Geralmente, o contexto do documento pode ser pensado como uma posição em um arquivo de origem, enquanto o contexto do código é uma posição de uma instrução de código em um fluxo de execução.

## <a name="see-also"></a>Confira também
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
