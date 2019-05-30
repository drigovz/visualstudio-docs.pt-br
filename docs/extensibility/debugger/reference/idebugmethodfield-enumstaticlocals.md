---
title: IDebugMethodField::EnumStaticLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 006f1975c18aa7464531654d9b71fd857953afc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324250"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Cria um enumerador para variáveis locais estáticas do método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parâmetros
`ppLocals`\
[out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de variáveis locais estáticas. Retorna um valor nulo se não houver nenhum estáticos locais.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum estáticos locais. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento é um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa os diferentes tipos de variáveis locais estáticas. Chame o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em cada objeto para determinar exatamente quais tipos de local estático que o objeto representa.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)