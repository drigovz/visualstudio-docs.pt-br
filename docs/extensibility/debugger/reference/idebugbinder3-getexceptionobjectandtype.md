---
title: 'IDebugBinder3:: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e25a0f7b4e1713a072359f1efdd962f36c50b774
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735742"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Esse método recupera a exceção associada a um objeto, se houver.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parâmetros
`ppException`\
fora Retorna o objeto que representa a exceção.

`ppField`\
fora Retorna o objeto que representa um campo específico que pode ter causado a exceção (esse pode ser um valor nulo).

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

> [!NOTE]
> Para verificar se há uma exceção, verifique o valor retornado por `ppException` : se for um valor nulo, nenhuma exceção será associada a esse objeto.

## <a name="see-also"></a>Confira também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
