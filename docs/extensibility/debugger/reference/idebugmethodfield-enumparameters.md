---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d455d380f66689cd2245070a7ef0bf9290a2455
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324216"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Cria um enumerador para os parâmetros do método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parâmetros
`ppParams`\
[out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de parâmetros para o método; caso contrário, retornará um valor nulo se não houver nenhum parâmetro.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum parâmetro. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento é um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa os diferentes tipos de parâmetros. Chame o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em cada objeto para determinar exatamente quais tipos de parâmetro que o objeto representa.

 Um parâmetro inclui seu nome de variável e seu tipo. O primeiro parâmetro para um método de classe normalmente é o ponteiro "this".

 Se apenas os tipos dos parâmetros for necessário, chame o [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)