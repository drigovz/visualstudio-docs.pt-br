---
title: IDebugEngine2::Anexar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731209"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Anexa um mecanismo de depuração (DE) a um programa ou programa. Chamado pelo Session Debug Manager (SDM) quando o DE está em processo para o SDM.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>parâmetros
`pProgram`\
[em] Uma matriz de objetos [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representam programas a serem anexados. São programas portuários.

`rgpProgramNodes`\
[em] Uma matriz de objetos [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representam os nós do programa, um para cada programa. Os nós do programa nesta matriz representam `pProgram`os mesmos programas que em . Os nós do programa são dados para que o DE possa identificar os programas a que devem ser anexados.

`celtPrograms`\
[em] Número de programas e/ou nós `pProgram` `rgpProgramNodes` de programa nas matrizes.

`pCallback`\
[em] O objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) a ser usado para enviar eventos de depuração para o SDM.

`dwReason`\
[em] Um valor da [enumeração ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica a razão para anexar esses programas. Para obter mais informações, consulte a seção Comentários.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Há três razões para anexar a um programa, da seguinte forma:

- `ATTACH_REASON_LAUNCH`indica que o DE está anexando ao programa porque o usuário lançou o processo que o contém.

- `ATTACH_REASON_USER`indica que o usuário solicitou explicitamente que o DE anexasse a um programa (ou ao processo que contém um programa).

- `ATTACH_REASON_AUTO`indica que o DE está anexando a um programa específico porque já está depurando outros programas em um determinado processo. Isso também é chamado de auto-attach.

  Quando este método é chamado, o DE precisa enviar esses eventos em seqüência:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (se ele ainda não tiver sido enviado para uma instância específica do mecanismo de depuração)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Além disso, se o motivo `ATTACH_REASON_LAUNCH`da anexação for, o DE precisa enviar o evento [IDebugEntryPointEvent2.](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

   Uma vez que o DE receba o objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) correspondente ao programa que está sendo depurado, ele pode ser consultado para qualquer interface privada.

   Antes de chamar os métodos de um `pProgram` nó `rgpProgramNodes`de programa na matriz dada por `IDebugProgram2` ou , personificação, se necessário, deve ser habilitado na interface que representa o nó do programa. Normalmente, no entanto, este passo não é necessário. Para obter mais informações, consulte [Problemas de segurança](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
