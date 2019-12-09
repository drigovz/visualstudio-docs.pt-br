---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8017237af68b3dc414dc64bf6ae077387f0a600
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340379"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Obtém o nome da porta.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrPortName`\
[out] Retorna o nome da porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interface é normalmente passado de um pacote de depuração (o cliente) para um fornecedor de porta (o servidor) para obter uma conexão a uma porta. O pacote de depuração e o fornecedor de porta estão cientes das possíveis opções para a porta. Se uma cadeia de caracteres simple pode descrever a porta, o `IDebugPortRequest2::GetPortName` método tem informações suficientes para fazer a conexão. Caso contrário, as interfaces adicionais podem ser fornecidos pelo cliente, que pode ser obtido usando o servidor `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Consulte também
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)