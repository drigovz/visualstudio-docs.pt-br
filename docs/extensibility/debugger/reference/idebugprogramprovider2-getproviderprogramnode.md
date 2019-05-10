---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 594fef8a83c01b4bad4d47fdb206d64e445ad515
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459024"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Recupera o nó de programa para um programa específico.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Parâmetros
 `Flags`\

 [in] Uma combinação de sinalizadores do [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumeração. Os sinalizadores a seguir são típicos para essa chamada:

|Sinalizador|Descrição|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Chamador está em execução no computador remoto.|
|`PFLAG_DEBUGGEE`|Chamador está atualmente em depuração (informações adicionais sobre a realização de marshaling serão retornadas para cada nó).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chamador foi anexado ao, mas não é iniciado pelo depurador.|

 `pPort`\

 [in] A porta que o processo de chamada está em execução.

 `processId`\

 [in] Uma [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que contém a ID do processo que contém o programa em questão.

 `guidEngine`\

 [in] GUID do mecanismo de depuração que o programa é anexado ao (se houver).

 `programId`\

 [in] ID do programa para o qual obter o nó do programa.

 `ppProgramNode`\

 [out] Uma [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa o nó de programa solicitado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)