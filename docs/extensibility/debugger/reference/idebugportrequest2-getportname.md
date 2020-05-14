---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724819"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Fica o nome do porto.

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

## <a name="parameters"></a>parâmetros
`pbstrPortName`\
[fora] Retorna o nome da porta.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A interface [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) geralmente é passada de um pacote de depuração (o cliente) para um fornecedor de porta (o servidor) para obter uma conexão com uma porta. Tanto o pacote de depuração quanto o fornecedor portuário estão cientes das possíveis opções para a porta. Se uma seqüência simples pode `IDebugPortRequest2::GetPortName` descrever a porta, então o método tem informações suficientes para fazer a conexão. Caso contrário, interfaces adicionais podem ser fornecidas pelo cliente, `IDebugPortRequest2::QueryInterface`que podem ser obtidas pelo servidor usando .

## <a name="see-also"></a>Confira também
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
