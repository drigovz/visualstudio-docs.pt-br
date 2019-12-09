---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a12838db0687fd7ebe20a5c576db0e06ece49107
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342407"
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
[out] Retorna o [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objeto que corresponde ao contexto de código. Se `S_OK` for retornado, ths deve ser não -`null`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Um mecanismo de depuração deve retornar um código de falha, como `E_FAIL` quando o `out` parâmetro é `null` como quando o contexto de código não tem nenhuma posição de origem associada.

## <a name="remarks"></a>Comentários
 Em geral, o contexto do documento pode ser pensado como uma posição em um arquivo de código-fonte enquanto o contexto de código é uma posição de uma instrução de código em um fluxo de execução.

## <a name="see-also"></a>Consulte também
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
