---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732076"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Move o ponteiro de leitura no fluxo de desmontagem um determinado número de instruções relativas a uma posição especificada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>parâmetros
`dwSeekStart`\
[em] Um valor da [enumeração SEEK_START](../../../extensibility/debugger/reference/seek-start.md) que especifica a posição relativa para iniciar o processo de busca.

`pCodeContext`\
[em] O objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) representando o contexto de código ao que a operação de busca é relativo. Este parâmetro é usado `dwSeekStart`  =  `SEEK_START_CODECONTEXT`apenas se; caso contrário, este parâmetro é ignorado e pode ser um valor nulo.

`uCodeLocationId`\
[em] O identificador de localização de código ao qual a operação de busca é relativo. Este parâmetro é `dwSeekStart`  =  `SEEK_START_CODELOCID`usado se; caso contrário, este parâmetro é ignorado e pode ser definido como 0. Consulte a seção Observações para o método [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) para obter uma descrição de um identificador de localização de código.

`iInstructions`\
[em] O número de instruções a mover `dwSeekStart`em relação à posição especificada em . Esse valor pode ser negativo para se mover para trás.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se a posição de busca foi a um ponto além da lista de instruções disponíveis. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Se a busca foi para uma posição antes do início da lista, a posição de leitura é definida para a primeira instrução da lista. Se a verificação foi para uma posição após o fim da lista, a posição de leitura será definida para a última instrução da lista.

## <a name="see-also"></a>Confira também
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
