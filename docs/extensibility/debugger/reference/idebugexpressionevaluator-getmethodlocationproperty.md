---
title: IDebugExpressionAtor::GetMethodLocationProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729524"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Este método converte um local de método e compensa em um endereço de memória.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>parâmetros
`upstrFullyQualifiedMethodPlusOffset`\
[em] A localização do método e deslocamento, expressa como uma string.

`pSymbolProvider`\
[em] O provedor de símbolos expressa como um objeto [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[em] Um endereço dentro do método, expresso como um objeto [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[em] O fichário expressa como um objeto [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
[fora] Retorna uma interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa o endereço de memória.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O endereço retornado pode ser usado para definir um ponto de ruptura, por exemplo.

 Apesar `upstrFullyQualifiedMethodPlusOffset`do nome, este parâmetro pode ser aprovado como um nome de método parcialmente qualificado. Nesse caso, o método selecionado é o `pAddress`que inclui . A forma como esse parâmetro é interpretado depende da implementação do avaliador de expressão e da linguagem que ele apoia.

## <a name="see-also"></a>Confira também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
