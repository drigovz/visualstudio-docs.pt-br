---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 265c77acdb15069c1fcd7f33d93d4ff74a528eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896143"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Grava um despejo em um arquivo.

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
no Um valor da enumeração [dumptype](../../../extensibility/debugger/reference/dumptype.md) que especifica o tipo de despejo, por exemplo, curto ou longo.

`pszDumpUrl`\
no A URL na qual gravar o despejo. Normalmente, isso está na forma de `file://c:\path\filename.ext` , mas pode ser qualquer URL válida.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um despejo de programa normalmente incluiria o quadro de pilhas atual, a pilha em si, uma lista dos threads em execução no programa e, possivelmente, qualquer memória que o programa possui.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
