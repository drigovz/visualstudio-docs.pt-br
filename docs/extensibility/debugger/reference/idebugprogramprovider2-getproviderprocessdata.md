---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc0884597454cf50cb5540d61b865dfe7686c25f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203773"
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

## <a name="parameters"></a>Parâmetros
`Flags`\
[in] Uma combinação de sinalizadores do [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumeração. Os sinalizadores a seguir são típicos para essa chamada:

|Sinalizador|Descrição|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Chamador está em execução no computador remoto.|
|`PFLAG_DEBUGGEE`|Chamador está atualmente em depuração (informações adicionais sobre a realização de marshaling serão retornadas para cada nó).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chamador foi anexado ao, mas não é iniciado pelo depurador.|
|`PFLAG_GET_PROGRAM_NODES`|Chamador está pedindo para obter uma lista de nós de programa a ser retornado.|

`pPort`\
[in] A porta que o processo de chamada está em execução.

`processId`\
[in] Uma [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que contém a ID do processo que contém o programa em questão.

`EngineFilter`\
[in] Uma matriz de GUIDs para os mecanismos de depuração atribuídos para depurar esse processo (eles serão usados para filtrar os programas que são retornados, na verdade, com base no que o suportam os mecanismos fornecidos; se não há mecanismos forem especificados, em seguida, serão retornados todos os programas).

`pProcess`\
[out] Um [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estrutura será preenchida com as informações solicitadas.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, esse método é chamado por um processo para obter uma lista de programas em execução nesse processo. As informações retornadas são uma lista dos [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos.

## <a name="see-also"></a>Consulte também
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)