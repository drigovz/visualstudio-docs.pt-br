---
title: 'IDebugProgramProvider2:: GetProviderProgramNode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fa9f4db6aa71e9bba1f456b13ba52abd24ab966
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198722"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera o nó do programa para um programa específico.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `Flags`  
 no Uma combinação de sinalizadores da enumeração de [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Os seguintes sinalizadores são típicos para esta chamada:  
  
|Sinalizador|Descrição|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|O chamador está sendo executado no computador remoto.|  
|`PFLAG_DEBUGGEE`|O chamador está sendo depurado no momento (informações adicionais sobre marshaling serão retornadas para cada nó).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|O chamador foi anexado a, mas não foi iniciado pelo depurador.|  
  
 `pPort`  
 no A porta em que o processo de chamada está sendo executado.  
  
 `processId`  
 no Uma estrutura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que mantém a ID do processo que contém o programa em questão.  
  
 `guidEngine`  
 no GUID do mecanismo de depuração ao qual o programa está anexado (se houver).  
  
 `programId`  
 no ID do programa para o qual obter o nó do programa.  
  
 `ppProgramNode`  
 fora Um objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representa o nó de programa solicitado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
