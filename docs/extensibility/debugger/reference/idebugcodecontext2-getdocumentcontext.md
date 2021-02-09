---
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaac527149d3224370f04d9dec46123b59568ac1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928738"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtém o contexto do documento que corresponde a este contexto de código. O contexto do documento representa uma posição no arquivo de origem que corresponde ao código-fonte que gerou essa instrução.

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

## <a name="parameters"></a>Parâmetros
`ppSrcCxt`\
fora Retorna o objeto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que corresponde ao contexto do código. Se `S_OK` for retornado, desse deverá ser não `null` .

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Um mecanismo de depuração deve retornar um código de falha, como `E_FAIL` quando o `out` parâmetro é `null` , por exemplo, quando o contexto do código não tem nenhuma posição de origem associada.

## <a name="remarks"></a>Comentários
 Em geral, o contexto do documento pode ser considerado como uma posição em um arquivo de origem enquanto o contexto do código é uma posição de uma instrução de código em um fluxo de execução.

## <a name="see-also"></a>Confira também
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
