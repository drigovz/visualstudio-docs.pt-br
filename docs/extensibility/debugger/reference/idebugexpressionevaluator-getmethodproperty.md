---
title: 'IDebugExpressionEvaluator:: getmethodproperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29a8e22301cbcd074c12d100d13601b57871a91a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930402"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Esse método obtém um objeto de propriedade que contém os locais, os argumentos e outras propriedades de um método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parâmetros
`pSymbolProvider`\
no O provedor de símbolos a ser usado, expresso como um objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
no O endereço no código, expresso como um objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , que deve ser resolvido para a função que a contém mais próxima.

`pBinder`\
no O associador a ser usado, expresso como um objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`fIncludeHiddenLocals`\
no Um valor diferente de zero ( `TRUE` ) significa incluir locais ocultos; zero ( `FALSE` ) significa deixar os locais ocultos

`ppProperty`\
fora Retorna um objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa o método.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Os locais ocultos são normalmente variáveis que são geradas pelo compilador.

## <a name="see-also"></a>Confira também
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
