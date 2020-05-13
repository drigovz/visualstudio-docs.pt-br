---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723403"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Este método adiciona um nó de programa para cada mecanismo de depuração (DE) especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>parâmetros
`guidLaunchingEngine`\
[em] O `GUID` de um DE que deve ser usado para lançar programas (e é assumido para adicionar seus próprios nós de programa).

`rgguidSpecificEngines`\
[em] Matriz `GUID`de s de DEs para os quais os nós do programa serão adicionados.

`celtSpecificEngines`\
[em] O número `GUID`de `rgguidSpecificEngines` s na matriz.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
- [Os Nós do Programa](../../../extensibility/debugger/program-nodes.md) serão adicionados `rgguidSpecificEngines`para cada DE listado — `guidLaunchingEngine`excluindo o mecanismo de lançamento (conforme dado em ), que é assumido para adicionar seu próprio nó de programa quando ele lança um programa.

## <a name="see-also"></a>Confira também
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nós de programa](../../../extensibility/debugger/program-nodes.md)
