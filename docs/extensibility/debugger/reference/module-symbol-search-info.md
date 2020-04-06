---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714255"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contém informações de status sobre os caminhos de pesquisa de símbolos que foram pesquisados.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Membros

`dwValidFields`\
Uma combinação de bandeiras da enumeração [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) especificando o tipo de informação de pesquisa descrita nesta estrutura.

`bstrVerboseSearchInfo`\
Caminho de pesquisa e resultados concatenados em uma única seqüência.

## <a name="remarks"></a>Comentários

Essa estrutura é devolvida a partir de uma chamada para o método [GetSymbolInfo.](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

Se `bstrVerboseSearchInfo` o campo não estiver vazio, ele contém uma lista de caminhos pesquisados e os resultados dessa pesquisa. A lista é formatada com um caminho, seguido de uma elipse ("..."), seguida pelo resultado. Se houver mais de um par de resultados de caminho, cada par será separado por um par "\r\n" (carriage-return/linefeed). O padrão é assim:

\<caminho>... \<resultado>\r\n\<caminho>... \<resultado>\r\n\<caminho>... \<> de resultados

Observe que a última entrada não tem uma seqüência \r\n.

Aqui está `bstrVerboseSearchInfo` uma possível seqüência que foi enviada para o padrão para fora.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requisitos

Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também

- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
