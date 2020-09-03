---
title: 'IDebugPortRequest2:: getportname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724819"
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
fora Retorna o nome da porta.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A interface [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) geralmente é passada de um pacote de depuração (o cliente) para um fornecedor de porta (o servidor) para obter uma conexão com uma porta. O pacote de depuração e o fornecedor de porta estão cientes das possíveis opções para a porta. Se uma cadeia de caracteres simples puder descrever a porta, o `IDebugPortRequest2::GetPortName` método terá informações suficientes para fazer a conexão. Caso contrário, interfaces adicionais podem ser fornecidas pelo cliente, que podem ser obtidas pelo servidor usando o `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Confira também
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
