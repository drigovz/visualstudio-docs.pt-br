---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727189"
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

## <a name="parameters"></a>parâmetros
`ppParams`\
[fora] Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) representando a lista de parâmetros para o método; caso contrário, retorna um valor nulo se não houver parâmetros.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna S_OK ou retorna S_FALSE se não houver parâmetros. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento é um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) representando diferentes tipos de parâmetros. Ligue para o método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) em cada objeto para determinar exatamente que tipo de parâmetro o objeto representa.

 Um parâmetro inclui tanto seu nome variável quanto seu tipo. O primeiro parâmetro para um método de classe é tipicamente o ponteiro "isso".

 Se apenas os tipos de parâmetros forem necessários, chame o método [EnumArguments.](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

## <a name="see-also"></a>Confira também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
