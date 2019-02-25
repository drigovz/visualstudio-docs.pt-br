---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8663e9e7d8c0428b362bbdbb099141ac86d01ee1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696786"
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

#### <a name="parameters"></a>Parâmetros
 `pbstrPortName`

 [out] Retorna o nome da porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interface é normalmente passado de um pacote de depuração (o cliente) para um fornecedor de porta (o servidor) para obter uma conexão a uma porta. O pacote de depuração e o fornecedor de porta estão cientes das possíveis opções para a porta. Se uma cadeia de caracteres simple pode descrever a porta, o `IDebugPortRequest2::GetPortName` método tem informações suficientes para fazer a conexão. Caso contrário, as interfaces adicionais podem ser fornecidos pelo cliente, que pode ser obtido usando o servidor `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Consulte também
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)