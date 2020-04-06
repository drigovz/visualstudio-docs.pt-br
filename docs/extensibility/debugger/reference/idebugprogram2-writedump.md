---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722729"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Escreve um despejo em um arquivo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>parâmetros
`DumpType`\
[em] Um valor da enumeração [DUMPtype](../../../extensibility/debugger/reference/dumptype.md) que especifica o tipo de despejo, por exemplo, curto ou longo.

`pszDumpUrl`\
[em] A URL para escrever o dump to. Normalmente, isso é na `file://c:\path\filename.ext`forma de , mas pode ser qualquer URL válido.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um dump de programa normalmente incluiria o quadro de pilha atual, a própria pilha, uma lista dos threads em execução no programa e, possivelmente, qualquer memória que o programa possui.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
