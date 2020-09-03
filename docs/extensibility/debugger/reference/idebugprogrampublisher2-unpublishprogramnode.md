---
title: 'IDebugProgramPublisher2:: UnpublishProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae2c3d9f3c9f6c500b10f580035312b2d045689a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721572"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
Remove um nó de programa especificado da disponibilidade para os mecanismos de depuração (DEs) e o Gerenciador de depuração de sessão (SDM).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT UnpublishProgramNode(
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int UnpublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parâmetros
`pProgramNode`\
no Um objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representa o nó do programa que está sendo removido.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Depois de removido, o nó do programa não estará mais disponível para ser consultado quanto às informações do programa.

 Para disponibilizar um nó de programa, chame o método [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) .

## <a name="see-also"></a>Confira também
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
