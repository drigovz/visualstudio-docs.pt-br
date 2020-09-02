---
title: 'IDebugEvent2:: GetAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc3fc1b7988401611190fdf09e8041bf0dc5b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729947"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Obtém os atributos para este evento de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Parâmetros
`pdwAttrib`\
fora Uma combinação de sinalizadores da enumeração do [eventoattributes](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) é comum a todos os eventos. Este método descreve o tipo de evento; por exemplo, é o evento síncrono ou assíncrono e é um evento de interrupção.

## <a name="see-also"></a>Confira também
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
