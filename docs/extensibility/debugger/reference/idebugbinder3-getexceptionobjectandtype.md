---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 22d048bb915146e6c966dd16ca3b2345b5d697ba
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614734"
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
[out] Retorna o objeto que representa a exceção.

`ppField`\
[out] Retorna o objeto que representa um campo específico que pode ter causado a exceção (Isso pode ser um valor nulo).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

> [!NOTE]
> Para verificar se há uma exceção, verifique o valor retornado por `ppException`: se ele for um valor nulo, nenhuma exceção está associada este objeto.

## <a name="see-also"></a>Consulte também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)