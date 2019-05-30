---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90d9d680ca83967f9f651269e186670fb90a771d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343624"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Grava um despejo de um arquivo.

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

## <a name="parameters"></a>Parâmetros
`DumpType`\
[in] Um valor a partir de [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumeração que especifica o tipo de despejo, por exemplo, curto ou longo.

`pszDumpUrl`\
[in] A URL para gravar o despejo. Normalmente, isso é na forma de `file://c:\path\filename.ext`, mas pode ser qualquer URL válida.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um despejo de memória do programa normalmente incluiria o quadro de pilhas atual, a pilha em si, uma lista dos threads em execução no programa e, possivelmente, nenhuma memória que possui o programa.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)