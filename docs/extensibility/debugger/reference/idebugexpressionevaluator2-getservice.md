---
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb0f822011a5f54cf97e58f53ec1cf03b5d26a23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926340"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera um objeto de serviço de acordo com seu identificador exclusivo.

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
no Identificador exclusivo do serviço a ser recuperado.

`ppService`\
fora Retorna um objeto que representa o serviço.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Isso pode ser consumido por um avaliador de expressão de terceiros para obter serviços de outro avaliador de expressão. Por exemplo, esse método pode ser usado para obter a interface do serviço Visualizador do avaliador de expressão padrão. Não é improvável que os avaliadores de expressão de terceiros precisem implementar essa interface.

## <a name="see-also"></a>Confira também
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
