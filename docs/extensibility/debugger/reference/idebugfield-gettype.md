---
title: IDebugField::GetType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c052f4b4c45080d8292dd8787c44777818bae585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333169"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
Esse método obtém o tipo de campo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetType( 
   IDebugField** ppType
);
```

```csharp
int GetType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parâmetros
`ppType`\
[out] Retorna o tipo de campo como outra [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)