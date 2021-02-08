---
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97b06179027549c0bebe83b2b4866e53c8fd9569
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842246"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera o número de cadeias de caracteres de valor a serem exibidas para a propriedade ou o campo especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parâmetros
`displayKind`\
no Valor da enumeração [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) .

`propertyOrField`\
no Uma interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa uma propriedade ou um campo.

`pcelt`\
fora Retorna o número de cadeias de caracteres de valor a serem exibidas.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
