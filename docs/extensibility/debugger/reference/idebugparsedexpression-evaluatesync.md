---
title: IDebugParsedExpression::AssessSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726011"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Este método avalia a expressão analisado e, opcionalmente, lança o resultado para outro tipo de dados.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>parâmetros
`dwEvalFlags`\
[em] Uma combinação de [constantes EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controlam como a expressão deve ser avaliada.

`dwTimeout`\
[em] Especifica o tempo máximo, em milissegundos, para esperar antes de retornar deste método. Use `INFINITE` para esperar indefinidamente.

`pSymbolProvider`\
[em] O provedor de símbolos, expresso como uma interface [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[em] O local de execução atual dentro de um método, expresso como uma interface [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[em] O fichário, expresso como uma interface [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`bstrResultType`\
[em] O tipo para o que o resultado deve ser lançado. Este argumento pode ser um valor nulo.

`ppResult`\
[fora] Retorna a interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa os resultados da avaliação.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O contexto de avaliação `pAddress`de expressão é dado por , o que torna possível determinar o método de contenção e, em seguida, usar regras de escopo de linguagem para determinar o valor dos símbolos na expressão.

## <a name="see-also"></a>Confira também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
