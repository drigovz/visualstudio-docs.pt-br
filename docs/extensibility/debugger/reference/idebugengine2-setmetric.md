---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10e4662536dbe8fef8c250122d22520df1736cf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352572"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Esse método define um valor de registro, conhecido como uma métrica.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parâmetros
`pszMetric`\
[in] O nome da métrica.

`varValue`\
[in] Especifica o valor da métrica.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Uma métrica é um valor do registro usado para alterar o comportamento de um mecanismo de depuração ou para anunciar a funcionalidade com suporte. Esse método pode encaminhar a chamada para o formulário apropriado do [auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) função, `SetMetric`.

## <a name="see-also"></a>Consulte também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)