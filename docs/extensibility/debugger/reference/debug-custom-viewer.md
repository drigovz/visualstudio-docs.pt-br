---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737536"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Uma estrutura que identifica um visualizador personalizado ou um visualizador de tipo.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Membros
`dwID`\
Um ID para diferenciar vários visualizadores `GUID`ou visualizadores implementados por um .

`bstrMenuName`\
O texto que aparecerá no menu suspenso.

`bstrDescription`\
Uma descrição do visualizador personalizado ou do tipo (deve ser um valor nulo se não for usado).

`guidLang`\
Linguagem do avaliador de expressão.

`guidVendor`\
Fornecedor do avaliador de expressão fornecido.

`bstrMetric`\
Métrica sob a qual o `CLSID` visualizador personalizado ou o visualizador de tipo é armazenado.

## <a name="remarks"></a>Comentários
Uma lista dessa estrutura é retornada por uma chamada para o método [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (e, por extensão, o método [GetCustomViewerList).](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
