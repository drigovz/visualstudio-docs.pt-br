---
title: IDebugStackFrame2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 424f8a8f51e714dab35f542974b6f25e5ecf3841
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457575"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Obtém uma descrição das propriedades de um quadro de pilha.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Parâmetros
 `ppDebugProp`\

 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que descreve as propriedades deste quadro de pilha.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chamar o [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método com os filtros apropriados pode recuperar as variáveis locais, parâmetros de método, registros e ponteiro "this" associado ao quadro de pilha.

## <a name="see-also"></a>Consulte também
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)