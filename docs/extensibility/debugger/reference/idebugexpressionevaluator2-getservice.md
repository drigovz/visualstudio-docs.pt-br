---
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a4027b4153f262eb8164a915f229f04c7cbed4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325559"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera um objeto de serviço recebe seu identificador exclusivo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parâmetros
`uid`\
[in] Identificador exclusivo do serviço a ser recuperado.

`ppService`\
[out] Retorna um objeto que representa o serviço.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Isso pode ser consumido por um avaliador de expressão de terceiros para obter serviços de outro avaliador de expressão. Por exemplo, esse método pode ser usado para obter a interface para o serviço de visualização simultânea do avaliador de expressão padrão. Avaliadores de expressão de terceiros provavelmente não precisará implementar essa interface.

## <a name="see-also"></a>Consulte também
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)