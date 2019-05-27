---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1161b97c642b7dc28f2b27037ef3253adf9f6eda
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209726"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Esse método avalia a expressão analisada e, opcionalmente, converte o resultado em outro tipo de dados.

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

## <a name="parameters"></a>Parâmetros
`dwEvalFlags`\
[in] Uma combinação de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) constantes que controlam como a expressão será avaliada.

`dwTimeout`\
[in] Especifica o tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use `INFINITE` para aguardar indefinidamente.

`pSymbolProvider`\
[in] O provedor de símbolo, expressado como uma [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface.

`pAddress`\
[in] O local atual de execução dentro de um método, expressado como uma [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

`pBinder`\
[in] O associador, expressado como uma [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface.

`bstrResultType`\
[in] O tipo de resultado deve ser convertido em. Esse argumento pode ser um valor nulo.

`ppResult`\
[out] Retorna o [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface que representa os resultados da avaliação.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O contexto de avaliação da expressão é determinado pela `pAddress`, que torna possível determinar o método de inclusão e, em seguida, o escopo do idioma de uso de regras para determinar o valor dos símbolos na expressão.

## <a name="see-also"></a>Consulte também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)