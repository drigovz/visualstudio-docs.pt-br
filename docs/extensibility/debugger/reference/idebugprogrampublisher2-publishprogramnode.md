---
title: IDebugProgramPublisher2::PublishProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df68e72ee8597805bf02cb9c6e1c3a0bcaf8a449
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721673"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Disponibiliza um nó de programa para uso por mecanismos de depuração (DEs) e pelo gerenciador de depuração de sessão (SDM).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>parâmetros
`pProgramNode`\
[em] Um objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representa o nó do programa para disponibilizar.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método permite que os programas sejam consultados para obter informações antes de selecioná-los e lançá-los para depuração.

 Para remover um nó de programa da disponibilidade, ligue para o método [UnpublishProgramNode.](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)

## <a name="see-also"></a>Confira também
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
