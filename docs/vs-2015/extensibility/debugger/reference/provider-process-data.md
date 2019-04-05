---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89192d814ccee3dd2a134807d8ce01880689d951
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924077"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa estrutura fornece informações sobre processos em execução em um computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Membros  
 Campos  
 Uma combinação de sinalizadores do [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) enumeração, que indica quais campos são preenchidos.  
  
 ProgramNodes  
 Um [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) estrutura que contém uma matriz de nós de programa.  
  
 fIsDebuggerPresent  
 Diferente de zero (`TRUE`) se o [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurador está em execução, zero (`FALSE`) se não for.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método onde ele é preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
