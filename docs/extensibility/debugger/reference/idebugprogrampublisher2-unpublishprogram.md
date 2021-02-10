---
title: 'IDebugProgramPublisher2:: UnpublishProgram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3841ba0698c5e63bbf58e47e0e4a8b8f75d068e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961204"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Torna um programa indisponível para ser depurado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parâmetros
`pDebuggeeInterface`\
no Uma `IUnknown` interface para o programa. Esse é o mesmo valor fornecido para o método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) e identifica exclusivamente o programa que está sendo removido (ou seja, é usado como um cookie).

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Para disponibilizar um programa para os mecanismos de depuração e o Gerenciador de depuração de sessão, use o método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .

## <a name="see-also"></a>Consulte também
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
