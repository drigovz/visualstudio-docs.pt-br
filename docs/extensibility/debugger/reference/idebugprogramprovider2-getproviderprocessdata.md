---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721832"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera uma lista de programas em execução de um processo especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>parâmetros
`Flags`\
[em] Uma combinação de bandeiras da [enumeração PROVIDER_FLAGS.](../../../extensibility/debugger/reference/provider-flags.md) As seguintes bandeiras são típicas desta chamada:

|Sinalizador|Descrição|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|O interlocutor está rodando na máquina remota.|
|`PFLAG_DEBUGGEE`|O chamador está sendo depurado no momento (informações adicionais sobre marshalling serão devolvidas para cada nó).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|O chamador foi anexado, mas não lançado pelo depurador.|
|`PFLAG_GET_PROGRAM_NODES`|Quem ligou está pedindo que uma lista de nomes do programa seja devolvida.|

`pPort`\
[em] A porta em que o processo de chamada está sendo executado.

`processId`\
[em] Uma [estrutura AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que contém a ID do processo que contém o programa em questão.

`EngineFilter`\
[em] Uma matriz de GUIDs para motores de depuração atribuídos para depurar esse processo (estes serão usados para filtrar os programas que são realmente devolvidos com base no suporte dos motores fornecidos; se nenhum mecanismo for especificado, todos os programas serão devolvidos).

`pProcess`\
[fora] Uma [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estrutura que é preenchida com as informações solicitadas.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é normalmente chamado por um processo para obter uma lista de programas em execução nesse processo. As informações retornadas são uma lista de objetos [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>Confira também
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
